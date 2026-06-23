<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>

  [[_TOC_]]

</details>

  

## 📝 Changelog
<br>

| Author                            | Modification Date       | Changes                                       |
|-----------------------------------|-------------------------|-----------------------------------------------|
|                 | 25/02/2025              | First Version Created                         |


<br>
 
<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b><span style="color:#7C3AED; font-size: 17px;">💡 READ THIS FIRST</span></b>
    <br><br>
    This training isn't a <b>"read and move on"</b> kind of thing—it's a <b>starting point</b>. You're expected to <b>research</b>, <b>think beyond what's here</b>, and <b>dig deeper</b>.
    <br><br>
    The resources provided are just a guide. Use them, but don't stop there.
    <br><br>
    <span style="color:#7C3AED;"><b>Security is about curiosity and problem-solving</b></span>. If something doesn't make sense, <b>figure it out</b>. If it seems too easy, you're probably missing something important.
    <br><br>
   Or, if you want to get all philosophical about it, Einstein said it best: <i>"I have no special talent. I am only passionately curious."</i>
</div>

# Service Line Basics

## Services 🚀

- **Security Posture Optimization**  
  - Identifying the right roadmap to strengthen a client’s security posture
  - Proposing priorities based on client objectives
  - Designing alert workflows and incident communication
  - Creating dashboards and reports aligned to client needs

- **CNAPP Administration and Operation**  
  - Deploying CNAPP solutions
  - Managing CNAPP tools
  - Troubleshooting and supporting incident resolution in CNAPP
  - Advising on CNAPP tool usage to maximize capabilities
  - Automations via scripts for routine tasks

- **Remediation Service**  
  - Addressing SOC findings (external/internal vulnerabilities)
  - Remediating cloud infrastructure SOC findings
  - Ensuring cloud infra SOC compliance

### 1.  File Organization 🗂

All work is stored in two primary places:

- **Teams**: For discussions, collaboration, file sharing
- **AzureDevOps**: For version control, backlog management, documentation

#### Teams 💬

We use **Microsoft Teams** as the main communication hub for this service line. It holds discussions, shared files, meeting notes. Plus, we use **Microsoft Planner** within Teams for tasks, ensuring better organization and tracking of ongoing work.

