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

## Cloud Entitlements ☁️

### Cloud Identity and Entitlement Management (KEEM/IAM) 🔐

Cloud Identity and Entitlement Management—referred as **IAM (Identity and Access Management)**—is a core component of cloud security. It defines **who** (users, systems, services) can access **what resources** and **what actions** they’re allowed to perform within a cloud environment.
Wiz continuously analyzes both **explicit IAM policies** and the **effective access** that results from those policies, roles, and conditions across cloud platforms. The goal is to identify toxic combinations that can lead to excessive access, lateral movement, and ultimately compromise.

> 🕹️ _Think of IAM as the player-permission screen in an online RPG: get the settings wrong and suddenly the healer can one-shot the raid boss._
* * *

### Why IAM Is Critical ⚠️

IAM misconfigurations are a **primary attack vector** in cloud environments. With complex policies spread across multiple accounts, roles, and services, it's easy for organizations to accidentally grant excessive or unintended permissions.

#### Top IAM Risks ⚡: 

*   **Overprivileged identities** that can perform high-risk actions they shouldn't.
    
*   **Lateral movement**, where an attacker moves between services/accounts after initial access.
    
*   **Access to sensitive data**, such as customer PII, secrets, or financial records, by identities that don’t require it.
    

> 🎬 _It’s the “Jurassic Park” lesson: just because you **can** doesn’t mean you **should**. Remember Nedry’s master key? Yeah, that._

Wiz helps detect and prioritize these risks so they can be remediated before being exploited.

* * *

### Understanding Risk in Wiz: “Toxic Combinations” 🧪

Wiz does not just look at whether an identity **has permissions**—it looks at whether they are **effectively usable**, and **whether they represent real risk** based on context.
For example:
*   If a user is granted full admin rights **but a higher-level restriction** (such as an AWS Service Control Policy) is in place that **blocks those permissions**, Wiz will **not classify the user as an admin**.
    
*   Similarly, if an identity only has access to **a specific resource** (e.g., a single database), Wiz understands that the **blast radius** is limited and will **not flag it as a high risk** for account takeover.
    
This logic allows Wiz to **accurately prioritize** the identities that matter most from a risk perspective.
> 💣 _A single stick of dynamite isn’t bad until someone wires it to the detonator._

* * *

### Wiz Defines Access at Four Main Levels 📊

Wiz classifies access levels based on the **scope of permissions**, the **type of resource affected**, and the **risk associated with each identity**. These levels help security teams prioritize and investigate the most critical entitlements.

* * *

1.  **Admin Privileges**
    
    These represent **full administrative access** across services and resources. Identities with this level of privilege can control infrastructure, networking, IAM policies, and monitoring configurations.
    **Examples:**
    *   Creating or deleting virtual machines, containers, or storage
        
    *   Modifying IAM roles and policies
        
    *   Managing firewall/security group rules
        
    *   Controlling encryption keys and KMS policies
        
    *   Disabling logging or alerting mechanisms
        
    > 🏰 _God-mode unlocked—handle with care._
2.  **High Privileges**
    
    These grant **powerful permissions**, typically within a more limited scope or specific cloud service. While not full admin, they still carry a high potential for disruption.
    **Examples:**
    *   Writing to or deleting production data
        
    *   Deploying workloads or services
        
    *   Modifying cloud configurations (e.g., IAM bindings, deployment settings)
        
    *   Managing environment variables, secrets, or certificates
        
     > 🛠️ _Like wielding Thor’s hammer—just because you can smash doesn’t mean you should._


3.  **Data Access Privileges**
    
    These allow identities to **read or write data** stored in databases, object storage, logs, or other systems. While infrastructure may remain untouched, data access is a major compliance and privacy concern.
    **Examples:**
    *   Reading or downloading files from S3 buckets, Azure Blobs, or GCS
        
    *   Querying production databases (SQL, NoSQL)
        
    *   Accessing sensitive telemetry or logs containing user data
        
    > 📚 _The difference between “look but don’t touch” and “scribble on the Mona Lisa.”_

