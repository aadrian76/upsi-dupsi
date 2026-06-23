
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
|                 | 05/03/2025              | Wiz Modules Added                             |


<br>

---


# ☁️ The Evolution of Cloud Risk Assessments and Security

In terms of the cloud security journey we need to understand how a few concepts involved and how they led to the current point.

First of all we need to understand how the risk assesments have evolved, some cloud technologies and some early attempts to secure the cloud and how they fell short and some of the gaps.

## 1. Traditional Risk Assessments (On-Premises)

Organizations traditionally conducted **on-premises risk assessments** focused on infrastructure, network, data, and physical security. These were aligned with best practices but came with **major limitations**:

- **Snapshots in time** – not continuous. *(Because attackers politely wait for your next scheduled audit.)*
- **Expensive** and resource-intensive.
- **Limited visibility** over dynamic environments.
- **Slowed down business innovation.**
- Required **deep technical expertise** to fix issues.
- Involved **many siloed teams.**



## 2. The Rush to the Cloud

The adoption of cloud technologies (IaaS, PaaS, SaaS) promised flexibility and scale. However, it also introduced **unexpected challenges**:

- Freedom to build from anywhere.
- Unprecedented speed of innovation.
- Microservices architecture across multi-cloud environments. *(Sounds great until you need to secure it...)*
- **Massive complexity** and fragmented architecture.
- **Limited visibility** into cloud workloads.
- No centralized management or tooling.


## 3. Early Attempts at Cloud Security

Security teams responded by **"lifting and shifting"** on-premises tools to the cloud. This introduced partial security coverage with **unintended consequences**:

> "Legacy tools were ported into the cloud, often failing to provide true cloud-native visibility and protection."

These created a fragmented toolbox of Gen 1 cloud tools:

- **CASB** – Monitored access to SaaS applications.
- **SASE / SSPM** – Network and serverless protections.
- **CSPM** – Analyzed configuration and compliance.
- **CIEM** – Managed identity and permissions.
- **DSPM / KSPM** – Focused on specific areas like data or Kubernetes.
- **CWPP** – Protected workloads using agents.

Each tool addressed a **specific slice**, but none provided **unified, contextual security**. *(The infamous security jigsaw puzzle.)*



## 4. Gaps and Customer Pain Points

As cloud adoption matured, these siloed tools led to **critical gaps**:

### Common Cloud Security Challenges:
- 🔍 **Lack of visibility**
- ⚙️ **Pace of change** *(The only constant in cloud is change!)*
- 🔀 **Architectural complexity**
- ❓ **Lack of context**
- 🚨 **Alert fatigue**
- 📚 **Outdated knowledge and skills** *(Yesterday’s solutions for tomorrow’s problems...)*
- 🧩 **Fragmented solutions for shared requirements**
- 🎯 **Cloud-savvy adversaries**



## 🧩 Common Limitations Across Gen 1 Tools

- 🔍 **Fragmented visibility** – No full picture of identity, workload, network, data.
- 🧱 **Siloed** – Tools operate in isolation, no risk correlation.
- ⚙️ **Agent-based or API-restricted** – Limited coverage, operational friction.
- ❌ **No true risk prioritization** – Cannot determine exploitability or blast radius.
- 🔄 **Reactive, not proactive** – Lack of continuous, integrated monitoring.

---

# 🛡️ CNAPPs: A New Approach with Wiz & Prisma

Cloud-native platforms like **Wiz** and **Prisma Cloud** address these issues with a **unified security platform** called **CNAPP (Cloud-Native Application Protection Platform)**.

### What CNAPP Platforms Provide:
- ✅ Unified view of cloud risks across identities, data, workloads, and configurations.
- 🚀 Agentless or low-friction deployment. *(Because life’s easier without a thousand agents.)*
- 📊 Context-aware prioritization – combines exposure, vulnerability, permissions, and data sensitivity.
- 🔄 Continuous monitoring and automated posture management.
- 💡 Scalable for multi-cloud and hybrid environments.



## ✅ Real-World Example: Wiz in Action

### 🎯 Scenario:
A container is deployed in AWS ECS with the following characteristics:

