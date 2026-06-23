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
 
## Effective Exposure 🛡️

### Network Exposure in Wiz 💡

In Wiz, **network exposure** refers to the **effective exposure** of cloud resources—that is, how accessible these resources are from the Internet, regardless of whether the exposure was intentional (e.g., for a public website) or not.

Every resource exposed to the Internet carries inherent risk, and Wiz models these risks by combining network information with other security signals to identify toxic combinations.

Now, let's talk about effective exposure. It's really comprised of three different phases: 

#### Three Layers of Exposure Analysis 🧅

1.  **Internet Exposure**  
    Detects any ingress path from the **public Internet** (`0.0.0.0/0`) to a cloud resource.
    
2.  **External Subscription Exposure**  
    Identifies resources that are accessible from **external accounts or subscriptions**, even if not exposed publicly.

>  🤝 **Neighborly Access or Unwanted Guests?**  
This is like your neighbor having a key to your back gate. It might be for a legitimate reason (a shared service between two company departments using different cloud subscriptions), or it could be an old key that was never retrieved, posing a risk. Think of it as a trusted P2P connection in a game that, if compromised on one end, could affect the other.    

3.  **VNet-to-VNet Exposure**  
    Highlights resources accessible from other **internal or hybrid networks**, indicating potential lateral movement paths.

> 🏃‍♂️ **Lateral Movement: The Intruder's Parkour** 

Once an attacker is inside one part of your network, this is how they jump to other parts. Think of John McClane crawling through the vents in _Die Hard_ (`NakatomiPlaza_VNet_01` to `NakatomiPlaza_VNet_02`), or a Xenomorph in _Alien_ using the ship's interconnected systems to move unseen. Wiz identifies these internal pathways.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/W9tMJBN.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Diiferent types of Network Access</div>
</div>
<br>

#### **Key Components of Network Exposure**  🔑

1.  **Network Architecture**
    *   **Building the Network Architecture**:  
        Wiz scans your cloud resources (e.g., virtual machines, containers, and other objects) within your cloud service provider and constructs a **Security Graph** that details how these resources are interconnected.
        
    *   **Calculating Effective Ingress**:  
        Using the network configuration data, Wiz determines the **actual, effective ingress**—in other words, the real-world exposure points where external traffic can reach your resources.
        
2.  **Effective Exposure Analysis**

       Calculating effective ingress into your different resources

2.  **Dynamic Scanner**
    *   **Validation of Exposure**:  
        The **Dynamic Scanner** periodically validates the exposure. It checks the status of the calculated open ports and IP addresses to ensure that what was assessed via cloud configurations still matches the actual state of the environment.
        
    *   **Application Endpoint Evaluation**:  
        This component ties network exposure to application endpoints, ensuring that the exposure model reflects not only static cloud configuration but also dynamic operational conditions.
        

* * *

### Network topology and object insights 🗺️

*   Fetching Cloud Resources:  
    When WiZ connects to your cloud environment, it fetches those cloud resources and maps them on the security graph. 
As a part of that process, we retrieve many different types of objects, such as: 

    *   **Virtual Machines (VMs)**
        
    *   **Containers** running on these VMs
        
    *   **Container Images** and the underlying technologies
        
    *   **Vulnerabilities** associated with these resources
        
    *   **Networking Properties** and configuration details from cloud assets
        
<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/3PJaGv0.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Wiz Graph of resources and their connection to the Internet</div>
</div>
<br>

*   **Onboarding into the Security Graph**:  
    Every resource object—including its networking configurations—is **mapped into the Security Graph**. This mapping allows Wiz to visualize and analyze how resources are interconnected and where the potential Internet-facing exposure lies.
    

> **Analogy**: Imagine your cloud environment as a large digital city. Wiz acts as an aerial reconnaissance drone that maps every road (network connections), building (resources), and gate (exposure points). It then highlights which buildings are accessible from the city’s perimeter, even if they were meant to be private or semi-private.

* * *

### **Why Effective Network Exposure Analysis Matters** 💥

*   **Inherent Risks of Exposure**:  
    Even intentional exposures, such as public websites, require careful monitoring because they are potential entry points for attackers.
    
*   **Modeling Toxic Combinations**:  
    By combining network exposure information with other risk signals (e.g., high-privilege identities, vulnerable applications, or exposed secrets), Wiz can detect dangerous attack paths that might facilitate lateral movement or data breaches.
    