4.  **Third-Party Access**
    
    These permissions are granted to **external identities or systems**—such as vendors, SaaS integrations, or federated identities. They introduce a unique set of risks, since the access extends beyond your organization's direct control.
    **Examples:**
    *   A third-party vendor with read access to logging or monitoring tools
        
    *   A CI/CD tool (e.g., GitHub Actions, GitLab CI) with deployment capabilities
        
    *   A federated identity provider (e.g., Okta, Azure AD B2B) granting access to internal resources
        
    **Risks include:**
    *   Limited visibility into external IAM or key hygiene
        
    *   Token leakage or compromise outside your perimeter
        
    *   Overly permissive access granted for convenience, not necessity
        
    *   Persistent access that remains after the external relationship ends

    > 🎟️ _Guest passes are great—until the guests never leave._

* * *

### **Principals in Wiz: Who Can Access Resources** 👥

Wiz refers to any identity with access rights as a **principal**.

#### A principal can be: 🗝️

*   A **user** (human identity)
    
*   A **service account** (machine identity)
    
*   An **IAM role**
    
*   A **group** (which may grant indirect permissions to users)
    
*   A **predefined group** (e.g., `admin`, `read-only`)
    
*   An **identity provider** (e.g., Azure AD, Okta)
    
Each of these entities can be evaluated based on **what permissions they hold** and **what resources they can access**.

* * *

### **IAM Evaluation Framework: The Who, What, and Where** 🧭

To properly assess the risk associated with each principal, Wiz evaluates three fundamental dimensions:
1.  **Who** is the principal?  
    Is it a user, service account, group, or federated identity?
    
2.  **What** actions can they perform?  
    – Can they read, write, or delete resources?  
    – Do they have wildcard permissions (e.g., `s3:*`, `iam:*`) that allow broad access?  
    – Can they manage security settings or identity configurations?
    
3.  **Which** resources can they access?  
    – Do they have access to core infrastructure (VMs, networks, IAM)?  
    – Can they access critical data (databases, object storage)?  
    – Are they limited to non-sensitive, scoped environments?

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/PzQ0TUU.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Diagram</div>
</div>
<br>  

 > 🔍 _Detective mode engaged—think Batman’s AR visor for your cloud._

Wiz uses this evaluation to surface **lateral movement paths**, **privilege escalation opportunities**, and **overexposed identities** that could be exploited in an attack.
    
### **High-Privilege Principals** 🔥

In Wiz, a **high-privilege principal** is any identity—whether a **user**, **service account**, **group**, or **role**—that holds permissions capable of **disrupting critical cloud resources** or **altering sensitive configurations**, even if they don’t have full administrative rights.
While they may not be able to manage IAM settings or create new users, their permissions still grant the power to:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/Wz9FHYk.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">High Privilege Principals</div>
</div>
<br>

*   Create or delete infrastructure
    
*   Modify security-relevant configurations
    
*   Delete or overwrite important data
    
These identities are considered dangerous due to the **operational risk** they pose, and they are a key focus of entitlement analysis in Wiz.

* * *

### **What Counts as High-Privilege Access?** 🎯

Wiz defines high-privilege access as **any permission or combination of permissions** that allow:
*   **Creation, modification, or deletion** of:
    *   Cloud resources (VMs, storage, containers, etc.)
        
    *   Networking components (e.g., subnets, firewalls)
        
    *   Resource configurations or metadata
        
*   **Assignment or reassignment** of other permissions or roles
    
*   **Disruption** to cloud workflows or operational stability
    

> **Example**: A service account with permission to delete database tables—even without user management rights—can irreversibly impact application availability and business operations.

 > 🎮 _A service account that can drop all your production tables is basically wielding a blue shell on lap three._

* * *

### **High-Privilege Permissions in Kubernetes** 🐙

In Kubernetes environments, Wiz follows three **industry-recognized criteria** to classify a permission as high-privilege:
1.  **Code Execution**  
    Any permission that allows creating a `Pod`, `Job`, or `Deployment` may lead to arbitrary code execution.  
    This applies at both **cluster** and **namespace** level.
    
2.  **Reading Secrets**  
    Permissions that allow access to Kubernetes secrets (e.g., service tokens, credentials) can enable:
    *   **Lateral movement**
        
    *   **Privilege escalation**
        
    *   **Credential theft**
        
3.  **Workflow Disruption**  
    Permissions that allow the **deletion** or **update** of critical components:
    *   IAM bindings
        
    *   Services
        
    *   Network policies
        
    *   Controllers
        
    These can be misused to **break the cluster** or disable its functionality.
    

* * *

### **Where to View High-Privilege Identities in Wiz** 🗂️

