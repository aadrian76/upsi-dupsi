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
|                 | 25/02/2025              | First Version Created                         |


<br>

# Secrets

> 🌟  _These are the crown jewels of your cloud kingdom—lose them and it’s game-over._

Secrets Overview
----------------

### What Are "Secrets"? 🤫

In cloud computing, **secrets** refer to **sensitive pieces of information** that enable secure communication and access between systems, services, and users. These include:
*   **API keys**
    
*   **Passwords**
    
*   **Encryption keys**
    
*   **Tokens**
    
*   **Certificates**
    
*   **User credentials**
    
These secrets are critical because they **authenticate** identity and **authorize** access to resources—like apps, databases, cloud storage, and APIs.

* * *

### Why Secrets Matter 🔐

Secrets are like the **keys to your digital kingdom**. If exposed or mishandled, they can lead to:
*   **Unauthorized access**
    
*   **Data breaches**
    
*   **Lateral movement inside cloud environments**
    
*   **Loss of trust in the system**
    

> 🎮 _Multiplayer comparison_: Snag someone’s login token and you can waltz around the lobby wearing their skin—same chaos in the cloud if a secret leaks.

* * *

### Types of Secrets in the Cloud 🗂️

1.  **Authentication Secrets**  
    Used to verify _who you are_ or _what system is calling_.  
    _Examples: API keys, access tokens, user credentials_
    
2.  **Encryption Keys**  
    Used to **encrypt and decrypt data** so that only authorized users can read it.  
    _Examples: AES-256 encryption keys used for bucket or volume encryption_
    
3.  **Certificates**  
    Used to **validate the legitimacy** of applications or websites.  
    _Common in HTTPS and mutual TLS (mTLS) communication_
    
4.  **SSH Keys**  
    Used to enable secure, encrypted remote access to machines or containers.  
    _Commonly used for accessing Linux VMs in cloud environments_
    
5.  **Database Connection Strings & Pre-signed URLs**  
    Used to connect to databases or access cloud storage securely.  
    _Often include usernames, passwords, tokens, or time-limited access links_
    
6.  **Cloud Access Keys**  
    Grant programmatic access to cloud provider services and APIs.  
    _Examples: AWS IAM access keys, Azure service principal secrets_
    
7.  **SaaS API Keys**  
    Provide access to third-party SaaS platforms and services.  
    _Examples: Stripe, Slack, or Twilio API keys used in cloud-native apps_
    

* * *

### Secrets in Action: Example Use Case 🎬

Imagine a **cloud-based web app** that stores user data in a **hosted database**.  
To work properly and securely, it will need:
*   A **username and password** or token to connect to the database
    
*   An **API key** to talk to another service (e.g., a billing system)
    
*   A **certificate** to prove the server is legitimate to end users
    
All of these are **secrets**, and if someone gets access to them, they can:
*   Steal data
    
*   Manipulate transactions
    
*   Impersonate users or services
    

* * *

### Secrets & Encryption in Cloud Storage 🛡️

Cloud services like AWS, Azure, or GCP offer **encryption at rest** and **in transit**:
*   **At rest**: Data stored on disks or volumes (e.g., S3 buckets, EBS volumes) is encrypted
    
*   **In transit**: Data moving across the network (e.g., from app to DB) is encrypted
    
To do this, they use **encryption keys**, such as:
*   **AES-256**: A highly secure, industry-standard encryption algorithm
    
*   **Key Management Services (KMS)**: Offered by cloud providers to handle key storage and rotation securely
    

> 🗝️ _Vault vibe_: Even if someone steals the safe, it’s useless without the combo (your key).

### Cloud Encryption Keys

Cloud encryption keys are used to **protect data at rest** by making it unreadable to unauthorized users, even if they gain physical access to the storage.
*   **Where they’re used**:  
    _Buckets (object storage), volumes (block storage), and databases._
    
*   **Encryption in practice**:  
    _For example, an S3 bucket or EBS volume is encrypted using keys stored in a secure service._
    
*   **Common algorithm**:  
    _AES-256 (Advanced Encryption Standard with a 256-bit key) is widely used for strong encryption._
    
*   **Key storage**:  
    _Keys are typically stored and managed by the cloud provider in services like:_  
    – AWS KMS or Secrets Manager  
    – Azure Key Vault  
    – Google Cloud Secret Manager
    
*   **How keys are accessed**:  
    _Applications retrieve keys securely via API calls—reducing the risk of hard-coding secrets or storing them locally._
    
