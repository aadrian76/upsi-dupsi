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
 
## Understanding Vulnerabilities, CVEs, and Wiz’s Role
-------------------------------------------------------

### What Is a Vulnerability?

A **vulnerability** is a **weakness in software or systems** that attackers can exploit to:
*   Gain unauthorized access
    
*   Expose or steal sensitive data
    
*   Escalate privileges or disrupt operations
    
These weaknesses might stem from:
*   Poor code practices (e.g., SQL injection)
    
*   Weak authentication (e.g., default passwords)
    
*   Misconfigurations (e.g., open ports or missing encryption)
    
In cloud environments, managing vulnerabilities is more difficult because of:
*   The **ephemeral** nature of workloads (e.g., auto-scaling groups that spin up and down)
    
*   The use of **third-party components** not directly managed by your organization
    

> **Example**: Think of a vulnerability like a hidden glitch in a competitive game—maybe a bug in _Fortnite_ that lets someone shoot through walls. If players (attackers) discover it before the developers do, they can gain an unfair advantage until it's patched.

* * *

### What Is a CVE? 🔖


**CVE** stands for **Common Vulnerabilities and Exposures**. It's the **industry-standard system** for assigning unique identifiers to known vulnerabilities.
*   Managed by the **CVE Program**, sponsored by **CISA** (U.S. Cybersecurity and Infrastructure Security Agency)
    
*   Active for over **25 years**, it serves as the backbone for vulnerability tracking in cybersecurity
    
*   Each **publicly disclosed vulnerability** receives a unique CVE ID (e.g., `CVE-2024-12345`)
    
*   The CVE system fosters **transparency** and **collaboration** in the security community
    

#### **Wiz as a CVE Numbering Authority (CNA)** ⚔️

In **2024**, **Wiz became a CVE Numbering Authority** (CNA), which means:
*   Wiz can **assign CVE IDs** to newly discovered vulnerabilities
    
*   This empowers Wiz to **share discoveries quickly and publicly**, helping protect the wider community
    
*   It reinforces Wiz’s role as a **contributor to global threat intelligence**
    

> **Analogy**: Becoming a CNA is like being part of the _official referee team_ in esports. You don't just play the game—you set the rules and alert everyone when someone finds an exploit that could ruin it for others.

* * *

### Why It Matters 🚀

*   Vulnerabilities are **constantly evolving**, and keeping up requires more than just tools—it requires **timely intelligence**.
    
*   Cloud environments are **highly dynamic**, and traditional vulnerability scanning can't keep up alone.
    
*   Wiz’s integration of **vulnerability feeds**, its **CNA status**, and **automated scanning** means faster identification, more reliable data, and **actionable findings** across your environments.



* * *
### How Vulnerability Findings Work in Wiz 🔎

When Wiz detects a vulnerability in your environment, it adds a **vulnerability finding** to the **Security Graph**. Each finding is specific to a resource (e.g., a file in a container, a vulnerable library on a VM).

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/2K8juzy.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Vulnerability Findings Dataflow</div>
</div>
<br>

However, a single vulnerability may not be critical by itself. **When combined with other risk factors**—such as an exposed secret or a lack of network segmentation—it can create a **“toxic combination”**, which Wiz refers to as a **Wiz issue**. These issues help you prioritize what's _actually_ urgent to fix.

* * *
### Wiz Vulnerability Scanning Architecture: How It All Works 🏗️


Wiz uses a **multi-layered architecture** to identify vulnerabilities across the entire cloud lifecycle—from developer desktops to cloud production environments. Let’s break it down:



#### **1. Data Collection: API & Workload Scanning** 📡

Wiz starts by **gathering data** from the customer environment using:
*   **API scanning** through cloud connectors  
    (e.g., querying your AWS, Azure, or GCP accounts)
    
*   **Workload scanning**, including:
    *   Virtual machines (VMs)
        
    *   Containers
        
    *   Serverless functions
        
