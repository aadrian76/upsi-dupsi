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
 
# 🔐 Wiz Access, Authentication, and Projects

## Wiz Projects 🗂️

Projects in Wiz are subdivisions of your cloud estate that allow for the organization and management of resources. When combined with role-based access control, Projects enable you to grant users access to only the resources and associated Issues for which they are responsible, and to limit the actions users can perform.

- **Logical Division**: Logically divide the cloud estate to support effective outcomes
- **Democratize Security**: Projects allows to democratize security in a focused and management way
- **Avoid Alert Fatigue**: Avoid Alert fatigue on resources that users don't manage and cannot resolve
- **Focus on What's Important**: Allows teams to focus on the task of improving the security of their environment which they understand and control. Projects provide actionable issues and findings within the context of evidence and impact of their environment

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://i.imgur.com/csiAj1j.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Different Project Organization Examples:</div>
</div>
<br>


Projects allows to group the cloud resources according to the needs or purposes. 
For example, you can divide by organizational units, you can create a project per OU or by purpose. 

Let's imagine you have an application, you might have a project for all the development environment of the application, and another project for all the testing environments, and maybe, other for production. This way you are breaking down tour resources, your alerts, and so on, by project. 

Another way to do it is by business units. Maybe, you'll have an HR project with all the HR applications, a sales projects, a Global HQ project, and so on. There are many ways to logically divide with projects

### Project Folders 🗄️

A Project Folder is a collection of Projects. Users who are granted access to a Project Folder inherit access to all of its child Projects, and therefore access to all of their cloud resources, Issues, etc.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/mSnus6f.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Project Hierarchical Structure</div>
</div>
<br>

Project Folders let you build hierarchical structures of Projects that mirror cloud resource ownership. For example, if a Project is created for each dev team, they can be grouped into Project Folders by department. Project Folders simplify setting up and maintaining role-based access control. For example, if the department heads are Project Admins for their respective Project Folders, they inherit access to the Projects of their development teams.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Fhow-projects-work-80918e399058fce2578bfbd596c58384eae14c4445eba2f6f3a6bc8001a7b461-project-folders.png&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Project Hierarchical Structure</div>
</div>
<br>


Custom Graph Controls created at the Project Folder level are visible to all child Projects. This allows admins to maintain risk definitions across multiple Projects. However, the Issues generated from these controls are still only visible to users that have access to the relevant Project.

A Project can be:
*   Moved to a Project Folder.
*   Moved from one Project Folder to another.
*   Removed from its parent Project Folder entirely.

### Project Resource Scoping: 🎛️

Projects not only allow you to logically configure your environment, but also gives access to the right people at the right time.

<div style="text-align: center; width: 50vw; margin: auto;">
    <img src="https://imgur.com/ZesgmyB.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Project Scopes</div>
</div>
<br>


When you create a project, you may choose to scope an entire subscription. This subscriptions is a normalized term for an AWS account, an Azure Subscription, or a GCP folder. you can scope entire cloud organizations, container registries or clusters. Any of these resources can be scoped to a project. 

We can also apply filters, For example, you might want to add clusters with a specific cloud tag. You can tag it in your cloud provider and then add this as a filter in the project. You can also filter by resource groups, namespaces and labels, tailoring the resources scoping to your needs and showing users only what matters to them.

### Projects Details 📌

1. Only Projects can be associated with cloud resources via cloud organizations, subscriptions, Kubernetes cluster, etc.
2. Only Project Folders can contain Projects; Projects cannot contain other Projects
3. A Project Folder can contain up to 5000 child Projects. Each Project can have at most one parent Project Folder
4. Projects can be archived, or deleted if there are no resources associaed with them.
5. The Project Folder/Project hierachy is currently limited to 5 levels of depth.
6. Project and Project Folder names must be unique

### Project Management 🛠️

#### Focus on a Project: 🎯

By default, Wiz displays information from all Projects to which you have access.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Fprojects-streaks-b9a7369-focus_project.png&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">How to Focus on a Project on Wiz Portal</div>
</div>
<br>

