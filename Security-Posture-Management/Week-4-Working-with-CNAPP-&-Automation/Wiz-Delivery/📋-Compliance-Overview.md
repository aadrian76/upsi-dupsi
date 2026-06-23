<details open>
  <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
    Table of Contents 📑
  </summary>

  [[_TOC_]]
</details>

## 📝 Changelog 🗓️  
> Up-to-date like patch notes after a season reset.

| Author | Modification Date | Changes |
|-----------------------------------|-------------------------|-----------------------------------------------|
|                 | 25/02/2025 | First Version Created |

# 📋 Compliance Overview  
> “With great power comes great paperwork.” —Every GRC team, ever.

Organizations aspire to achieve regulatory compliance to ensure they're aware of and have taken steps to comply with relevant laws, policies, and regulations.

In the cloud it means configuring resources, services and data to meet industry standards and regulations, continuously monitored through assessments. These assessments support governance, risk, and compliance efforts, but do not always equate to security alone.

Organizations like NIST, ISO, GDPR, CIS and so on play a crucial role in helping organizations identify and rectify potential compliance issues, avoiding legal and financial consequences associated with non-compliance.

In the cloud, compliance refers to best-practice configurations of cloud resources, services and data with continuous monitoring and ongoing assessment to ensure that an organization's cloud configurations comply with the relevant industry standards, regulatory requirements and internal policies.

It's a snapshot-in-time assessment as the configuration relates to those compliance guidelines. In the cloud, an assessment does not always equate to security, but it does attest to the diligence and attention to detail on the part of the complying organization by providing proper artifacts of regular assessment activities for use in audits and regulatory review.

<div style="text-align: center; width: 900px; margin: auto;">
  <img src="https://imgur.com/l6mscyN.png"
       style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
       alt="image caption">
  <div style="color: gray; font-size: small; font-style: italic;">Compliance Posture</div>
</div>

Wiz maps control lists and recommendations from each set of supported Compliance Frameworks to built-in Controls, Cloud Configuration Rules and Host Configuration Rules in Wiz. Whenever possible, requirements of every framework are mapped to categories and sub-categories.

Wiz-unique frameworks go beyond regulatory compliance, focusing on cloud threat prevention, detection and response. By assessing risk in context, Wiz helps organizations manage cloud security, reduce risks and be prepared for potential attacks.

From the Single Framework page you can drill down on any framework to see what's happening. The category, the rule, the number of passed checks, the overall compliance percentage—everything is available at a glance. You can also filter to see a project- or subscription-level view or a specific environment.

The checks are aligned to the compliance-framework guideline numbers, so you can quickly see what policies are defined to address each assessment.

Each framework has a unique name; the framework is divided into higher-level categories that consist of one or more guidelines, and within a guideline you can see the policies linked to it (controls, host configuration rules, etc.). Guidelines are the requirements that we're assessing.

### 📑 Guidelines  
> Benchmark rules are the “boss fights”; non-restrictive ones are the side quests.

It's possible to have two types of guidelines:

* **Benchmark guidelines** – Specific, prescriptive criteria serving as a standard for measuring and evaluating security configuration.  
  * Wiz implements identical policies to cover the requirement.  
  * Manual recommendations may not be covered.

* **Non-restrictive guidelines** – More flexible, providing general principles or recommendations without exact settings.  
  * Wiz interprets the rules and assigns existing policies.  
  * Covers only technical requirements; on-prem/HR/physical rules are not included.

Wiz supports both but only evaluates what it can technically verify. Blank categories remind you of areas outside Wiz’s scope.

## 🛠️ Compliance framework evaluation  
> Scoreboards aren’t just for gamers—GRC lives by them.

Each rule is assessed for each matching resource, and the total pass/fail dictates the compliance posture.

<div style="text-align: center; width: 900px; margin: auto;">
  <img src="https://imgur.com/ROFlgTs.png"
       style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
       alt="image caption">
  <div style="color: gray; font-size: small; font-style: italic;">Compliance Posture Framework Evaluation</div>