Scanners also analyze:
*   **Container images** in registries (e.g., Docker Hub, Amazon ECR)
    


#### **2. Data Flow: From Scan to Detection** 🌍

Once the environment is scanned:
*   All data is shipped to Wiz’s **Disk Analyzer**.
    
*   The **Vulnerability Engine** processes the scan results.
    
Here’s what happens next:
*   The scanned file metadata (e.g., packages, libraries, binaries) is **matched against the Wiz Vulnerability Catalog**.
    
*   If a match is found with a known vulnerability (e.g., a CVE), a **Vulnerability Finding** is created.
    
*   The finding is added to the **Security Graph** (if it’s high/critical or CISA KEV) or appears in the **Vulnerability Findings page**.
    

> **Example**: Think of this like scanning your PC with _Steam’s anti-cheat_, which then checks against a big cheat database. If it detects a known “cheat,” it flags your system. That’s what the vulnerability engine does with known CVEs.


#### **3. Runtime Validation with the Wiz Sensor** 🕔

The **Wiz Sensor** can validate whether the vulnerability is **actually being used at runtime**:
*   It checks whether the vulnerable code is actively loaded or executed in the running workload.
    
*   This helps reduce **false positives** and prioritizes **real threats**.
    

#### **4. Shifting Left with the Wiz CLI** ⌨️

The **Wiz CLI** (Command Line Interface) is a **lightweight executable** that empowers developers and DevOps teams to **catch vulnerabilities earlier**—before code ever reaches production.
You can use the Wiz CLI:
*   **In local development**:  
    Integrate with **VS Code** to scan for vulnerabilities directly on a developer’s machine.
    
*   **In CI/CD pipelines**:  
    Automatically scan code and containers during build or deployment stages.
    

> **Example:**: Think of the Wiz CLI like _Linting for security_—instead of just fixing bad formatting or unused variables, it tells you, “Hey, this library you’re importing is vulnerable. Patch it now.”



### Where Vulnerabilities Are Found 🔐

Wiz identifies vulnerabilities **across the entire development and deployment lifecycle**, not just in production environments. Vulnerability findings can appear in:
*   **Virtual machines**
    
*   **Containers**
    
*   **Serverless functions**
    
*   **Developer workstations**
    
*   **Standalone applications**
    
*   **Code and CI/CD pipelines**
    
Wiz enables **end-to-end visibility**, from the moment code is written to when it's deployed in the cloud—what Wiz calls **“code to cloud” security**.

Wiz uses **several methods** to detect vulnerabilities, depending on the type of component and where it's running:

| **Detection Type** | **Purpose** | **Examples** |
| --- | --- | --- |
| **Package Detection** | Identifies vulnerabilities in OS packages | `apt`, `yum`, `dnf`, Windows KBs |
| **Library Detection** | Scans app libraries & frameworks | Python (pip), Java (Maven), PHP (Composer) |
| **File Detection** | Finds vulnerable system files | DLLs, drivers, binaries |
| **OS Detection** | Detects kernel-level or vendor-supplied issues | Linux kernel, Google COS, Windows KB |
| **Hash-Based Detection** | Identifies known JAR files via their hash | Java archive (.jar) detection in Maven builds |
| **CPE Matching** | Matches tech to vulnerability sources | HAProxy, Angular, Oracle JDK |
| **OVL (Overlapping Vulnerability Logic)** | Goes beyond version match | Looks at registry keys, configs, permissions |

> **Example**: Think of Wiz like _Geralt in The Witcher_. Each type of monster (aka component) needs a different method to identify and defeat it—silver sword, potion, spell. Wiz does the same, using different detection tools for different system components.


* * *

### Runtime Validation & SCA (Software Composition Analysis) 🖥️

Wiz can:
*   Validate whether a vulnerability **actually exists in runtime** (e.g., if the vulnerable package is loaded and used).
    
*   Analyze **open-source library dependencies**, both direct and **transitive** (dependencies of dependencies), using **SCA**.
    