To focus on a Project:
*   From the  [Settings > Projects ↗](https://app.wiz.io/projects) page, click a Project name. The Overview board loads with the selected Project in focus, or
*   At the top left of any page, click **All Projects** then select a Project.

#### View child Projects 👁️

By default, the Projects page displays only Project Folders and Projects that do not have a parent Project, i.e. top-level Projects.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Fprojects-streaks-e502e71-project_folders.png&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">The Projects page, with the expand folder and view folder buttons called out</div>
</div>
<br>

To view the child Projects of a Project Folder:
*   To the left of the Project Folder's name, click .
*   On the right, click **View folder**.

#### Add a Project ➕

Before adding a Project, you need to configure Connectors for the cloud resources that will be associated with the new Project

1.  At the top left, verify that your Project scope is set to **All Projects**.
2.  On the  [Settings > Projects ↗](https://app.wiz.io/projects) page:
    *   At the top right, click **Add Project**, or
    *   On an existing Project Folder, click **More Options**, then click **Create a child project** or **create a child folder**.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://i.imgur.com/Ppp4y6q.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Project Creation Details</div>
</div>
<br>

3.  On the Project Details page:
    1.  Enter a short, unique, and meaningful **Project Name** to display in Wiz.
    2.  (Optional) Enter a longer **Description**. This text is shown when you hover over the Project's name.
    3.  (Optional) If the new Project will be a child of a Project Folder, click **Select a Parent Folder**, select an existing Project Folder, then click **Select**.
    4.  (Optional) Select **Make this project a folder**. Project Folders cannot directly contain cloud resources, only child Projects.
    5.  (Optional) Select or Create a **Project Category** to help define your project's purpose. Select a predetermined category or click **Custom** to create a new category. You can add up to 10 categories to a Project.
    6.  Review your **Project URL Slug** and modify it if necessary
    7.  (Optional) Enter a **Business Unit** to help track the Project.
    8.  (Optional) Add **Tags** to your projects to help organize/identify them based on your organizational standards. Tags are case sensitive, but tag search functionality is not. [Learn more](https://docs.wiz.io/docs/how-projects-work#tag-case-sensitivity).
    9.  Click **Continue**.
4.  If the new Project will contain cloud resources (Project Folders cannot contain cloud resources), on the Resources page:
    1.  Click **Resource Scopes** > **Add** > **Select Method**, then select a cloud resource type:
    2.  Select an **Environment** type.
    3.  Click **Continue**.
5.  On the Project Team page:
    1.  (Optional) Select existing Wiz users to be **Project Owners** and/or **Security Champions**. [Learn about roles in Wiz](https://docs.wiz.io/docs/role-based-access-control).
    2.  Click **Continue**.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/BP6DRjo.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Project Business Risks Specification</div>
</div>
<br>


6.  On the Project Risk Profile page, answer a few questions about the risks the new Project's resources might pose to your organization:
    1.  Select whether the Project is **customer facing** or **regulated**.
    2.  Select a **business impact**:
        *   High business impact—Production environments
        *   Medium business impact—Staging and dev environments
        *   Low business impact—Sandboxes and training environments
    3.  Select whether the Project has **authentication**, is **Internet facing**, **exposes an API**, or **stores data**.
7.  Click **Finish**.
Resources are associated with their Projects as they are scanned.

## Access Management 🔑

### Overview 📜

There are two ways a user can work with Wiz. 

They can either log into the portal and perform actions based on their scope and permissions, or they can use service accounts to programmatically work with Wiz through API calls or third-party integrations. Now, regarding users, there's two types. 

- Local user: They're created in Wi< and can log into the portal and perform tasks within their own permissions.
- SSO or single sign-on user: They're going to be integrated with that third-party identity provider, or IDP, that's going to allow you to use your current infrastructure to access Wiz. 

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/oN5saa1.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Diagram of Access to Wiz</div>
</div>
<br>


Both users and service accounts, they're going to operate through role-based access control, or RBAC. 

On the user side, there are predefined roles like global admin, global contributor, project admin, connector admin, and so on, which come out of the box. 

Administrators can assign these roles to users, both local and SSO, and can create some custom roles for specific needs. 

Service accounts have predefined access roles for tasks like sensor deployment, Wiz broker, and connectors. But custom roles can also be created for specific requirements.

### Wiz Users 👥

#### Local Users 🧑‍💻

Local users are managed in Wiz by using the third-party IDP of Amazon Cognito on the backend. Now users are unaware of this backend setup. They just see Wiz authentication. 

Local users can have only one role per user and some common use cases include testing or maybe proof of value or POV, support access, maybe a break glass account, you know, maybe a backup admin account in case the single sign-on stops working. 

Local users are used when customers have immature non-existing IAM or security teams.

#### SSO (Federated Users) 🌐

In terms of SSO, WIZ is going to use SAML 2.0, you know, anything that's SAML 2.0 compliant will be able to integrate. So it supports all the major third-party IDPs like:

- AD FS
- Google Workspace
- AWS IAM Identity Center
- JumpCloud
- Microsoft Entra ID (AAD)
- Okta SAML app
- OneLogin
- Ping Federate
- Ping Identity

SSO users can have more than one role and the role assignments will happen at the SSO mapping stage. So use cases for SSO include production users, multi-role assignments, security best practices as it allows that centralized and easier management of permissions through group assignments.

### Wiz User Roles 🏷️

In terms of the predefined roles in Wiz, there are many user roles that come out of the box. 

You can view these all under the Settings menu item and look at Access Management and then User Roles.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/fJoGny2.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">List of User Roles</div>
</div>
<br>

#### Scope details 🔍

Each role has predefined API scopes detailing which actions the role can perform. While predefined roles can't be edited, they can be used as a reference to create a custom role. 
<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/0cyAUx3.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">List of User Scopes</div>
</div>
<br>

Administrators can create custom roles by defining a name, description, project scope, and API scope.

### Wiz Role Assignment 🎫

#### Local Users 📨

to assign local users, you're going to go into: Settings > Access Management > User Managemenr > Add a User

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/CTStCYb.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Form to Invite a Nuew User on Wiz</div>
</div>
<br>

You're going to fill in the user's details, select Wiz as the Identity Provider, you know, you're going to indicate that they are, in fact, a local user, and you'll choose their role and their scope. 

For project-based scopes, you're going to need to select the specific project. You can also bulk invite users through an API call

#### SSO Users 🔄

After configuring SSO, you can go to Settings > Access Management > SSO > Login Security to set up the SSO role mapping. 

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/j7DQHix.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">SAML Role Mapping</div>
</div>
<br>

Here, you map group IDs from your IDP to roles in Wiz. This allows, again, that centralized management of user permissions through those group assignments in that IDP.

You can invite SSO users individually by creating a placeholder for them in Wiz. That needs to match the name and email sent through the SAML assertion. 

SSO users have the functionality to switch roles. If a user has more than one role, they can click on their avatar in Wiz, select Switch Roles, and choose the desired role, accessing the different permissions based on the role that's been selected.

### Wiz Service Accounts 🤖

Service accounts are used for: 
- API calls: Used my machine-to-machine interfaces in order to aouthenticate with the Wiz API
- Automating tasks
- Third-party Integrations: Used to set up 3rd party integrations (e.g. Slack, ServiceNow, Jira)
- Container security and IaC scanning: Kubernetes Connector, Admission Controller, Runtime Sensor

For example, setting up an integration with Slack or ServiceNow or Jira requires a service account. 

Predefined service accounts are used for sensor deployment, brokers, admission controllers, and connectors. 

To manage service accounts, you're going to go into Settings > Access Management> Service Accounts. 

You can create a new service account or view existing ones. For new service accounts, you can choose between custom integration, defining the scope and the allowed APIs, or predefined roles for that specific task. 

When the service account expires, it invalidates the secret and disables the service account. You're going to need to rotate that secret to re-enable it.

### Access Management Flow 🔄

Actions like accessing the portal or making API calls, they're granted through access scopes tied to service accounts or roles that are assigned to users. 

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://imgur.com/M2QRxHY.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Access Management Flow</div>
</div>
<br>

The combination of access scopes and portal scopes, which can be global or project-specific, that determines the permissions for users or service accounts in Wiz. In other words, the actions enforce the scopes permissions, not the roles.


### Wiz Browser Extension: Wiz Extend 🧩

The Wiz Chrome browser extension displays real-time security alerts and context-aware insights generated by Wiz while you navigate your cloud service provider's portal.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs-assets.wiz.io/images/wiz-browser-extension-ed84fda5.gif"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Wiz Extend Showcase</div>
</div>
<br>


The query name, e.g. **AWS Resources**, and Issue counts update as you navigate to console pages

From the Wiz browser extension, you can:
*   Click the ✦ at the top right of your browser to open the Wiz portal in a new tab
*   Click the query name to open the Wiz Security Graph in a new tab
*   Click the Issue counts to open the Wiz Issues page in a new tab
*   Click the arrows to minimize (or maximize) the Wiz extension
When you navigate to a console page that does not correspond to a supported resource, the extension automatically minimizes itself.

<div style="text-align: center; width: 900px; margin: auto;">
    <img src="https://docs.wiz.io/_next/image?url=https%3A%2F%2Fdocs-assets.wiz.io%2Fimages%2Fwiz-ext-start-686ed63-unsupported_resources.png&w=3840&q=75"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">An AWS console showing an unsupported resource; the Wiz extension is auto-minimized</div>
</div>
<br>