*   **Benefits**:
    *   Simplifies **key rotation**
        
    *   Supports **access control policies**
        
    *   Enables centralized **auditing and monitoring**
        

### Cloud Certificates

Cloud certificates are used to **secure communications** between resources, ensuring authenticity and encryption.
*   **Purpose**:  
    _Sign and encrypt data exchanged between systems—common in HTTPS/TLS._
    
*   **Real-world example**:  
    _SSL/TLS certificates used to secure website traffic._
    
*   **Management**:  
    _Stored and managed in services like:_  
    – **AWS Certificate Manager**  
    – **Azure Key Vault**
    
*   **Access**:  
    _Applications can retrieve certificates **on demand via API**, eliminating the need to store them locally._
    

* * *

### Cloud Access Keys 🛂

Cloud access keys are used to **authenticate and authorize** programmatic access to cloud services.
*   **Structure**:
    *   **Access Key ID**: Public identifier of the user or service
        
    *   **Secret Access Key**: Private component used to sign requests
        
*   **Function**:  
    _Together, they generate signed API requests—acting like a username/password for automated processes._
    
*   **Use Cases**:  
    _Enabling apps, scripts, or services to interact with cloud APIs securely._
    
*   **Security Considerations**:
    1.  **Avoid long-lived keys** – Prefer short-lived tokens (e.g., AWS STS, Azure AD tokens)
        
    2.  **Rotate regularly** – Reduces the impact of accidental exposure
        
    3.  **Apply least privilege** – Restrict access to only the needed resources
        
    4.  **Store securely** – Use vaults like:
        *   **AWS Secrets Manager**
            
        *   **Azure Key Vault**
            
        *   **Google Secret Manager**
            

> 🪪 Digital keycard rule: cloneable if you never change it—rotate often and limit the doors it opens.

### SSH Keys

SSH keys are used to **authenticate secure access** to virtual machines and systems, primarily by administrators or automated services.
*   **Function**:  
    _They replace usernames and passwords for secure, encrypted shell access (e.g., to Linux servers)._
    
*   **Usage**:  
    _Commonly used for system administration, CI/CD access, and secure automation._
    
*   **Storage**:  
    _Typically stored on a developer’s or admin’s local disk; needs to be secured properly to avoid misuse._
    
*   **Security Considerations**:
    *   **Protect private keys** with strong permissions and passphrases
        
    *   **Rotate keys** periodically
        
    *   **Use bastion hosts or keyless access (e.g., SSM)** when possible
        

> 🎟️ VIP backstage pass: lose it and anyone can stroll into prod like a rock star.

* * *

### Database Connection Strings

Database connection strings are used to **establish secure connections** between applications and databases.
*   **What they contain**:  
    _Host, port, database name, username, and password or token._
    
*   **Function**:  
    _Enables the application to authenticate with the database and start reading/writing data._
    
*   **Risks**:  
    _If exposed, attackers could access, steal, or manipulate sensitive data._
    
*   **Security Best Practices**:
    *   **Encrypt connection strings**
        
    *   **Store them in secret managers**
        
    *   **Avoid hard-coding them in source code**
        

> 📶 Same as sharing your Wi-Fi pass and router IP—only this one connects to treasure, not Netflix.

* * *

### Pre-signed URLs

Pre-signed URLs provide **temporary and limited access** to private cloud resources.
*   **Purpose**:  
    _Allow controlled access to files (e.g., for uploading or downloading from S3, GCS, etc.)_
    
*   **How they work**:  
    _A signed URL is generated with a time limit and access permissions, which can then be shared externally._
    
*   **Use Cases**:
    *   Secure file sharing
        
    *   Granting upload rights without exposing credentials
        
    *   One-time access to object storage
        
*   **Risks**:  
    _If shared improperly, anyone with the link can access the file until it expires._
    

> ⏳ Magic portal that closes in 10 minutes—miss the window and you’re locked out.

* * *

### SaaS API Keys

SaaS API keys are used to **authenticate your cloud application with external services** like Slack, Datadog, or Stripe.
*   **Function**:  
    _Grant programmatic access to third-party SaaS platforms._
    
*   **Uniqueness**:  
    _Every SaaS provider may use different key formats and auth mechanisms._
    
*   **Risks**:  
    _If leaked, attackers can impersonate your service, send spam, or access sensitive integrations._
    
*   **Security Considerations**:
    *   **Store API keys in secret managers**
        
    *   **Rotate keys periodically**
        
    *   **Monitor usage** for anomalies
        