📌 **Access the Teams Channel**: [Teams Channel](https://teams.microsoft.com/l/channel/19%3A70f5e16b80c54da7811d58c1aa162c2f%40thread.tacv2/%5BSL%5D%20Security%20Posture%20Management?groupId=25acf240-d040-4048-b94f-21e613ed9a8b&tenantId=e0793d39-0939-496d-b129-198edd916feb)  
📌 **Access the Planner**: [Planner](https://teams.microsoft.com/l/entity/com.microsoft.teamspace.tab.planner/_djb2_msteams_prefix_1834336748?context=%7B%22channelId%22%3A%2219%3A70f5e16b80c54da7811d58c1aa162c2f%40thread.tacv2%22%7D&tenantId=e0793d39-0939-496d-b129-198edd916feb)

#### File Structure

<div class="tg-wrap"><table><tbody>
  <tr>
    <td><b>01 General Assets</b><br><pre>+---00 Templates
¦   +---01 - Accenture Resources
¦   +---02 - Project Management
+---01 Comparativas
+---02 Vendors
¦   +---Vendors assets
¦   +---Vendors information
+---03 Other</pre></td>
    <td>The <b>General Assets</b> folder stores reusable artifacts for different clients and projects.<br><br>
    <ul>
      <li><b>Templates</b>: Word, PowerPoint, Excel templates with Accenture branding, plus icons.</li>
      <li><b>Comparisons</b>: Documents comparing various CNAPP solutions.</li>
      <li><b>Vendors</b>:
        <ul>
          <li><b>Vendors assets</b>: Our own scripts, custom policies, or automations.</li>
          <li><b>Vendors information</b>: Stuff directly from the vendors.</li>
        </ul>
      </li>
    </ul>
    </td>
  </tr>
  <tr>
    <td><b>02 Initiatives</b><br><pre>+---01 Campañas
+---02 SL Slide decks
¦   +---Capacidades Prisma Cloud
¦   +---Guias usuario
+---03 Activos propuestas
+---04 Workshops provided by Accenture
¦   +---EJIE Workshop
¦   +---ORANGE Workshops
¦   +---SIEMENS Workshop
¦   +---WIZ Workshops
+---05 Other</pre></td>
    <td>Key subfolders:<br><br>
    <ul>
      <li><b>Campañas</b>: Presentations highlighting the service line’s value for prospective or existing clients.</li>
      <li><b>SL Slide Decks</b>: Central collection of slides we’ve created (assets, proposals, add-on services).</li>
    </ul>
    </td>
  </tr>
  <tr>
    <td><b>03 Security Posture Optimization<br>04 CNAPP Administration and Operation<br>05 Remediation Service</b></td>
    <td>Each folder has assets related to that specific service. For example, under "03 Security Posture Optimization" you’d find docs relevant to posture assessments, roadmaps, etc.</td>
  </tr>
  <tr>
    <td><b>06 Projects</b><br><img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/projects.png" width="150"></td>
    <td>Holds both active and completed projects.<br><br>
    <ul>
      <li>Green = active project</li>
      <li>Red = completed project</li>
    </ul>
    </td>
  </tr>
</tbody></table></div>

#### AzureDevOps 🚀

**Azure DevOps** is our primary platform for code, repos, pipelines, and tool management. It ensures versioning and tracking of all dev efforts. We also maintain a **Wiki** in Azure DevOps to store doc on automations and tools for the service line—keeping everything up to date and accessible.

📌 **Azure DevOps**: [Link](https://dev.azure.com/Cloud-Application-Security/Security%20Posture%20Management)

</div>

### **🛠 2. Practical Exercises**

Now, apply what you just learned through these tasks. 

The tasks **must** be completed in order. Don't skip ahead. But most importantly, **DO NOT HALF-ASS them**—you'll only make more work for yourself later.
* * *
####**📝 Task 1 — Cloud Architecture Re-Design Challenge**

**Scenario.** A hobby project from _Lola Lolita_ just went viral. Right now **everything runs on a single t3.micro EC2 instance** that hosts:
*   a containerised Node.js API (`docker run -p 80:3000 node:18-alpine app.js`)
    
*   an SQLite file sitting on the same disk
    
*   a default security group with **SSH & HTTP open to 0.0.0.0/0**
    
*   no backups, no monitoring, no tags
    
**Mission:** propose a _minimal-touch_ upgrade path that achieves basic availability, security and cost control—**without** introducing RDS, Kubernetes or any managed service the team can’t learn in a weekend.

|  |  |
| --- | --- |
| **What to deliver** | 1. **“As-Is” sketch** (hand-drawn, draw.io or Lucid) – keep it raw.  <br>2. **“To-Be” sketch** highlighting only the components you add.  <br>3. **Action board** (Low/Medium/High Effort × Impact) for **5–6** specific improvements.  <br>4. One **FinOps KPI** you would track (e.g. “$ per 10 k API calls”). |
| **Must-have requirements** | • 1½ pages max, landscape PDF.  <br>• Use AWS official icons.  <br>• Each action tagged with at least one metric it boosts (RTO, RPO, MTTR, Cost). |
| **💡 Pro-tips** | • Start with _no-regret_ moves: attach an EBS snapshot schedule, enable CloudWatch basic alarms, restrict SSH to your office IP.  <br>• Explain why **Elastic IP + Auto-Recovery** might be “good-enough” HA for now. |
| **⚠️ Fails if…** | – You suggest “Migrate to EKS” without business justification.  <br>– The target diagram still shows 0 backups or ports wide open. |

* * *
#### **📝 Task 2 — Dockerfile + Trivy Quick Lab**


**Objective.** On Ubuntu, build a lean container image, scan it, and fix at least one high-severity vulnerability. **45 min max**—don’t over-engineer.

|  |  |
| --- | --- |
| **What to deliver** | 1. `Dockerfile` (< 12 lines) multi-stage or Alpine-based  <br>2. _Before_ & _after_ Trivy scan logs (`.txt` or Markdown fenced blocks)  <br>3. Final image size proof (`docker images` output)  <br>4. Mini README with a single-line run command |
| **Must-have requirements** | • Final image < 300 MB  <br>• High CVE fixed (≥ CVSS 7.0)  <br>• No root user inside container (`USER app`) |
| **💡 Pro-tips** | • Use `--no-cache` and clean apk/apt caches.  <br>• `trivy config` also scans your Dockerfile—earn bonus points fixing bad practices. |
| **⛔ Hard stop** | Image > 500 MB or any _critical_ CVE unfixed. |

* * *
#### 📝 **Task 3 — Hello-K8s Deployment (re-using your image)**

Take the image from the task 2, deploy it to a **local cluster**, and prove a zero-downtime rolling update.

|  |  |
| --- | --- |
| **What to deliver** | 1. `deployment.yaml` (≤ 60 lines) with 2 replicas, `readinessProbe` and `imagePullPolicy: IfNotPresent`  <br>2. CLI recording — screenshot or short GIF — of `kubectl get pods -w` during an image tag upgrade  <br>3. Curl output showing old ➝ new version without HTTP 500s |
| **Must-have requirements** | • Namespace `demo` (hard-code it)  <br>• Rolling update strategy: `maxSurge: 1`, `maxUnavailable: 0`  <br>• Works offline (no external image registry dependencies) |
| **💡 Pro-tips** | • Pin the initial tag `:0.1`, then rebuild as `:0.2` to trigger update.  <br>• Add simple `/healthz` endpoint in your app so the readiness probe is meaningful. |
| **⚠️ Fails if…** | Pods restart-loop or service downtime > 3 s during update. |

* * *

#### **📝 Task 4 — SPM Gap-Analysis Brief**

The company _Riot Games_ now owns **4 AWS accounts + 3 Azure subscriptions** and “some GCP stuff nobody tracks”. They ask for a one-pager exposing their **Security Posture Management gaps** and a 90-day action plan.

| **Area**| **Current Environment Details** |
| --- | --- |
| **Estructura multicloud** | - **AWS** (4 cuentas):  <br>**aws-prod:** Global production games (EKS, EC2, RDS, DynamoDB, S3, CloudFront)  <br>• `aws-dev`: CI/CD, automated testing, ECR.  <br>• `aws-analytics`: Data lake (EMR, Redshift, Glue, Athena).  <br>• `aws-security`: Centralized GuardDuty, IAM Identity Center  <br>- **Azure** (3 subscriptions):  <br>• `az-prod`: Matchmaking & chat (AKS, Cosmos DB, App Gateway).  <br>• `az-dev`: Integration pipelines (Azure DevOps).  <br>• `az-ml`: AI training (Azure ML)  <br>- **GCP** (“untracked inventory”):  <br>• Proyecto `gcp-liveops`: Live Ops microservices (GKE, Cloud SQL).  <br>• BigQuery dataset (game telemetry).  <br>• Cloud Storage (legacy player backups) |  
| **Key Workloads** | - ~250 containerized microservices  <br>- Public APIs peaking >4 M requests/sec  <br>- Sensitive data: emails, player IDs, in-game purchase records (PCI SAQ-A) |  
| **Teams & Processes** | - **Cloud Platform Team** (8): manages IaC with Terraform; no unified landing zone <br>**Security Engineering** (5): 24/7 AWS detection/response; no Azure/GCP coverage.  <br>- **Game Teams:** deploy directly; weak IAM governance. |
| **Herramientas actuales** | - **AWS:** GuardDuty; Config (15 rules); IAM Access Analyzer (inactive); Security Hub (40 % coverage).  <br>**Azure:** Defender for Cloud enabled; not configured for containers  <br>**GCP:** no posture tools enabled <br>- **CI/CD:** SonarQube & Trivy for image scanning; no artifact signing |
| **Current Pain Points** | 1. No unified multicloud inventory → uneven visibility.  <br>2. 32 % of S3 buckets inadvertently public  <br>3. AAKS/GKE lack manifest scanning; Live Ops have cluster-admin rights  <br>4. Centralized logging only in AWS; missing Azure Monitor & Cloud Logging  <br>5. ~1,400 long-lived access keys (> 90 days)  <br>6. No IaC drift detection; frequent manual changes  <br>7. No common data classification/encryption framework |

**1. Maturity Heatmap (3 × 3 Example)**

Evaluate the maturity of each domain in AWS, Azure and GCP using the following color key:
*   🔴 Red = Absent
    
*   🟠 Orange = Initial
    
*   🟡 Yellow = Intermediate
    
*   🟢 Green = Advanced
    

| Domain / Cloud | AWS | Azure | GCP |
| --- | --- | --- | --- |
| **Asset Inventory** |  |  |  |
| **IAM / CIEM** |  |  |  |
| **Configuration Baselines** |  |  |  |
| **Workload Protection (K8s / VM)** |  |  |  |
| **Data Protection & Classification** |  |  |  |
| **Threat Detection & Response** |  |  |  |
| **DevSecOps / SDLC** |  |  |  |
| **Compliance & Reporting** |  |  |  |
| **Incident Response & Forensics** |  |  |  |

> **Deliverable:**  
> Fill in each cell with 🔴, 🟠, 🟡 or 🟢.  
> Justify every rating with evidence drawn from the provided environment context.


**2. Critical Gaps Analysis**

*   **Identify the 5 most critical security posture gaps** that pose the highest risk to the confidentiality, integrity or availability of Riot Games’ global gaming services.
    
*   **For each gap**, explain:
    *   What the gap is (e.g. no unified asset inventory).
        
    *   Why it matters (impact scenario).
        
    *   Which cloud(s) it affects.
        


**3. CNAPP Solution Proposal**

Propose a single **Cloud-Native Application Protection Platform** that spans AWS, Azure and GCP. In your write-up, be sure to cover:
1.  **Core Capabilities**
    *   How the platform consolidates:
        *   CSPM (Cloud Security Posture Management)
            
        *   CWPP (Cloud Workload Protection)
            
        *   CIEM (Cloud Infrastructure Entitlement Management)
            
        *   DSPM (Data Security Posture Management)
            
2.  **Required Integrations**
    *   Infrastructure-as-Code (Terraform, ARM/Bicep, CloudFormation)
        
    *   Container registries (ECR, ACR, GCR)
        
    *   CI/CD pipelines (e.g. GitHub Actions, Azure DevOps)
        
    *   SIEM / Log Management (Splunk, Sentinel, Chronicle)
        
    *   Ticketing / Workflow (Jira, ServiceNow)
        
    *   ChatOps / Alerting (Slack, Teams)
        
3.  **Licensing Considerations**
    *   Account-based vs. asset-based licensing
        
    *   Included vs. add-on modules (e.g. runtime agents, data scanning)
        
    *   Cost drivers (number of cloud resources, containers, user seats)
        
    *   Any minimum commitments or tiers
