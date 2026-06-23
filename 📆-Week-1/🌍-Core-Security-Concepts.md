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
| @<C73C5218-17C3-6B53-B15D-E321D12689EB>                  | 15/02/2025              | First Version Created                         |

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

Security isn't about tools, checklists, or fancy dashboards—**it's about principles**. If you don't understand the core concepts, all the best security tools in the world won't save you. But if you do? You can secure anything—from cloud environments to applications to that janky LG washing machine that's probably [already part of a botnet](https://www.tomshardware.com/networking/your-washing-machine-could-be-sending-37-gb-of-data-a-day).

You need to know **why** security matters, **not just how to configure a tool**.

This section isn't about memorizing definitions or repeating "CIA Triad" like it's some kind of magic spell. It's about **understanding security at its core**. Because if you don't understand why things need to be secure, you'll never secure them properly.

You'll cover:

- **Security Models**: The fundamental ideas behind every security decision
- **Identity & Access Management (IAM)**: Who gets in, what they can do, and why "just give me admin" is always a terrible idea
- **Encryption & Cryptography**: Why sensitive data should always be protected and why "Base64 encoding" **is NOT** encryption
- **Secure Development**: The shift from "just make it work" to **"make it work securely"**

**Security isn't just a checkbox at the end** like many managers like to think... And sure as hell isn't something you can just slap on after everything is done.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/buddy-buzz-vulnerabilities-everywhere-meme-b7ef6e7b-59a7-49ae-9e6d-bac96dd3cf83.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main" 
         style="border: 3px solid lightgray; width: 500px; padding: 1rem; height: auto;" 
         alt="Buddy frightened by Buzz words">
    <div style="color: gray; font-size: small; font-style: italic;">Don't be buddy, don't be frightened, don't push vulnerabilities to prod</div>
</div>

If vulnerabilities make it to production, **fixing them is harder, riskier, and way more expensive**. Your job is to prevent problems before they exist, not play firefighter.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💭 Your role determines how deep you go</b>
    <br><br>
    <b>New hires must cover <i>Optional</i> sections as well</b>, but NOT <i>Advanced</i> ones, these are purely extra.
    <br><br>
    Interns? You get a slightly easier ride (but not by much).
</div>

## 🏛 Security Models

Security isn't just about **slapping on a firewall and calling it a day**. It's about understanding the **fundamental principles** that guide every security decision. These principles are called **security models**.

These models define **how** we secure data, infrastructure, and applications. If you don't understand them, you're just blindly following security rules without knowing why. And that's a great way to make bad security decisions.

They're not just theoretical nonsense. They're the foundation of every security decision you'll make. If you don't understand them, well, MAKE SURE YOU DO. They are THAT important!

You'll go through the **core security models** that shape every security decision:

- 🔺 **CIA Triad**. The golden rule of security thinking: Confidentiality, Integrity, Availability
- ⛔ **Zero Trust**. Assume nothing is safe. Ever
- 🧅 **Defense in Depth**. Security isn't a single layer; it's a whole damn onion
- 🔑 **Least Privilege**. If you don't need it, you don't get it
- ⚖️ **Segregation of Duties (SoD)**.Why one person shouldn't have **too much control**
- 🛠 **Security by Design**. Security isn't a feature; it's a requirement from the start
- 🧩 **Principle of Least Astonishment**. If it's surprising, it's probably a security issue
- 🔐 **Kerckhoffs's Principle**. The key to secure systems is the key, not the system
- 📊 **Pareto Principle (80/20 Rule)**. Focus on the 20% of security issues that cause 80% of the problems

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Tip</b>: Don't just memorize these. **Understand why they matter**. If you can't explain why "Least Privilege" is important, you don't really understand it
</div>

I know, they're a (whole) damn lot, but you need them. You'll thank me in one year when you're not crying over a misconfigured S3 bucket...

### 🔺 CIA Triad

Welcome to **THE** security model. If you don't know this one, you don't know security.

Everything we do in security **aligns with at least one of these principles**:

1. 🔐 **Confidentiality**. If you're not supposed to see it, you don't
2. ⚖️ **Integrity**. If data changes, you should know
3. 🖥️ **Availability**. If you can't access it when you need it, it's useless

The CIA Triad is often represented as a triangle, with each principle at a corner. The triangle is used to show the interdependence of these principles—if one fails, the others are affected and you get hacked. Simple as that.

But... as you can see in the below image, we've chosen to use circles. Why? Because they represent the **interconnectedness** of these principles better. If one circle is broken, the whole system is at risk. And because we're fancy like that.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/cia-triad-7d322409-414b-43ad-9043-02fd0fad6f28.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main" 
         style="border: 3px solid lightgray; width: 750px; padding: 1rem; height: auto;" 
         alt="CIA Triad">
    <div style="color: gray; font-size: small; font-style: italic;">Sad faces = bad security, but the center happy face = good security</div>
</div>

A system with great confidentiality but no availability? Useless. One that prioritizes availability but ignores integrity? Disaster waiting to happen. These three must be balanced based on risk and business needs.

When security fails, it's almost always because one (or more) of these principles was ignored. Real-world failures of the CIA Triad happen all the time, as you'll see in the next sections.

So it seems that this CIA Triad is _**somewhat** importante_, no?

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💭 Remember</b>. Security isn't about blocking everything—it's about balancing  <b>Confidentiality, Integrity, and Availability</b> based on <b>risk</b> and <b>business needs</b>.
</div>

<center>

::: video
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/kPPFNrlN3zo" 
    title="What is the CIA Triad" frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
</iframe>
:::

<br>
</center>

#### 🔐 Confidentiality

If you can't keep data private, **nothing else matters**. Confidentiality ensures that sensitive data is only accessible to authorized users.

**Why it matters?**

- **Data breaches** = instant disaster (think passwords, personal info, financial records)
- **Stops industrial espionage**—because **yes,** some people WILL absolutely try to steal your secrets
- **Keeps attackers, unauthorized employees, and curious idiots out**

**How to ensure it?**

- **Encrypt everything**. Data at rest (stored) and in transit (moving across networks), always. **If it's stolen, it's useless**
- **Use access controls**. Limit who can access what data, and when, e.g., role-based access control (RBAC), multi-factor authentication (MFA), and time-limited access
- **Monitor access**. Track who accesses what data, when, and why. If someone is **accessing sensitive data at 2 AM from Russia**, you should **know**

**Real-world failures**

- **Equifax (2017)**. 148 million records stolen because they didn't patch a **known** vulnerability
- **Snowden Leaks (2013)**. An admin with excessive access dumped NSA secrets worldwide

🔎 **Lesson?** You see the pattern? Bad access control = **someone takes your stuff**.

#### ⚖️ Integrity

If data can be **changed silently**, you can't trust **anything** that relies on it. Integrity ensures that **data is accurate, unchanged, and reliable**.

**Why it matters?**

- **Tampered logs** =  You won't even know you got hacked
- **Manipulated transactions** = Money disappears
- Prevents **supply chain attacks** where malware gets inserted into legitimate applications (hi, SolarWinds)

**How to ensure it?**

- **Use hashing**: Verify data hasn't been altered
- **Use digital signatures**: Ensure data authenticity
- **Implement change control**: If data **changes**, you better know **who, when, and why**

**Real-world failures**

- **SolarWinds Hack (2020)**. Attackers slipped malware into a **legit software update**, compromising 18,000+ companies
- **Stuxnet (2010)**. Malware altered data in Iran's nuclear program, causing centrifuges to **self-destruct**

🔎 **Lesson?** No integrity = **no trust**. And no trust means you're screwed.

#### 🖥️ Availability

If your system **is down when you need it**, it's **useless**. Availability ensures that **data, applications, and services are accessible whenever required**—even under attack.

**Why it matters?**

- **Downtime** = lost revenue, lost access, lost trust
- **Critical systems** (hospitals, banking, infrastructure) can't afford to go down
- **Ransomware & DDoS attacks** target availability because it hurts the most

**How to ensure it?**

- **Redundancy**: If one system fails, another takes over
- **Backups, backups, backups**: If ransomware wipes data, you can restore it
- **Load balancing & failover systems**: So no single system can bring everything down
- **Incident response plans**: Recover **fast** when something goes wrong

**Real-world failures**

- **Colonial Pipeline (2021)**. Ransomware attack shut down **fuel supply to the U.S. East Coast**
- **AWS Outage (2021)**. One internal tool failure **broke Netflix, Disney+, Slack, and more**. I'd love to see that AWS bill...