*   **Continuous Validation**:  
    The dynamic scanner ensures that the exposure assessed based on cloud configurations remains accurate over time, adapting to changes in the environment.

### How Wiz Builds Effective Network Exposure

Once Wiz has onboarded a resource into the **Security Graph**, it proceeds to analyze its **network exposure** by attaching virtual network structures and modeling connectivity paths across cloud components.
This process allows Wiz to detect and map exposure **even when cloud-native configurations are abstracted or missing**.

* * *

**0. Agentless Cloud Scanning**

Wiz connects to your cloud environments (AWS, Azure, GCP, OCI, etc.) via **APIs** to:
*   **Scan all resources** across compute, storage, and networking
    
*   Perform **agentless**, read-only scans
    
*   Build a detailed **Security Graph** representing your entire cloud topology
    

**1. Attaching Network Interfaces**

Every resource that is evaluated for network exposure in Wiz is **linked to a network interface**:
*   **For resources with native interfaces** (e.g., Virtual Machines):  
    Wiz attaches the **actual network interface** defined in your cloud service provider (CSP).
    
*   **For resources without a native interface** (e.g., AWS Lambda, PaaS databases):  
    Wiz **artificially attaches a virtual network interface**, enabling it to perform exposure modeling even when no explicit NIC exists.
    
> This ensures all resources can participate in **network exposure analysis**, regardless of their architecture.



2. Modeling Network Connectivity*

Wiz adds additional **network connectivity objects** to the graph using two key types of information:

#### **A. Network Security Rules**

These represent **allow/deny rules** typically found in:
*   **Security Groups** (AWS)
    
*   **Network ACLs**
    
*   **Firewall rules** (on VMs or other resources)
    
*   **Cloud-native configurations** (e.g., “Block Public Access” on a database)
    
If a resource is **explicitly configured to deny public access**, Wiz will model that as a **deny rule**.

#### **B. Proxy Rules** 

Proxy rules simulate the **logical flow of network traffic** between resources, often abstracted through infrastructure components such as:
*   **Load balancers** (e.g., combination of listener rule + target group)
    
*   **API Gateways**
    
*   **Ingress controllers**
    
These are **modeled as a single proxy rule** that captures how traffic is routed from source to destination.

> 📜 **The Rule Books of Your Kingdom** These are like the laws and gate controls of your digital realm. "Allow port 443 from Internet" is like saying "The main gate is open for HTTPS traffic." "Block Public Access" on an S3 bucket is like putting a "No Trespassing - Keep Out!" sign on your treasure vault.

* * *

 **3. Graph-Based Exposure Modeling**

Once all network interfaces and rules are in place, Wiz uses the Security Graph to:
*   Map **connectivity relationships**
    
*   Determine **network exposure status** for each resource
    

#### **Security Graph Example**: 📊

You might see a **virtual machine** node that:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/b1eIL7e.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Example of a VM</div>
</div>
<br>

*   Is **behind a load balancer**
    
*   Has a connected **network interface** and **security group**
    
*   Is linked to an **application endpoint**
    
*   Is **reachable from the Internet**
    
This provides full visibility into the **network path**—from the Internet, through the infrastructure, to the exposed resource.



### Effective Exposure Analysis 🏗️

Wiz performs **effective ingress analysis** based on graph data. This identifies whether a resource is **truly reachable**, not just **configured to be reachable**.

Now Wiz takes information from the graph and identify an ingress path to the resource. 

The exposure does not have to be direct. We take into account load balancers, API gateways, and other cloud infrastructure such as that. 

And when Wiz is done with that, the results are added to the resource, including exposure from different locations, such as the internet, other VNets, custom IP ranges. The calculation is performed completely based on the graph objects themselves.


#### **Excluded by Default** : 🗑️

To avoid false positives, Wiz **excludes** certain resources from exposure analysis:
*   **Inactive resources** (e.g., powered-off VMs)
    
*   Resources that **don’t expose TCP ports**
    
*   **Unhealthy nodes** (e.g., VMs in failing target groups)

> 🎯 **Focusing on Active Threats: Noise Reduction**  This is smart. Why raise an alarm for a powered-off VM? It's like a detective focusing on active leads and not dusty, cold cases. Or in a game, you wouldn't worry about an enemy unit that's already been neutralized or isn't on the map. This helps you concentrate on what _actually_ poses a current risk.
    

