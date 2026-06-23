details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>
  
  [[_TOC_]]
</details>

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



### **What is SCA?**

Software Composition Analysis (SCA) is a **security practice focused on analyzing the open-source and third-party components** used within an application.  
Modern applications are not built entirely from scratch; they heavily rely on **external libraries, frameworks, and packages**. While these components speed up development, they also introduce security risks if they contain known vulnerabilities.
SCA provides **visibility and control** over these components, helping organizations avoid inheriting risks from external sources.


<div style="background:#E0F2FE; padding:15px; margin-top:15px; border-left:8px solid #0284C7; border-radius:6px; color:#0F172A;"> 
📘 <b>Want to learn more about SCA?</b><br><br> 
Check out this extended resource for a deeper dive into how Software Composition Analysis works, its benefits, and implementation best practices: 👉 
<a href="https://www.paloaltonetworks.com/cyberpedia/what-is-sca#what" target="_blank">
<b>What is SCA? – Palo Alto Networks Cyberpedia</b>
</a> 
</div>


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

### 🔍 **Types of Risks Detected by SCA**

SCA tools are designed to uncover a wide range of risks across your software supply chain, including:
*   🛡️ **Known vulnerabilities**  
    Identifies publicly disclosed security flaws (CVEs) in open-source components.
    
*   📆 **Outdated or unsupported components**  
    Flags dependencies that are no longer maintained or have reached end-of-life.
    
*   🧨 **Malicious packages**  
    Detects potential supply chain attacks, such as dependency confusion or typosquatting.
    
*   ⚖️ **License violations**  
    Highlights non-compliant or risky licenses that could lead to legal exposure.

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

⚙️ **Installing & Running OWASP Dependency-Check** (CLI)
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
    
1.   Sign up using your email address.
    
1.   Check your inbox:  
    
You will receive a **verification code** and a **link**.
    
1.   Click the link and **enter the verification code** to complete the process.
    
1.    Once verified, your **API key** will be displayed. 
 
   
⚠️ **Store it securely.** The key is unique and **must not be shared in public repositories or insecure locations**.

* * *

### 2️⃣ Use the API Key in Dependency-Check

**Option A — Pass as a command argument**

`dependency-check.bat --scan "C:\path\to\project" --format HTML --out "C:\path\to\report" --nvdApiKey <YOUR_API_KEY>`


#📂 Exercise
***
1. Download the code ZIP file to scan the application.

   [juice-shop-master.zip](https://ts.accenture.com/:u:/s/IniciativaTrainingPathAST/EWWKV_Z5KTZJjMoFvjZ-eSgBnUkz8H04z1nBfbGNlSVRNQ?e=RCSDYM)

2. Use this report to complete your answer.

   [Report SCA.docx](https://ts.accenture.com/:w:/s/IniciativaTrainingPathAST/EXkHUbBDRANOpNuVMGi7fqABr_kts9vZp6wwQRXlIvC_vw?e=AbUNRN)