Wiz provides visibility into high-privilege principals via the **Cloud Entitlements page**:
*   Navigate to the **Explorer** section in the left-hand Wiz UI
    
*   Select **Cloud Entitlements**

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/idPrIvJ.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Cloud Entitlements</div>
</div>
<br>


*   Use filters to search for principals flagged with **high privileges** based on Wiz’s internal risk definitions
    
From this view, security teams can:
*   Audit which users or service accounts pose disruption risk
    
*   Investigate if these identities are overprivileged
    
*   Take action to reduce permissions in line with the **principle of least privilege**
    

> **Pro Tip**: Combine this with exposure context in the **Security Graph** (e.g., public access or exposed secrets) to identify toxic combinations.


### Admin Permissions 🛠️

As expected, **admin permissions** grant **broad and unrestricted control** over cloud environments. However, Wiz goes beyond surface-level policy checks and classifies admin access based on whether the permissions actually enable **persistence**, **identity control**, or **environment-wide disruption**.

> 🏰 _The keys to the kingdom—and the moat, the drawbridge, and the dragon._

* * *

#### What Counts as Admin Access? 🏷️
 
Wiz defines admin permissions as any permissions—explicit or effective—that allow an identity to:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/cx7olhZ.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Cloud Entitlements with admin filter</div>
</div>
<br>

*   Create, delete, or modify identities (users, roles, service accounts)
    
*   Manage IAM policies or roles
    
*   Grant other principals additional privileges
    
*   Use wildcard (`*`) permissions at the subscription, project, or account level
    
*   Bypass governance controls or gain persistent footholds
    
This includes full-access roles (like `Owner` in GCP or `AdministratorAccess` in AWS), as well as combinations of scoped permissions that produce admin-level outcomes.


#### Effective Admin Access (Context-Aware) 🧐

Wiz analyzes access **in context**, so not every identity with admin-like permissions is immediately flagged as such:
*   If a user is granted admin permissions **but restricted by higher-level controls**, such as an **AWS Service Control Policy (SCP)** or an **organizational policy**, Wiz **will not classify them as an admin**.
    
*   Similarly, if a user has admin-level permissions **only over a single, scoped resource**, and **not over the broader environment**, Wiz considers the **real impact radius** and may not flag the user as an admin.
    
This **effective access analysis** ensures accuracy and avoids false positives.


#### Admin Access in Kubernetes 🛠️

In Kubernetes, Wiz classifies **admin access** as:
*   **Wildcard (`*`) permissions at the cluster level**, not just namespace-specific access.
    
This includes:
*   Full control over RBAC policies
    
*   Ability to create/update/delete cluster-wide resources (e.g., `ClusterRole`, `Node`, `PersistentVolume`)
    
*   Actions that can enable persistent presence or compromise the control plane
    

* * *

### Data Permissions 📁

**Data permissions** refer to privileges that allow a principal to **read, write, delete, or manipulate actual data**, rather than manage infrastructure or policies.
Wiz identifies data access down to the **most granular level** possible in each cloud service.

> 📦 _These are the loot crates attackers really want to open._

#### Examples of Data Permissions: 🔍

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/feDlI0a.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Graph with data findings example</div>
</div>
<br>

*   **S3 `GetObject` / `DeleteObject`** — Accessing or removing individual files from an AWS S3 bucket
    
*   **GCP Storage `storage.objects.get`** — Reading a file from a GCS bucket
    
*   **Azure Blob `Read` / `Write` access** — Downloading or modifying blobs
    
These permissions are sensitive because they:
*   Enable direct access to **PII, credentials, logs, or application data**
    
*   May be granted indirectly via roles or service accounts
    
*   Often go unnoticed due to their “non-admin” appearance, but still present high risk
    

> **Insight**: Admin permissions pose a threat of **environmental takeover**, while data permissions are a direct threat to **data confidentiality, integrity, and privacy**.

* * *

### **Determining Who Can Access Sensitive Data in Wiz** 🧩

Understanding **who has access to sensitive data** in your cloud environment requires evaluating **both access permissions** and **the contents of the data itself**. Wiz combines these two dimensions to provide a full and accurate view of **data exposure risk**.

> 🎲 _Roll for initiative: who has both the map **and** the master key?_

 1. **Calculating Effective Permissions**

Wiz begins by analyzing **effective access** across all detected resources. This includes:
*   Permissions granted directly to **users**, **roles**, or **service accounts**
    