- Running a vulnerable version of `log4j`.
- Exposed to the internet via an open security group.
- Hardcoded secret key in the container.
- Over-permissioned IAM role with access to a sensitive S3 bucket.



### 🔍 With Gen 1 Tools:

- **CSPM** may flag the open security group.
- **CWPP** may detect the log4j vulnerability.
- **CIEM** could flag IAM role permissions.
- **DSPM** might notice S3 access to sensitive data.
- But none of them **correlate the findings** or escalate it as a high-risk incident. *(Result: Lots of alerts, little clarity.)*



### ✅ With Wiz:

- Wiz **correlates all the signals** across configuration, identity, network, vulnerabilities, and secrets.
- Identifies the **real risk**: the container is internet-exposed, vulnerable, and holds credentials that allow access to sensitive data.
- Raises this as a **critical, exploitable risk** for immediate response. *(“You should probably fix this now” is a pretty clear message.)*



## 🚀 Summary: Why CNAPP Matters

| **Legacy Tools** | **CNAPP (Wiz, Prisma)** |
|------------------|-------------------------|
| Siloed | Unified platform |
| Limited visibility | Full-context, agentless coverage |
| Basic misconfiguration checks | Deep analysis: identity, data, exposures, and vulns |
| Reactive | Proactive and continuous |
| Alert fatigue | Risk-based prioritization *(Because quality beats quantity in security alerts.)* |




# 🌐 Challenges in Securing Modern Cloud Environments

Modern cloud environments are incredibly powerful but also **highly complex**. These challenges can be broken down into three critical areas:

---

## 🏗️ Complex Environment

### Multiple Clouds
Organizations often operate across **AWS, Azure, GCP, and Kubernetes**, creating fragmentation.

### Multiple Architectures
Includes **VMs, containers, serverless, and PaaS**, each with its own security model and risks.

### Thousands of Technologies
The number of **services, apps, libraries, and APIs** is growing exponentially, making manual management nearly impossible.

---

## ⚠️ Complex Risk

### Effective Internet Exposure
What is **actually exposed** to the internet? Many environments have hidden exposures due to misconfigurations.

### Vulnerabilities & Misconfigurations
What risks make your assets vulnerable? This includes **unpatched software, open ports, weak IAM roles**, etc.

### Lateral Movement
What is the **effective internal access** if an attacker breaches a single point? Lateral movement is often overlooked.

---

## ⚙️ Complex to Operationalize

### Lack of Visibility
Most teams do not have a **complete, unified picture** of the cloud environment. Data is scattered across tools.

### Complex Suite of Tools
Security is managed across **5+ different tools** — each with agents, APIs, sidecars, and different data sources.

### Lengthy Time to Resolve
Due to fragmented ownership (**security, DevOps, developers**), it takes a long time to respond to issues.

---

## 🎯 Why This Matters

> Without addressing these complexities, cloud environments remain **vulnerable, fragmented, and difficult to secure** effectively.

Modern solutions like **CNAPP (Wiz, Prisma Cloud)** are designed to tackle these exact pain points by unifying visibility, context, and control in a single platform.


# 🚀 How Wiz affront this siutation: A Modern Approach to Cloud Security

Wiz provides a **cloud-native, agentless CNAPP solution** that secures entire cloud environments by combining deep analysis with unified risk prioritization and remediation.

---

## 1️⃣ Agentless Scan of Cloud and Workloads

Wiz performs a 100% API-based approach **agentless, read-only scans** across all layers of your environment:

- **Serverless** (e.g., AWS Lambda, Azure Functions)
- **Containers** (e.g., ECS, GKE, AKS, EKS)
- **Virtual Machines** (across AWS, Azure, GCP)
- **PaaS Services** (databases, storage, services)

> ⚡ No agents, no sidecars, no performance impact.

---

## 2️⃣ Perform a Deep Cloud Assessment

Once done the API scans, a deep assessment of the cloud is performed with:

### 🔍 Traditional Scanning:
- Vulnerabilities and missing patches
- Misconfigurations
- Malware detection
- Sensitive data discovery

