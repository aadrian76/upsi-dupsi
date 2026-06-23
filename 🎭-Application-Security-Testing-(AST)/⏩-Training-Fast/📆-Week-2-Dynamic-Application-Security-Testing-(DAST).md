<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>
  
  [[_TOC_]]
</details>



<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b><span style="color:#7C3AED; font-size: 17px;">👋 WELCOME!!</span></b>
    <br><br>
    <b>You made it</b> (or you were forced to). Do yourself a favor and <b>use this wiki</b>. 
    <br><br>
    For the next few weeks (and probably long after), you'll be spending a lot of time here. If you're stuck, just <b>USE IT</b>. Simple. <b>We keep it updated</b>, so don't let it go to waste...
    <br><br>
    Of course, you <i>could</i> ignore it and try to figure everything out the hard way. That's a choice. <b>Not a smart one</b>, but a choice.
    <br><br>
    <span style="color:#7C3AED;"><b>No corporate jargon, no BS, and NO FLUFF</b></span>. Just <b>short, direct info</b>. A bit of sarcasm, yes, to keep things smooth.
</div>

* * * 



#**What is DAST?**

## 🧾 **Definition**

**Dynamic Application Security Testing (DAST)** is an **application security (AppSec) testing method** where the application is examined **while it is running**, without any knowledge of its internal structure, source code, or system-level design.  
This approach, known as **“black-box testing”**, evaluates the application **from the outside in**, focusing on how it behaves under simulated attack conditions.
During testing, DAST tools send **crafted requests** to the application, mimicking potential attack vectors, and analyze its responses to determine whether vulnerabilities exist.  
If the application reacts in an unexpected or insecure way, this behavior may indicate weaknesses that could be exploited in a **real-world attack**.  
By replicating an attacker’s perspective, DAST helps uncover flaws in authentication, authorization, input validation, and runtime configurations that static analysis alone cannot detect.



<div style="background:#E0F2FE; padding:15px; margin-top:15px; border-left:8px solid #0284C7; border-radius:6px; color:#0F172A;"> 📘 <b>Want to learn more about DAST?</b><br><br> Check out this extended resource for a deeper dive into how Dynamic Application Security Testing works, including use cases and best practices: 👉 <a href="https://www.blackduck.com/glossary/what-is-dast.html" target="_blank"><b>What is DAST? – Black Duck Glossary</b></a> </div>


* * *


##🚀 **Importance of DAST in Secure Development**


The increasing reliance on **web and mobile applications** has made application vulnerabilities one of the **leading causes of data breaches**. Organizations must adopt **dynamic testing methods** like DAST to secure applications against the growing and evolving threat landscape.

### ✅ **Key Reasons Why DAST Is Critical**
___
*   **📈 Expanding Attack Surface:**  
    With the rise of **cloud-native technologies**, **microservices**, and **APIs**, applications have become more complex, exposing new entry points for attackers.
    
*   **🧩 Increasing Use of Third-Party Code:**  
    Modern applications heavily rely on **open-source and third-party components**, which may introduce vulnerabilities beyond the organization’s direct control.
    
*   **⚡ Fast-Paced Development (DevOps):**  
    Rapid release cycles leave little room for traditional security testing, requiring **automated and lightweight solutions** like DAST to keep up with code velocity.
    
*   **🌐 Realistic Testing:**  
    Unlike static analysis, DAST evaluates applications **in their running state**, identifying vulnerabilities that attackers could exploit in production environments.
    
*   **🛡️ Risk Reduction:**  
    By detecting **real exploitable vulnerabilities**, DAST helps prevent **data breaches**, protecting both organizations and end users from costly incidents.
    
*   **🔄 Integration with DevSecOps:**  
    DAST findings can be fed directly into **SecOps** and **DevOps pipelines**, ensuring that detected vulnerabilities are **prioritized and remediated quickly**.
    

* * *

### ✨ **Benefits of Implementing DAST**

*   ✅ **Identifies inherited and newly introduced vulnerabilities.**
    
*   ✅ **Provides actionable vulnerability reports** to speed up remediation.
    
*   ✅ **Supports developer education** with insights into real attack vectors.
    
*   ✅ **Protects critical assets and customer trust** by preventing breaches before they occur.
    

* * *

🧨 **Types of Vulnerabilities Detected**
----------------------------------------

**DAST** specializes in finding vulnerabilities that emerge **when the application is running**. By simulating real-world attacks, it uncovers weaknesses that could be exploited in production environments.
DAST is particularly effective at detecting:
*   🔥 **Injection Flaws** – Such as **SQL Injection** or **Command Injection**, where malicious inputs alter queries or commands executed by the server.
    
*   🎭 **Cross-Site Scripting (XSS)** – Attackers inject scripts into web pages, compromising user sessions or stealing sensitive information.
    