> 🍿 Netflix-token analogy: if someone steals it, they binge on your account—and ruin your recs.

Exposed Secrets and Detection 🚨
--------------------------------

In cloud environments, **secrets** like API keys, tokens, SSH keys, and credentials play a crucial role in authenticating access to systems and services. But when these secrets are **exposed or mismanaged**, they become a high-impact security risk.

* * *

*   **Security risks**:  
    Exposed secrets can lead to unauthorized access, lateral movement, privilege escalation, and full system compromise.
    
*   **Compliance risks**:  
    Violations of standards like **HIPAA**, **GDPR**, and **PCI-DSS** can result in regulatory penalties and audit failures.
    
*   **Business impact**:  
    Mishandled secrets can cause service outages, data breaches, financial loss, and long-term reputational damage.
    
*   **Data exposure**:  
    Secrets embedded in code, misconfigured storage, or leaked via pipelines can expose sensitive data.  
    Attackers may extract customer PII, payment data, or internal IP, leading to privacy violations and legal consequences.
    
*   **Lateral movement and account takeover**:  
    Once an attacker accesses a system using a leaked secret, they can move laterally through the environment.  
    By abusing **over-permissive roles** or **privileged service accounts**, they may escalate to full administrative access across accounts and services.
    

> 🔓 Dropping your keycard in _Warzone_: whoever picks it up owns your entire loadout.

* * *

### Attack Example in the Wiz Security Graph 🎯

<div style="text-align: center; width: 900px; margin: auto;"> <img src="https://imgur.com/L532Wkh.png" style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;" alt="image caption"> <div style="color: gray; font-size: small; font-style: italic;">Attack Path Example</div> </div> <br>
Wiz visually maps attack paths:
*   An attacker gains entry through an exposed **port 80 or 22** on a public VM.
    
*   They exploit a vulnerability and access the VM.
    
*   Inside, they find an **account key** (a secret).
    
*   That secret grants access to a **service account** with admin permissions.
    
*   The attacker now controls the environment.
    

* * *

### How Wiz Detects Secrets 🔎

Wiz uses a multi-stage process to detect secrets across your environment—from code to runtime—without ever exposing or storing the actual secret value.
<div style="text-align: center; width: 900px; margin: auto;"> <img src="https://imgur.com/a8Mf0fH.png" style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;" alt="image caption"> <div style="color: gray; font-size: small; font-style: italic;">Phases</div> </div> <br>

#### 1. Scan

Wiz scans your environment using multiple methods:
*   **Cloud Connectors** – Scanning cloud configurations and metadata
    
*   **Workload Scans** – Analyzing VMs, containers, and disks
    
*   **Data Scans** – Examining storage buckets and volumes
    
*   **Wiz CLI** – Local scans in developer machines or CI/CD pipelines
    

#### 2. Search

Wiz searches through every scanned file to identify potential secrets using **RegEx patterns** crafted for API keys, tokens, credentials, and certificates.

#### 3. Match

A secret is detected **only** if it matches a defined **RegEx pattern and structural logic**:
*   Unique format or prefix (e.g., `AKIA`, `ghp_`)
    
*   Specific length and character set
    
*   Contextual hints (e.g., variable names like `SECRET=`, `token:`)
    

#### 4. Ingest

After detection:
*   Wiz **reduces and anonymizes** the result
    
*   **No cleartext secret** is stored or displayed
    
*   Only **metadata** (secret type, location, detection method) is sent to Wiz backend
    

* * *

### Secrets in the Security Graph 🗺️

Secrets are treated as **graph nodes**, like any other cloud resource.
*   **Secret Data Object**: The actual secret (e.g., SSH public key).
    
*   **Secret Instance Object**: A location where that secret is found (e.g., a specific VM).
    
If the same secret appears in multiple places, Wiz links each instance to the central data object.
**Normalized Types**:
*   `secret`
    
*   `managed certificate`
    
*   `encryption key`
    

* * *

### Where to Find Secrets in Wiz 📍

Secrets and their related findings can be seen in:
*   **Boards**
    
*   **Controls**
    
*   **Graph queries**
    
*   **Cloud configuration rules**
    
*   **CI/CD and code policies**
    
*   **Threat detection rules**
    
This multi-layered visibility allows security teams to:
*   Detect secret exposures early
    
*   Investigate lateral movement potential
    
*   Enforce remediation through policies and automation