### 🧠 Wiz Cloud Risk Engine:
- **External exposure** mapping
- **Excessive permissions** detection
- **Exposed secrets**
- **Lateral movement** path discovery

### 🧪 Wiz Threat Research:
- Continuously updated with novel cloud vulnerabilities and attack patterns.

---

## 3️⃣ Prioritize the Most Critical Risks

Wiz correlates all signals across the environment to identify **real attack paths**, highlighting the **risks that matter most**, such as:

- A vulnerable container **exposed to the internet**
- A secret inside a VM with **excessive access rights**
- Serverless function with **open access** and sensitive data

> 🎯 Prioritization based on actual exploitability and blast radius, not just raw findings.

---

## 4️⃣ Proactively Harden Your Cloud

Wiz helps teams **respond and remediate quickly**, through:

### 🔄 Partner Integrations:
Over **20+ integrations** including:
- Slack
- Jira
- ServiceNow
- PagerDuty

### 🛠️ Cloud Remediation:
- **One-click remediation**
- Automated security workflows
- Policy-driven hardening

### 🔧 CI/CD Guardrails:
- **One policy** across containers, VMs, IaC
- Container and VM image scanning
- Infrastructure-as-Code (IaC) template scanning
- Kubernetes Admission Controllers

---

## ✅ Result

> Wiz enables teams to secure their cloud **continuously**, **comprehensively**, and **collaboratively** — from Dev to Sec to Ops.
---
## Request Access to Wiz Partner Portal Accenture

1. Go to <https://partners.wiz.io/English/>
2. Select Request Access
3. Type your Accenture email address
4. Select **Proquire LLC (Partner) Chicago, Illinois, USA** to continue.
5. Check your Inbox for an email from Wiz. The email will contain the credentials to login.
---

## Wiz: Cloud Security Platform


Wiz is a comprehensive cloud security platform designed to provide full visibility, protection, and risk management throughout the entire lifecycle of cloud applications. Its unified, agentless approach enables advanced security measures without negatively impacting system performance.

**Key Features**

- Agentless security for cloud environments.

- Comprehensive risk assessment and real-time threat detection.

- Seamless integration with development, security, and operations tools.

- Prioritization of critical risks and reduction of the attack surface.


## Wiz Modules
Wiz is divided into several powerful modules, each focusing on a different aspect of cloud security. Below, we explore the core modules of Wiz.

---


### Wiz Code

Wiz Code ensures visibility and security throughout the development phase of cloud applications. It integrates seamlessly with development environments and CI/CD pipelines, providing end-to-end protection.

**Key Features**

- **360° Visibility:** Establishes direct connectivity with version control systems and CI/CD pipelines for immediate insights.

- **Graph-Based Contextualization:** Visualizes the relationships between cloud resources and application code.

- **Fundamental Code Risk Assessment:** Includes Software Composition Analysis (SCA), Software Bill of Materials (SBOM) generation, Infrastructure as Code (IaC) scanning, malware detection, and secret exposure analysis.

- **Security Posture Management in Pipelines:** Strengthens version control, authentication, authorization, and change management policies.

- **Toxic Combinations Analysis:** Detects and prioritizes potential attack vectors and security vulnerabilities.

- **Automated Remediation and Prevention:** Provides intelligent recommendations and automatic fixes within IDEs, pull requests, and CI/CD workflows.
---

### Wiz Cloud

Wiz Cloud is a comprehensive cloud security platform designed to provide full visibility, protection, and risk management across the entire lifecycle of cloud applications.

### Wiz Essentials
Wiz Essentials offers foundational cloud security capabilities to enhance visibility and risk mitigation within cloud environments. It includes:

- **Agentless Scanning**: Provides comprehensive security assessments without requiring agents.  
- **Wiz Security Graph**: Offers a visual representation of the cloud security architecture, enabling better risk assessment and analysis.  

- **Toxic Combinations**: Identifies critical security risks by detecting dangerous combinations of vulnerabilities and misconfigurations.  
- **Developer Tools**: Facilitates collaboration between security and development teams, integrating security measures within development workflows.  
- **Threat Center**: Serves as a centralized hub for identifying and remediating newly discovered vulnerabilities.  

