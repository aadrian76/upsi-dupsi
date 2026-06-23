<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>
  
  [[_TOC_]]
</details>

## 📝 Changelog

<br>

| Author                            | Modification Date       | Changes                                       |
|-----------------------------------|-------------------------|-----------------------------------------------|
|                 | 25/02/2025              | First Version Created                         |


# Workload Scanner 🛠️

Is a service which gathers much of the metadata about cloud workloads, Wiz leverages this data to perform many enrichments that lead to different types of findings that include findings, like vulnerabilities and secrets.

## Workload Scanner Overview 🔍



Scanners extract data from the environment, analyze it, and save the insights to the Explorer and Reports pages. The Workload Scanner is responsible for scanning cloud workloads, such as VM disks and serverless functions.

First we have to remember the high level data flow:

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Fagentless-scanning-1e0298c-SaaS_Deployment_Diagram_-_updated_-_System_Architecture.jpeg&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">A diagram showing the SaaS deployment model of Wiz.</div>
</div>


**1. Cloud Scanner (API)** 
   
   The Wiz Cloud fetcher is gonna run and make all the required API calls to pull the cloud resources and infrastructure data into the portal.
Once the fetcher completes, we see the cloud resources in the environment, their basic configurations and their raw json

**2. Enrichers**
   
   Once the fetcher completes the graph enrichers start to run, they are gonna go over all the data that the fetcher brought back into Wiz, it's going to enumerate all the different configuration. It's gonna make the data go through a process of graph enrichment to calculate the effective meaning behind configurations.

   During this stage the IAM principles are marked for high and admin privileges, cloud resources are marked for internet accessibility, and the full access path from the internet, or look the effective IAM bindings of who can access what resources that appear on the graph.

**3. Workload Scanning**

   Also referred as Disk Scanning (snapshots) or perhaps clone permissions, depending on the CSP.
   Wiz creates snapshots, then they scan them to determine:

   *   List of installed packages + versions
   *   List of programming languages libraries + versions
   *   Local users
   *   Authentication configuration
   *   Operating system info
   *   Hashes of all files
   *   CIS benchmarks output
   *   Secret metadata (without the sensitive info)
   *   Data classifier metadata (without the sensitive info)
   *   Deployed Git repositories
   *   Deployed containers
   *   For Windows machines: installed programs, services, and installed KBs
   *   Specific logs and artifacts from the VM disks

After these 3 stages, all the resources and all the findings are now on the graph.  

**4. Controls**
     
   The controls are just queries, plus the severity that runs against the database looking for issues. So in the moment all these three stages have completed, all that information is on the security graph, and then the controls are going to run automatically to collect all those resources that are reflected in attacker playbooks.

   So, Wiz looks for those type of patterns, at the control stage, we can now if a resource have exposure, and vulnerability and impact on the graph, so its possible to perform the final contextual analysis and generate context-based findings or issues and populate them in the portal.


## Wiz Workload Scanning Architecture 🏗️

Let's take a deeper look on the Workload Scanner:

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/YgGzmX6.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Wiz Workload Scanning Diagram</div>
</div>

<br>

What you see on the image is the Wiz back-end, that's running somewhere in AWS, this is were Wiz does all the enrichment, where the graph and the other databases land and the portal and so on.

We can also see a regional cloud within that region we gonna see two tenants.
- The customer tenant that Wiz want to connect via the deployment
- Regional Wiz tenant that is the home for the workload scanner and that's within that same region.

The disk analysis account its basically sitting right next door to the customer account, it's in the same cloud, same region, workload scans are always performed on the in the same region to avoid any sort of data sovereignty issues, it also improves performance and scaling.

### Step by step: 🔄

🥇 **Step 1:**

As part of the connector deployment, Wiz create that trust between the Wiz backend and the customer cloud environment (Wiz Read-only role/app/service account depending on the CSP). Something that give Wiz permission to operate inside the customer account. This read-only role defines the permission that Wiz uses to read those specific services. The role ensures very granular control with least privilege access.

Sometimes the cloud changes their permissions and Wiz no longer has the access that it did prior to that change. So a new connector needs to be rolled out.
Now once this is established, this trust is established, the Wiz backend is going to assume that trusted role in the customer tenant, and again that's going to happen on a scheduled basis, usually once per day.

🥈 **Step 2:**

Wiz is going to fecth all those supported objects as their configurations.
They're going to just get a list of all of the objects and save that to the graph database.

The Wiz backend assumes that role to perform the API calls that fetches that specific data from the environment, again every 24 hours or so, the backend triggers that cloud scanner to scan the connected environment and extract the metadata about it. And this data is going to include things like networking, identity, cloud configurations of all the objects in that environment, and again these results are published back to the Wiz backend

🥉 **Step 3:**

The Wiz backend sends the list of volume IDs to the workload scanner. The workload scanner runs in a dedicated account, which is Wiz disk analysis account, and that's got clusters in, again, every cloud and every region where the customer has a workload.

Specifically for workload scanning, Wiz is interested in getting the volume IDs of the OS disks attached to any VMs, Also, they're getting containers and serverless functions. T 

🏅 **Step 4:**

The workload scanning process is pretty simple at a high level, Wiz is going to assume another role in the customer account that has the permissions to create the snapshots, share the snapshots with the scanning cluster and then delete the snapshots when the scan is completed.

🎖️ **Step 5:**

Wiz gets a volume ID for a VM, then its going to create that snapshot of the volume ID, which again is a snapshot in time of that VM's boot volume. The customer account is going to share that snapshot with the Wiz account and then the workload scanner cluster performs the scan. But it's important to note here that we never actually copy the snapshot. 

It's called zero copy. Then Wiz mount a disk using the snapshot, create it on the customer side, they use a zero copy because it's cheaper, provides better accuracy, is more secure and takes less time than a full copy.

🏆 **Step 6:**

These snapshots are created and shared to the Wiz Workload Scanner with a tag called Wiz auto gen snapshot. So that's going to help to identify them when Wiz is doing the cleanup.

🎯 **Step 7:**

Once the workload scanner has completed, the findings are passed to the Wiz backend. There's no data passed, like no actual customer data is passed, out of the scanner account. It's just metadata on the scan results

🛑 **Step 8:**

Around the same time the Wiz account is gonna do the cleanup. It's just going to dele the snapshots that were tagged by Wiz.

🖼️  AWS Workload Scan Cycle:

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/fJcLpAF.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">AWS Workload Scan Diagram</div>
</div>


GCP Workload Scan Cycle

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/WyuWFIZ.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">GCP Workload Scan Diagram</div>
</div>
<br>

🔷 Azure Workload Scan Cycle: Managed App Conector

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/5AABiwX.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Azure Workload Scan Diagram</div>
</div>

### Serverless and Container Workload Scanning 🐳

**Serverless** 🛸

1. Using the Cloud COnnector scan, retrieve list of serverless functions
2. The files are pulled via the APIs
3. Scanned via the serverless disk scanner

**Container from Disk** 📦

1. During the disk scan of VMs/nodes, scanner gets a list of running containers on the disk
2. Containers are mounted in the disk scanner and analyzed
3. Serverless container scanning (Using a registry connector)

**Container from Registry** 🗂️

1. Periodically pull images from registry
2. Images are mounted in the disk scanner and analyzed
3. Mapped back to running instances

## Workload Scanner Tuning 🔧

Tuning: Settings > Scanners > Workload Scanner

Adjust what is scanned, how, and intervals, including the following settings:

- Share CMKs for AWS
Non-OS Disks
AWS LightSail
Eve

