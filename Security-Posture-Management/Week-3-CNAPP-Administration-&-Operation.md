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
|                   | 14/02/2025              | First Version Created                         |

<br>

---

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

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ LISTEN UP</span></b>
    <br><br> Before continuing, let me make one thing <b>very clear</b>. The <b>Training Path is not for us, but FOR YOU</b>. We don't really care about the content of your deliverables or how well you answer the questions. We care that you <b>LEARN</b>.
    <br><br>
    <b>We don't expect perfection, but we do expect effort.</b> Your work must be done by <b>YOU</b>, not by some LLM. AI-generated content is too obvious—even if you try to mask it. If we catch it, it's getting rejected. No excuses. No exceptions.
    <br><br>
    <b>Don't be that person.</b>
</div>

Before you do **anything**, make sure you've **read the Phases page**:
👉 **[📚 Fases](/✏️-Guía-del-Training/📚-Fases)**

If you skipped it, **go back now**—we’re not repeating everything here. That page explains:
- **Intern vs New Hire paths** (so you don’t ask)
- **Checkpoints & Expectations** (so you don’t ask)
- **How to approach exercises** (so you don’t ask)

If you still ask something that’s **clearly there**, we *will* judge you and maybe, just maybe, not answer.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b>☝️🥸 Google exists.</b> If you're stuck, use it. If you're still stuck, then ask—but ask <b>smart questions</b>
</div>

### 🛠 Practical Exercises

#### **📝 Task 1 — Module Matching (Quiz)**

**Instructions:** Match each feature to its Wiz module (Code, Cloud, Essentials, Advanced, Defend).

| Feature | Module |
| --- | --- |
| a. Generates an SBOM and scans your Terraform templates in CI/CD |  |
| b. Continuously analyzes runtime behavior in your VMs and containers |  |
| c. Correlates vulnerabilities, network exposure, identity risk, and data |  |
| d. Automates one-click remediation and policy-driven hardening |  |
| e. Ingests logs, detects anomalies, and builds attack timelines |

* * *
#### **📝 Task 2 — True / False: Wiz Architecture**

**Objective:** Check understanding of deployment models and scanners.
1.  Wiz Outpost moves both the Cloud Scanner and the Workload Scanner into your environment.
    
2.  Agentless scanning never uses snapshots or disk clones.
    
3.  The Cloud Scanner runs every 24 hours by default.
    
4.  Zero-copy mounts are used to share snapshots with Wiz for analysis.
    
5.  You must install an agent on every VM to use the Wiz Runtime Sensor.
* * *
#### **📝 Task 3  — Connector Deployment**

**Objective:** Walk through setting up a cloud connector.
1.  **Scenario:** You have a new AWS account under the `prod` OU.
    
2.  **Tasks:**
    *   Decide whether to deploy a connector at the Organization or Account level—and justify your choice.
        
    *   Write out (in pseudocode or actual Terraform) the steps to create the `WizAccessRole`, attach the required policies, and configure the trust relationship.
        
    *   Outline how you’d verify in the Wiz console that the connector is healthy and has full visibility.
* * *
#### **📝 Task 4 —  Design Challenge: Outpost vs. SaaS**

**Prompt:**  
A financial-services customer in the EU must ensure no VM disk data ever leaves their environment, yet still wants full runtime vulnerability scanning.
*   Draw a simple diagram comparing a pure SaaS deployment vs. an Outpost deployment.
    
*   List **three pros** and **three cons** of the Outpost model for this customer.
    
*   Recommend which model they should choose—and why.
* * *
#### **📝 Task 5 — Wiz Connector Deployments**

