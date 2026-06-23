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

#### **📝 Task 1 — Technologies & Inventory Lab**

**Objective**  
Master Wiz’s asset discovery and technology inventory capabilities across AWS, Azure, and GCP by completing the official self-paced labs.

Instructions

1.  **Enroll & Access the Course**
    *   Log in to your **Wiz Partner Academy** account at https://partners.wiz.io/academy
        
    *   Find and enter the **“Wiz Tech Essentials”** course.
        
2.  **Complete the Following Lab**
    1.  **Self-Paced Technologies Inventory Lab**
        
3.  **Deliverables**  
    For **each lab**, include in your report:
    *   **Step-by-Step Summary:** A numbered list of the actions you performed (connecting the CSP, configuring inventory settings, running the discovery).
        
    *   **Key Screenshots:**
            
        1.  The **Technologies & Inventory** dashboard in Wiz displaying at least five discovered resource types (e.g. VMs, containers, databases).
            
        3.  An example of filtering or grouping assets by tag, region, or technology.
            
    *   **One Inventory Insight:** Describe a surprising or unmanaged resource you found (e.g. an unexpected old snapshot, untagged S3 bucket), and recommend one remediation or tagging policy.
        
4.  **Grading Criteria**
    *   Completion of the lab.
        
    *   Clarity and relevance of screenshots (annotate as needed).
       
> **Submission:** PDF document with your step summaries, annotated screenshots, inventory insight narrative.
* * *
#### **📝 Task 2 — Security Graph Queries: Network Exposure**

**Objective**  
Use the Wiz Security Graph Query Editor to discover internet-exposed resources, 
craft custom queries

*   **Enroll & Access the Course**
    *   Log in to **Wiz Partner Academy**: https://partners.wiz.io/academy
        
    *   Navigate to the **“Managing Cloud Security Posture”** course and select the ** Security Graph Queries: Network Exposure****.
        
*   **Complete the Lab**
    *   Follow the lab guide to open the **Graph Query Editor** in the Wiz portal.
        
    *   Load the provided **Network Exposure** sample queries.
        
    *   Run the queries against your connected AWS, Azure, and GCP environments.

**Deliverables**  
In your PDF report, include:
1.  **Step-by-Step Summary**
    *   Clearly number the actions you took (e.g., opened the query editor, pasted the sample query, ran the query).
        
2.  **Key Screenshots**
    *   The **Graph Query Editor** with your final query visible.
        
    *   The **Query Results** pane showing at least five exposed resources (VMs, load balancers, containers, etc.).
        
    *   A filtered view where you refine the query to show only resources with port 22 or port 3389 open to the internet.

1.  **Grading Criteria**
    *   Successful execution of both the provided and custom queries.
        
    *   Clarity and completeness of screenshots (queries and results).
        
    *   Quality of your exposure insight and appropriateness of your mitigation recommendation.
        
         
> **Submission:** PDF document containing your numbered steps, annotated screenshots, custom query text & results, exposure insight.

* * *
#### **📝 Task 3 — Security Graph Queries: Secrets and Cloud Entitlements**
**Objective**  
Leverage the Wiz Security Graph Query Editor to discover exposed secrets and over-privileged identities, craft custom queries.

*   **Enroll & Access the Course**
    *   Log in to **Wiz Partner Academy**: https://partners.wiz.io/academy
        
    *   Navigate to the **“Managing Cloud Security Posture”** course and select the **Self-Paced Lab - Security Graph Queries: Secrets and Cloud Entitlements**.
        
*   **Complete the Lab**

**Deliverables**  
In a single PDF report, include for **each** query (built-in and custom):

**Screenshots:**
1.  Query Editor showing your query.
    
2.  Query Results pane with the results.

**Grading Criteria**
*   Correct execution of both built-in and custom queries.
    
*   Clarity and completeness of screenshots (queries and results).

> **Submission:** PDF document with query texts, annotated screenshots, analysis/recommendations.

* * *
#### **📝 Task 4 — Security Graph Queries: Vulnerabilities and Malware**

**Objective**  
Use the Wiz Security Graph Query Editor to identify vulnerable assets and malware indicators, craft custom queries for specific CVEs

*   **Enroll & Access the Course**
    *   Log in to **Wiz Partner Academy**: https://partners.wiz.io/academy
        
    *   Navigate to the **“Managing Cloud Security Posture”** course and select the **Self-Paced Lab - Security Graph Queries: Vulnerabilities and Malware**.
        
*   **Complete the Lab**

**Deliverables**  
In a single PDF report, include for **each** query (built-in and custom):

**Screenshots:**
1.  Query Editor showing your query.
    
2.  Query Results pane with the results.

**Grading Criteria**
*   Correct execution of both built-in and custom queries.
    
*   Clarity and completeness of screenshots (queries and results).

> **Submission:** PDF document with query texts, annotated screenshots, analysis/recommendations.
* * *
#### **📝 Task 5 — Wiz Policy Management**

**Objective**  
Learn to create, test, and enforce custom security policies in Wiz using Policy-as-Code and built-in controls.

**Deliverables**

**Step-by-step summary** of what you did with key screenshots.

*   **One issue you encountered** (e.g. missing permissions), and how you resolved it.

> **Submission:** PDF with step summaries and screenshots.

* * *

#### **📝 Task 6 — Wiz Policy Management**