🔎 **Lesson?** If attackers **own your availability**, they own your business.

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|---|---|---|
| [The CIA Triad: Definition, Components, and Examples](https://www.csoonline.com/article/568917/the-cia-triad-definition-components-and-examples.html) | An in-depth exploration of the CIA Triad with real-world applications | **CSO Online** |
| [What Is the CIA Triad?](https://www.coursera.org/articles/cia-triad) | A comprehensive overview of the CIA Triad principles and their significance in cybersecurity | **Coursera** |
| [CIA Triad: Confidentiality, Integrity, and Availability](https://www.sailpoint.com/identity-library/cia-triad) | Detailed insights into each component of the CIA Triad and its role in information security | **SailPoint** |

**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|---|---|---|
| [What is the CIA Triad](https://www.youtube.com/watch?v=kPPFNrlN3zo) | 4 min | **IBM Technology** |
| [Cybersecurity Architecture: Fundamentals of Confidentiality, Integrity, and Availability](https://www.youtube.com/watch?v=EqNe55IzjAw) | 12 min | **IBM Technology** |

**🛠 Tools & Hands-on Labs**

| 🛠️ **Tool / Lab** | 🔍 **Description** | 🔗 **Link** |
|---|---|---|
| [TryHackMe: Security Principles - Task 2](https://tryhackme.com/room/securityprinciples) | Interactive challenge on applying CIA Triad principles | **TryHackMe** |

**📌 TL;DR**

- **📖 Read** → Articles, official documentation & case studies
- **🎥 Watch** → Short & long-form videos  
- **🛠 Try** → Tools and hands-on labs  

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn
</div>

### ⛔ Zero Trust

"Trust but verify" is dead. **Trust nothing. Verify everything.** That's Zero Trust in one sentence.

It doesn't matter if you're inside the corporate network, on a company laptop, or using your own account. **You still need to prove you belong.** Every request is **a potential threat** until confirmed otherwise. If you're not verified, you're not getting in. Simple as that.

But wait a minute, how did we get here? Is there a problem with trust? Well, actually... there is.

Companies used to think that if you were on the corporate network, you were safe. That illusion shattered when VPN credentials started showing up for sale on the dark web. Attackers realized they didn't need to break in when someone would hand them the keys. And if the network had no internal controls, they could go from "just logged in" to "full domain admin" in minutes.

So, in short, there are **three big problems with trust**:

1. Networks aren't _so_ safe anymore
2. Lateral movement is a real threat—once inside, attackers can go anywhere
3. Users are the weakest link—phishing, stolen credentials, and social engineering are still the top attack vectors

Zero trust isn't paranoia—it's **common sense**.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/Zero%20Trust%20meme%20-%20Batman%20slapping%20Robin-95635d57-fa69-4c56-84bb-faa1b965037c.jpeg&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main" 
         style="border: 3px solid lightgray; width: 500px; padding: 1rem; height: auto;" 
         alt="Zero Trust meme - Batman slapping Robin">
    <div style="color: gray; font-size: small; font-style: italic;">If you don't want to get slapped, you better apply this model...</div>
</div>

#### 🔍 How it Works

Zero Trust means verifying everything, no matter where it comes from. That's not just slapping MFA on your login screen and calling it a day. It means:

- **No implicit trust.** You don't get access just because you're inside the network. Every request is treated as suspicious until proven otherwise
- **Least privilege.** You only get access to what you need, nothing more, nothing longer than needed
- **Microsegmentation.** Splitting the network into tiny zones. No more "flat networks" where one breach = full access = laterally moving everywhere*

Zero Trust is about **limiting the damage** an attacker can do. If they breach one system, they can't move laterally. If they steal one set of credentials, they can't access everything. It's about making sure that even if something goes wrong, it's not a disaster.

*_See what I did there? Laterally, literally... I'm a genius, I know._

#### 💀 What Happens When it Fails?

When companies don't enforce Zero Trust, attackers move freely once they get in. Here are two of the worst real-world cases:

- **Capital One (2019)**. An ex-AWS engineer found a misconfigured IAM role and walked away with 100M+ customer records
- **Uber (2022)**. Weak MFA + social engineering = attackers got full admin control over internal systems. Ouch

Zero Trust doesn't stop attacks—it makes them expensive, time-consuming, and frustrating. In short, a pain the ass. Attackers don't like hard targets. Be one.

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|---|---|---|
| [Zero Trust Architecture](https://www.csoonline.com/article/3247848/what-is-zero-trust-a-model-for-more-effective-security.html) | An in-depth look at the Zero Trust security model and its implementation | **CSO Online** |
| [Zero Trust Overview](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview) | Microsoft's comprehensive guide to understanding and deploying Zero Trust principles | **Microsoft** |
| [NSA Guidance on Zero Trust](https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/3791171/nsa-releases-guidance-on-the-visibility-and-analytics-pillar-of-zero-trust/) | NSA's insights into the Visibility and Analytics pillar of Zero Trust | **NSA** |
| [Google's BeyondCorp](https://cloud.google.com/beyondcorp) | Google's approach to Zero Trust security with BeyondCorp | **Google Cloud** |

**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|---|---|---|
| [Zero Trust Explained in 4 mins](https://www.youtube.com/watch?v=yn6CPQ9RioA) | 4 min | **IBM Technology** |
| [Cybersecurity and Zero Trust](https://www.youtube.com/watch?v=FMMWSLIcaME) | 5 min | **IBM Technology** |

**🛠 Tools & Hands-on Labs**

| 🛠️ **Tool / Lab** | 🔍 **Description** | 🔗 **Link** |
|---|---|---|
| [Zero Trust Lab Guide](https://microsoft.github.io/ztlabguide/) | A structured guide by Microsoft to build your own Zero Trust lab environment | **Microsoft** |
| [Palo Alto Networks Zero Trust Lab](https://github.com/PaloAltoNetworks/lab-aws-zero-trust) | Hands-on lab setup scripts for deploying Zero Trust policies using Palo Alto Networks' VM-Series on AWS | **GitHub** |
| [ATARC Zero Trust Lab](https://atarc.org/atarc-zero-trust-lab/) | Lab showcasing integrated Zero Trust solutions across various vendors | **ATARC** |

**📌 TL;DR**

- **📖 Read** → Articles, official documentation & case studies
- **🎥 Watch** → Short & long-form videos
- **🛠 Try** → Tools and hands-on labs

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn
</div>

### 🧅 Defense in Depth

Security isn't a single layer—**it's a whole damn onion**. If you only rely on one defense mechanism, congratulations, you just made an attacker's life easy.

**Defense in Depth (DiD)** is the idea that security should have **multiple overlapping layers**, so that if one fails, there's another one right behind it to stop the attack. Every layer slows the attacker down, increases their risk of detection, and makes their life miserable.

The **core idea** is simple: multiple layers of security = more chances to stop an attack.

Think of a medieval castle. If all you have is a big front gate, attackers will just go around, tunnel under, or bribe the guard. That's why castles had:

- **A moat (perimeter security)** makes it harder to even get close
- **The front gate (firewalls)** blocks obvious threats but isn't impenetrable
- **Armed guards (authentication)** check who's allowed in
- **Locked doors inside (least privilege)** even if someone sneaks in, they can't go everywhere
- **Watchtowers (logging & monitoring)** spot threats before they get too far

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/defense-in-depth-castle-631fcd3a-85f1-4239-939e-d2ae0b868b6a.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main" 
         style="border: 3px solid lightgray; width: 750px; padding: 1rem; height: auto;" 
         alt="Defense in Depth: A Medieval Castle Analogy">
    <div style="color: gray; font-size: small; font-style: italic;">Layers on layers on layers. Great if you're a castle, not so much if you're an attacker</div>
</div>

If one fails, the others still stand. **That's the whole point**.

But there's no universal one-size-fits-all set of layers. What you protect—and how you deploy it—determines which defenses you need.

<center>

::: video
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/hQXvsfoEhfg" 
    title="Cybersecurity Fundamentals - Defense in Depth" frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
</iframe>
:::

<br>
</center>

#### 🏰 The Core Layers

These apply **everywhere**, whether you're securing a data center, a SaaS app, or a home router:

1. **Perimeter Security**. The first line of defense. It's about keeping threats **outside** your network or application. Firewalls, VPNs, and WAFs are common here
2. **Network Security**. Once attackers get past the perimeter, you need to stop them from moving around. Segmentation, VLANs, and NAC
3. **Authentication & Access Control**. Who gets in, and what they can do once they're there. MFA, RBAC, and ABAC
4. **Endpoint Security**. Protect devices with antivirus, EDR, hardening, patching
5. **Logging & Monitoring**. Detect attacks **before** they spread. SIEM, IDS/IPS, and EDR

These are the **core layers**. But depending on what you're securing, you might need more.

#### 🎭 Variable Layers

Security is about **context** meaning that the layers change depending on what you're protecting and how it's deployed:

- **Data Security**. Encrypting data at rest and in transit, DLP, and data masking
- **Application Security**. Secure coding practices, WAFs, SAST, DAST, and SCA
- **Cloud Security**. IAM, secure configurations, CSPM, and CASB
- **Physical Security**. Cameras, alarms, security guards, badge access, biometric authentication

For example, if you're securing a cloud environment, you might need:

- **IAM**. To control who can access what, enforce least privilege, and apply MFA
- **Secure configurations**. To avoid misconfigurations (open S3 buckets, weak permissions, exposed APIs)
- **Logging & monitoring**. To spot threats before they become disasters

But if you're securing an application, you might need:

- **Secure coding practices**. To prevent vulnerabilities from being introduced
- **WAFs**. To block attacks before they reach the app
- **SAST, DAST, SCA**. To find and fix vulnerabilities before they're exploited

The key is to **understand what you're protecting** and **how it's exposed**. That's how you build the right layers.

#### 🛡️ DiD in Action

Imagine an attacker trying to break into your system.

1. **They steal a password**: MFA blocks them
2. **They phish an employee**: No admin rights, can't do much
3. **They find an unpatched server**:→ Network segmentation stops lateral movement
4. **They drop ransomware**: Backups restore everything, no ransom paid
5. **They try exfiltrating data**: DLP (Data Loss Prevention) shuts them down

Each layer stops them, slows them down, or makes their life miserable. That's the power of DiD.

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|---|---|---|
| [Defense in Depth Explained](https://www.csoonline.com/article/2120511/what-is-defense-in-depth.html) | Introduction to Defense in Depth, covering its importance and implementation | **CSO Online** |
| [Fortifying Digital Frontiers](https://medium.com/@stevan.lake/fortifying-digital-frontiers-a-cyber-threat-intelligence-journey-71141824428d) | A cybersecurity professional’s perspective on strengthening defenses | **Medium** |
| [Microsoft’s DiD Guide](https://docs.microsoft.com/en-us/microsoft-365/security/defender/defense-in-depth?view=o365-worldwide) | Microsoft’s approach to Defense in Depth in cloud environments | **Microsoft** |
| [NIST Guide to Defense in Depth](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-53r5.pdf) | Official NIST guidelines on implementing layered security | **NIST** |
| [SANS Guide to Defense in Depth](https://www.sans.org/blog/defense-in-depth-a-practical-strategy-for-achieving-information-assurance-in-todays-highly-networked-environments/) | A deep dive into practical strategies for layered security | **SANS** |

**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|---|---|---|
| [Concept of Defense in Depth](https://www.youtube.com/watch?v=CHKS2FcEMek) | 7 min | **John Savill's Technical Training** |
| [Defense in Depth Is Dead, Long Live Depth in Defense](https://www.youtube.com/watch?v=3Qv1ZJ3v7ZQ) | 14 min | **RSA Conference** |
| [What is Defense-in-Depth? - How to implement defense-in-depth](https://www.youtube.com/watch?v=a3JR1i2HBoU) | 25 min | **CyberPlatter** |

**📌 TL;DR**

- **📖 Read** → Articles, official documentation & case studies
- **🎥 Watch** → Short & long-form videos

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn.
</div>

### 🔑 Least Privilege

Least Privilege is about giving users **only the access they need** to do their job—no more, no less. Because every extra permission is **another attack vector**. "Give me admin rights" and "just this once" are the **two most dangerous phrases** in security.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/least-privilege-elmo-meme-83ea0476-ee0b-4476-b06a-a66038bb1a3e.jpg&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main" 
         style="border: 3px solid lightgray; width: 450px; padding: 1rem; height: auto;" 
         alt="Elmo bad, elmo dones't implement least privilege">
    <div style="color: gray; font-size: small; font-style: italic;">Security teams <b>loves</b> shiny new stuff</div>
</div>

How to implement:

- Use role-based access control (RBAC) to strictly limit permissions, i.e. assign permissions based on roles, not individuals
- Regularly review and revoke unneeded access
- Apply time-bound privileges for high-risk actions

Let's say you're a developer. You don't need access to the production database, right? But if you have it, you can do a lot of damage: delete records, steal data, or just mess things up.

But you're not the only one who we need to worry about. **What if your credentials are stolen**? If you have admin rights, the attacker can do anything you can. If you only have access to what you need, the worst you (or an attacker) can do is... well, not much.

That's the power of Least Privilege.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>☝️🤓 Remember</b>.  When access is given to someone, you're not just trusting them—<b>you're trusting everyone they interact with</b>
</div>

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|---|---|---|
| [Principle of Least Privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege) | Comprehensive explanation of the principle | **Wikipedia** |
| [Principle of Least Privilege: Definition, Methods & Examples](https://www.okta.com/identity-101/minimum-access-policy/) | Overview of least privilege policies and implementation strategies | **Okta** |
| [The Principle of Least Privilege Explained (with Best Practices)](https://www.splunk.com/en_us/blog/learn/least-privilege-principle.html) | Insights into the principle and best practices for implementation | **Splunk** |
| [Implementing Least-Privilege Administrative Models](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) | Guide on applying least privilege in administrative contexts | **Microsoft** |
| [Security Best Practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) | Recommendations for Identity and Access Management, emphasizing least privilege | **AWS** |


**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|---|---|---|
| [What is the Principle of Least Privilege?](https://www.youtube.com/watch?v=8GZ6516Kao4) | 7 min | **Google Cloud Tech** |

**🛠 Tools & Hands-on Labs**

| 🛠️ **Tool / Lab** | 🔍 **Description** | 🔗 **Link** |
|---|---|---|
| [IAM Access Analyzer](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html) | AWS tool to help identify and reduce broad permissions, aligning with least privilege principles. | **AWS** |
| [Privileged Access Management Solutions](https://www.beyondtrust.com/resources/glossary/privileged-access-management-pam)) | BeyondTrust's suite of tools to enforce least privilege across environments. | **BeyondTrust** |

**📌 TL;DR**

- **📖 Read** → Articles, official documentation & case studies
- **🎥 Watch** → Short & long-form videos
- **🛠 Try** → Tools and hands-on labs

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn
</div>

### ⚖️ Segregation of Duties (SoD)

No one should be able to both prepare the crime **and** approve it. That's the core of Segregation of Duties. It stops **one person** from having too much control.

Think about financial fraud: If the same person is both the accountant and the approver, **they can easily cook the books**. But if one person prepares the transaction and another approves it, it's much harder to commit fraud. **That's why banks require dual approval for big transactions**.

<center>

::: video
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/gdReLybtn3s" 
    title="Segregation of Duties" frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
</iframe>
:::

<br>
</center>

🔑 **Key practices:**

- Divide critical tasks among multiple roles
- Ensure no one person has end-to-end control over a process
- Implement dual authorization for sensitive operations
- Regularly audit and rotate duties to avoid concentration of power

The last one, specifically the **rotation of duties**, seems like a **pain in the arsehole**, a bureaucratic nightmare if you ask me. But it's **necessary** to avoid **collusion, fraud, and human error**. If you're the only one who can do something, you're the only one who can screw it up. **Rotating duties keeps everyone on their toes**.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>🏛️ SoD isn't about bureaucracy</b>—it's about ensuring one person's mistake (or malice) <b>doesn't bring everything down</b>
</div>

SoD is common in multiple areas

- 💰 **Finance**: One person submits a transaction, another person approves it
- 💻 **IT**: Separating development, testing, and deployment
- 🔐 **Security**: The person who sets security policies shouldn't be the one auditing them

#### 💀 What Happens When it Fails?

Bad things happen, as always. Here are **two of the worst real-world cases**:

- **Enron Scandal (2001)**. One of the most infamous corporate fraud cases. SoD failures were a major factor. Employees could **manipulate financial records** because there was no separation. The same people handled **both financial reporting and accounting irregularities**. No oversight. No checks. Just an open door for fraud.

- **Wells Fargo (2016)**. Employees **created millions of fake accounts** to meet sales targets. **SoD failures** made it possible. The same people could **create and approve accounts** without oversight, as some had both sales and account management roles

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|---|---|---|
| [Segregation of Duties Basics and Best Practices](https://www.indeed.com/hire/c/info/segregation-duties-basics-best-practices) | Overview of SoD principles and actionable best practices | **Indeed** |
| [Implementing Segregation of Duties: A Practical Experience Based on Best Practices](https://www.isaca.org/resources/isaca-journal/issues/2016/volume-3/implementing-segregation-of-duties-a-practical-experience-based-on-best-practices) | An in-depth guide on effectively implementing SoD to prevent errors and fraud | **ISACA** |
| [Segregation of Duties (Preventive & Detective)](https://www.finance.ucla.edu/corporate-accounting/controls-and-accountability/control-practices/segregation-of-duties-preventive-detective) | Insights into preventive and detective controls for SoD | **UCLA Finance** |

**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|---|---|---|
| [Segregation of Duties](https://www.youtube.com/watch?v=gdReLybtn3s) | 5 min | **Edspira** |

**📌 TL;DR**

- **📖 Read** → Articles, official documentation & case studies
- **🎥 Watch** → Short & long-form videos

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn
</div>

### 🛠 Security by Design

Why slap security on at the end when you can build it in from the start? Security needs to be designed in **from the start**. Security by Design is about making sure security is part of every decision, from architecture to deployment.

These are the core principles of Security by Design:

- **Conduct threat modeling** before writing a single line of code, figure out where the risk are
- The **safest configuration should be the default**, not something users have to enable manually
- Use **secure coding practices** to prevent vulnerabilities from being introduced
- **Automate security testing** to catch vulnerabilities early and often
- Systems should be built assuming some part will eventually be compromised
- **Educate, educate and, you guessed it, educate**. Everyone needs to understand security basics

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|---|---|---|
| [Secure by Design](https://www.cisa.gov/securebydesign) | Guidance from CISA on integrating security into the software development lifecycle to prevent vulnerabilities | **CISA** |
| [Security by Design: The Ten Principles of Getting It Right](https://medium.com/@tahirbalarabe2/security-by-design-the-ten-principles-of-getting-it-right-68c6ff00ffe1) | An article outlining ten essential principles for implementing Security by Design effectively | **Medium** |
| [Security by Design: An Annotated Resource List](https://www.lawfaremedia.org/article/security-by-design-an-annotated-resource-list) | A curated list of government documents, guidelines, and analyses on Security by Design | **Lawfare** |

**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|---|---|---|
| [10 Principles for Secure by Design: Baking Security into Your Systems](https://www.youtube.com/watch?v=3l8GwLv2f3E) | 15 min | **YouTube** |
| [Secure by Design: Hardening Best Practices](https://www.youtube.com/watch?v=cGoWeFlV2ZQ) | 20 min | **YouTube** |
| [Secure by Design Principles](https://www.youtube.com/watch?v=lL1Lg-DvnYk) | 12 min | **YouTube** |

**🛠 Tools & Hands-on Labs**

| 🛠️ **Tool / Lab** | 🔍 **Description** | 🔗 **Link** |
|---|---|---|
| [Microsoft Threat Modeling Tool](https://www.microsoft.com/en-us/securityengineering/sdl/threatmodeling) | A tool by Microsoft to help identify and mitigate potential security issues during the design phase | **Microsoft** |
| [IriusRisk](https://www.iriusrisk.com/) | A platform offering automated threat modeling and secure design features to integrate security into the development process | **IriusRisk** |

**📌 TL;DR**

- **📖 Read** → Articles, official documentation & case studies
- **🎥 Watch** → Short & long-form videos
- **🛠 Try** → Tools and hands-on labs

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn
</div>

### 🧩 Principle of Least Astonishment

If your system does something that makes users go **"WTF just happened?"**, congratulations—you've created a security risk.

Security is already hard enough. The last thing you need is a UI that actively sabotages users into making dumb mistakes. The Principle of Least Astonishment (PoLA) is about making sure systems behave in ways that are **obvious, predictable, and don't feel like a trap.**

Think about it:

- A **"Cancel"** button that actually **deletes everything**? Astonishing. Also a lawsuit waiting to happen
- A **popup asking for a password** but giving no indication of why? Suspicious as hell
- A **security setting that silently resets after an update**? Might as well just hand your data to hackers

Bad UX isn't just annoying—it's a security issue. If users don't understand what's happening, they'll either screw up or get tricked. Probably both.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/bad-ux-meme-07d83312-344e-42f9-9b0a-8e438dc9dacf.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main" 
         style="border: 3px solid lightgray; width: 450px; padding: 1rem; height: auto;" 
         alt="A user fails to log in, resets the password, but the system rejects it as the 'old password.' The user stares at the sunset in defeat">
    <div style="color: gray; font-size: small; font-style: italic;">Windows login be like: <i>"Wrong PIN."</i> Try again. <i>"Still wrong."</i> Reboot. <i>"Welcome!"</i> Oh, so now you remember?</div>
</div>

#### 🤝 General Guidelines

- **Make security actions clear**. If someone is deleting data, say so **explicitly.**
- **Use clear, consistent language**. If a button says "Delete," it should delete, not archive
- **Avoid hidden actions**. If a user can't see it, they can't predict it
- **Reduce unnecessary prompts**. If users are trained to blindly click "OK," you've failed
- **Use defaults wisely**. Default settings should be safe, not surprising
- **Provide feedback**. If something happens, tell the user what it is and why

Basically, don't create something that you wouldn't want to deal with yourself.

#### 💀 What Happens When it Fails?

- **Windows UAC - User Account Control (2006)**. The popup that asks for permission for everything. Users got so used to clicking "OK" that they stopped reading it. And let me tell you, malware authors loved it. So much so that Microsoft had to tone it down in later versions
- **Apple Rootpipe (2014-2015)**. A hidden backdoor in macOS that gave attackers root access without a password. It was discovered in 2014, Apple quietly patched it in 2015, but then left it unpatched for older macOS version

**Lesson?** Don't be that guy at Apple.

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |  
|---|---|---|
| [The Principle of Least Astonishment](https://www.nngroup.com/articles/consistency-and-standards/) | How inconsistent UI patterns lead to user frustration and security risks | **Nielsen Norman Group** |  
| [Dark Patterns: How Bad UX Tricks Users](https://www.darkpatterns.org/) | A collection of deceptive UX practices that confuse users, often compromising security | **DarkPatterns.org** |  
| [How Violating The Principle of Least Surprise Can Introduce Subtle Bugs to Your Code](https://medium.com/u2i-blogs/how-violating-the-principle-of-least-surprise-can-introduce-subtle-bugs-to-your-code-8902cc51dc29) | How unexpected behavior in code and UI can lead to security vulnerabilities and bugs | **Medium** |  
| [Why people ignore security alerts up to 87% of the time – Sophos News](https://news.sophos.com/en-us/2016/08/19/why-people-ignore-security-alerts-up-to-87-of-the-time/) | Study on why users dismiss security warnings and how to make them more effective | **Sophos News** |  

**🎥 Videos**  

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|---|---|---|
| [The Fog of Warnings: How Non-Essential Notifications Blur with Security Alerts](https://www.youtube.com/watch?v=gJjzHUkFclA) | 20 min | **SOUPS 2019 Conference** |
| [STOP Ignoring Microsoft's Security Warnings! What You Need to Know](https://www.youtube.com/watch?v=sQVg9uLnfr8) | 15 min | **Peter Rising MVP** |

**📌 TL;DR**

- **📖 Read** → Articles, official documentation & case studies
- **🎥 Watch** → Short & long-form videos

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Don't just read—experiment</b>. Break things. Fix them. That's how you <b>really</b> learn
</div>

### 🔐 Kerckhoffs's Principle

If your system relies on secrecy to stay secure, **it's not secure.**

Kerckhoffs's Principle (from the 19th century, but still relevant) states: **A system should be secure even if everything about it is public—except the key.** In other words, if your security collapses the moment someone figures out how it works, **you're screwed.**

Think of it like this: A good lock remains secure even if someone knows the exact model, the mechanism inside, and how it's built. The only thing that matters is **the key.** Just ask the _LockPickingLawyer_, he'll crack that 'secure' lock in five seconds and then explain in detail why it's garbage.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>🏃‍♂️If you ever hear</b> a company say, <i>"Our encryption is unbreakable, but we can't tell you how it works,"</i> <b>run</b>
</div> 

A perfect example? **DRM (Digital Rights Management) in video games.**

DRM systems try to prevent piracy by using **"security through obscurity"**—if no one knows how it works, it _must_ be secure, right? But the moment someone reverse-engineers it, the entire system collapses. That's why **every major DRM system gets cracked**—sometimes within days. That's why DRM is a joke. And that's why I... _nevermind_.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/drm-meme-b2e75455-e936-44bd-950c-5ddf477751bd.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main" 
         style="border: 3px solid lightgray; width: 450px; padding: 1rem; height: auto;" 
         alt="Meme of a pirate saying, 'Well yes, but actually no,' with 'DRM' over his face, mocking digital ownership">
    <div style="color: gray; font-size: small; font-style: italic;">Companies that use DRM think they're smart—until they get cracked</div>
</div>

Even today, companies try to market **"proprietary encryption"** like it's a good thing. It's not. Security through obscurity doesn't work because once someone **figures it out**, your whole system collapses. That's why modern cryptography uses **public, well-tested** algorithms like AES, RSA, and ECC—because they've been **brutally** tested by security researchers and still hold up.

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|-------------|-------------------|--------------|
| [The Flaw of Security by Obscurity](https://medium.com/@tahirbalarabe2/the-flaw-of-security-by-obscurity-3b75cb160945) | Discusses the pitfalls of relying on hidden mechanisms for security and emphasizes transparency | **Medium** |
| [A Note About Kerckhoffs's Principle](https://blog.cloudflare.com/a-note-about-kerckhoffs-principle/) | Explores the importance of designing cryptographic systems that remain secure even when everything about the system, except the key, is public knowledge | **Cloudflare Blog** |
| [How DRM Harms Our Computer Security](https://www.eff.org/deeplinks/2014/05/how-drm-harms-our-computer-security) | Examines how Digital Rights Management (DRM) technologies can introduce vulnerabilities and hinder security research | **Electronic Frontier Foundation (EFF)** |
| [Kerckhoffs's Principle vs. Security Through Obscurity: Which is Better?](https://yeow.ong/kerckhoffs-principle/) | Compares the effectiveness of Kerckhoffs's Principle and security through obscurity in system design | **Yeow Ong's Blog** |

**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|-------------|--------------|--------------|
| [Security Via Obscurity Is A Bad Idea](https://www.youtube.com/watch?v=yeMutpl-uuc) | 3 min | **Phil Koopman** |
| [Q&A: Security Through Obscurity](https://www.youtube.com/watch?v=bNp-DrMcyiI) | 15 min | **Surveillance Report** |
| [The Worst DRM Systems in Modern Times](https://www.youtube.com/watch?v=YNUSxFX4elY) | 13 min | **Mental Outlaw** |

**📌 TL;DR**

- **📖 Read** → Articles on the pitfalls of security through obscurity, the importance of transparent cryptographic practices, and the security implications of DRM
- **🎥 Watch** → Videos discussing why hiding security mechanisms doesn't work and how DRM is utter garbace

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Remember</b>, if your security relies on secrecy, <b>it's not secure</b>
</div>

### 📊 Pareto Principle (80/20 Rule)

Not all security problems are created equal. **The Pareto Principle states that 80% of your security risks come from just 20% of the issues.**

Translation? Most of your attack surface is caused by a small handful of **really stupid, really preventable problems.** Instead of trying to secure _everything_, focus on **the few things that actually get you hacked.**

So, what are these magical 20% of issues?

- **Unpatched software**. The \#1 cause of breaches. Patching is boring, but it's also the most effective way to stop attacks
- **Phishing**. The most common attack vector. Improve filters and educate users
- **Misconfigured cloud storage**, like open S3 buckets
- **Look at past incidents.** What caused security failures before? Fix those patterns first

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>🫦 Most attackers aren't geniuses</b>—they're just exploiting the same dumb mistakes over and over
</div>

Applying this principle is easy:

1. Patch your software
2. Focus on identity and access controls
3. Eliminate low-effort, high-reward attack: misconfigurations, weak passwords, and phishing

Cut off the easy wins first, then worry about the rest.

#### 📚 Further Reading

Want to go deeper? Here are our **go-to choices** to reinforce what you just learned.

**📖 Articles & Documentation**

| 🔗 **Title** | 📜 **Description** | 🔍 **Source** |
|-------------|-------------------|--------------|
| [Applying the 80-20 Rule to Cybersecurity](https://www.darkreading.com/cybersecurity-operations/applying-the-80-20-rule-to-cybersecurity) | Discusses how focusing on critical areas can yield significant security benefits | **Dark Reading** |
| [80/20 Cyber Security—Reduce 80% Risk with 20% Effort](https://www.pivotpointsecurity.com/80-20-cyber-security-how-to-reduce-80-of-your-cyber-risk-with-20-of-the-effort/) | Explores how applying the Pareto Principle can optimize cybersecurity efforts | **Pivot Point Security** |
| [The 80 / 20 Principle - Risk & Cybersecurity](https://www.philvenables.com/post/the-80---20-principle) | Insights into how the 80/20 rule applies to risk management and cybersecurity | **Phil Venables** |

**🎥 Videos**

| 🎬 **Title** | ⏳ **Length** | 🔍 **Source** |
|-------------|--------------|--------------|
| [Kenna Security: Using data science to patch fewer vulnerabilities - fix the 5% that matter most!](https://www.youtube.com/watch?v=k4v4IimaNjQ) | 36 min | **BytesTechnology** |
| [Using Paretos Principle for Securing AWS with SCPs - DEF CON 27 Cloud Village](https://www.youtube.com/watch?v=RiZxb98sGTk) | 31 min | **DEFCONConference** |

**📌 TL;DR**

- **📖 Read** → Articles on applying the Pareto Principle to cybersecurity
- **🎥 Watch** → Videos discussing efficient vulnerability management and security assessments

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Focus on the critical 20%</b> to mitigate 80% of your security risks.
</div>

## 🗝 Identity & Access Management

If security had a single point of failure, **this would be it**. Identity & Access Management (IAM) is the **gatekeeper** of your entire system. If it fails, nothing else matters—because **attackers won't hack your servers if they can just log in.**

Companies love to invest in fancy security tools. But if an attacker can bypass all of that just by stealing a password, **none of it matters**. Weak IAM turns every other security measure into a delayed failure.

**👏 Stop. 👏 Doing. 👏 This. 👏**

IAM is about **who gets in, what they can do, and for how long.** Think of it like airport security:

- **Authentication (AuthN):** Proving who you are
- **Authorization (AuthZ):** Controlling what you're allowed to do
- **Session Management:** Making sure access expires when it should

> **💡 Remember:** Authentication = "Who are you?" / Authorization = "What can you do?"

Sounds simple, right? Apparently not, because **most security incidents involve IAM failures in some way**. Attackers don't need to break in when they can just log in. And once they're in, a bad IAM setup lets them move freely, escalate privileges, and do whatever they want.

### 🪪 Authentication

Authentication is **step one** of IAM. If it fails, nothing else matters. Attackers don't need exploits if they can just log in. Most credential theft comes down to **either weak authentication or bad user behavior.**

There are three ways to verify identity:

1. **Something you know**: passwords, PINs, security questions
2. **Something you have**: a device, security key, authenticator app
3. **Something you are**: biometrics like fingerprints or face recognition

> ⚠️ **MFA should combine at least two of these**. Using two passwords (e.g., password + security question) is not real MFA—it's just more of "something you know."

#### Authentication Weaknesses

Authentication fails in two ways:

- **Weak MFA and Password Security**. If authentication is weak, IAM is just an illusion
- **Long-Lived Sessions & Session Hijacking**. Authentication isn't just about **getting in**—it's about making sure **attackers can't stay in

> **💡 Most credential theft happens** because authentication is either too weak or too inconvenient—so users bypass it.

##### [Advanced] Weak MFA and Password Security

- **SMS-based 2FA**. SIM swapping is so easy that attackers **literally have call centers** dedicated to scamming mobile carriers
- **Email-based verification**. If an attacker compromises your email, **they own everything**
- **Biometric-only authentication**. Your face and fingerprints **can't be changed** if compromised. Worse, **deepfake attacks** and **sensor spoofing** are getting better
- **Hardcoded credentials in source code**. Developers still do this, and attackers still love scanning GitHub for exposed keys

##### [Advanced] Long-Lived Sessions & Session Hijacking

- **No session expiration**. If an attacker steals an old session token, they're in forever
- **No reauthentication for critical actions**. A user should be forced to verify identity before changing security settings or performing sensitive action
- **Session hijacking via cookies**. If an attacker steals a session cookie (e.g., via **XSS** or **MITM attacks**), they bypass authentication entirely

#### Best Practices

- **Use phishing-resistant MFA everywhere**. No SMS-based 2FA. FIDO2, passkeys, hardware tokens only
- **Enforce strong password policies**. Block reused, weak, or breached passwords
- **Rotate and expire session tokens**. Limit exposure by enforcing automatic logouts
- **Use adaptive authentication**. If a user logs in from a new device or location, ask for extra verification
- **Implement single sign-on (SSO)**. Fewer passwords = fewer chances to screw up

#### Authentication Protocols

These are the **industry-standard** authentication protocols that everyone working in IAM **must** understand:

- **OpenID Connect (OIDC)** The most widely used **authentication** protocol, built on top of OAuth 2.0. Used for web and mobile logins (e.g., "Sign in with Microsoft)
- **Kerberos**. A **ticket-based** authentication protocol used in enterprise environments (Active Directory, corporate SSO). Eliminates password reuse by using cryptographic tickets
- **FIDO2/WebAuthn**. A **passwordless authentication** standard that uses cryptographic keys stored in hardware security devices (e.g., YubiKeys, biometric authentication)

> **💡 OAuth 2.0 is NOT an authentication protocol.** It's an authorization framework. That's why OpenID Connect exists—to add authentication on top of OAuth.

#### Further Reading

[TODO]

### 👮 Authorization

Even if an attacker gets valid credentials, **authorization should prevent them from doing real damage.** Authentication determines **who gets in**, but authorization controls **what they can do** once inside.

Bad authorization is why attackers **don't need 0-days**—they just need to compromise **one overprivileged account** and suddenly they own the system.

#### Authorization Weaknesses

Authorization failures **don't always look like breaches** at first. Many of them are **silent permission mistakes** that sit unnoticed—until an attacker exploits them.

- **Overprivileged accounts**. If everyone has admin rights, no one does
- **Misconfigured Cloud IAM Policies**. Open S3 buckets, exposed APIs, and weak permissions are the result of bad IAM policies
- **Lack of Access Reviews & Auditing**. If you don't know who has access to what, you can't spot overprivileged accounts

##### [Advanced] Overprivileged Accounts

Most users have **way more access than they actually need**. This is a disaster waiting to happen.

- **"Just in case" access**. Instead of granting permissions only when needed, users get way too much access by default
- **Admin accounts used for daily tasks**. If an attacker compromises an admin account, they get everything
- **No role separation**. Developers with direct access to production. Finance teams able to modify logs. Disaster waiting to happen

##### [Advanced] Misconfigured Cloud IAM Policies

Cloud permissions are **notoriously easy to screw up.** Attackers love **misconfigured IAM policies** because they often lead to **accidental full access.**

- **Overly broad permissions**. `"Action": "*"`, `"Resource": "*"`—these mean **full access to everything**
- **No service account restrictions**. A leaked API key with unrestricted permissions = **attackers running cloud infrastructure on your dime**
- **No network-based restrictions**. IAM should consider location, device, and behavior, not just username and password

AWS data leaks have happened over and over because S3 buckets were misconfigured as public—allowing anyone to download sensitive data without even logging in.

##### [Advanced] Lack of Access Reviews & Auditing

IAM is often **set up once and forgotten**, leading to unnoticed security holes.

- **Orphaned accounts**. Ex-employees still having access after months—or years
- **No access logs**. If you don't track IAM activity, you have no way of knowing when it's abused
- **Privilege creep**. Permissions accumulate over time until low-level users have near-admin access

#### Best Practices

- **Implement Role-Based Access Control (RBAC)**. Assign permissions to roles, not individuals
- **Use Attribute-Based Access Control (ABAC)**. Limit access based on user location, device, and behavior
- **Enforce Just-in-Time (JIT) Access**. Grant admin rights only when needed, then revoke them automatically
- **Require approval for privilege escalation**. No one should be able to grant themselves admin access
- **Regularly review and remove unused permissions**. If a user doesn't need access anymore, remove it

#### Authorization Models

Different models dictate how permissions are assigned and enforced:

- **Role-Based Access Control (RBAC)**: Permissions are assigned based on roles (e.g., "Finance" role gets access to accounting software)
- **Attribute-Based Access Control (ABAC)**: Uses attributes (e.g., location, department, security level) to determine access
- **Discretionary Access Control (DAC)**: Users can grant access to others—great for collaboration, terrible for security
- **Mandatory Access Control (MAC)**: Strict, policy-driven access used in high-security environments (e.g., military, government)

RBAC is the most common because it's simple, but **ABAC is more flexible for modern cloud environments.**

#### Further Reading

[TODO]

### ⏳ Session Management

Authentication gets you in, **session management keeps you in check.** It controls **how long you stay authenticated**, whether your session is still valid, and how quickly an attacker can abuse a stolen token.

A session is essentially the **state of an authenticated user**. The problem? If attackers steal a session token, they don't need credentials anymore—they just **reuse an existing session and walk right in**.

Session security has three main rules:

1. No session should last forever. If you're still logged in from **2019**, something is very wrong
2. Important actions, like changing passwords or security settings, should **force reauthentication**
3. If you change your password or revoke a session, **all existing sessions should be killed instantly**

Session management is **just as important as authentication**. If attackers steal or hijack a session, **they don't need credentials anymore**—they're already inside.

**Fix your session handling, or don't bother with authentication at all.**

#### Common Session Security Failures

Session management fails in four ways:

- **Long-lived sessions**. If sessions never expire, attackers keep access forever
- **Session Hijacking**. An attacker steals your session token (via XSS, MITM, or malware) and reuses it to bypass authentication entirely
- **Session Fixation**. Attackers force victims to use a pre-set session ID, so when they log in, the attacker already has their session
- **No Session Revocation**. If password resets don't kill active sessions, **your reset did nothing**

The **bottom line is** that Sessions = Credentials. If attackers steal your session, **they ARE you**.

This is **why session management matters**. If you don't control sessions properly, you're basically **leaving the door open** and hoping no one walks in. Spoiler: they will.

Most of these issues happen because of **bad token handling**.

- Use **short-lived sessions** and enforce expiration
- **Rotate tokens** and bind them to device/IP, so stolen tokens are useless
- **Lock down session cookies** so they can't be stolen
- **Secure your session ID generation**—if your session IDs are predictable, you're practically handing out guest passes

##### [Advanced] Long-Lived Sessions

A session that **never expires** is basically a **permanent backdoor**. If an attacker gets a valid session token, they own the account forever—**even if the user changes their password**.

This happens because:

- Sessions last indefinitely with no forced logout
- "Remember Me" options allow sessions that never expire
- APIs use **static tokens** with no expiration.

How to fix it:

- **Force session expiration** after a set time, even if the user is active
- **Shorten inactivity timeouts**—sessions should expire in minutes, not hours.
- **Use refresh tokens instead of infinite sessions**—OAuth2 does this properly

**Real-World Failure:**

Slack (2022) – Hardcoded session tokens never expired, meaning stolen tokens **remained valid even after password resets**. Because who needs session security when you can just... hope for the best?

##### [Advanced] Session Hijacking

Attackers don't need your password **if they can just steal your session**. A valid session token means **full access without authentication**.

This happens because:

- **XSS attacks** steal session cookies from `document.cookie`
- **MITM attacks** intercept session tokens over unencrypted connections
- **Session replay** lets attackers reuse stolen tokens if they don't expire
- **Weak cookie security** (`HttpOnly`, `Secure`, `SameSite=Strict` missing) makes it **too easy** to steal session data

How to fix it:

- **Use `HttpOnly` cookies** to block JavaScript from accessing tokens
- **Enforce HTTPS everywhere**—unencrypted traffic is an open invitation
- **Rotate tokens and bind them to device/IP**—force reauthentication if location or device changes
- Set **`Secure` and `SameSite=Strict` flags** to prevent CSRF attacks from hijacking active sessions

**Real-World Failure:**

Okta Breach (2023) – Attackers stole session tokens, bypassing authentication for high-privilege accounts. The breach was possible due to **weak session security** and **lack of token rotation**.

Apparently, "security company" doesn't always mean "secure company."

##### [Advanced] No Session Revocation

If changing a password **doesn't log out old sessions**, an attacker **still has access** even after the user "secures" their account.

This happens because:

- Password resets don't kill active sessions
- Users **can't view or revoke** active sessions
- Single Logout (SLO) isn't implemented in federated logins

How to fix it:

- **Expire all sessions on password reset**—this should be non-negotiable
- **Allow users to manage active sessions** (e.g., "Log out from other devices")
- **Implement Single Logout (SLO)** for federated authentication (SSO)

**Real-World Failure:**

Facebook (2018) – 50 million accounts compromised due to session tokens **remaining valid even after a reset**. The breach was possible because **password changes didn't kill active sessions**.

That's right, resetting your password did absolutely nothing. Bravo, Facebook.

##### [Advanced] Session Fixation

A sneaky way to **force victims to use a session ID that the attacker already controls**.

This happens when:

- The system **doesn't regenerate session IDs after login**
- Users authenticate into **an existing session ID set by an attacker**

How to fix it:

- **Regenerate session IDs after login**. Always create a new session when authentication happens
- **Never accept externally supplied session IDs**. The server should always generate them
- **Lock down session cookies** to prevent tampering

**Real-World Failure:**

PHP Session Handling (2010s) – Older versions of PHP allowed session fixation attacks by **not regenerating session IDs on login**.

#### Best Practices

Good session management isn't just about **keeping users logged in**—it's about **keeping attackers out**. If you get this wrong, you're practically handing out VIP passes to your system.

##### Use Short-Lived Sessions

- **Set strict expiration times**. Sessions should **expire in minutes, not days**
- **Use refresh tokens** instead of extending sessions indefinitely
- **API tokens should be short-lived**, and long-lived API keys should require additional authentication (e.g., OAuth 2.0 flows)

##### Rotate and Revalidate Sessions

- **Regenerate session tokens on every login** to prevent session fixation
- **Rotate tokens on privilege changes**—if a user gets admin rights, issue a new session token
- **Enforce reauthentication** for high-risk actions like changing passwords, modifying IAM policies, or accessing sensitive data

##### Bind Sessions to Context

- **Restrict sessions to specific IPs or devices**. If an IP or device changes, force reauthentication
- **Detect anomalies**—if a session suddenly jumps locations, assume it's compromised

##### Harden Your Cookies

- **Use `HttpOnly` cookies** so JavaScript can't access session tokens
- **Set `Secure` flag** to prevent cookies from being sent over HTTP
- **Use `SameSite=Strict`** to block cross-site request forgery (CSRF) attacks
- Never store tokens in **localStorage or sessionStorage**—they're just as vulnerable as cookies

##### Kill Sessions When They're No Longer Needed

- **Expire all active sessions when a user logs out or resets their password**
- **Show users their active sessions** and let them revoke unwanted ones
- **Implement Single Logout (SLO) for federated logins**—logging out from one service should log you out from all linked services

#### Hardening YOUR Sessions

Good session management isn't just about **what happens on the server**, your own system and habits matter too. Even the best security setup won't save you if an attacker has persistent access to your machine.

1. Always use non-privileged user account to login interactively and to operate your system on a daily basis
2. **Run your browser in a separate, non-privileged account**. This isolates cookies and makes session hijacking harder
3. **Enable "Core Isolation" and Memory Integrity (Windows)**. Prevents attackers from messing with system memory to persist after hijacking a session
4. **Enable "Controlled Folder Access" (Windows)**. Protects critical files from ransomware and unauthorized modification. Add only known and trusted programs to the "Authorized" list
5. **Use Admin account with care** and ensure you are 100% sure what you're doing
6. If you're seeing logins from places you've never been, **assume you're compromised**

No excuses now—**secure your sessions.**

### 📚 Further Reading

**🎥 Videos**

- [Introduction to Session Management - Identifying Security Vulnerabilities](https://www.youtube.com/watch?v=usqf6EhUdoA): Explains the basics of session management and common vulnerabilities
- [Session vs Token Authentication in 100 Seconds](https://www.youtube.com/watch?v=UBUNrFtufWo): Quick comparison of session and token-based authentication
- [Session Hijacking Attack | Session ID and Cookie Stealing | SideJacking](https://www.youtube.com/watch?v=oI7dX6DWyTo): Breakdown of attack techniques and mitigation strategies

**📖 Guides & Cheat Sheets**

- [OWASP Session Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html): The Bible for secure session handling
- [Snyk: Session Management Security](https://snyk.io/blog/session-management-security/): Covers token security, session expiration, and proper cookie settings
- [ScreenConnect: Best Practices](https://www.screenconnect.com/blog/session-management-best-practices/): Practical steps for securing sessions in web apps

**📰 Articles & Case Studies**

- [Ping Identity: How Session Hijacking Works](https://www.pingidentity.com/en/resources/blog/post/session-hijacking.html): Covers both theoretical and practical prevention steps
- [Descope: Session Hijacking Explained](https://www.descope.com/learn/post/session-hijacking): Deep dive into session theft methods and mitigations
- [Behind the Headlines: A Technical Analysis of the Okta Breach](https://soteri.io/blog/okta-breach-technical-analysis): Detailed breakdown of the Okta breach and how session tokens were abused

**🔬 Technical Papers**

- [An Exploration Into Web Session Security](https://arxiv.org/abs/2310.10687): Systematic review of session vulnerabilities and defenses
- [Encryption Algorithm for TCP Session Hijacking](https://arxiv.org/abs/2002.01391): RSA-based cryptographic defenses against session hijacking

## 🔐 Cryptography & Encryption

If encryption didn't exist, security wouldn't either. **Everything—your passwords, banking info, private messages—relies on cryptography.** If someone breaks encryption, they **own your data**. Simple as that.

The good news? **Modern cryptography is (mostly) solid.** The bad news? **People constantly screw up how they use it.**

But cryptography isn't just about scrambling data; it's about ensuring **confidentiality, integrity, and authenticity** (sound familiar? Yeah, it ties directly into the CIA Triad).

Before we get into the details, let's clear up a common misunderstanding:

- **Cryptography**: The **broader field** that also includes hashing (for **integrity**), digital signatures (for **authenticity**), and key exchange
- **Encryption**: A **subset of cryptography** that protects confidentiality. It scrambles data so only someone with the right key can read it

Encryption fails? Your data is exposed. Cryptography fails? You don't even know if the data is real.

### 🔑 Encryption

Encryption converts **plaintext** into **ciphertext**, making it unreadable without the correct key. **If attackers can't read your data, they can't steal it.**

There are **two main types of encryption**:

- **Symmetric Encryption**. **One key** to encrypt and decrypt. Fast, but **if the key is leaked, you're screwed**
- **Asymmetric Encryption**. **Two keys**, one public (to encrypt) and one private (to decrypt). Slower, but better for secure key exchanges. Used in HTTPS, SSH, and secure messaging apps

Good encryption is based on **proven, publicly tested algorithms**. **If your encryption method is "proprietary" or "custom," it's garbage.**

Data can be stolen in :, so encrypt it in all of them

- **Data at Rest**: Encrypting files, databases, and storage (AES-256, BitLocker, LUKS)
- **Data in Transit**: Encrypting network traffic to prevent eavesdropping (TLS, SSH, VPNs)
- **Data in Use**: Encrypting data **while it's being processed**, using **secure enclaves** (Intel SGX, AWS Nitro) or **homomorphic encryption** (still experimental)

In short, **data**.

Each of these has different risks and requires **different encryption strategies**. Encrypting stored data is useless if you're transmitting it in plaintext.

#### [Optional] Symmetric Encryption

Fast and efficient, but **both sender and receiver need the same key**. If the key gets stolen, **game over**. This method requires **secure key distribution** to keep it secure.

- **AES (Advanced Encryption Standard)**: Gold standard and used everywhere. Secure and fast. Use **AES-GCM** for higher security (not CBC)
- **ChaCha20**: Faster than AES on mobile/low-power devices (used in TLS 1.3)

**Common Mistakes:**

- Using **AES-ECB** (no randomness, patterns leak)
- **Reusing IVs in AES-CBC** (makes it predictable)

**Real-World Failure**

WEP (Wireless Equivalent Privacy). Used weak encryption that could be cracked in minutes, making early Wi-Fi networks a joke.

#### [Optional] Asymmetric Encryption

Instead of one shared key, **asymmetric encryption uses two keys**:

- **Public Key** (to encrypt)
- **Private Key** (to decrypt)

Used for **TLS, SSH, digital signatures, and secure key exchange**.

- **RSA**: Being phased out. Use **2048-bit minimum** (better: ECC)
- **ECC (Elliptic Curve Cryptography)**: Stronger than RSA at **smaller key sizes**. Preferred for modern encryption
- **Diffie-Hellman (DH)**: Used for secure key exchanges. **Don't use plain DH**—use **ECDH**

**Real-World Failure**

PlayStation 3 Private Key Leak. Sony screwed up its implementation of ECC by reusing the same key for all consoles. Hackers reverse-engineered it, permanently breaking PS3 security—allowing piracy, and cheating forever, just the way I like it...

#### [Advanced] Hybrid Encryption

Why choose when you can have both? **Hybrid encryption** combines the best of symmetric and asymmetric encryption:

1. **Asymmetric encryption (RSA/ECDH)** to securely exchange a symmetric key
2. **Symmetric encryption (AES/ChaCha20)** to encrypt the actual data

This way, you get the **speed of symmetric encryption** and the **security of asymmetric encryption**. One thing though, DO NOT STORE your session key in plaintext. 👏 IT 👏 DEFEATS 👏 THE 👏 WHOLE 👏 POINT 👏

**Real-World Failure**

Heartbleed (2014). OpenSSL screwed up memory handling, **leaking private keys and session data**. This meant encrypted traffic could be stolen, including passwords, banking details, and session cookies

#### [Advanced] Deprecated Encryption

Some encryption methods are **so broken** that using them is basically **asking to be hacked**. If you see these, **run**:

- **DES/3DES**: Too small key sizes, **cracked in hours**
- **MD5/SHA-1**: **Broken**
- **RC4**: **Insecure** and **deprecated**
- **RSA-1024**: **Cracked in 2022**, use **2048+**

### [Advanced] 🛠 Key Management

Encryption is **useless** if you don't protect the keys. Losing an encryption key is like locking your door and throwing away the key. Using a weak key is like **locking your door with a piece of string**.

Common key management mistakes:

- **Hardcoded keys**: If your encryption key is in your source code, **it's not secure**
- **Weak key lengths**: If you're using **AES-128**, **RSA-1024**, or **ECC-160**, you're asking to be broken
- **Reusing the same key everywhere**: If one system is compromised, they all are
- **Storing keys in plaintext**: Just... why?

And, to fix it:

- **Use strong key lengths** like 256-bit AES, or even better, 2048-bit RSA
- **Rotate keys regularly**: Even the strongest key is **not meant to last forever**
- **Use a Key Management System (KMS)**: AWS KMS, Azure Key Vault, HashiCorp Vault
- **Use HSMs (Hardware Security Modules) for high-security environments**

> **Perfect Forward Secrecy (PFS)**. If an attacker steals your key, they can decrypt all past traffic. PFS ensures that **even if a key is compromised, past data remains secure**.
>
> FPS does this by generating **ephemeral keys** for each session, so even if one key is stolen, it can't decrypt past sessions. TLS 1.3 enforces PFS by default.

**Real-World Failure**

Marriott (2018). Used **encryption but stored the decryption key next to the data**. Might as well have left it in plaintext.

### 🔏 Other Uses of Cryptography

Cryptography isn't just about encryption. It's about **protecting data, ensuring integrity, and proving authenticity**. If encryption is the lock, cryptography is the key, the door, and the security guard. There's also:

- **Hashing**: Creating a fixed-size, unique hash of data. It's used for integrity checks and password storage
- **Digital Signatures**: Using asymmetric encryption to prove data hasn't been tampered with
- **Randomness & Key Generation**: Strong encryption depends on strong randomness. Weak keys are like leaving your door unlocked

#### Hashing (Data Integrity & Password Security)

This shouldn't need to be said, but **Base64 is not encryption**. It's just a way to encode data.

Unlike encryption, **hashing is one-way**. It's a way to **scramble data** so you can **check if it's the same** without revealing the original. Used for **password storage, data integrity, and digital signatures**.

- **SHA-256**: Used in Bitcoin, secure for now
- **Argon2, bcrypt, PBKDF2**: Used for password hashing. **Never store raw passwords**
- **MD5, SHA-1**: **Broken**. If you see these, **run**

Hashing is like a **fingerprint** for data. If the hash changes, you know the data has been tampered with.

Just so we're clear:

| Feature     | Encryption           | Hashing                     |
|-------------|----------------------|-----------------------------|
| Reversible? | Yes (with key)       | No                          |
| Used for    | Protecting data      | Data integrity              |
| Common uses | Disk encryption, TLS | Password storage, checksums |

Bad password security happens when people **hash passwords with MD5/SHA-1** or **store them in plaintext like absolute morons**.

**Real-World Failure**:

LinkedIn (2012). Stored passwords with SHA-1. Attackers cracked millions of them **because SHA-1 is garbage**.

#### Digital Signatures & Certificates (Authenticity & Verification)

Prove that **a message or file hasn't been tampered with**. Used in **software updates, emails, and SSL/TLS**.

- **RSA/ECDSA signatures**: Used to verify emails (DKIM), software (code signing), and HTTPS certificates
- **TLS certificates**: Encrypts and authenticates websites (HTTPS)

**Real-World Failure**

Stuxnet. Attackers **stole legitimate digital certificates** to sign malware, making it look like **trusted software**.

#### [Advanced] Randomness & Key Generation

Weak keys = attackers can guess keys. **Randomness is everything**, and cryptography depends on it.

- **Secure random number generators (CSPRNGs)**. Used for key generation
- **Avoid predictable seed values**. If an attacker knows your seed, they know your keys

**Real-World Failure**

Debian OpenSSL (2008). Developers **accidentally removed entropy**, making private keys **trivially guessable**.

### 🚨 Common Cryptographic Failures

If you think **"we use encryption, so we're secure,"** you're wrong. Most crypto failures come from **bad implementations**.

- **Rolling your own crypto**. Unless you're a cryptographer, you're doing it wrong
- **Weak key sizes**. 1024-bit RSA? **Might as well not encrypt at all**.
- **Reusing IVs in AES-CBC**. This leaks patterns and **weakens encryption**
- **Poor password hashing**. If you hash passwords with MD5 or SHA-1, **you're already hacked**
- **Broken RNG (Random Number Generators)**. Predictable Randomness = Predictable Keys
- **Using Expired or Weak Certificates**. Expired TLS certificates break security and **allow MITM attacks**

> **Real-World Failure**: Adobe (2013). Encrypted passwords **without hashing**. Attackers **just decrypted them** like a normal file.

#### [Advanced] Post-Quantum Cryptography

Quantum computers could break RSA and ECC. Future-proof alternatives (**Kyber, Dilithium, Falcon**) are being developed, but **not yet widely adopted**.

- **Problem**: Shor's Algorithm could theoretically break RSA/ECC once quantum computing scales
- **Solution**: Post-Quantum Cryptography (PQC) introduces lattice-based, hash-based, and code-based cryptographic schemes
- **Status**: NIST is currently standardizing **Kyber** (key exchange), **Dilithium** (digital signatures), and **Falcon** (alternative signatures)

For now, **don't panic**, but **don't ignore it either**—the transition is coming.

### 📚 Further Reading

**🎥 Videos**

- [Asymmetric Encryption - Simply Explained](https://www.youtube.com/watch?v=AQDCe585Lnc): Straightforward explanation of encryption
- [How NOT to Store Passwords! - Computerphile](https://www.youtube.com/watch?v=8ZtInClXe1Q): Why bad password hashing gets you hacked
- [Cryptography Tutorial For Beginners | Edureka](https://www.youtube.com/watch?v=5jpgMXt1Z9Y): Deep dive into cryptographic principles

**📰 Articles**

- [AES Explained Simply](https://privacycanada.net/aes-encryption-guide/): Beginner-friendly AES explanation
- [Guide of the Advanced Encryption Standard](https://medium.com/quick-code/understanding-the-advanced-encryption-standard-7d7884277e7): In-depth look at AES encryption
- [The Irony (and Dangers) of Predictable Randomness](https://www.keyfactor.com/blog/the-irony-and-dangers-of-predictable-randomness/): Why weak randomness is a security disaster
- [NIST's Post-Quantum Cryptography Standardization](https://csrc.nist.gov/projects/post-quantum-cryptography): Future-proofing against quantum threats

**📖 Books**

- *Serious Cryptography* by Jean-Philippe Aumasson. Probably the best modern cryptography book
- *Introduction to Modern Cryptography* by Jonathan Katz and Yehuda Lindell. More theoretical but extremely solid
- *Cryptography and Network Security* by William Stallings: A classic reference covering encryption, digital signatures, and cryptographic protocols

## 🛡 Network Security

Network security isn't just about **firewalls and VPNs**. If your network is insecure, **attackers don't even need to exploit software vulnerabilities—they just walk right in**.

The **goal** of network security is simple: **Keep unauthorized people out and limit what authorized people can do**.

Attackers **love** weak networks because **bad configurations, outdated protocols, and exposed services** make their job **way too easy**.

**A bad network = an easy target.** If your **firewalls suck, your segmentation is nonexistent, and your protocols are outdated**, **you're already owned**.

- **Deny by default**
- **Segment everything**
- **Block bad protocols**
- **Monitor and respond**

Because **if you don't secure your network, attackers will use it for you.**

### Common Network Security Failures

Most **network breaches** happen due to:

- **Open ports everywhere**. If you expose **SSH, RDP, or databases to the internet**, you're **asking to be hacked**
- **Weak or no segmentation**. If one compromised machine means total network access, **you have no network security**
- **Exposed credentials in network traffic**. If your apps still send passwords **in plaintext**, enjoy being breached
- **No monitoring**. If an attacker is inside your network **and you don't even notice**, congrats, they own you
- **Unpatched network devices**. Routers, firewalls, and VPNs **aren't magic boxes**—they have vulnerabilities too

If you **get these wrong**, no firewall in the world will save you.

### 🔌 Perimeter Security

This is the **first layer** of network security—**keeping unauthorized users out**.

#### Firewalls & ACLs

Firewalls are **the network bouncers**. They should:

- **Deny everything by default**. If you allow all traffic by default and only block some things, **you've already failed**
- **Restrict inbound AND outbound traffic**. Outbound **exfiltration matters too**
- **Log everything**. If you don't log traffic, you have **zero visibility**

**Common Mistakes:**

- **"Allow All" Rules**. If you see `"0.0.0.0/0"`, **fix it NOW**
- **Forgetting outbound filtering**. Attackers **love** when they can exfiltrate data without restriction
- **No firewall logging**. If an attacker gets in, how will you know?

### 🕵 Network Segmentation

If an attacker **compromises one machine and gets access to everything**, **you have no security**. **Segmentation limits the blast radius** of an attack.

#### How to Segment Properly

- **Separate production, staging, and dev environments**. No mixing—EVER
- **Limit access between internal systems**. If your dev machines can access the **production database**, fix it
- **Use VLANs and Subnets**. Different systems should never be in the same flat network
- **Enforce Zero Trust**. Don't assume that just because something is **inside** the network, it's **safe**

### 🔑 Secure Remote Access

Remote access is a **huge** attack vector. **If it's exposed to the internet, it's vulnerable.**

#### Common Remote Access Mistakes

- **Exposed SSH/RDP on the internet**. If you expose RDP, **congrats, you just invited ransomware**
- **Weak VPN configurations**. If your VPN **doesn't enforce MFA**, it's **not secure**
- **No logging on remote connections**. Attackers love when **you don't track logins**

#### How to Fix It

- **Never expose RDP/SSH directly to the internet**. Use **bastion hosts**
- **Force MFA on all remote access**. No exceptions
- **Log every remote login** and flag weird locations

### 🌐 Securing Network Protocols

Attackers **love** weak network protocols because **they were never built for security**.

#### Protocols You Shouldn't Be Using

- **Telnet, FTP, SNMPv1, SMBv1**. If you're still using these, **you're already breached**
- **Unencrypted HTTP traffic**. If **login pages don't use HTTPS**, attackers **see every password**
- **LDAP without TLS**. **Your authentication traffic is in plaintext**—fix it

#### Protocols You Should Be Using

- **SSH instead of Telnet**
- **SFTP instead of FTP**
- **TLS instead of plaintext protocols**
- **SMBv3 instead of SMBv1**

### 📡 Detecting & Responding to Network Threats

Network security isn't just **blocking attacks**—you need to **detect and respond** too.

#### Network Monitoring Basics

- **Capture network traffic logs** (NetFlow, Zeek)
- **Monitor unusual outbound traffic**—if a server **suddenly starts sending data to Russia**, **that's bad**
- **Use an IDS/IPS** (Intrusion Detection/Prevention System)

#### Common Signs of an Active Breach

- **Unexpected outbound connections** to weird locations
- **High data transfer rates from internal machines**
- **Strange login attempts from new locations**

### 🚨 Common Real-World Network Security Failures

**Capital One (2019).** Misconfigured firewall let an attacker access **private S3 buckets** directly from the internet. **Fix: Restrict IAM roles and firewall rules**.

**Equifax (2017).** Unpatched Apache Struts vulnerability let attackers **exfiltrate 147 million records**. **Fix: PATCH YOUR SYSTEMS**.

**Marriott (2018).** Network breach lasted **FOUR YEARS** because **no one noticed the data exfiltration**. **Fix: Monitor network traffic**.

### 🔥 Best Practices

- **Default-Deny Firewalls**. **Block all traffic unless explicitly allowed**
- **Segment Networks**. Dev machines shouldn't talk to prod databases
- **Use Strong VPN Configs**. Force **MFA**, use **TLS**, and **disable weak ciphers**
- **Block Outbound Traffic Too**. **Exfiltration is just as bad as intrusion**
- **Monitor Everything**. If you don't log it, you won't see the breach coming

### 📚 Further Reading

**🎥 Videos**

- [Computerphile - How Hackers Intercept Network Traffic](https://www.youtube.com/watch?v=5xFjC8hY7Ew)
- [How Firewalls Work - Simple Explanation](https://www.youtube.com/watch?v=Gz7nvld9sMs)
- [Network Security Explained | Edureka](https://www.youtube.com/watch?v=HS0lRz9TzUo)

**📰 Articles**

- [Zero Trust Networking Explained](https://www.cloudflare.com/learning/security/glossary/what-is-zero-trust/)
- [Why You Should Never Expose RDP to the Internet](https://blog.rapid7.com/2020/06/16/how-rdp-exposure-leads-to-ransomware/)
- [How SMBv1 is Still Getting Companies Hacked](https://unit42.paloaltonetworks.com/eternalblues-smbv1-vulnerability-scanner/)

**📖 Books**

- *Practical Packet Analysis* by Chris Sanders (How to analyze network traffic)
- *The Web Application Hacker's Handbook* by Dafydd Stuttard & Marcus Pinto (Web network security)
- *Zero Trust Networks* by Evan Gilman & Doug Barth (Network segmentation & access control)