</div>

Let's unravel the four different scores you see and how they relate:

Let's look at the compliance scoring in a little bit more detail.

For each framework, we're going to unravel the four different scores that we see here and understand how they relate. We're starting at the top and moving clockwise.

Let's start with the past checks. This score looks at each subcategory to see whether every resource for every guideline and policy has passed. In this example, we see seven out of 28 categories have fully passed with no failures on any resource.

The compliance posture, it's much more granular. It's looking at each policy and each resource as a possible check. This score sums up all the past checks and divides the sum by the total number of checks both passed and failed. It's presented as a percentage.

Now, if we look, for example, at protecting stored cardholder data as an example, we see the compliance posture there is 29%, but the number of past checks is zero out of two.

This formula is used for the category, the guideline, and the policy scores as well. Now, dropping down to one of the guidelines, in this case, 3.4.1, we can see that 5% of the possible tests by resource in this guideline have passed. Overall, though, the score is failed. This is because all of the policies must pass before the guideline is marked as passed. And lastly, looking at an individual policy, we see that out of 16 resources checked, seven have passed the check. That equates to 43% and an overall failure on the policy. And those are the numbers behind the compliance score for a single framework.

You can also click into any of the passed or failed checks to see the resources behind the numbers, and then you can start to remediate specific findings. It's pretty easy to find, understand, and take action.

### 🔥 Compliance heatmap  
> Instant overview—like the minimap in an FPS showing red dots for danger.

* Quickly spot gaps across frameworks, projects, subscriptions.  
* Sort by High/Medium/Low business-impact projects.

<div style="text-align: center; width: 900px; margin: auto;">
  <img src="https://imgur.com/4a7h1sS.png"
       style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
       alt="image caption">
  <div style="color: gray; font-size: small; font-style: italic;">Compliance HeatMap</div>
</div>

### 📤 Compliance reporting  
> Give auditors the receipts before they even ask.

One of the most critical teams in any organization is the Governance and Regulatory Compliance Team, or the GRC.

Wiz can help your teams in such efforts. Using role-based access controls and projects, you can ensure these teams have the access to the reports and compliance frameworks that they need to review the status.

They can define scheduled reports to send artifacts, or confirm linkages to long-term events, or ensuring that during an audit, they can produce the requisite artifacts to maintain the strictest compliance.

> Role-based access and projects ensure GRC teams see exactly what they need. 
Schedule reports to buckets or email so evidence is always ready for an audit boss fight.

### 🔧 Toggle compliance frameworks  

From the Reports > Compliance Framework page:
*   Enable frameworks
*   Disable frameworks
*   Duplicate framework
*   Define custom frameworks

GRC teams are legally required to resolve compliance issues within a few days of being made aware of them. So automated tools, while being super helpful, can also be very stressful for a GRC team because they're creating a lot of legally obligated work and perhaps more than the team is staffed to address within the legal time frame.

Wiz can help there too. By default, only some of the frameworks are enabled. When we talk about all frameworks, that includes frameworks that assess host and application configuration settings such as the CIS Windows and Linux benchmarks. So what's the value? Well, it means that you can enable only the frameworks that matter to your business. And what's more, you can define custom frameworks to extend or combine just the guidelines and policies that you need. Start with a built-in framework and duplicate it. Disable the original and customize that copy.

> Only equip the gear your party actually needs.

From **Reports › Compliance Frameworks** you can enable/disable frameworks, duplicate them, or create customs tailored to your org.

### 🐢 Toggle guidelines to slow-roll a framework  

Another feature is the ability to slowly roll out a new framework: you can turn on a new or custom framework with all of the policy checks disabled for that framework. It'll take a while to turn them all off, but then you can start turning them on very slowly, one at a time, maybe taking minutes, hours, or days to enable them.

On the Singe Framework page:

*   Enable guidelines
*   Disable guidelines
*   Re-run assessment

It's also possible to see open tickets, findings the graph or define automation rules for any policy

> Turn on checks one at a time—no sudden “difficulty spike” for the team.


