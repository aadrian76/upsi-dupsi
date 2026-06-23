<details open>
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


<i>👉 This course is structured around three key pillars of AST: SCA, SAST, and DAST. Understanding how they complement each other is crucial before diving into each.</i>

</div>

---

#**🔐 1. Introduction to Application Security Testing (AST)**
---------------------------------------------------------

Application Security Testing (AST) refers to the set of practices, methodologies, and tools used to identify and mitigate vulnerabilities in software applications throughout the Software Development Life Cycle (SDLC).  

The primary objective of AST is to ensure that applications are built securely, minimizing the risk of exploitation by attackers and protecting both the organization and end users.

These practices are not isolated efforts, but form part of a holistic security strategy that must adapt to evolving threats and development workflows.


::: video
<iframe width="560" height="315" src="https://www.youtube.com/embed/-4rxtmIQyXA" frameborder="0" allowfullscreen></iframe>
:::



### **Why is AST Important?**

✅   **Applications are prime targets:** The majority of data breaches exploit vulnerabilities in applications    rather than networks.
    
✅ **Increasing complexity:** Modern applications are built on microservices, interconnected APIs, and third-party components, each of which expands the potential attack surface.
    
✅   **Regulatory compliance:** Organizations must meet security requirements (GDPR, ISO 27001, PCI DSS) where secure applications play a key role.
    
✅   **Cost reduction:** Detecting vulnerabilities early in the development lifecycle is significantly cheaper than fixing them after deployment.
    

* * *

###🛠️ **AST in the Software Development Life Cycle (SDLC)**

AST is not a single event; it is an **ongoing process** integrated into every phase of the SDLC:

1️⃣  **Planning:** Security requirements are defined.
    
2️⃣  **Development:** Code is scanned (SAST) to detect vulnerabilities early.
    
3️⃣  **Build & Integration:** Open-source components are analyzed (SCA) to avoid introducing known risks.
    
4️⃣  **Testing:** Runtime testing (DAST) identifies real-world exploitable flaws.
    
5️⃣  **Deployment & Maintenance:** Continuous monitoring ensures new threats are detected and mitigated.
    
This approach aligns with **DevSecOps** practices, where security is embedded in every stage rather than added as an afterthought.

* * *




### **How AST Fits Our Service Line**

In our department, AST is a **core capability**. Our team applies security testing across multiple projects, ensuring that applications delivered to clients meet strict security requirements.  
We use a combination of:
*   **SCA** to secure dependencies.
    
*   **SAST** to secure the code itself.
    
*   **DAST** to secure the deployed application.