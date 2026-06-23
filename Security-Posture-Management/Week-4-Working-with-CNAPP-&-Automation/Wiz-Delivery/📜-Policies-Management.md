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
 

## Cloud Configuration Rules 🛠️

Is a configuration check that applies to a specific cloud resource type. If a resource does not pass a rule, a cloud configuration finding is generated and associated with a resource on the security graph, but can also correlate other resources. 

For example:
*   Neptune Database Encryption Disabled
*   IAM Users With Console Password Has No MFA
*   Terraform file is using an external provider

The cloud configuration rules in Wiz are powered by Open Policy Agent, or OPA, OPA provides a high-level declarative language called REGO that lets you define security policies as code.

Every Cloud Configuration Rule is defined by:

*   Matcher
— Cloud, Admission Controller, or IaC
*   Resource type—Virtual machine, bucket, etc.
*   Severity—Info, low, medium, high, or critical.
*   Scope—By default, all Cloud Configuration Rules apply to all Subscriptions, but you can edit the Rule to apply it only to resources from specific Subscriptions.
*   Status—Disabled or enabled.

### Use Cases 🎯

Evaluate a single cloud resources configuration
Evaluate non-normalized configuration detailed
- Require near real-time assessment (event triggered)
Create Automation Rules for Remediation and Response
Require RegEx evaluation, such as path evaluation
Require a shift-left evaluation
Block I

### Data Flow 🔄

1.  Every scan cycle, Wiz uses API calls to fetch raw information directly from your cloud environment about every supported resource. For instance, `GetBucketLocation`, `GetBucketPolicy`, and `GetBucketTagging` could be used to fetch all of the raw information about S3 buckets.
    In some cases, Wiz also triggers near real-time fetching for a specific resource or resource type when a certain event has been detected.