#### **Indirect Exposure Paths**: 

Wiz considers:
*   **Load balancers**
    
*   **API Gateways**
    
*   **Other routing infrastructure**
    
> Exposure does **not** have to be direct to be dangerous.

* * *

#### **Exposure Results Include 📋**: 

*   **Ingress source**: Internet, custom IP ranges, other VNets
    
*   **Access method**: Port and protocol used (e.g., HTTP on port 80)
    
*   **Visibility of the route**: Including proxy and security rule chains
    

* * *

#### **What Wiz Does _Not_ Do** 🚫

Wiz does **not perform packet inspection or traffic sniffing**.  
All exposure is calculated **entirely from Security Graph data**—ensuring:
*   Agentless operation
    
*   No performance impact
    
*   No access to actual traffic
    

* * *

#### **Kubernetes Exposure Modeling** 🚢

To analyze Kubernetes network exposure:
*   The **Kubernetes cluster must be connected** via the Wiz K8s Connector
    
*   This enables onboarding of internal services, pods, ingress controllers, and policies into the graph
    

* * *

#### **Limitations** 🚧

Wiz may be unable to model network exposure when:
*   **Third-party firewalls or appliances** manage traffic paths (e.g., Palo Alto, Fortinet)
    
*   **External proxies or services** haven’t been onboarded (e.g., API gateways from SaaS providers)
    
*   **Missing network components** prevent full graph resolution
    

> In such cases, exposure modeling will be incomplete, and the resource may appear as “partially analyzed” in Wiz.

### Mock Analysis: Effective Network Exposure in Wiz

To understand how Wiz performs effective network exposure analysis, it helps to walk through a real-world mock scenario. Wiz uses data collected via APIs from your cloud environment to build a **Security Graph**, calculate exposure paths, and identify **internet-exposed resources**.


**Step 1: Mapping the Core Resources**

Wiz starts by identifying all the cloud components that matter most:
*   **Virtual Machines**
    
*   **Databases**
    
*   **Containers**
    
*   **Buckets**
    
*   **Serverless Functions**
    
These resources are **onboarded to the WizGraph**, forming the foundation of the exposure model.


**Step 2: Adding Network Elements**

Wiz extends the graph by modeling **network infrastructure**:
*   **Network Interfaces**
    
*   **Subnets / VNets / VPCs**
    
*   **Internet Gateways**
    
*   **Load Balancers**
    
*   **Security Groups / Firewalls**
    
*   **Proxy Rules (e.g., listener + target group)**
    
This builds a **complete architectural view** of how traffic can flow between the internet and internal resources.

**Step 3: Calculating Exposure Paths**

Using the **network security rules** and **proxy rules** modeled in the graph, Wiz calculates **effective exposure** by analyzing:
*   What is exposed?
    
*   Who or what is it exposed to?
    
*   Through what path (e.g., load balancer, API Gateway)?
    

> This analysis **does not involve traffic sniffing or packet analysis**—everything is derived from **configuration and metadata**.

**Step 4: Applying Deny Rules and Ingress Filtering**

Wiz **excludes certain resources** from exposure based on cloud configurations:
*   **Buckets** or **Databases** with “Block Public Access” or similar deny settings
    
*   **Serverless Functions** with explicit **deny rules** (e.g., `0.0.0.0/0`)
    
*   **Inactive** or **unhealthy** resources
    

#### **Example:**
<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/PzpHsWr.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Effective Exposure Example</div>
</div>
<br>

*   A storage bucket appears public but has a config that **denies all public access** → Wiz marks it as **non-exposed**
    
*   A serverless function is set to **deny all inbound traffic from 0.0.0.0/0** → also marked as **non-exposed**
    
**Step 5: Identifying Truly Exposed Resources**

Once deny rules are factored in, **only truly exposed resources remain**.
For each exposed resource, Wiz adds a **Network Insights panel** showing:
*   Source of exposure (e.g., **0.0.0.0/0** — meaning the whole internet)
    
*   Number of **open ports**
    
*   Validation results (which ports are confirmed open)

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/M8TcQRD.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Network Insights</div>
</div>
<br>

* * *
**Step 6: Investigating in Wiz UI**

You can explore all exposure findings via the **Network Exposure page** under the **Issues tab**.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/psYNxkX.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Network Exposure</div>
</div>
<br>

**This view includes:**

*   All **internet-exposed resources**
    
