  

<div style="text-align: justify;">

  

# ☁️Cloud SecurityCore Continuation
  

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
|                | 27/02/2025              | First Version Created                         |

<br>
  

## 🚦 1. Service Availability

  

### 📘 1.1 Concepts

  

#### 📈 Auto-Scaling

  

Imagine you own an online store that experiences spikes during sales or holiday seasons—kind of like people rushing into a store on Black Friday (minus the injuries). **Auto-scaling** is like having checkout lanes magically appear exactly when you need them. When customers flood in, lanes (servers or instances) pop open automatically, and when demand drops, these lanes disappear—saving money and energy.

  

- **🧐 Why it matters**:  

  - Keeps apps smooth under pressure (like a calm barista during the morning rush).  

  - Saves cash by shrinking infrastructure when it's quiet (no unnecessary coffee breaks).

- **🛒 Real-world example**: An e-commerce site using AWS Auto Scaling or Azure Scale Sets to handle Black Friday madness—then relax afterward.

  

<center>

  

::: video

  

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/yhWzXrHhZ6g" title="How the Autoscaling system works." frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

  

:::

  

🎥 *How the Autoscaling system works*

</center>

  

#### ⚖️ Active-Active vs. Active-Passive

  

These two strategies determine how multiple systems or data centers stay ready for action:

  

- **🚀 Active-Active**:  

  Think of this like two Starbucks across the street from each other—both open and serving coffee. If one runs out of espresso (ouch!), customers seamlessly shift to the other without noticing.

  - **📌 Use Case**: Global apps (like your favorite social media) balancing users for speed and reliability.

  

- **⏳ Active-Passive**:  

  Imagine having a spare Starbucks stocked and ready but closed until the main one runs out of coffee beans. Then, boom, it opens immediately.

  - **📌 Use Case**: Budget-conscious companies needing reliable disaster recovery without running multiple sites constantly.

  

<center>

  

::: video

  

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/MDuCFh1XuZU" title="Active-Active vs. Active-Passive" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

  

:::

  

🎥 *Active-Active vs. Active-Passive*

</center>

  

#### 🩺 Health Checks and Self-Healing

  

Driving a car? Your dashboard lights tell you when something goes wrong (or you ignore them until something explodes). **Health checks** do the same for cloud resources, ensuring they're healthy and responsive.

  

- **🛠️ Self-Healing**:  

  When a server goes down, cloud platforms automatically swap it with a fresh one—like changing a tire while still driving (without the screaming).

- **🚧 Practical example**: Kubernetes restarting containers when they stop responding—like a digital paramedic at your service.

  

#### 🌐 Content Delivery Networks (CDNs)

  

Got users worldwide? Serving content from one data center means slow loading for faraway users (hello, buffering). A **CDN** is like opening local bookstores everywhere, ensuring readers get popular books instantly.

  

- **📌 Typical usage**: Websites delivering images, videos, or static files globally.

- **🚀 Benefit**: Faster user experience, happier customers (no waiting!).

  

#### 🌎 Multi-Region Deployments

  

Multi-region deployments scatter infrastructure across the globe—similar to franchising your burger joint worldwide. If one region takes a hit (natural disaster, network glitch, Godzilla attack), traffic reroutes elsewhere effortlessly.

  

- **📍 Common scenario**: Financial services or streaming platforms demanding global uptime.

- **🛡️ Advantage**: Improved resilience and faster connections (no one likes waiting).

  

#### 🚨 Disaster Recovery (DR) Strategies

  

Disaster Recovery is your "break-glass-in-case-of-emergency" plan, helping you get back up after major outages, cyberattacks, or natural disasters.

  

- **📦 Key DR Approaches**:

  - **💾 Backup and Restore**: Secure off-site backups restored when needed.

  - **🔥 Pilot Light**: Minimal "always-on" version ready to scale up quickly.

  - **🌤️ Warm Standby**: Scaled-down, standby environment—ready to scale instantly.

  - **☀️ Hot Standby**: Full duplicate environment immediately ready to take over.

  
  

### 📊 1.2 Metrics

  

#### ⏱️ Recovery Time Objective (RTO)

  

Think of **RTO** as the maximum coffee break your business can handle before the chaos sets in. If your RTO is 2 hours, you better be back online before your customers notice you're gone!

  

#### 🕑 Maximum Tolerable Downtime (MTD)

  

If **RTO** is your ideal downtime, **MTD** is when everyone officially panics. Surpass MTD and you'll be dealing with disasters—both technical and managerial.

  

#### 💾 Recovery Point Objective (RPO)

  

**RPO** is how much data loss you can stomach if things go sideways. An RPO of 15 minutes means at worst, you'll lose 15 minutes of data—any more than that, and heads roll.

  

#### 🔧 Mean Time to Repair (MTTR)

  

**MTTR** is your "pit stop" speed when fixing failures. A low MTTR means your tech crew works faster than an F1 pit crew (almost).

  

#### 🛠️ Mean Time Between Failures (MTBF)

  

**MTBF** measures system endurance—how long your system runs smoothly before hiccuping. The higher the MTBF, the less often your engineers cry.

  

