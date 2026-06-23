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

### **What is SAST?**

### 🧾 **Definition**

**Static Application Security Testing (SAST)** is a **white-box** testing methodology that analyzes an application’s **source code, bytecode, or binaries** to detect vulnerabilities before the software is executed or deployed.  
It inspects the code internally, allowing developers to identify **insecure coding patterns** and logic flaws early in the SDLC, when fixes are easier and less costly.  
SAST tools use **rules and data flow analysis** to detect weaknesses like **SQL Injection, Cross-Site Scripting (XSS), hardcoded secrets,** and insecure cryptography.  
Modern solutions integrate with **IDEs** and **CI/CD pipelines**, enabling **continuous security feedback** throughout development.  
By embedding SAST into workflows, organizations can **reduce risks**, improve code quality, and deliver more secure applications.

<div style="background:#E0F2FE; padding:15px; margin-top:15px; border-left:8px solid #0284C7; border-radius:6px; color:#0F172A;"> 
📘 <b>Want to learn more about SAST?</b><br><br> 
Check out this extended resource for a deeper dive into how Static Application Security Testing works, including benefits, challenges, and best practices: 👉 
<a href="https://www.paloaltonetworks.com/cyberpedia/what-is-sast-static-application-security-testing" target="_blank">
<b>What is SAST? – Palo Alto Networks Cyberpedia</b>
</a> 
</div>


* * *

🚀 **Importance of SAST in Secure Development**
-----------------------------------------------

Static Application Security Testing (SAST) plays a **critical role** in building secure software, as it allows security to be addressed proactively instead of reactively. By analyzing the code before it is executed, SAST helps organizations detect and remediate vulnerabilities **long before they can be exploited**.
*   ✅ **Early Detection:** SAST identifies vulnerabilities **during development**, preventing insecure code from progressing through the pipeline and significantly reducing remediation costs.
    
*   ✅ **Developer-Friendly:** Findings include **precise code locations** and remediation advice, enabling developers to fix issues quickly without guesswork.
    
*   ✅ **Compliance Support:** By aligning with security standards such as **OWASP Top 10**, **CWE**, **PCI DSS**, and **ISO 27001**, SAST helps organizations meet regulatory and industry requirements.
    
*   ✅ **Security from the Start:** By integrating into the SDLC, SAST ensures that security is built into the development process from the very beginning, allowing vulnerabilities to be detected early and resulting in **safer** and more **resilient** applications.

* * * 


🛡️ **Common Vulnerabilities Detected by SAST**
-----------------------------------------------

*   💉 **SQL Injection (SQLi):** Attackers inject **malicious SQL queries** to manipulate or extract data from databases.
    
*   🛠️ **Improper Input Validation:** Failure to **sanitize user input**, opening the door to attacks like SQLi, XSS, or buffer overflows.
    
*   🎭 **Cross-Site Scripting (XSS):** Injection of **malicious scripts** into web pages, allowing attackers to steal cookies or hijack sessions.
    
*   🎯 **Cross-Site Request Forgery (CSRF):** Tricks users into performing **unintended actions** while authenticated.
    
*   📂 **Path Traversal:** Manipulating file paths to **access sensitive files** outside the intended directory.
    
*   💥 **Buffer Overflow:** Overwriting memory buffers, leading to **application crashes** or **arbitrary code execution**.



* * * 


🧠 **How Static Analysis Works**
--------------------------------

SAST tools perform a **static examination of source code, bytecode, or binaries** to uncover security weaknesses without executing the application. This analysis is based on **predefined rules**, **pattern recognition**, and **data flow tracking**, enabling the detection of both simple coding flaws and complex vulnerabilities.
The process usually follows these **five key steps**:

1️⃣ **Code Scanning** – The tool scans the project, inspecting every file to identify insecure coding patterns. 
 
2️⃣ **Pattern Matching** – Potential vulnerabilities are flagged by comparing code against known weakness signatures (CWE, OWASP Top 10).  

3️⃣ **Data Flow Analysis** – The tool evaluates how data moves through the code to detect risks like **unsanitized inputs** reaching sensitive operations.  

4️⃣ **Reporting** – Findings are compiled into a report with **severity levels**, affected files, and detailed descriptions.
  
5️⃣ **Remediation Guidance** – Developers receive **clear recommendations** on how to fix each issue, streamlining the secure coding process.

✨ This workflow ensures that vulnerabilities are **not only detected but also understood and efficiently resolved**, reinforcing secure development practices.


* * *


🔗 **Integration of SAST in the Development Cycle**
---------------------------------------------------

Integrating **Static Application Security Testing (SAST)** into the development process is essential to ensure that vulnerabilities are detected and remediated as early as possible. Unlike traditional security testing performed only at the end of the cycle, SAST integrates security checks early in the development workflow, allowing vulnerabilities to be fixed before they reach later stages. This reduces the likelihood of vulnerabilities reaching production and strengthens the overall security posture of the application.
SAST can be applied at multiple stages:
*   ✍️ **During coding:** Developers can run scans directly from their IDEs, receiving **real-time feedback** on insecure coding practices. This immediate detection allows vulnerabilities to be fixed before they propagate further into the project.
    
