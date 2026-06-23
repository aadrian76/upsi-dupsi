
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
|                 | 05/03/2025              | Wiz Modules Added                             |


<br>

---



## Boards 📊


### Overview 🗺️ 

Boards provide an intuitive, visual summary of issues detected in your environment to make it easier to monitor risk, track progress, and prioritize issues by risk domain. 

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/DBnQgOv.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Overview Board</div>
</div>
<br>


They present risk domain and operational domain-specific views of your environment. They align two areas of responsibility or knowledge, and they focus on a unified security outcome, proactively preventing common attacker playbooks from being successful in your cloud estate. 

They provide KPIs, trends, and focused views of issues to get you started working on what offers to be the best security outcome for the effort. They can be customized to align your teams using resource-level views called projects, or role-focused by creating custom boards and viewing permissions.

#### View a custom or built-in board 👀  

The Overview board includes mini-summaries of each risk domain dashboard (Log4Shell Vulnerability, External Exposure, Cloud Entitlements, etc.).
To view a custom board or the full built-in board for a risk domain, click its name in the Boards hover-over menu.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Findex-6cb2251-image.png&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Board Selection</div>
</div>
<br>



From a specific board you can perform actions including print, duplicate, set as default, and view in TV mode.

Also we've got boards managed by Wiz, which is the built-in dashboards that are accessible to everyone who logs in. But these are at a risk and an operational domain specificity. 

Wiz also has private boards. Now these ones are user-defined. So each user of Wiz who has permissions to create boards can define custom views.

Wiz also got shared boards and those are the custom boards essentially that have been created by other users in the organization and that have been shared. Now maybe they're shared at the project or the global or the organizational level.

### Create Custom Boards ✨ 

Anybody who has the right permissions can create a private dashboard. No one else can see it, but once you've got it where you want it, then you can change the permissions and share that with a larger audience.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/MaMR8YG.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Visibility selection when creating a Dashboard</div>
</div>
<br>

1. On the boards page: Click + Create Dashboard
2. Give it a name
3. Select who can view it.

   Now, when controlling access to boards, there's two types of filtering techniques. One, you can do it through who can access it, and two, you can define which resources are visible to the viewer

| Visibility | Read | Edit & delete |
| --- | --- | --- |
| **Private** | The user who created it, except for Documentation Reader, Connector Reader, Connector Admin, Settings Admin, and Global Graph Reader roles | The user who created it |
| **Project** | Project-scoped user roles with access to the selected Project(s) | Project Admin role with access to the selected Project(s) |
| **Global users** | Users with global roles, except for Global Graph Reader role | Global Admin and Global Contributor roles |
| **Organization** | All users, except for Documentation Reader, Connector Reader, Connector Admin, Settings Admin, and Global Graph Reader roles | Global Admin and Global Contributor roles |

> Scoping board visibility to a Project does not affect the content displayed in the board widgets. To scope the information displayed in the widgets, use the Project filter in the top bar of the portal or scope the widgets to specific Project when creating them.

4. Click Create.
5. Add dashboards widgets. You have two options:
   - Copy an existing widget
   - Create a new widget 
6. Organize the widgets on your dashboard.

#### Widget Types 🧩

Widget unique properties:
- Custom name or widget title
- Visualization scheme or widget type

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/HNayvlV.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Examples of Widget Types</div>
</div>
<br>

The following widget types exist:
- Wiz Defined: Found on pre-defined boards. Can be added as is but not re-scoped
- Lists: A tabular list view. Multiple varieties exists. Resizable
- Metrics: Count of one or more values within a scope. Scope with filters and graph queries
- Speedometer chart: A speedometer chart view of compliance scores and SLAs
- Trend Chart: Line graph view for comparisons. Multiple varieties exists. Resizable and supports the Time Range filter.

### Terms and Definitions 📖

| **Term** | **Definition** |
| --- | --- |
| Risk domain | An area of cloud security focused on identifying, analyzing, and mitigating finding types that impact objectives of that domain. |
| Widget | An applet that plugs into a dashboard and presents a defined view into data. |
| Risk assessment | Evaluate and analyze potential risks to assess likelihood and impact to an environment. |
| Alert | An audit event or assessment result that is noteworthy. It does not have context. |
| Finding | A weakness or comprisable aspect of a cloud resource determined by an assessment. |
| Toxic combination | An issue that combines findings from multiple security domains to define risk profile. |
| Attack blueprint | A strategy playbook for an attack that can be described abstractly. |
| Rule / Control | A programmatic expression (query) that codifies an attack blueprint.  |
| Issue | A resulting match of a resource to a control. With rare exception, it is a toxic combination.  |
| Project​ | A Wiz-unique way of filtering issues and dashboards to a specific set of cloud resources.​ |
| Threat Center | The latest threat research contextualized so you can assess the impact to your cloud. |

### Use Cases 🎯

In Wiz, dashboards address the following customer use cases:
*   Focus all available resources/teams to a single, unified security outcome
    *   **Democratize security**.  Empower disparate teams around a unified security outcome.
    *   **Accelerate Business.** Focused work on achievable, understandable outcomes that align to disciplined skills sets.

*   Consolidate siloed tools into a single pane of glass and focused security posture
    *   **Bring siloed views together**.  Leverage context from one risk domain across others automatically.
    *   **Increase operational efficiency**. Same tool for multiple teams with actionable views only.
    *   **Where to focus first**.  Each day presents unknown challenges from day 0 exploits, new vulnerabilities, patches, etc. The Wiz dashboards roll up the issues where fixes have the biggest impact on security.  