*   Modifiers like **resource-based policies**, **IAM conditions**, and **group inheritance**
    
*   Boundary-level controls such as:
    *   **Service Control Policies (SCPs)** in AWS
        
    *   **Organization Policies** in GCP
        
    *   **Azure Management Groups & RBAC constraints**
        
Rather than simply listing what policies _exist_, Wiz answers:

> “What can this principal actually do against this specific resource?”

This is **true effective access**, and it is context-aware.



 **2. Scanning for Sensitive Data**

To determine whether a resource contains sensitive data, Wiz uses the **Wiz Data Scanner**, an extension of the Workload Scanner.
**How it works:**
*   Takes a **sample** of the contents from supported storage resources like:
    *   S3 buckets
        
    *   Azure Blob Storage
        
    *   GCP Cloud Storage
        
    *   Cloud-native databases (e.g., DynamoDB, Cloud SQL, Cosmos DB)
        
*   Matches the sample content against **your organization's data classification rules**
    *   Examples: PII, credentials, credit card numbers, secret tokens, internal identifiers
        

> **Important**: Wiz **does not store actual data**.  
> Only **metadata results** are kept, and partial, redacted samples are shown in the UI for context.



**3. Combining Access + Data Sensitivity = Real Risk**

By correlating:
*   **Who has access**
    
*   **What they can do**
    
*   **Whether sensitive data is present**
    
Wiz builds a **comprehensive data access model**.
This model allows you to identify:
*   Excessively exposed sensitive data
    
*   Identities with **write or delete access** to critical datasets
    
*   External or third-party principals with access to sensitive content
    
*   Unused or forgotten storage resources that still contain sensitive information
    

* * *

### **Example: Investigating an S3 Bucket with Sensitive Data** 🪣

When a data finding is detected on a resource like an **S3 bucket**, the Wiz UI makes it easy to:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/JT3u82S.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">S3 Details</div>
</div>
<br>

*   View **what sensitive data was found**
    
*   Identify **which principals** have access to that bucket
    
*   Understand the **type and level of access** each identity has (e.g., read, write, delete)
    
*   Quickly take action (e.g., revoke access, tighten bucket policy)
    
This allows you to shift from **reactive discovery** to **proactive remediation**.

* * *

> **Insight**: It’s not enough to know where sensitive data lives—you also need to know _who can touch it_ and _what they can do with it_. Wiz brings both sides of the equation together into one view.

### Risks & Remediation in Wiz: Controls and Toxic Combinations

When assessing risk in Wiz—especially in the context of **entitlements** and **effective access**—the core mechanism for detection and response is through **controls**.

### Controls as Toxic Combination Detectors 🚦

Wiz defines a **toxic combination** as a **converging set of conditions** that, when found together, indicate a **high-risk scenario**.

> A toxic combination is not just one misconfiguration or one finding—it’s a **chain of weaknesses**.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/undefined.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Attack Path Graph of the Issue</div>
</div>
<br>

For Example: 
> "A publicly exposed virtual machine or serverless function that contains a high or critical severity network vulnerability, has a known exploit, and stores sensitive data."

If this combination is found, the control:
*   Flags the affected VM or function as **risky**
    
*   Highlights the path from the **internet**, through the **vulnerability**, into the **data resource**
    
*   Shows **privileged principals** associated with the resource that could enable **lateral movement** or **privilege escalation**
    
Individually, these findings may not raise alarms. **Together, they represent a clear attack path.**

### What Drives a Control? ⚙️

Each control is powered by a **Security Graph query**. This query defines:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/W5ySXQn.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Example of a query</div>
</div>
<br>

*   What types of **resources** it applies to
    
*   What types of **findings** it’s looking for (e.g., vulnerabilities, secrets, misconfigurations)
    
*   What **relationships** must exist between those elements (e.g., exposure → to → data)
    
When that query returns results:
*   A **control violation** is recorded
    
*   One or more **issues** are generated and attached to specific resources
    
*   An **attack path** is rendered in the Security Graph to visualize the full context

### Control Details Page

Clicking into a control allows you to:
*   Read a **description** of the control, including:
    *   What it looks for
        
    *   Why it matters
        
*   See related **compliance frameworks** (e.g., PCI-DSS, NIST, ISO)
    
*   View associated **risk categories** (e.g., Lateral Movement, Data Access, Privilege Escalation)
    
*   Determine whether the control is set to **generate issues**
    
