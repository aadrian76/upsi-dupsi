
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


<br>


# 🛠️ Wiz Architecture and Standard Deployments 

### Terms and Abbreviations

The following terms relate to the Wiz architecture.
*   **Agentless scanning**. Technique used to discover and evaluate full stack technologies for risk without agents.
*   **Cloud Scanner**. Identifies all API retrievable technologies for all connected clouds. Refreshes every 24 hours.
*   **Workload\Disk Scanner**. Identifies client and server applications running on the OS partition of a workload.
*   **Event-triggered scanning**. Based on key cloud events, typically, create, delete, update, for specific cloud resources, Wiz rescans via cloud and workload scanners those specific events in between regular full-cloud refresh scans.

# Wiz Architecture Overview 🏗️

### Key Concepts 🔑

- Eventual consistency: Prioritizes performance and availability over immediate data consistency.
- Asynchronous: Breaking the application into independent components using a microservice containerized architecture to scale process in parallel
- Resiliency: Ensures high availability and fault tolerance.

## System Architecture: 🖥️

Here we will be seeing the Wiz's Standard Deployment Model SaaS.

Wiz's standard deployment model is entirely Software-as-a-Service (SaaS), but there are several optional components that are not purely SaaS:


*   Wiz Outpost—Performs all workload scanning in the own environment using the own infrastructure of the client. (We will get this into more detail later)
*   Runtime Sensor—Cloud-native detection and response eBPF-based executable that offers real-time visibility into your cloud and Kubernetes workloads.
*   Wiz CLI—A command line version of the Wiz detection engine that can detect IaC misconfigurations, vulnerabilities, sensitive data, secrets, host misconfigurations, and more both locally and as part of your CI/CD pipeline.
*   Wiz Admission Controller—Enforce security policies in your Kubernetes clusters, preventing resources from being deployed or modified if they would violate pre-defined polices.
*   Wiz Broker—A lightweight reverse proxy that is used to provide secure connectivity between the Wiz backend and isolated resources and environments.


> All communications between Wiz and our cloud estate are encrypted using TLS 1.2 (or higher)

* * *

## Deployment and modules 🚀

Wiz is an agentless cloud security service (SaaS) that uses API connectors to scan your cloud estate, code repositories, container registries, etc. Wiz does not require the installation of any endpoint agents, does not sniff network traffic, and does not perform active scans in the network.

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Fsystem-architecture-2019e333bc35250151fb4d82c29f9a00d9f2580652772b742a5cbf24c78a612d-System_Architecture__Deployment_and_modules_V1.1_9.png&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">A diagram of functional blocks and modules in Wiz</div>
</div>

The fully agentless deployment model can be adjusted and supplemented in several ways:
*   SaaS Deployment (Standard)
*   Wiz Outpost moves the workload scanner (only) out of the Wiz backend and into your environment.

Optional Deployments that add different functionalities, depending on the deployment option. These Deployments run in your cloud on your workloads.
*  **Kubernetes deployments:** Connect, deploy and install everything necessary to scan and protect Kubernetes clusters.
*  **Remediation & Response:** Fix misconfigurations and respond to potential threats manually or automatically [right now on preview]
*  **Runtime Sensor:** Deploy to workloads to enable real-time threat detection, vulnerability validation and more.
*  **Secure Auto-remediation:** Remediate misconfigurations using your own infrastructure and permissions
*  **Wiz Admission Controller:** Audit or block potentially unsafe changes to k8s clusters via centrally managed policies.
*  **Wiz Broker:** Install a lightweight reverse proxy to connect the Wiz backend to isolated resources and environments
*  **Wiz CLI:** Scan for secrets, misconfigurations, etc. locally or in CI/CD pipelines
*  **IDE Extension:** Integrate Wiz with your IDE to scan code and container images locally

### Configuration scanning 🔍

Wiz uses cloud service providers' APIs to extract relevant information about the control plane of your cloud environments and Kubernetes services.

#### Cloud Platform ☁️

