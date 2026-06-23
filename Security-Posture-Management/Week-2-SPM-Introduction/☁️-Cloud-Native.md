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
 

---


<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b><span style="color:#7C3AED; font-size: 17px;">🚨 Cloud Native Computing Overview 🚀</span></b>
    <br><br>
    Cloud Native is a methodology for building and running software that harnesses the inherent benefits of the cloud computing model, such as scalability, elasticity, resiliency, and flexibility. 🌍☁️
    <br><br>
    This approach empowers developers to frequently deliver impactful changes to shippable software with minimal effort, enabling organizations to produce high-quality software quickly and respond swiftly to customer demands. 🚀
    <br><br>
    This methodology leverages microservices, containers, service meshes, and APIs to create resilient, manageable, and observable systems with robust automation. 🛠️
</div>

  

## **🚀 Introduction to Cloud Native Computing Foundation (CNCF)**

The **Cloud Native Computing Foundation ([CNCF](https://www.cncf.io/))** is a project under the **Linux Foundation**, established in 2015. Its primary goal is to advance container technology and align the tech industry around its evolution. CNCF supports and oversees fast-growing cloud native projects, fostering collaboration among developers, end users, and vendors to create sustainable ecosystems for cloud native software.


<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://www.cncf.io/wp-content/uploads/2023/04/cncf-main-site-logo.svg"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">CNCF Logo</div>
</div>


### **🔹 Notable CNCF Projects 🏗️**

- 🐳 **Kubernetes**: A leading container orchestration system that offers scalability, high availability, self-healing, and load balancing.

- 📊 **Prometheus**: A powerful monitoring and alerting toolkit designed for reliability and scalability.

- ⚓ **Helm**: A package manager for Kubernetes that simplifies the deployment and management of applications.

Every project supported by CNCF is listed in this website: **[CNCF Projects Landscape](https://landscape.cncf.io/)**.

## **🔹 Principles of Cloud Native Computing**

- 🚀 **Scalability**: Achieved through microservices, distributing functionalities across services.

- 🔄 **Resiliency**: Ensured via load balancing, autoscaling, and distributed architectures.

- 🛠️ **Manageability**: Simplified through tools like Helm for package management.

- 👀 **Observability**: Provides deep insights into application state and health through logging and monitoring tools.

- 🤖 **Automation**: Drives consistency and enables continuous integration/delivery (CI/CD).
  

<div style="background:#F3E8FF; padding:15px; border-left:10px solid #7C3AED; border-radius:6px;">
    <b>💡 Tip</b>: Automation and observability enhance software quality and operational efficiency. 🚀
</div>


## 🔹 Building Blocks of Cloud Native 🏗️

To achieve and adhere to cloud native architecture principles and gain the benefits of cloud computing, we need to incorporate several key concepts into our software development process:

- **Microservices** 🏛️: Application components are smaller services that can be updated on demand.

- **Containers** 📦: Packaging applications and their dependencies to run smoothly on any platform.

- **Continuous Delivery** 🚀: The ability to deliver software consistently.

- **DevOps** ⚙️: Collaboration between development and operations teams.

A **microservices architecture** allows structuring applications into smaller, independent services. These services serve specific business needs and are **loosely coupled**, meaning they do not depend on each other. Each service can be **scaled, upgraded, updated, restarted, or deployed** individually rather than packaging the entire application.


**Containers** package applications with dependencies, ensuring **smooth operation on any platform**. They provide **fine-grained control over resource allocation**, leading to **efficient use of computing capacity**.

Cloud native is not just about **architecture and deployment**, it represents a **cultural shift**. **DevOps** promotes collaboration between development and operations teams, facilitating **better coordination, ownership, and faster software delivery**.

**Continuous Integration and Continuous Delivery (CI/CD)** helps deliver incremental software changes into production **more quickly**. Through automation, **CI/CD enables frequent software releases and faster feedback loops**. 🔄

---


## **🔹 The 4 C’s of Cloud Native Security 🛡️**

This modern approach to software development not only enhances scalability but also introduces new security challenges. As a result, security is a crucial aspect of cloud-native computing. Securing and hardening cloud-native applications can be a complex and time-consuming process. In this discussion, we will explore various strategies to strengthen their security.

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://documents.trendmicro.com/images/Figure1_The%204%20Cs%20of%20cloud%20native%20security.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">4 Cs of cloud-native security</div>
</div>

Security in cloud-native environments is structured across four layers:

### 1. **Cloud ☁️**

From a security perspective, it is very important to understand the **shared responsibility model** of cloud services. Responsibilities vary by provider, but generally follow the same principles. In **on-premises environments**, customers handle everything, including physical security. However, in the cloud, some responsibilities shift to the provider, while others remain with the customer.

Key areas that customers must secure:

- **Identity and Access Management (IAM)** 🔑: Use **RBAC (Role-Based Access Control)** and **MFA (Multi-Factor Authentication)** to protect accounts.

-🌐 **Network Security** : Implement **firewalls, security groups, and private networks** to restrict unauthorized access.

-📦 **Storage Security** : Secure cloud storage with **encryption, access controls, and firewalls**.

-🛠️ **Application Security** : Follow **secure coding practices** and ensure **regular vulnerability assessments**.

-🔒 **Data Protection** : Encrypt databases **at rest and in transit**.

-🏛️ **Governance & Compliance** : Apply **security policies** to prevent misconfigurations.

### 2. **Cluster 🏗️**

A **Kubernetes cluster** is the backbone of modern cloud-native applications. Protecting it is essential to prevent **unauthorized access, privilege escalation, and data leaks**.

Security best practices include:

- **RBAC (Role-Based Access Control)**: Limit user and service account permissions.

-🔒 **TLS Everywhere** : Encrypt all communication within the cluster, including **API server interactions** and **pod-to-pod traffic**.

-🌍 **Network Policies** : Restrict **pod-to-pod communication** to prevent lateral movement.

-🗝️ **Secrets Management** : Store sensitive information securely using **Kubernetes Secrets** or **external vault solutions**.

-📊 **Audit Logging & Monitoring** : Continuously track **cluster activity** for anomalies and security threats.

-📦 **Supply Chain Security** : Use **image signing, vulnerability scanning, and policy-based admission controls** to ensure only trusted container images are deployed.

### 3. **Containers 📦**

Containers form the core of cloud-native applications, but **misconfigured containers** can introduce security risks.

#### Securing the container lifecycle:

🔹 **Building the Image Securely**

- Use **minimal base images** to reduce the attack surface.

- Scan for **vulnerabilities** before pushing to a registry.

- Ensure **proper file permissions**.

- Never hardcode **secrets** in images.


🔹 **Running Containers Securely**

- **Restrict system calls** to prevent privilege escalation.

- Avoid running containers in **privileged mode**.

- Implement **read-only file systems** whenever possible.

🔹 **Securing the Host System**

- Keep the **OS updated** and **patched**.

- Use **Kernel security modules** (AppArmor, SELinux) to enforce security policies.

### 4. **Code 💻**

The **application code** inside containers is **a major attack surface**. Security vulnerabilities in code can lead to **data breaches, privilege escalation, and application takeovers**.


Key security practices:

-📂 **Third-Party Dependency Analysis** : Regularly scan for **vulnerabilities in dependencies**.

-🔎 **Static Application Security Testing (SAST)** : Identify **security flaws in source code** before deployment.

-🚀 **Dynamic Application Security Testing (DAST)** : Simulate **real-world attacks** to uncover **runtime vulnerabilities**.

-🔬 **Software Composition Analysis (SCA)** : Detect **outdated and insecure libraries** in the application stack.

-🚨 **Principle of Least Privilege (PoLP)** : Ensure **minimal permissions** are assigned to application services and APIs.
  

## **🔹 Monolith vs Microservices**

### Monolith 🏢

**Traditional** monolithic application design is an architectural style where the application is built as a single unit in a single code base. Although this way of architectural style is **easy to get started**, over a period of time as application grows it adds to more complexity and becomes extremely difficult to deploy, **manage and scale the application**.

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://admin.wac.co/uploads/Detailed_Insight_to_Monolithic_Architecture_e3e827d4bc.jpg"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Monolith Architecture</div>
</div>

### Microservice 🏭

**Microservice** is an **architectural** approach to **build an application** that comprises of smaller chunks of services that are light weight and runs in its own process and communicates with each other **using API's**. Services are loosely coupled. **Independent of each other** and have their own database.

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://i0.wp.com/i.postimg.cc/ZRDSWQWK/Microservice-Image.png?w=1230&ssl=1"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Microservices Architecture</div>
</div>

  

### Monolith vs Microservices 🏢⚡🏭

| Architecture  | Strengths  | Weaknesses  |
|--------------|-----------|------------|
| **Monolith 🏢**  | Simple to deploy, manage, and scale for small apps | Difficult to scale, high maintenance complexity, high failure impact |
| **Microservice 🏭** | Independent development, scalability, resilience, flexibility | High learning curve, complex monitoring, multiple repositories |


## **🔹 Continuous Integration/Continuous Delivery (CI/CD) ⚙️**

**CI/CD** is a DevOps methodology ensuring code is automatically built, tested, and deployed efficiently. Key tools include:

- **Jenkins**: 🔄 Automates builds and deployments.

- **GitLab CI/CD**: 🏗️ Provides integrated pipelines for continuous development.


<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn. 🎯
</div>