*   See the **query** logic powering the control by clicking **“View on Security Graph”**
    
This allows teams to:
*   Understand what makes the control **trigger**
    
*   Visualize **how** findings and resources connect
    
*   Validate or tune the control based on internal context

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/RviDEht.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Graph Control</div>
</div>
<br>

* * *

### Enhancing Risk Context with Threat Detection & Excessive Access Analysis 🔍

While controls and findings provide deep insight into misconfigurations and attack paths, Wiz further **augments** this view with:

1.  Threat Detection Rules
    
2.  Excessive Access Findings
    
3.  Permission Reduction Recommendations
    
These features allow security teams to **connect policy violations with real activity**, and **tighten identity permissions** to reduce lateral movement and privilege escalation risk.

* * *

### 1. Threat Detection Rules 🚨

**Threat detection rules** in Wiz monitor cloud resources for behaviors that suggest **potentially malicious activity**, such as:

*   Anomalous authentication attempts
    
*   Suspicious service account usage
    
*   Abnormal API calls
    
Wiz correlates this behavioral telemetry with findings from:

*   Controls
    
*   Vulnerabilities
    
*   Exposure paths
    
*   IAM configurations
    

> **Why it matters**: When you layer a threat detection signal **on top of an existing toxic combination**, it shifts the context from "theoretical risk" to **"possible active exploitation."**
> 🕰️ _When Clippy starts brute-forcing SSH at 3 a.m., Wiz notices._

#### Example Use Case:

*   A publicly exposed VM is detected with a known vulnerability and sensitive data.
    
*   Separately, Wiz detects a **threat signal** showing active authentication attempts from that machine.
    
*   This validates the **attack path is being exercised**—not just a risk, but a real-time threat.
    
You can find these enriched cases in the **Issues page**, filtering for **identity-based resources** flagged by a **threat detection rule**.


### 2. Excessive Access Findings 🛡️

Excessive access is a common identity-related risk where users, roles, or service accounts:

*   Are granted more permissions than they use
    
*   Hold sensitive permissions that haven’t been exercised
    
*   Violate internal security principles (e.g., least privilege)
    

#### Types of Excessive Access Findings:

*   Unused Permissions:  
    Permissions that haven’t been used in the past **90 days by default**.
    
*   Overly Permissive Roles:  
    Identities that hold **dangerous permissions** like user or role creation (e.g., `IAMCreateUser`, `IAMCreateRole`) but don’t actively use them.
    

#### Risk Example:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/Qtphypf.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">High Finding Example</div>
</div>
<br>

A service account with `IAMCreateRole` could be assumed by an attacker, who then **creates a new role** and **assigns it admin permissions**, escalating their access within your environment.

### 3. How Wiz Tracks Permission Usage 📈

Wiz integrates with **native cloud activity monitoring tools** to assess which permissions have or haven’t been used:

| Cloud Provider | Usage Source |
| --- | --- |
| AWS | IAM Access Advisor |
| GCP | IAM Recommender |
| Azure | Azure Activity Logs / Cloud Events |


### 4. Permission Reduction Recommendations ✂️

When excessive permissions are detected, Wiz generates **automated recommendations** to:
*   Identify unused or high-risk permissions
    
*   Highlight which permissions should be **removed**
    
*   Show the remaining **effective policy** after reduction
    

#### **Wiz UI Details:**

*   **Left Column**: Unused or dangerous permissions (highlighted in **red**)
    
*   **Right Column**: Final state of permissions after applying the recommendation
    
*   This view helps security teams **understand impact** and **take action confidently**
    

* * *

### 5. Customizing the Inactivity Window ⏲️

By default, Wiz considers a permission **“unused” after 90 days**, but this is configurable.

#### How to adjust the inactivity threshold:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/VIRSNXp.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Inactivity threshold configuration</div>
</div>
<br>

1.  Go to **Settings > Scanners > Cloud Entitlements**
    
2.  Modify the **“Excessive access analysis period”** to:
    *   Match internal policies (e.g., 30 days for high-security environments)
        
    *   Align with external frameworks (e.g., CIS Benchmarks)
        
This flexibility ensures **compliance alignment** and **fine-tuned detection sensitivity**.

### Lateral Movement and Identity Risk in Wiz 🛣️