*   🔑 **Broken Authentication & Session Management** – Weak login mechanisms or poor session handling that can lead to account takeovers.
    
*   📂 **Sensitive Data Exposure** – Insecure handling of confidential data that can be intercepted or leaked.
    
*   🧭 **Insecure Redirects & Forwards** – Manipulated redirects that send users to malicious sites or bypass access controls.
    
*   ⚠️ **Security Misconfigurations** – Flaws in server, database, or application settings that create exploitable gaps for attackers.
    

* * * 


##✅ **10 DAST Best Practices**


1.  **🎯 Define Clear Objectives** – Establish what applications, features, and vulnerabilities (SQLi, XSS) will be tested to focus efforts effectively.
    
2.  **🛠️ Select the Right Tools** – Choose tools that match your tech stack, integrate with CI/CD, support automation, and provide detailed reporting.
    
3.  **📊 Baseline Testing** – Perform an initial scan to create a security benchmark for tracking improvements over time.
    
4.  **🧪 Test in a Staging Environment** – Run scans in a safe environment that mirrors production to avoid disruptions and allow aggressive testing.
    
5.  **♻️ Perform Regular Scans** – Integrate DAST into the SDLC and CI/CD pipeline to continuously detect new vulnerabilities.
    
6.  **🔐 Credentialed Scanning** – Use authenticated scans to test protected areas and uncover session management or access control flaws.
    
7.  **🎛️ Fine-Tune Scans** – Customize scan scope and sensitivity to reduce false positives/negatives and focus on critical components.
    
8.  **🩹 Remediation & Retesting** – Fix vulnerabilities promptly and rerun scans to confirm they’ve been resolved without introducing new issues.
    
9.  **📡 Stay Updated** – Keep DAST tools, rules, and methodologies current to detect emerging threats effectively.
    
10.  **📑 Compliance & Reporting** – Generate comprehensive reports to track vulnerabilities, support audits, and ensure regulatory compliance.
    

* * *

## 🔄 **DAST Cycle**


1️⃣ **🔍 Crawling & Mapping** – The tool explores the application, mapping **endpoints, parameters, forms, and workflows** to understand the attack surface.

2️⃣ **🎯 Attack Simulation** – It launches a series of **automated test payloads** (SQLi, XSS, authentication bypass attempts) to probe for weaknesses.

3️⃣ **📡 Response Analysis** – The responses are examined for **anomalies or security flaws**, such as error messages, unexpected data exposure, or improper redirects.

4️⃣ **📑 Reporting** – Results are compiled into detailed reports, including **severity levels, affected components, and proof-of-concept exploits**.

5️⃣ **🛠️ Remediation Guidance** – Developers receive **actionable recommendations** to fix vulnerabilities, and the cycle repeats after applying patches to validate the fixes.

 


<div style="background:#FEF9C3; padding:20px; margin-top:30px; margin-bottom:30px; border-left:10px solid #EAB308; border-radius:6px; color:#1C1917;"> <h2 style="margin-top:0;">🔧 Time to Get Hands-On!</h2> <p style="font-size:16px;"> You've completed the theoretical foundations. Now it's time to apply your knowledge in real-world scenarios and practical labs. Prepare your tools, focus on methodology, and remember: <b>hands-on practice is where real learning happens</b> 🔍💻 </p> </div>


🛠 Installation Guide (WSL + Docker + Juice Shop + Tools)
=========================================================

This guide explains how to set up **OWASP Juice Shop** inside **WSL (Windows Subsystem for Linux)** and install basic pentesting tools: `nmap`, `dirb`, and `wfuzz`.


1️⃣ Open WSL
------------

From **Windows Terminal** or **PowerShell**:


<code>wsl</code>

2️⃣ Update the system
-----------------

<code> sudo apt update && sudo apt upgrade -y</code>

3️⃣ Install Docker
-------------------
<code>sudo apt install docker.io</code>

4️⃣ Download and run OWASP Juice Shop
-

<code>docker pull bkimminich/juice-shop</code>

<code>docker run --rm -p 3000:3000 --name juice bkimminich/juice-shop</code>

Access from Windows: <code>       [http://127.0.0.1.nip.io:3000/#/](http://127.0.0.1.nip.io:3000/#/)</code>


5️⃣ Install Windows tools
-------------------------

In addition to the Linux-based tools, install the following in **Windows** (not inside WSL):
*   **Burp Suite Community Edition**:  
    Download from https://portswigger.net/burp/communitydownload
    
*   **OWASP ZAP**:  
    Download from https://www.zaproxy.org/download/
    
Both tools will be used later for **web application security testing**.


# **Scan Report Documentation**  

In this section, provide all necessary information related to the scan results. Please ensure the report is fully completed and ready for review and presentation.

[Plantilla Report.docx](/.attachments/Plantilla%20Report-7ff11049-aa8e-4023-9c2d-a78e99e7d38b.docx)