*   Scan **code artifacts in CI/CD pipelines** before they reach production.
    

> **Example:**: Think of a vulnerability finding like discovering an old plugin in your _Minecraft_ server that could let anyone log in as an admin. If it’s installed but unused, that’s one thing—but if it’s active and accessible, then you’ve got a real problem. Wiz can tell the difference.

* * *

### **Vulnerability Data Feeds & Scoring** 📊

Wiz maintains a **Vulnerability Catalog**, updated **daily** or in real-time during critical security events. 

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/c3VMpWJ.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Vulnerability Catalog</div>
</div>
<br>

This catalog includes all known vulnerabilities, whether or not they currently exist in your environment.

#### **Sources Wiz Uses for Its Catalog:**

*   National Vulnerability Database (NVD)
    
*   ExploitDB
    
*   Cloud Service Providers (CSPs)
    
*   Product-specific advisories
    
*   GitHub Security Advisories
    
*   And many more...
    

#### **Scoring System** 📚

*   Wiz uses the **CVSS (Common Vulnerability Scoring System)** to assign severity.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/Zhe68WN.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Vulnerability Finding </div>
</div>
<br>

*   **However**, for _vulnerability findings_, Wiz **prioritizes vendor severity** over NVD severity, offering a more accurate risk picture.
    
*   Both **NVD** and **vendor severities** are shown in the vulnerability finding details.
    

* * *

### **Third-Party Integrations** 🔗

To support incident response workflows, Wiz can forward vulnerability data to:
*   **SOAR tools** like _QRadar_ and _Cortex XSOAR_
    
*   **SIEM platforms** like _Azure Sentinel_ and _Splunk_
    
*   Other third-party systems via APIs or native integrations
    

* * *

### **Pro Tip** ⏳

A **newly added CVE** will only generate findings during the **next scan** of your environment, so there might be a **24–48 hour delay** between public disclosure and visibility in Wiz.

> **Example**: Imagine _LOL_ just released patch notes and someone finds an exploit 30 minutes later. Wiz is like the anti-cheat that reads those patch notes, waits for your system to load the next game, and then flags if you’re still using the broken item.

* * * 

### The Wiz Security Graph vs. Vulnerability Findings Page 🗒️

Wiz processes **huge volumes of vulnerabilities** across dynamic cloud environments. To keep performance high and avoid information overload, **not all vulnerabilities appear in the Security Graph**.

#### **What's Included in the Security Graph?**

Only the most urgent vulnerabilities are shown, specifically:
*   **High** and **Critical** severity vulnerabilities
    
*   **CISA KEV-listed CVEs** (Known Exploited Vulnerabilities)
    
These are considered the most likely to contribute to **toxic combinations** and real-world exploits, so they’re prioritized for visibility and response.

#### **Where to Find the Rest?**

All other vulnerabilities (including lower-severity ones) are available on the:
*   **Vulnerability Findings Page**  
    This page is optimized for **searching, sorting, filtering, and investigating** vulnerabilities in bulk.

### **What Is a Vulnerability Object?** 📚

A **Vulnerability Object** represents a **known vulnerability in general terms**—it’s not tied to any specific resource in your environment. Think of it as the _“encyclopedia entry”_ for a vulnerability.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/G4eDXMr.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Vulnerability Object</div>
</div>
<br>

It includes:
*   **CVE ID** (e.g., `CVE-2024-12345`)
    
*   **Description of the issue**
    
*   **Attack vector** (e.g., network, physical)
    
*   **Exploitability info**
    
*   **References to public advisories**
    
*   **Severity** (from NVD and vendors)


### **Vulnerability Reporting in Wiz**

Wiz offers **built-in reports** for vulnerability findings. You can generate:
*   **One-time reports** for audits or snapshots
    
*   **Scheduled reports** (daily, weekly, etc.) to keep stakeholders informed over time
    
These reports help:
*   Track progress on remediation
    
*   Share data with compliance teams or external tools
    
*   Support vulnerability management programs