
### **What is SCA?**

Software Composition Analysis (SCA) is a **security practice focused on analyzing the open-source and third-party components** used within an application.  
Modern applications are not built entirely from scratch; they heavily rely on **external libraries, frameworks, and packages**. While these components speed up development, they also introduce security risks if they contain known vulnerabilities.
SCA provides **visibility and control** over these components, helping organizations avoid inheriting risks from external sources.

* * *

###⭐ **Why is SCA Important?**

  🔹 **80–90%** of modern code is open-source.
    
  🔹 Attackers exploit **known flaws** (Apache Struts → Equifax breach).
    
  🔹 Vulnerabilities in dependencies compromise secure code.
    
  🔹 Licensing mistakes can cause legal issues.
    

* * *

🛠️ **How Does SCA Work?**
--------------------------

1.  🧭 **Identify** all components.
    
2.  🗂️ **Match** them against databases like **CVE** and **NVD**.
    
3.  📊 **Report** vulnerabilities with severity (CVSS).
    
4.  🛠️ **Recommend** remediation (upgrade).
    
5.  ✅ **Check** license compliance.
    
These scans are typically **automated** and can be integrated into CI/CD pipelines to ensure that vulnerabilities are detected as early as possible.

* * *


###⚠️ **Risks of Using Open-Source Components**

Using open-source components offers great flexibility but also introduces notable risks that developers must manage.

**Security vulnerabilities** are a major concern. While the community actively discovers and patches flaws, developers are responsible for keeping their applications updated. Once a vulnerability becomes public, exploits often follow quickly, making even minor flaws dangerous. This issue is compounded by the fact that many vulnerabilities exist not in the main packages but in **deep dependency chains**, meaning updating only the root components may not fully resolve the risk.

Another challenge is **license compliance**. Open-source projects use a variety of licenses, each with its own rules. Some require attribution, while others may oblige developers to publish their application’s source code. Tracking and correctly applying these requirements across all components can be complex and, if neglected, may result in legal or compliance issues.

* * *


### 🧩 **Dependency Management**

Modern applications rely on numerous open-source components. Managing these dependencies is key to maintaining security and compliance.

#### 🔍 **Types of Dependencies**

*   **Direct dependencies:** Explicitly added by developers (`pom.xml`).
    
*   **Transitive dependencies:** Indirect dependencies required by direct ones. Often hidden, harder to control.
    

#### ⚠️ **Why It Matters**

*   Vulnerabilities often reside **deep in transitive chains**.
    
*   Fixing direct dependencies is easy — **transitive ones may depend on third-party maintainers**.
    
*   License issues can arise from both types, impacting compliance.