To scan cloud configurations, Wiz connects through API connectors to supported cloud platforms as well as their managed Kubernetes environments, e.g. Elastic Kubernetes Service (Amazon EKS), Azure Kubernetes Service (AKS), Google Kubernetes Engine (GKE). These connectors allow Wiz to scan for misconfigurations for all the aspects of your cloud environment including:
*   Compute—Virtual machines, autoscaling groups, containers, serverless functions.
*   Storage—Databases, elastic storage, buckets/blobs, elasticCache, and more.
*   Network—Subnets, routing tables, VPCs, gateways, ELB/ALB.
*   Identity and access management—Effective permissions and their usage for users, groups, service accounts, roles. 
*   Keys & secrets—Secret storage and management.
*   Logs—AWS Cloudtrail, Azure Search, and Google Logging.
*   Clusters—EKS, AKS, GKE, ECS, OKE, etc.

#### Kubernetes services ☸️

Wiz scans managed Kubernetes services through connectors. In Azure and GCP, the cloud platform permissions enable automatic onboarding of the AKS and GKE clusters. In AWS, there is an additional step required to onboard EKS environments.

Wiz can also scan self-managed Kubernetes clusters. They simply require separate onboarding because there is no underlying cloud connector.

Once connected, Wiz leverages read-only APIs to read the configuration of the cluster, similar to the operation of the Cloud Connector. Wiz scans the identities, permissions, network configuration, and container-related configurations on the Kubernetes clusters allowing for one consolidated and normalized view through the Wiz portal.



### Workload and data scanning (SaaS) 🔬

Wiz Cloud scans your cloud agentless to extract raw metadata required for risk assessment. This approach offers a wide variety of benefits compared to legacy tools:
*   Least privilege—You do not need to grant Wiz administrative permissions
*   Ease of setup—New Connectors take only a few minutes to create
*   Ease of maintenance—New permissions can be added to existing Connectors to support new features
*   No blindspots—New workloads are automatically detected and scanned
*   Scalability & reliability—The cloud providers' own APIs and services are used to perform all scans
*   Minimal performance impact—Workloads do not need to dedicate their CPU, memory, or other computing resources to scanning themselves

* * *

## Wiz high level dataflow: 📈

**Phase 1: Connect to the cloud.**

The Cloud Scanner connects using read-only permissions to your cloud APIs (AWS, Azure, GCP, OCI, Kubernetes, etc.) in order to list your cloud resources and interrogate the control plane for their configuration.

**Phase 2: Workload Scanning**

Agentless scanning is the new way to perform workload scanning. Instead of using an agent, Wiz leverages cloud-native tools to perform scans without interrupting or impacting production workloads. Agentless scanning achieves deep analysis of the workload without any impact or interruption to the live workload.


<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Fagentless-scanning-1e0298c-SaaS_Deployment_Diagram_-_updated_-_System_Architecture.jpeg&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">A diagram showing the SaaS deployment model of Wiz.</div>
</div>


**Phase 3: Enrichment phase**

Wiz does a deeper analysis above all the collected data, this is done by the analysis engine, which is composed of multiple modules that enables Wiz to create a full-stack view of the environment from code to cloud.

Some examples are:

- [Control engine](https://docs.wiz.io/docs/system-architecture#control-engine)

  Wiz runs analytics on top of the graph to detect exploitable attack vectors and weak points. The Wiz control engine also enables customers to compose and run custom queries on top of the graph, to further customize and build a customer-specific experience.

- [Data analyzer](https://docs.wiz.io/docs/system-architecture#data-analyzer)

  Wiz samples and analyzes data in resources in order to detect sensitive data (PII/PCI/PHI) and secrets. These data findings are correlated with all other risk factors like exposure, vulnerabilities, or data lineage to provide a full risk assessment of your data assets. This analyzer is enabled by default only for public buckets. You can opt in to scan private buckets, cloud-managed database, and disks.

- [Enrichment and parsing](https://docs.wiz.io/docs/system-architecture#enrichment-and-parsing) 

  Wiz automatically parses and maps external scan results, layering them on top of the graph for additional enrichment.

- ### [Identity analyzer](https://docs.wiz.io/docs/system-architecture#identity-analyzer)

  The Wiz identity analyzer identifies and protects your identities and permissions in the cloud. The Wiz identity analyzer analyzes which permissions are granted to assets and which permissions are in use with a unique set of graph algorithms.  Wiz discovers risky lateral movement paths, marks unused identities and permissions, and highlights high privileged roles.

- [Image analyzer](https://docs.wiz.io/docs/system-architecture#image-analyzer)

  The Wiz image analyzer module intakes the Wiz image scans and assesses the VMs and containers loaded in your environment, scanning for high-risk vulnerabilities. Using these continuous assessments, the image analyzer creates a complete tech stack map of the applications and hosted technologies running on top of it, third parties, and custom (homegrown) apps allowing for unparalleled visibility. 

-  [Malware analyzer](https://docs.wiz.io/docs/system-architecture#malware-analyzer)

   The Wiz malware analyzer identifies generative malware using a set of YARA Rules which are written and maintained by the Wiz Research Team. The malware analyzer is a Wiz propriety engine, and is used in addition to threat intel from ReversingLabs that is used to detect hash-based malware. All malware findings are correlated with other risk factors to provide a full risk assessment of your infected resources.

- [Network analyzer](https://docs.wiz.io/docs/system-architecture#network-analyzer)

   Wiz network analyzer identifies your public-facing resources (VMs, containers, DB servers, and more) and the effective exposure of each resource. Wiz uses complex graph and network algorithms to find not only directly exposed resources but also the full exposure path.

-  [Secret analyzer](https://docs.wiz.io/docs/system-architecture#secret-analyzer)

   Wiz analyzes the scanned system volumes to detect exposed secrets like cloud platform access keys, domain certificates, SSH keys, and more. These secrets when not managed correctly expose you to a variety of attacks and data leakage. Wiz alerts on these secrets bringing to light the risk they pose allowing you to remove the secrets and manage them.

**Phase 4: Refine**

Wiz validates what has been collected from Phase 2 and 3, using that data Wiz tune their view of what is happening on the cloud at resource level. It's a series of independent validations to reduce false positives

**Phase 5: Analyze and prioritize**

Al the data is analyzed and check where **toxic combination exists** and prioritize the list of resulting issues.

[Graph database and relational enrichment](https://docs.wiz.io/docs/system-architecture#graph-database-and-relational-enrichment)

 Wiz maintains a graph database to provide visibility and control capabilities across your cloud environments. The graph stores the data collected from the cloud and Kubernetes API connectors, as well as the findings identified by [Cloud Service Provider](https://docs.wiz.io/docs/csp-scanner-sources-settings) and [third-party ↗](https://www.wiz.io/integrations/apply) scanners. The graph is continuously updated with every new scan of your cloud environment.

Wiz leverages the graph by running different analytical modules that enrich the entities with additional risk factors and insights. After enrichment, the graph allows finding all the risk correlations by traversing connected components and by running built-in and custom rules to surface security issues in your environment.


## Deployments 🛠️

Before beginning to understand a deployment, first we need to understand the components that make it possible:

### Connectors: 🔗

Wiz must be connected to your cloud estate in order to perform agentless risk assessments of cloud resources, container registries, and more.

- Registry Connectors: Identify vulnerabilities in container images at-rest in registries
- Version Control Connectors: Identify risks like exposed secrets and vulnerabilities in code stored GitHub and other VCs.
- SaaS Connectors: Grant read-only access to third-party SaaS tools to enable agentless risk correlation and prioritization
- Cloud Connectors: Grant read-only access to your cloud estate to enable agetnless risk correlation and prioritization

#### Cloud Connectors 📡

This are the core scanning operation in Wiz. They identify the cloud resources, the metadata and determine which resources pass to the workload scanner.

Wiz has connectors to all the major Cloud Service Providers and others, for example:

- Amazon Web Services
- Microsoft Azure
- Google Cloud Platform
- Alibaba Cloud
- Oracle Cloud Infrastructure
- VMware vSphere
- Linode Cloud

In order to understand the wiz structure, we have to know the Aligning Terms used by Wiz:

| Wiz Resource Type         | AWS               | Azure                                                        | GCP                                 |
|---------------------------|--------------------|---------------------------------------------------------------|--------------------------------------|
| Cloud Organization        | Organization       | Root management group (AAD Tenant) / Management Group        | Organization, Workspace Org.         |
| *Also Cloud Organization* | Organization Unit  | Org. Management Group                                         | Folder (nesting)                     |
| Subscriptions             | Account            | Subscription                                                  | Project                              |
| Resource Group            |                    | Resource Groups                                               |                                      |
| (Workloads)               | Resources          | Resources                                                     | Resources                            |


But to have the connectors up and running we have to bear in mind some considerations:

- **Global dependencies:**
   
  What are the global settings that matter to ensure we get de visibility and connectivity that we need.
We have to bear in mind things like how we access to the cloud. 

  Do it has a specific URL or IP addresses or accounts IDs that are required in order to connect?

- **Scope**

   What are the different levels of scope that a connector can operate at. It's important to understand to avoid leaving blind spots.
When we connect to Wiz we can select what level in our cloud organization we are going to connect.

  The implication of this selection is a critical decission:

  - Cloud organization-level connectors (Generally recommended)
     
     Top level connections to ensure automatic discovery and any sub organization or subscription that belongs to an organization. It ensures if a new subscription is added its automatically detected by Wiz.


  - Subscription-level connectors (often used in POV)

    Focuses on a low level structure or a single account its often used to logically partition resources in a organization serving as security or resource or data isolation


   Why it matters?

  - Prevent visibility gaps as new accounts are onboarded
  - Insights into org and account structure config and resources
  - Single place upgrade or convert
 


- **Permissions**

   What permissions are required by the different CSPs

   In AWS the standard SaaS connector creates a single role, the WizAccessRole and adds to built-in policies: 
    - ViewOnlyAccess 
    - SecurityAudit

   The same role has either one or two custom policies from Wiz. There's a Wiz full policy. That's gping to be required to enable the cloud fetcher and the OS or non-OS volume scans. We can read all the cloud services and workloads. We can create share and delete a snapshot.

  There's also the Wiz Data Scanning Policy which enables the sensitive data scants and it¡s added if de DSPM features are added to the connector.

- **Connection process**  

  How we actually connect.

  When we deploy to AWS what we are really doing is defining a role in AWS that Wiz can assume. The last part of the connection is gonna tell wiz what to connect to and use for the first scan.
  
  Deployment steps:

  - Define scope of connector: organization or account.

  - Create the WizAccess-Role.

  - Attach policies to the Wiz role in AWS 

  -  Configure WizAccess-Role trust policy to allow WIz Scanner to assume role

  - Input WizAccess-Role ARN into Wiz portal


  These steps can be done manually, but Wiz offers the CloudFormation script which will set up the role and the necessary permissions.
  
- **System Health > Deployments**

  Identifies issues with deployments (connectors) that restrict visibility, failures to connect or other permission issues that prevent scanning.

  Why it matters?
  - Understand blind spots
  - Ignore with confidence
  - Full deployment coverage


How we do ensure that everything went smoothly?

By looking the System Health issues, thats gonna demonstrate risks that impact Wiz Deployments according to their severity, source and deployment type:


<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/QEDerpY.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">List of Cloud Connectors on Wiz</div>
</div>


It's easy to assess the health of a connector by looking the number and severity of issues that it has.

As well as expand and have a clear picture of the issue and remediation guidance:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/49LYVwl.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Health Issues of the Connector</div>
</div>

<br>

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/YQ8sQGL.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Health Issue Overview</div>
</div>

- **Replacing Deprecated Connectors**
   
  1. Process today is to "recreate" the connector using the latest scripts

  2. Wait 24 houts and then disable the old one

  3. Wait 7 days and then delete the old one

# Wiz Outpost Architecture and Deployment

Using its standard SaaS deployment model, Wiz gathers information from your cloud environment using two fundamentally different modules:
*   Cloud Scanner—Cloud Service Provider (CSP) APIs are used directly to extract metadata such as VM names, tags, and statuses; networking rules; and security groups.
*   Workload Scanner—Snapshots or disk clones of VM volumes are created, scanned, and then deleted. From these, Wiz gathers information about installed packages, exposed secrets, malware, etc.

Using the Outpost deployment model, all Workload Scanner functionality is pulled out of the Wiz backend and recreated in your own environment. Snapshots/disk clones are still created, scanned, and deleted in the same manner, but all analysis occurs in your environment. Only the results—metadata including installed packages, exposed secrets, malware, etc.—are sent to the Wiz backend.
Performing all workload scans in your own environment using your own infrastructure ensures that Wiz never has direct access to VM volumes, which satisfies many regulatory requirements regarding data residency and access.

## SaaS vs Outpost: 🔄

|     |   SaaS | Outpost |     
| --- | --- |--- |
| **Data Access** | Wiz infrastructure scans snapshots/disk clones; only metadata is stored | Customer infrastructure scans snapshots/disk clones; Wiz receives and stores only metadata |
| **Deployment** | Super simple | A bit more complex: requires a dedicated account and provisioning of multiple resources. See [below](https://docs.wiz.io/docs/wiz-outpost?lng=en#deployment). |
| **Workload scanning costs** | Negligible | The customer pays the CSP to maintain and operate the workload scanning infrastructure. See [below](https://docs.wiz.io/docs/wiz-outpost?lng=en#pricing-considerations). |

## Outposts Overview 🌐

What is Wiz Outposts?

Is an alternative deployment model to the standard SaaS deployment model. It allows customers to perform all workload scanning in their environment.

Some of the main points when describing outposts:

- **Data stays within customer's cloud** - Only metadata is sent including vulnerabilities, tech stack, config issues 

- **Fully managed solution** - Cluster management and monitoring by Wiz

- **Multi-account support** - scalability, management and isolation capabilities.


### Difference between SaaS Scanning and Outpost Scanning: ⚖️

SaaS Scanning:
Using its standard [SaaS deployment model](https://docs.wiz.io/docs/agentless-scanning), Wiz gathers information from your cloud environment using two fundamentally different modules:


<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/tI195Oc.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">SaaS Scanning Diagram</div>
</div>


*   Cloud Scanner—Cloud Service Provider (CSP) APIs are used directly to extract metadata such as VM names, tags, and statuses; networking rules; and security groups.
*   Workload Scanner—Snapshots or disk clones of VM volumes are created, scanned, and then deleted. From these, Wiz gathers information about installed packages, exposed secrets, malware, etc.

Outposts Scanning:

Using the Outpost deployment model, all Workload Scanner functionality is pulled out of the Wiz backend and recreated in your own environment. Snapshots/disk clones are still created, scanned, and deleted in the same manner, but all analysis occurs in your environment. Only the results—metadata including installed packages, exposed secrets, malware, etc.—are sent to the Wiz backend.

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/Xn2BeaI.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Outpost Scanning Diagram</div>
</div>


On the SaaS, the Wiz Scanner Account is a trusted Wiz Account that exists in the client CSP and not in the Customer Environment.
Meanwhile in Outposts scanning, the main difference is that the data on Outposts Scans **NEVER** leaves the Customer Environment.

**Resources scanned by Outposts**

- OS disks
- Containers
- PaaS Databases
- Data Disks
- Container Registries
- Private and non-internet facing resources
- Serverless Functions
- Storage buckets


**Outposts use cases:**

- Customers in highly regulated industries where data can not leave their environment

- Customers that want to scan resources with no direct internet access

- Certain Sovereign clouds require Outposts to be fully scanned

### **Different types of Outposts** 🗃️

- **Wiz Outposts**

  The preferred method.

  - Fully automated deployment of all resources.

  - Customer is only responsible for running the script/terraform provided by Wiz
  
  - This is the best method for most customers.

- **Wiz Self-Managed Network Outpost (BYON)**

  Required for specific scenarios.

  - Customer is responsible for the creation and maintenance of network components.

  - Can be used to scan private container registries and private resources in customer environments.

- **Wiz Self-Managed Network Outpost**

  Rarely ever required

  - Customer is responsible for deployment and maintenance of every component associated with the Outpost.

  - Very complex with increased responsibility for the customer to deploy and maintain Outpost.
  
### **Pros and Cons of Outposts:** ➕➖

**Pros**

- Customer infrastructure scans workloads; Wiz receives and stores only metadata.
- Customer has more control over account that hosts the disk scanning infrastructure.
- The Outpost is fully managed by Wiz – minimal maintenance [hardening, secret rotation] is required from the customer side.

**Cons**

- Deployment requires a dedicated account where Wiz provisions multiple resources within the dedicated Outpost account.
- The customer becomes responsible for ensuring that the infrastructure is up and running.
- Additional cost to provide + support the workload scanning infrastructure needed by Wiz to perform disk scanning.

### Basic components of all Outposts. 🧩
- State Bucket: This is a critical component, it holds charts for Workloads running on a K8s cluster.

  - AWS - S3 Bucket.
  - Azure - Storage Account w/Blob
  - GCP - Google Cloud Storage Bucket

 - Principals: Enable build/manage k8s and to perform scanning

   - AWS - IAM Roles

   - Azure - Roles assigned to enterprise applications

   - GCP - Roles assigned to Wiz managed service account

- Message Querue: Revieves volumeIDs, passes them to k8s for scanning.

   - AWS - Simple QUeue Service

   - Azure Service Bus

   - GCP - Pub/Sub

- K8s Cluster: Where disk scanning takes place:

   - AWS - Elastic Kubernetes Services (EKS)
   - Azure - Azure Kubernetes Service (AKS)
   - GCP Google Kubernetes Engine (GKE)

- Secrets: Enable secure access to prinicpals

   -  AWS - KMS Keys stored in AWS Secrets Manager
   -  Azure - Secrets stored in AzureKeyVault
   -  GCP - Keys stored in Google Cloud Secrets Manager

Outpost Architecture: Permission Scopes: 🛂

- Read Only: Role associated with the connector, s the connector is able to perform read-only API callson cloud resources during the initial connector fetch.
   - AWS - IAM Wiz Access Role
   - Azure - Wiz Enterprise App
   - GCP - Wiz Service Account (SA) 

- Orchestrator: Provisions and creates scanning resources required for the Outpost to perform workload scanning in the customer`s account
   - AWS - IAM Wiz Orchestrator Role
   - Azure - Role assigned to Wiz Orchestrator app
   - GCP - Roles assigned to Wiz Orchestrator SA

- Worker: Manages workload scanning infrastructure and performs scaling up/down of k8s components
   - AWS - IAM Wiz Orchestrator EKS Role and Wiz Orchestrator Node Pool roles
   - Azure - Roles assigned to Wiz Worker app
   - GCP - Roles assigned to Wiz Orch + Worker SA

- Scanner: Enables workload scanning (snapshotting/cloning of volumes) and ensures that the workload resources et passed to the k8s clusters for analysis.

   - AWS - IAM Wiz Scanner Role
   - Azure - Roles assigned to Wiz Scanner app
   - GCP - Roles assigned to Wiz Worker SA

**Outpost Scan Flow** 🌀

Steps:

1. Volumes IDs are sent via a queue
2. K8s cluster assumes scanner role
3. Snapshots are created and shared
4. Snapshots are scanned, then deleted
5. Scan results /metadata) are sent to Wiz