2.  The assembled raw JSONs are saved and then fed into the Cloud Configuration Rules engine, which identifies all Cloud Configuration Rules that apply to that resource type.
3.  Each Rule returns `Passed`, `Unresolved`, or `Ignored`.
4.  Results are recorded:
    1.  On the [Findings > Cloud Configuration Findings ↗](https://app.wiz.io/explorer/cloud-configuration-findings) page.
    2.  (`Unresolved` only) On the [Security Graph ↗](https://app.wiz.io/graph), a Configuration Finding object is linked to both the resource that failed the Rule and the Configuration Rule itself. Use [this query ↗](https://app.wiz.io/graph#~(query~(type~(~'CONFIGURATION_FINDING)~select~true))) to see all Cloud Configuration Findings on the Security Graph (for IaC Configuration Findings—only Terraform is supported).
    3.  (`Unresolved` only) On CSV reports created via the [Reports > My Reports ↗](https://app.wiz.io/reports/my-reports) page (not available for IaC Configuration Findings).
    4.  (`Unresolved` and `Passed` only) On the [Reports > Compliance Posture ↗](https://app.wiz.io/compliance/framework) page, for those Rules that are associated with a compliance framework.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/Qy750Fu.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Data Flow</div>
</div>
<br>

### Edit a built-in Cloud Configuration Rule ✏️ 

You can edit the following built-in Cloud Configuration Rule's metadata: Rule name, description, severity, remediation steps and tags. If you want to edit the Cloud Configuration Rule further, you can create your own Cloud Configuration Rule by duplicating the built-in Rule, editing whatever you want, and then disabling the built-in Cloud Configuration Rule.
To edit a built-in Cloud Configuration Rule
1.  For the Cloud Configuration Rule you want to edit, click  **Edit**.
2.  Edit the relevant metadata.
3.  Click **Save**.

### Disable a Cloud Configuration Rule 🚫 

By default, all built-in Cloud Configuration Rules are enabled and applied to all resources from all Subscriptions, using severities defined by Wiz.

To prevent a Cloud Configuration Rule (whether built-in or custom) from generating Cloud Configuration Findings, click **More Options** > **Disable**. To set the Rule to generate Cloud Configuration Findings, click **More Options** > **Enable**.

### Create a custom Control from a Rule ⚙️ 

By default, Cloud Configuration Rules generate Cloud Configuration Findings associated with specific cloud resources, not Issues. If you would like a Rule to also generate Issues, a custom Control must be created from the Cloud Configuration Rule.

To create a Control from a Rule, use the **Generate Issues** toggle on the Cloud Configuration Rule editor.

## Host Configuration Rules 🖥️

The Host Configuration Scanner uses two different components to validate Host Configuration Rules: the Workload Scanner and the Dynamic Scanner, each using a different type of matcher

The Workload Scanner assesses Host Configuration Rules only on VMs while the Dynamic Scanner assesses Host Configuration Rules on the following compute workloads: virtual machines, container hosts, serverless functions, and serverless containers.

### How it works 🛠️

1.  Wiz detects hosted technologies in your environment by using both the Workload Scanner, which scans the OS disks of all VMs, and the Dynamic Scanner, which performs application fingerprinting on all compute workloads.
2.  The Host Configuration Scanner assesses the detected hosted technologies against Host Configuration Rules, which are based on matchers
3.  The results of the assessment are recorded on the Host Configuration Findings  page. In addition, failed checks generate Host Configuration Findings on the Security Graph.

### Use Cases 🎯 

- Industry, regulatory, or business bestpractice benchmark settings
- Close gaps with custom compliance frameworks developed elsewhere.
- Perform OS-specific configuration checks at scale, such as require password for all local accounts
- Perform application-specific confighuration checks at scale.
- Isolate configuration findings to be ingnored for a subset
- Monitor and detect runtime drift with deployed 3rd-party hardening guidance

### What they check and when ⏱️

They validate static configurations for cloud resources.

The Host Configuration Rules run at that 24-hour scan cycle or during a manual assessment, or even during a triggered assessment if they're configured that way.

Generally speaking, they're going to run every 24 hours unless I go in and manually scan a particular resource.

Similar to any other rule type like we just talked about with the cloud configuration rules, host configuration rules generate findings that appear on the security graph and on the host configuration rules findings page

### Dataflow 🔄 

1.   **API-based scanning** of cloud providers collects information about the environment and associated volumes.
    
2.   **Volume IDs** are passed to the **Workload Scanning Cluster**, where in-depth assessment begins.
    
3.   **Host Configuration Rules** are evaluated against the gathered data from virtual machines, containers, etc.
    
4.   **Findings** are generated and reflected across:

     *   The **Security Graph**
        
       *   The **Host Configuration Findings page**
        
       *   **Wiz Controls** (which can escalate findings to **issues** based on toxic combinations of risk factors

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/nbIRxOw.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Dataflow</div>
</div>
<br>

### Host Configuration Pages 📄 

To **view Host Configuration Findings**:
*   Go to the Wiz UI
    
*   Navigate to **Findings > Host Configuration Findings**
    
*   Use filters to isolate specific types of findings or resources
    
To **view or edit Host Configuration Rules**:
*   Navigate to **Policies > Host Configuration Rules**
    
*   Options available:
    *   **Create new rules** from scratch
        
    *   **Duplicate and modify** existing rules to meet specific use cases

## Issues ⚠️ 

Also known as Toxic Combinations in Wiz
The Issues page presents the risks and threats that Wiz has identified in your cloud environment, as defined by Policies. By default, Issues are generated by Controls or critical/high severity Threat Detection Rules.

### How Wiz Analyzes Data 🖥️

Wiz conducts an in-depth inspection of your cloud environment by analyzing scan results and compiling all the relevant settings, controls, and relationships. This comprehensive approach includes evaluating identities, network exposure, lateral movement, and secrets using its Cloud Risk Engine. 

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/bMnjGvN.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">How Wiz Analyzes Data</div>
</div>
<br>

Wiz also incorporates traditional scanning methods for detecting vulnerabilities, malware, and misconfigurations, while leveraging cutting-edge research from its Threat Research Center to identify novel cloud vulnerabilities and attacks. management, and vulnerabilities.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/JIoi9U8.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Scanning Check Process</div>
</div>
<br>


With this holistic understanding, Wiz performs checks against key risk categories, including external exposure, cloud entitlements, secure configuration, secrets, vulnerabilities and Malware.

### Overview  🧠

Accessing a vulnerability's risk isn't straightforward without understanding its broader context. For example, a vulnerability on a virtual machine or VM requires more than just detection. 

It depends on the workload context, like whether the VM is exposed to the Internet, it has permissions to sensitive data, or maybe it's running in production. A VM with these risk factors is far more critical than a development VM with no Internet exposure.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/jMdSdIw.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Issue Proccess Creation</div>
</div>
<br>

Wiz identifies and correlates the toxic combination of issues that represent real risks so teams can prioritize their most critical risks accurately, reducing noisy alerts and time spent on manual efforts.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/ox5NOjn.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Example of Correlation of findings</div>
</div>
<br>

By correlating multiple factors such as vulnerabilities, exposure, and permissions, Wiz pinpoints toxic combinations that present real threats. This reduces noisy alerts and minimizes time spent on manual efforts.

### How are Issues generated? 🖥️

By default, Issues are generated by:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/fEPdsbK.png "
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Wiz issue creation flow</div>
</div>
<br>

- Controls: Combine a Security Graph query defining a risk with a Severity
- Threat Detection Rules: Detect potential threats in an environment, are assessed in near real-time, and are based on Cloud Events and the Runtime Sensor.
- Cloud Configuration Rules: Can also be set to generate Issues

### Investigating Issues

From the Issues page, you can investigate and manage issues, configure automations and responses. Issues inherit the compliance framework set at the controls or threat detection rules. They also inherit their project association from the primary resource

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/j6N4Px6.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Issue Details</div>
</div>
<br>

Meaning, if there's an issue that's created on a resource and assigned to projects A and B, then Wiz will also associate that issue with both projects. Alternatively, you can scope a control or threat detection rule to certain projects to reduce noise and false positives.

### Resolving and ignoring issues

Only issues generated by Threat Detection Rules can be manually resolved. All other types of issues are automatically resolved by Wiz. If a later scan indicates, their risks have been remediated. 

The one thing you can do, though, is to set an issue to be ignored.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/a5aUqzh.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Ignore a Issue</div>
</div>
<br>


To do that, you would open the Details drawer for an issue associated with a specific resource. In this Details drawer, you're going to go to Status, and then Ignore. 

In the Resolve Issue dialog, you're going to select a reason, you're going to provide a comment, and you're going to click Ignore Issue. To better monitor why issues were ignored, you should require a note when they are going to be ignored.

## Findings 🧨

Also known as the components of an issue
The Findings pages list all the findings Wiz has detected in your environment according to the respective Wiz rules that generated them.

| Type of finding | Description |
| --- | --- |
| [Vulnerability Findings](https://docs.wiz.io/docs/vulnerability-findings) | A instance of a vulnerability detected on a specific resource. Contains info specific to the properties of the resource |
| [Cloud Configuration Findings](https://docs.wiz.io/docs/cloud-configuration-findings) | The result of a failed Cloud Configuration Rule that monitors resources in the cloud environment to ensure adherence to the organization guidelines|
| [Host Configuration Findings](https://docs.wiz.io/docs/host-configuration-findings) | The result of a failed Host COnfiguration Rule that monitors virtual machines, hosted apps and operating systems to ensure adherence to organization guidelines|
| [Data Findings](https://docs.wiz.io/docs/data-findings) | A Wiz abstraction that represents a Sensitive data detection. Based on a Data Classification RUle. Result of disk scan + data analysis engine |
| [Secret Findings](https://docs.wiz.io/docs/secret-findings) | A Wiz abstraction that represents a specfici secret identified on a specific resource. The same secret can be identified multiple times on the same resource and on several resources, generating a new Secret Instance each time. Result of disk scan + secret analysis engine |
| [Network Exposure](https://docs.wiz.io/docs/network-exposure) | Review your exposed resources, where they're accessible from, the exposure path, and more. |
| [External Attack Surface](https://docs.wiz.io/docs/external-attack-surface) | Review scan results of the Dynamic Scanner regarding Application Endpoints detected by the network analyzer. |
| [Code & Build Scans](https://docs.wiz.io/docs/cicd-code-scans) | Review all VCS and Wiz CLI scans performed in your environment, whether of code or in the CI/CD pipeline. |
| [Kubernetes Admission Reviews](https://docs.wiz.io/docs/kubernetes-admission-reviews) | Review all Wiz Admission Controller Reviews performed in your environment. |

### Managing findings ❗

Just like with issues, findings cannot be manually marked as resolved. Only Wiz can do that once it's been remediated and passed evaluation.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/nL2FzvK.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">How to Ignore a Finding</div>
</div>
<br>

 If you want the finding to be silenced or hidden, you can set it to ignore, but you have to include a reason why it's being ignored

You can also set a rule to be ignored.

### Ignore rules 🚫

Ignore Rules allow you to define conditions to automatically ignore or modify Findings in different lifecycles (build, deploy, and runtime).

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/Fnp9QB3.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Ignore Rules List</div>
</div>
<br>


 Use them to exclude or manage Findings at scale and reduce noise by ignoring or modifying known or expected security risks.

- Filter for Unresolved Findings

## Options for Detection rules improvements / fine-tuning 🔍

Once you understand how **policies**, **rules**, **findings**, **controls**, and **issues** work together in Wiz, the next step is learning how to **tune policies** to reflect your organization’s security strategy and reduce noise from irrelevant alerts.

### Why tune a Policy? 🔮

Policy tuning allows you to tailor security evaluations to your environment. This may be necessary for several reasons:
*   **Ignoring false positives** (e.g., a known safe configuration that is flagged incorrectly).
    
*   **Delaying alerts** for findings with no current remediation (e.g., missing patches that are not yet available).
    
*   **Managing accepted risks** (e.g., risks that are documented, approved, and monitored, such as known deviations for specific resources).
    

> **Important:** Ignoring issues should be the exception, not the rule. Ignored issues should be regularly reviewed to ensure that the risk is still acceptable and remediation is still unavailable or unnecessary, and always provide thorough justification.

### How to Manage Ignored Issues and Findings 🛰️

*   Go to the **Issues page** in Wiz and use the **Status filter** to show issues marked as _Ignored_.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/W7JtCNU.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Issue marked as Ignored</div>
</div>
<br>


*   Similarly, individual **findings** (e.g., cloud configuration findings or host configuration findings) can also be ignored through their detail page.
    
*   It is best practice to establish a **review cadence** to revisit ignored items and reassess their validity.



### **Malware Exclusion Rules** 🔔

Wiz generates a **hash for every file** on each disk to detect malware. However, in certain use cases, such as Honeypots or testing environments, malware detection might not be relevant.

#### Malware exclusion rules 🦠
Allows you to suppress alerts for specific files:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/cKjegMu.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Malware Exclusion Rules</div>
</div>
<br>

*   Target specific resources using filters such as:
    *   Directory path
        
    *   File name or extension
        
    *   Resource name
        
    *   Project or subscription
        
    *   Resource tag
        
Example:  
If a **Honeypot** VM contains intentional malware to attract attackers, you might set an exclusion rule to ignore a file path on that specific instance.

#### Custom file detection 🧾

You can also upload hashes of files (e.g., sensitive documents or intellectual property) and be notified whenever those files are detected in your environment—useful for **data leakage detection**.
<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/3GltoGW.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Custom file Detection</div>
</div>
<br>


### Tuning Dynamic Scanner Policies 🔍

Tuning can also apply to the **Dynamic Scanner**, which evaluates application endpoints and exposure levels.


#### Exposure Levels 🌐

In some use cases, you might not want issues triggered for known at-risk resources like Honeypots. 

You might want to treat exposed resources with authentication enabled as a non-critical exposure. So as long as there's some kind of authentication enabled on there, you're OK with that.

You might want to treat forbidden status codes as non-critical exposure too. 

But you might also want to focus on critical exposures in your environment. One of the ways we can do this is the application endpoint exposure level policy

Wiz categorizes exposure levels to help prioritize issues:
*   **Passive policy**: Generates low-exposure issues.
    
*   **Moderate policy** (default): Triggers medium-exposure issues.
    
*   **Strict policy**: Flags critical exposures.
    
You can tune exposure level policies based on your context:
*   Treat **known-at-risk resources** like Honeypots as _low exposure_ to avoid noise.
    
*   Consider **authenticated but publicly exposed endpoints** as _non-critical_ if that exposure is intentional.
    
*   Downgrade **HTTP 403/Forbidden status** alerts if they do not represent real risk.
    
> These exposure levels are used across various **controls** in Wiz, meaning tuning them can significantly reduce or raise the number of triggered issues in your environment.

### Ignore Rules in Wiz 🤫

**Ignore rules** are a key part of policy tuning in Wiz, allowing security teams to suppress findings or issues that are either false positives or acceptable risks under specific conditions. These rules help focus attention on the most critical security risks while temporarily setting aside those that do not require immediate remediation.

#### When to Use Ignore Rules 🚫

Ignore rules should be used **tactically**, not broadly. Their goal is to fine-tune visibility—not to silence legitimate issues indefinitely. Some appropriate scenarios for using ignore rules include:
*   **No available fix**: A known vulnerability has been identified, but a patch or remediation is not yet released.
    
*   **Vendor-required configuration**: A configuration flagged as a misconfiguration is required due to a third-party dependency (e.g., legacy system requirements).
    
*   **Business-accepted risk**: A non-critical misconfiguration is a known and accepted tradeoff in the current architecture.
    

#### How to Create Ignore Rules 🛠️

Creating an ignore rule in Wiz is similar to creating any other rule. When defining a new ignore rule, you can scope it with various filters and criteria to ensure precision:

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/xtAr9a3.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Ignore Rule Creation </div>
</div>
<br>


*   **Project scope**: Apply the rule to a specific project.
    
*   **Rule type**: Target a particular type of rule (e.g., cloud config, host config, exposure).
    
*   **Severity level**: Limit the rule to findings of a specific severity.
    
*   **Rule lifecycle state**: Filter by rule status (active, deprecated, etc.).
    
*   **Finding type**: Choose what kind of finding (vulnerability, exposure, configuration).
    
*   **Targeted resources**: Use tags, names, or IDs to apply the rule to specific assets.
    
<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/CvE3zK0.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Ignore Rule Creation 2</div>
</div>
<br>

* * *

### **Best Practices for Using Ignore Rules** 🎯

To ensure ignore rules are effective and not abused:
1.  **Be surgical, not broad**  
    Avoid blanket suppressions. Use precise filters to apply the rule only to the relevant findings.
    
2.  **Set expiration dates**  
    Every ignore rule should have an expiration to enforce regular review. Risks evolve—what was acceptable last quarter may not be today.
    
3.  **Review regularly**  
    Establish a **review cadence** (monthly, quarterly) to revisit all ignored issues and rules. Evaluate:
    *   Has a fix become available?
        
    *   Is the risk still acceptable?
        
    *   Has the environment changed (e.g., asset decommissioned)?
        
4.  **Document the rationale**  
    Always provide a reason when ignoring a finding or issue. This creates an audit trail and helps others understand the context for the decision.