*   **Cross-subscription exposure** paths
    
*   Resources exposed to **custom IP ranges**
    
*   Exposure through or bypassing **load balancers**
    
*   Number of **hops from the internet**
    
*   Full **exposure path trace**
    

> **Bonus**: This view reveals network exposure insights that may not be immediately visible from the raw Security Graph.

### Application Endpoints 📍

When Wiz determines that a resource is exposed to the **entire public internet on at least one port**, it creates an **Application Endpoint** for that resource.

> **Definition**:  
> An **Application Endpoint** is attached when a resource is exposed to `0.0.0.0/0` on **at least one port**, indicating **full public internet exposure**.

For customers **without the Dynamic Scanner**, this marks the end of exposure analysis—exposure is **inferred from configuration**, but not **actively validated**.

#### What Triggers the Creation of an Application Endpoint? ✨

An Application Endpoint is created when:
1.  **Effective exposure** is calculated through the Wiz Security Graph analysis.
    
2.  The resource is accessible from the Internet via a direct or indirect path (e.g., through load balancers or gateways).
    
3.  The ingress is wide (from 0.0.0.0/0), meaning it is reachable by any IP address.
    
4.  The **Dynamic Scanner** validates the port as actually open from the Internet (if the feature is licensed).
    
If the exposure is confirmed by the Dynamic Scanner, the endpoint is marked as "validated."


#### Properties of an Application Endpoint 🏷️

Each Application Endpoint object includes the following attributes:
*   **IP Address and Port**: The specific combination determined to be exposed.
    
*   **Exposure Validation**: Indicates whether the Dynamic Scanner has confirmed that the port is truly open.
    
*   **HTTP Response Data**: For HTTP/S ports, Wiz stores:
    *   Status Code (e.g., 200, 403)
        
    *   Content Type (HTML, JSON, etc.)
        
    *   Response Body (up to 1,000 characters, redacted if sensitive data is detected)
        
    *   Page Title
        
    *   Screenshot (if applicable)
        
*   **Associated Resource**: The cloud resource (VM, container, serverless, etc.) this endpoint belongs to.
    
*   **Wide Internet Exposure**: A boolean flag indicating full Internet exposure.
    

#### Application Endpoint and the Dynamic Scanner 🛰️

If you have Wiz Cloud Advanced or Wiz for Gov Advanced, the **Dynamic Scanner** enhances endpoint analysis by:
*   **Validating open ports** using TCP handshakes.
    
*   Sending **HTTP GET requests** to check for running web services.
    
*   Capturing screenshots of web interfaces.
    
*   Identifying exposed technologies using **Application Fingerprinting**.
    
*   Redacting sensitive values returned in headers or response bodies.
    
The Dynamic Scanner ensures that the Application Endpoint is not just theoretically exposed (based on configuration) but actually reachable and responding.


#### Exposure Policy and Severity ⚖️

Application Endpoints also have an associated **exposure level** that influences issue severity. This level can be controlled via **Exposure Policies**, which take into account:
*   **Authentication Mechanism** (e.g., none, basic auth, SSO)
    
*   **HTTP Status Code**
    
*   **Resource Type**
    
You can choose between three exposure policy modes:
*   **Permissive**: Sets lower severity if any auth is present
    
*   **Moderate (default)**: Medium severity for basic auth, high if no auth
    
*   **Strict**: Treats all exposed endpoints as high severity


#### Application Fingerprinting 👣
 
Wiz detects what technology is running behind the application endpoint by parsing HTTP responses. Examples include:
*   Jenkins
    
*   Apache
    
*   nginx
    
*   Node.js
    
If the technology identified by the Dynamic Scanner differs from the workload scan, Wiz will record both versions.

#### Where to View Application Endpoints 🖥️

You can inspect Application Endpoints:
*   Directly on the **Security Graph**
    
*   On each **resource page** under Network Insights
    
*   In the **Issues page** when filtering for network exposure-related findings
    

### Excluding Known or Intentional Exposure ✅

To **avoid noise from intentionally exposed resources**, use:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/MrlKYa7.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Custom Detection</div>
</div>
<br>

#### **Custom IP Ranges**: 🗺️

*   Configure in:  
    `Settings > Scanners > Custom Detections > Custom IP Ranges`
    