### Wiz Advanced
Wiz Advanced builds upon Wiz Essentials by incorporating additional security measures for enhanced threat detection, response, and automation. It includes:

- **Advanced Security Controls**: Performs automated attack path analysis, Data Security Posture Management (DSPM), and host configuration assessments.  
- **CI/CD Security Guardrails**: Extends Wiz security capabilities into CI/CD pipelines through Wiz CLI, ensuring security policies are enforced during development and deployment.  

- **Cloud Detection and Response (CDR)**: Continuously monitors cloud resources in real time, detecting and contextualizing threats to enable rapid prioritization and mitigation.  
- **Wiz Runtime Sensor**: Provides real-time workload protection and risk validation within execution environments, ensuring security at runtime.  
- **Advanced Workflow Automation**: Supports features such as auto-remediation, custom reporting, and enterprise-grade integrations to streamline security operations.  
---
 
### Wiz Defend

Wiz Defend enables Security Operations (SecOps) teams to overcome the challenges of cloud threat detection and response. It leverages Wiz's cloud threat intelligence and Security Graph to provide comprehensive coverage and contextual insights from code to cloud.

**Key Features**

- **Unified Log Collection and Retention:** Seamlessly integrates supported log types within minutes, enhancing detection coverage and visibility.  

- **Threat Detection:** Identifies anomalies, behavioral threats, and signature-based attacks to detect any potential cloud security risks.  

- **Graph-Based Analysis:** Provides deep contextual insights and visual representations of attack timelines and their impact radius.  

- **Focused Cloud Threat Investigation:** Ensures continuous coverage for emerging attack types and techniques, allowing proactive threat management.  

- **Simplified Investigations:** Presents an intuitive attack timeline to facilitate a clear understanding of security incidents and the necessary response actions.  

- **Precision Remediation:** Enables direct response actions at the control plane or workload layer while identifying root causes and providing actionable remediation steps.  


### Solutions
Wiz helps you identify, analyze, prioritize and remediate risks from many different sources:
- AI Security
- API Security
- Compliance
- Container & Kubernetes Security
- Data Security
- Identity Security
- Secure Cloud Configuration
- Secure Host Configuration
- Secure Use of Secrets
- Service Catalog
- Vulnerability Management
- External Attack Surface

### Coverage

#### Cloud Service Providers

Wiz offers feature parity across the three main cloud service providers (CSPs) and is continually expanding support for others.

- Alibaba
- AWS
- Azure
- GCP
- Linode
- OCI
- VMware

#### Data & AI
Connect Wiz to data and AI tools to add a wide variety of risk assessments, enrichments, and workflows.

- OpenAI
- Snowflake

Security & Identity

- CrowdStrike
- Okta

#### Kubernetes

Connect Wiz to your Kubernetes clusters to identify risks associated with Kubernetes-specific identities, secrets, configurations, etc. as well as map cluster architectures.

- AKS
- EKS
- GKE
- OKE
- OpenShift
- Self-managed Kubernetes

#### Container registries

Connect Wiz to your container registries to scan container images at rest and identify risks such as vulnerabilities and potentially sensitive data.

- Generic Registry
- Docker Hub
- ECR
- JFrog

### Additional capabilities

Wiz offers a wide variety of innovative and useful features to make your life better and your day more productive:

- Wiz Integrations (WIN)
   
  Share information between Wiz and other third-party tools for greater context in your cloud security ecosystem. Improve your visibility and efficiency by sending one-way or bi-directional data across platforms, and set up Actions and Automation Rules in Wiz to push only the most pertinent information.

- Threat Intelligence

   Wiz Threat Intelligence (Wiz TI) gathers information from the cloud threat landscape to keep you informed about the latest threats to your environment. Wiz TI identifies Indicators of Compromise (IoCs), explores the Tactics, Techniques, and Procedures (TTPs) utilized by threat actors, and discerns threat behaviors. It enables organizations to mitigate risks and improves their ability to detect and respond to actual threats.

- Wiz Outpost

- Wiz for Gov

- Wiz Terraform Provider

- Ask AI

- System Health

- Wiz Browser Extension

- Security Graph