**Lateral movement** is one of the most dangerous tactics used in cloud-based attacks. It occurs when an attacker compromises one resource (e.g., a VM or user account) and **moves laterally** across systems, escalating privileges, collecting credentials, and accessing **high-value targets**, often referred to as **crown jewels**.

> 🏃 _Parkour through the cloud—except Wiz blocks the shortcuts._

### What Wiz Looks for in Lateral Movement 🔄

Wiz identifies and calculates **potential lateral movement paths** across your environment by analyzing:
1.  **IAM bindings** and effective access
    
2.  **Secrets present on resources** (e.g., access keys, tokens)
    
3.  **Privileged identity exposure**
    
4.  **Proximity to sensitive data or administrative targets**
    

> The goal is to reveal:  
> _“Can an attacker move from a publicly exposed or low-privilege resource to a high-impact target such as an admin role or sensitive data store?”_

**Crown Jewels**

Wiz defines **crown jewels** as the most critical and sensitive assets in your environment.  
This includes:
*   **Admin identities** and resources capable of privilege escalation

* **Admin resource**
    
*   **Databases**, **buckets**, or instances containing **sensitive or regulated data**
    
*   **Control plane services**, such as Kubernetes clusters
    
Lateral movement findings focus on protecting these by analyzing the **paths** attackers could use to reach them.

### How Wiz Calculates Lateral Movement Paths 🗺️

*   Wiz maps IAM relationships and secret exposure paths across **up to 10 hops**.
    
*   These paths may involve:
    *   Publicly exposed resources
        
    *   VMs with embedded credentials
        
    *   Service accounts with role-assumption capabilities
        
    *   Privileged resources or users with escalation permissions
        

#### Example Path:

`Internet → Exposed VM → Secret Key → Service Account → Admin Role → Sensitive Data`

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/yLflpEf.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Example Path</div>
</div>
<br>

Each **lateral movement finding** includes:
*   The full **attack path**
    
*   All **involved identities, permissions, and secrets**
    
*   The specific **crown jewel target**
    
This data is **visualized on the Security Graph** and contextualized inside issues and entitlement views.

* * *

### **Where to Investigate Identity Risk in Wiz** 🕵️‍♀️

Wiz provides **multiple tools and dashboards** to investigate entitlements and lateral movement vectors:


**1. Cloud Entitlements Page**

*   Located under the **Explorer** menu in the UI

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/UTEK42F.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Cloud Entitlements Page</div>
</div>
<br>

*   Shows all **principals** and the **resources** they can access
    
*   Includes details such as:
    *   IAM bindings
        
    *   Granted permissions
        
    *   Access types
        
    *   Visual access paths
        
    *   Associated findings
        
**Updated every 24 hours** based on the latest scan.
**Filters available:**
*   Admin privileges
    
*   High privileges
    
*   Data access
    
*   Third-party access
    
 **2. Cloud Identities Page**

*   Found in the **Inventory** section of the UI

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/TL0mZiU.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Cloud Identities Page</div>
</div>
<br>

*   Displays all **identities** across all cloud platforms (AWS, Azure, GCP)
    
*   Use cases:
    *   Find **inactive users**
        
    *   Identify users **without MFA**
        
    *   Detect developers with access to **version control systems**
        
**Drill-down available:**
*   Click identity name to open **details drawer**
    
*   See associated user accounts, identity insights, and open issues
    
*   Filter by developer, platform, or specific access level
    

 **3. Cloud Entitlements Board**

*   Provides a **comprehensive view** of entitlements, permissions, and identity-based risk

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/wPAsX4i.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Cloud Entitlements Board</div>
</div>
<br>
   
*   Supports:
    *   **Preset entitlement queries**
        
    *   **Custom view creation** (adjustable columns, filtering, sorting)
        
    *   **Visualization of identity risk**
        
Think of it as the **centralized dashboard** for reviewing all cloud IAM relationships in one place.



 **4. Identity-Focused Reports**

*   You can create **Cloud Entitlement Reports** for identity-specific investigations.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/yi5LqHi.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Identity Focused Report</div>
</div>
<br>

**Example use case:**

> “Find all identities with **admin rights** that haven’t been used in the last 90 days.”

**Configuration options:**
*   Same logic as the Explorer view (graph-query style)
    
*   Schedule automated reports via email or storage (e.g., S3 bucket)
    
*   Export for audits or long-term tracking
    
These reports are perfect for:
*   Audit preparation
    
*   Historical tracking
    
*   Regulatory evidence
    