## 📈 2. Optimization

  

### 🔍 2.1 Metrics

  

Optimization begins by measuring what's going on—CPU usage, memory, I/O, and network latency. If your CPU consistently hits 90%, it’s like trying to run a marathon after Thanksgiving dinner—you need to scale or improve efficiency!

  

### 🚨 2.2 Alerts

  

Instead of manually checking metrics, set up **alerts**. They’ll scream (politely via notifications) if your memory spikes, preventing minor hiccups from becoming major catastrophes.

  

### 📏 2.3 Rightsizing

  

Rightsizing is the Goldilocks approach—ensuring resources are neither too big (over-provisioned and costly) nor too small (under-provisioned and causing meltdowns). Just right.

  

### 🧑‍🏫 2.4 Advisors

  

Cloud advisors (AWS Trusted Advisor, Azure Advisor) offer tips on cost, security, and performance—like your friendly gym trainer, but without the sweaty towels.

  

### 💸 2.5 Cost Management (FinOps)

  

FinOps is finance meeting tech—a culture where engineers and finance folks actually agree (crazy, right?) to optimize costs while keeping performance stellar.

  

- **Budgeting & Forecasting**: Predicting cloud bills accurately (avoiding financial heart attacks).

- **Resource Scheduling**: Turning things off when unused (your wallet will thank you).

- **Tagging**: Labeling resources to know exactly who to blame for overspending.

  

### 🚀 2.6 Performance Tuning

  

Performance tuning is your app’s regular health check-up. Profiling code, spotting slowdowns, and tuning things up like a well-maintained sports car—making your users (and servers) happier.

  

## 🏗️ 3. Landing Zone High-Level Design

  

A cloud landing zone is your blueprint for cloud growth. It covers:

  

- **🌐 Networking**: Secure, efficient connections.

- **🔑 Identity Management**: Making sure everyone has the right keys.

- **🔒 Security & Compliance**: Setting safety guardrails.

- **📜 Governance**: Rules to keep everything neat and compliant.

  

Get this right from day one, or face an endless cleanup nightmare.

  

## 🛡️ 4. Security Support Solutions

  

Beyond native cloud security, additional solutions provide extra armor:

  

- **🚓 IDS/IPS**: Stops suspicious traffic like a digital bouncer.

- **🧱 Web Application Firewall (WAF)**: Shields web apps from attacks.

- **🔎 SIEM**: Analyzes logs to catch bad guys in real-time.

- **📖 Incident Response**: A playbook detailing the “who-does-what” when things explode.

  

## 📋 5. Cloud Governance, Compliance

  

Governance and compliance ensure everyone follows the rules (so you don’t get sued):

  

- **🛂 Policy Enforcement**: Automatic checks to keep everyone honest.

- **📑 Regulatory Requirements**: Proof you’re doing everything by the book.

- **🔍 Risk Management**: Regular audits to catch troublemakers early.

  

## ⚙️ 6. Cloud Operations

  

### 🔭 6.1 Observability

  

Observability lets you see everything happening in your systems:

  

#### 📜 Logging

  

- **📂 Centralized Logging**: All logs in one place, no log left behind.

- **🗃️ Structured Logs**: Logs formatted neatly, easy to read (even before coffee).

  

#### 🚦 Monitoring and Alerting

  

- **📈 Metrics**: Real-time numbers—your cloud’s vital signs.

- **🚩 Alerts**: Loud enough to notice but polite enough not to ruin your day.

  

#### 🔗 Distributed Tracing

  

Follows user requests through microservices, tracking latency or errors—think package tracking but for your code.

  

#### 📡 Advanced Analytics

  

- **🔍 Anomaly Detection**: Spots weird stuff before it’s a big issue.

- **🔮 Predictive Analytics**: Forecasts problems before they happen (fortune-telling but useful).

  

### 🛠️ 6.2 Building for Scalability

  

#### ⚖️ Load Balancing

  

Spreads the load so no server feels overwhelmed—like multiple baristas handling the morning rush.

  

#### 🌀 Chaos Engineering

  

Intentionally breaking things in controlled ways—Netflix-style—to strengthen resilience (yes, breaking stuff on purpose).

  

### 🔄 6.3 Workload Life Cycle

  

1. **✏️ Plan & Design**: Good planning = fewer emergencies.

2. **🚀 Deploy**: Automated deployments, zero drama.

3. **⚙️ Operate**: Smooth operations with continuous monitoring.

4. **🔧 Optimize**: Constant improvements for maximum efficiency.

5. **🗑️ Retire**: Say goodbye neatly to unused resources.

  

## 📌 7. Project Governance and Collaboration

  

### 📂 7.1 Project Creation

  

Organize cloud projects like neat corporate departments—everyone gets their own space but plays by the same rules.

  

### 🔐 7.2 Permissions Model

  

- **👓 Read-Only Access**: Full visibility for transparency.

- **✏️ Edit Access**: Limited editors, fewer accidents.

  

### 📝 7.3 Governance & Compliance

  

- **🔍 Change Management**: Every change reviewed—avoiding chaos.

- **📈 Auditing & Reporting**: Tracking all moves—compliance and clarity.