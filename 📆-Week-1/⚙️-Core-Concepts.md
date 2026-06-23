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
| @<C73C5218-17C3-6B53-B15D-E321D12689EB>                  | 22/02/2025              | First Version Created                         |

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

Security is **not just configuring firewalls and running scans**. If you don't know **how technology actually works**, you're just **blindly applying security principles** with zero understanding.

This section covers **key technical concepts** that form the **backbone of everything in cybersecurity**. You'll go through:

- **🌐 Frontend vs Backend**. What happens on the surface vs. behind the scenes
- **🛠 Microservices**. Why modern apps are split into smaller pieces—and why that's a security nightmare
- **📦 Containers**. The backbone of cloud security (and also why attackers love misconfigured clusters)
- **⚙️ Infrastructure Basics**. Networking, virtualization, and compute essentials
- **🔗 APIs & Web Architecture**. The backbone of modern software—and attack surfaces
- **🛡️ Security Implications**. Why understanding tech concepts makes you better at security

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b>🚀 Security Starts with Understanding</b>
    <br><br>
    If you want to <b>break things securely</b>, you need to <b>know how they're built</b> first.
    <br><br>
    Weak understanding of these concepts = weak security skills. No way around it.
</div>

## 🌐 Frontend vs Backend  

The frontend is what **users interact with**. The backend is **where the real magic happens**.

| **Aspect**       | **Frontend**                                     | **Backend**                                   |
|-----------------|------------------------------------------------|----------------------------------------------|
| **Definition**   | The part users see & interact with            | The part that handles logic & data processing |
| **Runs on**      | User’s browser (HTML, CSS, JavaScript)         | Server-side (Node.js, Python, Java, etc.)    |
| **Main role**    | Displays content, collects input               | Processes data, handles logic, manages storage |
| **Security Risks** | XSS, CSRF, Clickjacking                      | SQL Injection, Broken Authentication         |

If you don't understand **where an attack happens** (frontend or backend), you won’t know **how to defend against it**.

## 🛠 Microservices

Microservices = **breaking an application into multiple small, independent services**.  

**Why use them?**

- Faster development and scaling
- More flexibility in choosing tech stacks
- **Less impact when one part fails**

| **Architecture**  | **Description** |
|-----------------|-----------------|
| **Monolithic**  | One big codebase, everything runs together |
| **Microservices** | Multiple small services, each handling a specific function |

**Security Considerations**

- **More APIs = More Attack Surface**  
- **Authorization is critical**. Each service must verify access **independently**  
- **Data flow between services must be secured** (e.g., encryption in transit)  

Think **"small, specialized services = bigger security challenges"**.

## 📦 Containers  

Containers **package an application and its dependencies into one unit** so it **runs consistently anywhere**.

- **Why use them?**

  - Works the same in **dev, test, and production**.
  - Lightweight compared to VMs.
  - Faster to start and scale.

| **Tech**  | **What It Does** |
|-----------|-----------------|
| **Docker**  | Creates & manages containers |
| **Kubernetes** | Orchestrates and scales containers |

**Security Challenges**

- **Images must be hardened** (or attackers will inject vulnerabilities).
- **"Running as root" = Recipe for disaster**.
- **Container escape attacks** are a thing. Don't ignore them.

Containers power **modern security problems**. You need to know them inside out.