*   Meet your team where they are and save time achieving better outcomes.
    *   **Close knowledge gaps in role**. No need to change what you know well or how you work.
    *   **Meet your team where they are**.  Domain-specific views get your teams right to work without requiring new knowledge or skills. Leverage their skills and knowledge to resolve findings now.

## Threat Center 🛡️

### Wiz Cloud Threat Research Team 🧑‍🔬

- Vulnerability & Threat Research

  - Prioritize risks & vulnerabilities
  -  Discover cloud threats
     - PyLoose
     - BingBang
     - Log4Shell
     - ChaosDB
     - OMIGod

- Data & Security Research
  - Response to emerging threats
  - State of the Cloud
  - PEACH Framework
  - Share Expertise
     - Crying Out Cloud
     - Blog Series
 
- Product Contributions
  - Threat Center
  - Malware
  - Vulnerability
  - Controls (New & improve)
  - Forensics 
  - Threat Detections and responses (Sensor)


### Overview 🌐

The Threat Intel Center, it's a unique Wiz-created and maintained dashboard, it shows the most important emerging threats in the Cloud Threat Landscape to which you need to pay attention and what action you should take - first detect and eliminate Threats, then mitigate Issues and review related Findings. 

Emerging threats are collected by the Wiz Threat Research team from a variety of sources, including CISA, CERT-EU, and internal research.

> *   Not every vulnerability or emerging threat merits an entry in the Threat Intel Center. Wiz researchers try to focus on critical, exploited-in-the-wild vulnerabilities, critical RCEs in prevalent technologies, novel cloud risks, and ongoing cloud attacks. More rarely, they add something less severe if it is receiving significant media coverage and generating a lot of questions.
> *   Not every risk covered by a Threat Intel Center advisory justifies a dedicated Control. Wiz only adds Controls for high-profile vulnerabilities or misconfigurations that have special exploitation requirements, such as certain open ports or configurations. Use the Vulnerability Findings page to check for findings with related Issues generated by built-in Controls.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/NR8dqmR.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Threat Intel Center</div>
</div>
<br>

For every listing in the [Threat Intel Center ↗](https://app.wiz.io/#~(dashboard~'threat-center)), you can:
*   Discover if Issues or Findings, related to the emerging threat, were found in your environment. This is indicated by clickable icons with a number, such as  , . Click on the icon to go to the relevant page and mitigate the risk.  
    You can also see in what type of resource the findings were found (indicated by a colored icon):  code (such as GitHub repository),  deploy (such as Docker Hub repository), or  cloud resources.

| Scenario | <br><br>Display<br><br> |
| --- | --- |
| Issues or Finding were found in your environment |  **4 Issues** |
| Wiz has relevant  Threat detection Rules or  Controls for this threat, but none were matched in your environment | <br><br> **No Issues**<br><br> |
| Wiz does not have relevant Threat detection Rules or  Controls for this threat | <br> <br> |

*   Click the name of the advisory to open the full Wiz advisory for an emerging threat. The advisory contains additional details about the threat and recommendations for detecting and minimizing risk against it.
*   Perform additional actions

### Threat Actors 🎭

The [Threat Actors ↗](https://app.wiz.io/boards/threat-actors) page provides profiles of threat actors involved in cloud security incidents, analyzed by the Wiz Threat Research team, to help with risk assessment and threat modeling. 

For every threat actor, various details are provided, such as: target industries, typically used MITRE tactic, and more, as well as information on how they affect, or can affect, your environment.

Access the Threat Actors page from the top right corner of the Threat Intel Center.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Factors-d23c889c.jpg&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Threat Actor Board</div>
</div>
<br>


### Additional Actions ⚙️

*   Search for advisories using the top search bar.
*   Click **Create Automation** to trigger an Action when Wiz detects a new high-profile Issue.
*   Click **Subscribe to Threat Center updates** to receive an email notification when the Wiz Threat Research Team posts a new threat advisory. Alternatively, you can query the Threat Center API using the following request:

#### Action and Automations rules 🔄

| <br><br>Component<br><br> | Description | Example(s) |
| --- | --- | --- |
|  **Action** | The information sent from Wiz to the third-party tool using the Integration. | <br>*   A JSON describing a new Issue<br>*   Custom headers and request body for a webhook<br> |
|  **Automation Rule** | A set of conditions (WHEN, IF, THEN) linking a change in the state of a source, like an Issue or Cloud Event, with an Integration and an Action. | WHEN an Issue is created, IF it is Critical severity, THEN send a Slack message to the #cloud-sec channel |

### Use Cases 🚀

In Wiz, the threat center address the following customer use cases:
*   Assessing whether a headline threat could affect the cloud or not  
    *   **Stay informed of emerging cloud threats**. What is it? No need to change what you know or how you work. Wiz Threat Research breaks down each threat, its IOCs, criticality, mode of operation, and guidance for remediation and/or prevention.
    *   **Where to focus first.**  Each day, Wiz Threat Research team assesses the array of new threats (headline, novel, and emerging) to prioritize what matters to cloud so you don't have to.

*   Answering the simplest question: “Are we affected by this new cloud threat?”   
    *   **Accelerate security response**. Rapidly assess the impact to your cloud environment for emerging, headline, and novel cloud threats. 
    *   **Increase operational efficiency**. Quickly respond to management or board status request regarding new threats as it pertains to your entire cloud estate without leaving the portal.

