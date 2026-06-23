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
 
## Technologies Inventory 📋

The [Inventory > Technologies ↗](https://app.wiz.io/inventory/technologies) page presents a categorized view of all technologies, cloud resources, and cloud services detected across all connected cloud environments and container registries. You can search for technologies, identify workloads or Projects running technologies, review and classify technologies, and more.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/TpLj6kf.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Technologies Inventory</div>
</div>
<br>


The technologies page lists all technologies that were identified in your cloud environment along with counts of how many resources were discovered, whether they're approved technologies or not, and what type they are, like a cloud service offering versus a code library or perhaps a server application.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/p0N2cnB.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Types of Data an the Service related</div>
</div>
<br>

With Wiz you get full detection of cloud services with deep visibility into what's running, where it is, and who can access it. This provides you with that unprecedented control over shadow IT without crippling your development team's ability to experiment and try new technologies.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/Cz22Wqr.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Technologies Detected in an Environment</div>
</div>
<br>

Here's a normalized view that allows you to quickly understand what technologies you are seeing and how they fit into the broader cloud concept.

If Wiz see something new, They will let you know that it's new and we'll give you an overview of what it is. This feature set allows you to see and manage shadow IT for your full cloud estate and your full technology stack.
<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/tzuksse.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Category selection</div>
</div>
<br>

All cloud service providers plus workload technologies, including client and server applications like operating systems and databases and so on, these are all categorized under a Wiz-specific term.


#### Technology types 🤖

<table>
  <thead>
    <tr>
      <th>Category</th>
      <th>Technology type</th>
      <th>Description</th>
      <th>Examples</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2"><strong>Cloud Platform Service</strong></td>
      <td>Cloud platform service (full coverage)</td>
      <td>Any service that is offered and managed by your cloud provider(s). This includes both IaaS and PaaS.</td>
      <td>AWS EC2, Azure App Service</td>
    </tr>
    <tr>
      <td>Cloud platform service (partial coverage)</td>
      <td>Any service that is offered and managed by your cloud provider(s).</td>
      <td>AWS Machine Learning, Azure Workspace</td>
    </tr>
    <tr>
      <td rowspan="4"><strong>Hosted technologies</strong></td>
      <td>Library</td>
      <td>Frameworks or code libraries detected on a compute resource or code repository.</td>
      <td>React, npm</td>
    </tr>
    <tr>
      <td>Server Application</td>
      <td>Software or libraries installed on a compute resource that expose services through a network (either internal or external).</td>
      <td>MongoDB, NGINX</td>
    </tr>
    <tr>
      <td>Client Application</td>
      <td>Any software installed on a compute resource that is not a server application.</td>
      <td>CrowdStrike, Splunk Agent, DataDog Agent, Google Chrome</td>
    </tr>
    <tr>
      <td>Virtual Appliance</td>
      <td>Compute resources that reside in your cloud environment and run a third-party vendor's software (typically VMs created by a service like AWS Marketplace).</td>
      <td>PAN-OS, FortiOS</td>
    </tr>
    <tr>
      <td>—</td>
      <td>Code technology</td>
      <td>
        <ul>
          <li>VCS Graph objects (e.g. Code Organizations, Repositories, and User Accounts).</li
          <li>Programming languages identified in repositories detected in your VCS or within your compute resources (i.e. VMs, containers, container images, or services).</li>
        </ul>
      </td>
      <td>Github Repository, C, JavaScript</td>
    </tr>
    <tr>
      <td><strong>Identity</strong></td>
      <td>Cloud Service (SaaS)</td>
      <td>A service that is hosted by a third party (outside your cloud environments).</td>
      <td>Datadog Monitoring, Burp Suite</td>
    </tr>
  </tbody>
</table>


### Working with Technologies Inventory 📱

#### Search for technologies 🔍

The [Inventory > Technologies ↗](https://app.wiz.io/inventory/technologies) page can be used to view all technologies supported by Wiz, only those detected (or not detected) in your environment, or only the technologies you search for.
To search or filter technologies, you can:
*   Clear the **Detected in environment** filter to view the full technology catalog supported by Wiz
*   Set the **Detected in environment** filter to "true" to show only technologies detected in your environment
*   Select the category, subcategory, or [types](https://docs.wiz.io/docs/cloud-inventory#technology-types) using the filters or widgets
*   Search by technology name
*   Select one or more statuses by their icons ([learn about status](https://docs.wiz.io/docs/technologies#review-technology-status))
*   Add additional filters (**Properties**, **Subscription**, etc.)
*   Click **+ More** to select a built-in filter:
    *   **Coverage**—Whether Wiz provides full or partial coverage of the technology
    *   **Has EOL Support**—Whether the technology is supported for End-of-Life ([learn more](https://docs.wiz.io/docs/vuln-mgmt#patch-management-enrichment-properties))
    *   **Region**—Where the resources running a technology are located
*   Click **Reset** to remove all filters
*   Click  to select a filter from the quick filters

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/tRHm0Gi.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Technologies Filters</div>
</div>
<br>

#### Suggest a Technology 👨‍💻

If Wiz does not support a technology that is important to your organization, let us know:
1.  At the top right of the Inventory page, click **Suggest a technology**.
2.  Provide a detailed description about what technology you'd like Wiz to support and the security use case.
3.  We'll let you know soon if we're already planning to support it, or if it can be added to our roadmap.

#### Review technology status 🧰

You can track and review new technologies using the technology status. By default, the status of every technology is **Unreviewed**. You can manage technologies by setting their status to **Required**, **Approved**, or **Unwanted**. Once set, the status is automatically applied to any new instances of the technology in your cloud environment.

You can then set up an alert for when a new unreviewed hosted technology is detected or an unwanted technology is detected. Statuses can also be used for custom queries like [VMs running unwanted technologies ↗](https://app.wiz.io/graph#~(query~(type~(~'VIRTUAL_MACHINE)~select~true~relationships~(~(type~(~(type~'RUNS))~with~(type~(~'HOSTED_TECHNOLOGY)~relationships~(~(type~(~(type~'HAS_TECH))~with~(type~(~'TECHNOLOGY)~select~true~where~(status~(EQUALS~(~'Unsanctioned)))))))))))).

You can set the status of technologies even before they are detected in your environment.

To change the status of a technology:
1.  Search for a technology.
2.  Click the technology name to view its details.
3.  In the details drawer, select a different status.
4.  (Optional) Set up notifications for new or unwanted technologies.
<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/bG1fKvB.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Technologies Status</div>
</div>


#### Explore a hosted technology ⚙️

A Hosted Technology runs on a VM, container, or serverless function, or is installed on an image (e.g. applications, OS, libraries, etc). 

You can find where technologies are running, and also where they're not. This is useful for verifying coverage of agent-based endpoint protection applications, such as Microsoft Defender for Endpoint (ATP).

You can also use the Security Graph to search for Technologies

#### Patch Management, Properties of Hosted Technology: 📹

This functionality only exists at the hosted technology level. Again, this is closely related to the graph and what you can do with it, but hosted technology has a key set of actionable attributes that let you quickly find resources that meet the criteria. 

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/gHUYcye.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Technology Details</div>
</div>
<br>

For example, you can find all the resources that are running a hosted technology that's not the latest version. So some useful insight here is around patch management, the types of technologies, and so on. You can find out which resources are running the highest number of out-of-date technologies.

### Terms and Abbreviations 🗂️

The following terms relate to the Technologies page and operations around it.
*   **Connectors**. Via API integration, a connector interrogates a subscription to discover the status and inventory of the cloud state.  Can connect to a Cloud, Kubernetes, and Registry Connectors. Cloud event scanning is configured per connector.
*   **Agentless scanning**. Technique to discover and evaluate full-stack technologies for risk without agents.
*   **Cloud Scanner**. Identifies all API retrievable technologies for all connected clouds. Refreshes every 24 hours.
*   **Workload\Disk Scanner**. Identifies client and server applications running on the OS partition of a workload.
*   **Coverage**. 
    *   _Supported_. Normalized technology is well understood by Wiz.
    *   _Partial_. Technologies discovered but not normalized.  Highlights cutting-edge technologies for shadow IT review.
*   **Subscriptions**. A normalized view in Wiz that represents Subscriptions (Azure), Projects (GCP), Accounts (AWS and Alibaba Cloud), and Compartments (OCI). Detected and provisioned automatically if Wiz connects on to management group (Azure), organization (GCP, AWS, and Alibaba Cloud), or Tenancy level (OCI).
*   **Event-triggered scanning**. Based on key cloud events, typically, create, delete, update, for specific cloud resources, Wiz rescans via cloud and workload scanners those specific events in between regular full-cloud refresh scans.
*   **Container image**. A container image is a lightweight, standalone, and executable software package that includes everything required to run a piece of software, including the code, runtime, system tools, system libraries, and settings.
*   **Container Registry**. A container registry is a storage hub for container images, allowing users to save, share, and access these packaged software units easily. Examples include Docker Hub, JFrog, and Amazon ECR.

### Use Cases 🛰️

*   **Comprehensive Visibility Across Clouds**. Achieve a unified view of all assets, regardless of cloud provider or region, to eliminate blind spots in security monitoring.
*   **Multi-Cloud Inventory Management**. Effectively manage resource adoption and usage across multiple cloud platforms while addressing unique challenges posed by each provider.
*   **Agent enforcement**.  Detect workloads without required agents.
*   **Automated regional awareness**. Restrict cloud services or technologies by region.   
    Lifecycle, version, and patch management support for technologies running in your clouds.
*   **Turn on the lights for your cloud environment**   
    *   _Increase operational efficiency_. No rule maintenance as normalization enables seamless detection of new technologies, even new, unsupported cloud services.
    *   _Rapidly Improve your security posture_. Turn the lights on, Use common language, see the unknown, single pane of glass, all clouds, Kubernetes flavors, and vSphere. 
    *   _Transform your operating model_. Only focus on what is there; updates every 24 hours. Deep evaluation; full stack. Full insights into all your clouds. 
    *   _Accelerate business_. Automate artifacts. rapid assessment for compliance across large set of frameworks.