**Instructions**
1.  **Enroll & Access the _Wiz Tech Essentials_ Course**
    *   Sign up for a free account at the **Wiz Partner Academy**:  
        👉 [https://partners.wiz.io/academy](https://partners.wiz.io/academy)
        
    *   Access the **Wiz Tech Essentials** course.
        
    ![==image_0==.png](/.attachments/==image_0==-ce8e94ab-a57d-43d7-99c0-f36ec10c2063.png)
    
2.  **Complete the Following Labs in Order:**
    1.  **Self-Paced Lab — AWS Connector Deployment**
        
    2.  **Self-Paced Lab — Azure Connector Deployment**
        
    3.  **Self-Paced Lab — GCP Connector Deployment**
        
3.  **Deliverables**  
    For each lab, include the following in your submission:
    
🔹 **Common to All Labs**
    
   *   A **step-by-step summary** of what you did during the deployment.
        
   *   At least one **issue you encountered** (e.g., missing permissions) and how you resolved it.
        
   *   **Connector Health Page** screenshot in the Wiz portal showing a **Healthy** status.
        
   *   **Deployment status**:
        *   Screenshot when the deployment is in **Initializing** status.
            
        *   Screenshot when the deployment is **Active**.
            
   *   **Details page** of the connector deployment (showing cloud provider-specific information).
        
    
🔹 **AWS Lab Specific Screenshots**
    
   *   VM instance running in the AWS Console.
        
   *   IAM role creation in the AWS Console.
        
   *   S3 Bucket settings with **"Block all public access" set to OFF**.
        
    
🔹 **Azure Lab Specific Screenshots**
    
   *   VM instance in the Azure Portal.
        
   *   Apache Welcome page loaded from the VM.
        
   *   Azure Enterprise App creation.
       
   *   Screenshot of **`mystorageaccount` > Properties > Blob service**, showing **"Blob anonymous access" set to Enabled**.
        
   *   Terminal output of the connector deployment command.
        
    
🔹 **GCP Lab Specific Screenshots**
    
   *   Running VM instance in GCP.
        
   *   Public access configuration proving that the bucket is accessible over the internet.
        
   *   Terminal output of the connector deployment command.
        
4.  **Grading Criteria**
    *   All three labs completed in the specified order.
        
    *   All required screenshots are included, clear, and relevant.
        
    *   Well-structured narrative and issue resolution for each lab.
        

* * *

> **📤 Submission Format:**  
> Submit a **PDF document** including your written summaries, screenshots, and issue resolution for each lab.
* * *
#### **📝 Task 6 — Cloud Workload Scanning**

**Objective**  
Reinforce your understanding of workload scanning in AWS, Azure, and GCP by completing the official self-paced labs available in the Wiz Partner Academy.

**Instructions**
1.  **Enroll & Access the Course**
    *   Log in to your **Wiz Partner Academy** account:  
        👉 [https://partners.wiz.io/academy](https://partners.wiz.io/academy)
        
    *   Open the **“Wiz Tech Essentials”** course.
        
2.  **Complete the Following Labs in Order:**
    1.  **Self-Paced Lab — AWS Workload Scanning**
        
    2.  **Self-Paced Lab — Azure Workload Scanning**
        
    3.  **Self-Paced Lab — GCP Workload Scanning**
        

* * *

**Deliverables**  
For each lab, submit **only the screenshots** explicitly required in the lab instructions.
      

**Grading Criteria**
*   All labs completed in the correct sequence.
    
*   All screenshots clearly captured and aligned with lab instructions.
    
*   Visibility of relevant configuration details and results in the screenshots.
    

* * *

> **📤 Submission Format:**  
> Upload a **PDF document** with the required screenshots for each cloud provider’s lab.

* * *

#### **📝 Task 7 — Outpost Deployment**

**Objective**  
Gain hands-on experience deploying and validating the Wiz Outpost model in AWS and Azure by completing the official self-paced labs available in the Wiz Partner Academy.

**Instructions**
1.  **Enroll & Access the Course**
    *   Log in to your **Wiz Partner Academy** account:  
        👉 [https://partners.wiz.io/academy](https://partners.wiz.io/academy)
        
    *   Open the **“Wiz Tech Essentials”** course.
        
2.  **Complete the Following Labs in Order:**
    1.  **Self-Paced Lab — AWS Outpost Deployment**
        
    2.  **Self-Paced Lab — Azure Outpost Deployment**
        

**Deliverables**  
For the labs, your submission must include the following screenshots:
*   **AWS CloudFormation Stack Deployment:**
    *   Screenshot of the CloudFormation console showing the stack status as **CREATE_COMPLETE**.
        
*   **Wiz Portal - Connector Deployment Status for both**
    *   Screenshot showing the connector status as **Initializing**.
        
    *   Screenshot showing the connector status as **Active**.
        

> ⚠️ No step summary or issue/resolution narrative is required for this task.

**Grading Criteria**
*   All requested Outpost deployment screenshots are present and clearly show the required states.
    
*   Screenshots are well-captured, relevant, and legible.

> **📤 Submission Format:**  
> Submit a **single PDF document** containing the required screenshots for the AWS Outpost lab.

* * *
#### **📝 Task 8 — Boards & Threat Center**

**Objective**  
Learn to effectively use the **Wiz Dashboard (Boards)** and the **Threat Center** to visualize risks and monitor emerging threats in your cloud environment.

**Instructions**
1.  **Enroll & Access the Course**
    *   Log in to the **Wiz Partner Academy**:  
        👉 [https://partners.wiz.io/academy](https://partners.wiz.io/academy)
        
    *   Open the **“Wiz Tech Essentials”** course.
        
2.  **Complete the Following Lab**
    *   **Self-Paced Lab — Boards and Threat Center**
        

**Deliverables**  
For this task, you are only required to submit screenshots from the following exercises:

📊 **Wiz Dashboard (Boards)**

*   **Exercise 1:** Screenshot showing the creation form of a new dashboard (name and visibility settings).
    
*   **Exercise 2:** Screenshot displaying at least three different widgets added to your custom board.
    

🔍 **Wiz Threat Intel Center**

*   **Exercise 1:** Screenshot of the Threat Intel Center main page showing at least two advisories.
    
*   **Exercise 2:** Screenshot showing the creation of an automation rule or subscription to an advisory (depending on lab instructions).

**Grading Criteria**
*   Screenshots from all four exercises are provided.
    
*   Screenshots are relevant, clearly captured, and show the required views.
    

> **📤 Submission Format:**  
> Submit a **single PDF document** containing the required screenshots.