*   Use cases:
    *   Exclude **trusted corporate VPNs** from "external" exposure
        
    *   Treat **B2B partner IPs** as external if they are untrusted
        
    *   Highlight **sensitive internal apps** (e.g., GitHub Enterprise)
        
This ensures exposure is **context-aware**, aligning findings with business intent.
    

### Dynamic Scanner 📡

The **Dynamic Scanner** in Wiz is a powerful component used to **validate the exposure status of ports and IP addresses** that have been flagged as potentially accessible based on Wiz's effective exposure analysis. 

Its role is to **confirm whether resources are truly reachable from the public Internet**, thereby increasing the accuracy of findings related to external exposure.

#### Key Capabilities 💪

1.  **Exposure Validation**  
    The Dynamic Scanner periodically tests if identified ports and IPs are actually reachable from the Internet, providing an extra layer of confirmation to effective exposure calculations.
    
2.  **Application Endpoint Management**

    *   It's responsible or Application Endpoint Creation

    *   Adds or removes **Application Endpoints** based on live validation.
        
    *   Ensures only confirmed exposure to `0.0.0.0/0` results in an Application Endpoint.
        
3.  **License Requirement**  

    Use of the Dynamic Scanner requires:
    *   Wiz Cloud Advanced license
        
    *   Wiz for Gov Advanced license
        

* * *

#### How It Works ⚙️

*   **Port Scanning**:
    *   Uses a list of known ports (e.g., 80, 443, 22, 8080) to test for open ports.
        
    *   Performs TCP handshakes to verify accessibility.
        
*   **HTTP Validation**:
    *   Sends HTTP GET requests to supported HTTP(S) ports.
        
    *   Captures HTTP response status codes (e.g., 200, 403, 404).
        
    *   Pulls metadata: headers, content types (e.g., HTML, JSON).
        
    *   Stores up to 1,000 characters of the response body.
        
    *   Takes screenshots of rendered web pages when applicable.
        
*   **DNS and External Records**:
    *   Also scans DNS records pointing to externally hosted services.
        
    *   Adds external records for scanning even if not mapped by Wiz.
        
*   **Security & Redaction**:
    *   If sensitive data or secrets are found in HTTP responses, they are redacted from the Wiz UI.
        
#### **Real-World Scenario (Step-by-Step)**

1.  **Initial Setup**:
    *   EC2 instance with public IP `2.2.2.2`.
        
    *   No security group rules → No exposure.
        
    *   No dynamic scan performed.
        
2.  **IP Whitelisted**:
    *   SG rule allows ingress from `1.1.1.1/32` on port 80.
        
    *   Internet exposure = true (limited).
        
    *   No dynamic scan (not quad zero).
        
3.  **Wide Exposure Enabled**:
    *   SG rule updated to allow ingress from `0.0.0.0/0`.
        
    *   Dynamic Scanner scans port 80.
        
    *   App Endpoint is added and validated.
        
4.  **Service Goes Down**:
    *   Web server is shut off, but port still open.
        
    *   Dynamic Scanner sees no response → removes app endpoint.
        

* * *

#### Application Fingerprinting 👣

Dynamic Scanner performs **application fingerprinting** by:
*   Analyzing HTTP response content.
    
*   Matching known templates (e.g., Jenkins login screen).
    
*   Adding detected technologies to the application endpoint.
    
If a workload scan also detects hosted technologies, both are retained unless they match. Matching results are marked as **validated in runtime**.

* * *

#### Authentication Detection 🆔

Dynamic Scanner can detect authentication methods such as:
*   Basic Auth
    
*   SSO with providers like Google, Microsoft, Okta
    

* * *

#### Exposure Levels & Policies ⚖️

Wiz lets users set **Application Endpoint Exposure Policies** to prioritize findings based on organizational risk tolerance.

#### Policy Examples:

*   **Moderate (default)**: Basic Auth = Medium Severity
    
*   **Permissive**: Basic Auth = Low Severity
    
*   **Strict**: All exposure = High Severity
    
This customization allows teams to suppress expected exposure or flag any exposure as critical (e.g., honeypots).

* * *

#### Summary 🏁

The Dynamic Scanner provides runtime validation and rich context around network exposure, helping security teams:
*   Confirm real-time risk
    
*   Detect live services
    
*   Understand tech stacks
    
*   Prioritize based on validated exposure
    
It bridges the gap between **configuration-based analysis** and **real-world exposure validation**, enhancing confidence in exposure findings and refining threat prioritization.