*   🔄 **In build and integration phases:** Automated scans integrated into **CI/CD pipelines** ensure that no insecure code is merged into the main branch. Failing builds on critical findings enforces security as a quality gate.
    
*   ✅ **Before deployment:** Final SAST scans serve as a **last line of defense**, verifying that the application meets internal and regulatory security requirements prior to release.
    
Automation plays a key role in this process. When SAST is integrated into the pipeline, scans run **automatically with every commit or pull request**, ensuring that security checks are continuous and do not slow down development. Combined with proper configuration, SAST can also enforce **policies** (blocking releases with critical vulnerabilities) and integrate results into **issue tracking systems** for efficient remediation.

Integrating SAST with other practices—such as **secure coding guidelines**, **code reviews**, and complementary testing methods like **DAST** and **SCA**—creates a **multi-layered security strategy**, enabling teams to deliver secure applications faster and with greater confidence.


* * * 

🗂️ **Managing Results in SAST**
--------------------------------

Running a SAST scan is only the first step. The **real value** lies in how the results are analyzed, prioritized, and acted upon. Effective result management ensures that vulnerabilities are addressed efficiently without overwhelming development teams.


### 🎯 **1. Identifying and Prioritizing Vulnerabilities**

Detecting vulnerabilities is important—but **knowing which ones to fix first** is critical.
This step involves **evaluating** each finding based on:

🔴 **Severity** — How dangerous is the vulnerability? Could it lead to serious consequences like data breaches or system compromise?

🛠️ **Exploitability** — How easily can an attacker take advantage of it?

📉 **Potential Impact** — What damage could it cause to the business, users, or system availability?

Combining these factors allows teams to **prioritize remediation efforts**, focusing first on high-risk, high-impact issues—especially those that are easy to exploit.


    


### ⚠️ **2. Handling False Positives and False Negatives**

*   **False Positives**: Issues flagged by the tool that are not actual vulnerabilities.
    *   ❗ Can waste time if not filtered.
        
    *   ✅ Use **manual review** and **custom rules** to reduce noise.
        
*   **False Negatives**: Real vulnerabilities missed by the scan.
    *   ⚠️ Relying solely on SAST is risky—combine with other AST methods (DAST, SCA) for full coverage.


<div style="background:#FEF9C3; padding:20px; margin-top:30px; margin-bottom:30px; border-left:10px solid #EAB308; border-radius:6px; color:#1C1917;"> <h2 style="margin-top:0;">🔧 Time to Get Hands-On!</h2> <p style="font-size:16px;"> You've completed the theoretical foundations. Now it's time to apply your knowledge in real-world scenarios and practical labs. Prepare your tools, focus on methodology, and remember: <b>hands-on practice is where real learning happens</b> 🔍💻 </p> </div>

#📂 Exercise
***
1. Download the code ZIP file to scan the application.

   [juice-shop-master.zip](https://ts.accenture.com/:u:/s/IniciativaTrainingPathAST/EWWKV_Z5KTZJjMoFvjZ-eSgBnUkz8H04z1nBfbGNlSVRNQ?e=RCSDYM)

#🔍 How to Access Polaris and Perform a Scan
-----------------------------------------------

### 1. Access the Portfolio

*   Log into **Polaris**. 

    https://eu.polaris.blackduck.com/portfolio/portfolios/3b1c24bc-5288-4d30-842f-7c6a47216e78/portfolio-items?pagingLimit=25&pagingOffset=0&searchTerm=
    
*   Once inside, navigate to the appropriate **Portfolio** where your applications are listed.
    

### 2. Open the Test Menu

*   Within the selected portfolio, go to the **Test** dropdown menu located in the top navigation bar.
    

### 3. Create a New Test

*   Click on **“Create New Test”**.
    
*   In the test creation wizard:
    *   Select the relevant **Application**.
        
    *   Choose the project: **Training Path Juice Shop**.
        
    
        

### 4. Run the Test

*   Start the test and wait for it to complete. Depending on the size of the application, this may take a few minutes.
    

### 5. Start the Triage Process

*   Once the scan is finished, access the test results by entering the **project** from the dashboard.
    
*   Begin **triage** by reviewing each **vulnerability** found.
    

### 6. Classify the Vulnerabilities

*   For each identified vulnerability, determine the appropriate status:
    *   ✅ **To Be Fixed** – if the issue poses a valid risk and needs remediation.
        
    *   ❌ **Dismissed** – if the issue is a false positive or not relevant.
        

### 7. Add Comments for Each Decision

*   For every decision made (either _To Be Fixed_ or _Dismissed_), add a **comment** explaining the rationale behind your choice. This is essential for traceability and auditing purposes.
    