📘 **Want to learn more?**  
For a deeper understanding of software dependencies and how to manage them effectively, check out:  
👉 [_Software Dependencies: A Beginner’s Guide_ – Sonatype](https://www.sonatype.com/blog/software-dependencies-a-beginners-guide)

* * *

### ✅ **Best Practices for SCA**

Adopt these key practices to maximize the effectiveness of Software Composition Analysis:
*   🕒 **Shift left:** Integrate SCA scans early in the Software Development Life Cycle (SDLC) to catch issues before deployment.
    
*   🔁 **Continuous monitoring:** Keep watch for newly disclosed vulnerabilities in both direct and transitive dependencies.
    
*   🚨 **Real-time alerts:** Use tools that notify you immediately when a risky component is detected.
    
*   🩹 **Remediate fast:** Replace or patch vulnerable libraries as soon as fixes become available.
    
*   📦 **Track everything with SBOM:** Maintain a clear and updated **Software Bill of Materials** to ensure visibility across your entire dependency tree.
    

* * *

###🗄️ **Vulnerability Databases**

SCA tools rely on public vulnerability databases to detect risks:
* 📌  **CVE (Common Vulnerabilities and Exposures):** A list of publicly known security flaws, each with a unique identifier.
    
*  📌 **NVD (National Vulnerability Database):** Provides additional metadata, CVSS scores, and analysis for CVEs.

* * *

### 🧩 **How SCA Fits into Our Work**

In our AST team, **SCA serves as the first line of defense** in securing applications. It helps us:
*   🔍 **Gain visibility** into all open-source and third-party components.
    
*   🎯 **Identify and prioritize** vulnerabilities based on severity and impact.
    
*   📄 **Deliver actionable reports** with clear remediation steps and tailored client recommendations.


* * * 

🔧 **SCA Tools Overview**
-------------------------

<div align="center">

| Tool | Description | Logo |
| --- | --- | --- |
| **Dependency-Track** | Continuous monitoring using SBOMs. CI/CD-friendly. | <img src="https://tse4.mm.bing.net/th/id/OIP.GbN_Iau2mK652PwQEEDNGgHaBl?rs=1&pid=ImgDetMain&o=7&rm=3" alt="Dependency-Track" width="100"> |
| **OWASP Dependency-Check** | Open-source scanner for known CVEs. Integrates early in SDLC. | <img src="https://1.bp.blogspot.com/-XFQF3YnaGaA/Wocam-LrNbI/AAAAAAAAKTE/0jSjI79KaJwsdRg0UbLgpJDl7t7s-ff6ACLcBGAs/s640/DependencyCheck.png" alt="OWASP Dependency-Check" width="120"> |
| **Checkmarx SCA** | Commercial tool with dashboards and license compliance. | <img src="https://tse1.mm.bing.net/th/id/OIP.N6n-LRxGQgZvzXQp2aecIgAAAA?rs=1&pid=ImgDetMain&o=7&rm=3" alt="Checkmarx SCA" width="100"> |
| **Veracode SCA** | Strong governance, continuous monitoring, cloud-native. | <img src="https://tse4.mm.bing.net/th/id/OIP.8G5cRYUo1koqshZF3EwP5AHaFj?rs=1&pid=ImgDetMain&o=7&rm=3" alt="Veracode SCA" width="90"> |
| **Kiuwan Insights** | Risk scoring, policy enforcement, good for compliance. | <img src="https://tse4.mm.bing.net/th/id/OIP.tnPtMt6qJaH2zREpOiPogAAAAA?rs=1&pid=ImgDetMain&o=7&rm=3" alt="Kiuwan" width="100"> |

</div>

<div style="background:#FEF9C3; padding:20px; margin-top:30px; margin-bottom:30px; border-left:10px solid #EAB308; border-radius:6px; color:#1C1917;"> <h2 style="margin-top:0;">🔧 Time to Get Hands-On!</h2> <p style="font-size:16px;"> You've completed the theoretical foundations. Now it's time to apply your knowledge in real-world scenarios and practical labs. Prepare your tools, focus on methodology, and remember: <b>hands-on practice is where real learning happens</b> 🔍💻 </p> </div>



##🔧 **Practical Setup: Software Composition Analysis (SCA) with OWASP Dependency-Check**
-----------------------------------------------------------------------------------

### 🧰 **1. Prerequisites**

Before installing Dependency-Check, make sure your system has:
*   ✅ **Java JDK 8+**
    
*   ✅ **Maven or Gradle** (for Java projects)
    
*   ✅ Internet connection (to download vulnerability databases)
    

* * *

⚙️ **Installing & Running OWASP Dependency-Check** (CLI) (Optional)
----------------------------------------------------

### 1️⃣ Download

1.  Go to the official **OWASP Dependency-Check** releases page:  
    🔗 [OWASP Dependency-Check | OWASP Foundation](https://owasp.org/www-project-dependency-check/)
    
2.   Scroll **to the bottom of the release assets** and look for the section **"Command Line"**.  
    Download the **latest `dependency-check-x.x.x-release.zip`**.
    
3.   Extract the `.zip` into a folder of your choice (`C:\dependency-check` on Windows or `/opt/dependency-check` on Linux).
    

* * *

### 2️⃣ Update Vulnerability Database

Before the first scan, update the **NVD (National Vulnerability Database)**:

Windows CMD: 

`cd C:\dependency-check\bin`

`dependency-check.bat --updateonly`

* * *

### 3️⃣ Run a Scan

Run the scan against your project folder and generate an **HTML report**:


`dependency-check.bat --scan "C:\path\to\project" --format HTML --out "C:\path\to\reports"`

Run the scan against your project folder and generate an **JSON report**:

`dependency-check.bat --scan "C:\path\to\project" --format JSON --out "C:\path\to\reports"`

* * *

### 4️⃣ View the Report

Open the generated `dependency-check-report.html` in your browser.  
Focus on:
*   **Critical & High severity** issues first.
    
*   **Direct vs transitive dependencies**.
    
*   Suggested fixed versions.
    

* * *

💡 **Tip:** Store the extracted folder in a fixed location and reuse it for future scans — no need to reinstall every time, just run the update before scanning.




#🔑 Configuring Dependency-Check with NVD API Key

Dependency-Check relies on the **NVD (National Vulnerability Database)**. To improve performance and avoid rate limits, configure an **NVD API Key**.

* * *

### 1️⃣ Get an NVD API Key

1.    Go to:  
    [https://nvd.nist.gov/developers/request-an-api-key](https://nvd.nist.gov/developers/request-an-api-key)
    
2.   Sign up using your email address.
    
3.   Check your inbox:  
    
You will receive a **verification code** and a **link**.
    
4.   Click the link and **enter the verification code** to complete the process.
    
5.    Once verified, your **API key** will be displayed. 
 
   
⚠️ **Store it securely.** The key is unique and **must not be shared in public repositories or insecure locations**.

* * *

### 2️⃣ Use the API Key in Dependency-Check

**Option A — Pass as a command argument**

`dependency-check.bat --scan "C:\path\to\project" --format HTML --out "C:\path\to\report" --nvdApiKey <YOUR_API_KEY>`


#📂 Exercise (2 days)
***
1. Download the code ZIP file to scan the application.

   [juice-shop-master.zip](https://ts.accenture.com/:u:/s/IniciativaTrainingPathAST/EWWKV_Z5KTZJjMoFvjZ-eSgBnUkz8H04z1nBfbGNlSVRNQ?e=RCSDYM)

2. Use this report to complete your answer.

   [Report SCA.docx](https://ts.accenture.com/:w:/s/IniciativaTrainingPathAST/EXkHUbBDRANOpNuVMGi7fqABr_kts9vZp6wwQRXlIvC_vw?e=AbUNRN)



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

#📂 Exercise (2 days)
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
    

