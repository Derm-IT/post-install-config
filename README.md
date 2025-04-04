# osTicket: Post-Installation Configuration

## Overview

This repository details the post-installation configuration of the osTicket helpdesk system, focusing on setting up roles, departments, teams, user access controls, agents, users, SLAs, and help topics. This configuration is essential for tailoring osTicket to specific organizational needs and workflows.

## Objective

To configure osTicket after installation, customizing it for efficient ticket management and support operations.

## Prerequisites

* A successfully installed osTicket instance, as described in the "osTicket: Prerequisites and Installation" repository.
* Access to the osTicket Admin Panel.

## Key URLs

* **Admin/Agent Login Page:** `http://localhost/osTicket/scp/login.php`
* **End Users osTicket URL:** `http://localhost/osTicket`

## Steps

### 1. Initial osTicket Configuration (Via Admin Panel)

* If stopped, start your Windows VM in Azure and reconnect
* Log into the Admin Panel (`http://localhost/osTicket/scp/login.php`) using the admin credentials created during setup.
* ![image](https://github.com/user-attachments/assets/a845a81d-c3bf-499d-96a3-3651cbd118a1)
* You will see the Admin Panel when logged in and can switch to Agent Panel at the top
* ![image](https://github.com/user-attachments/assets/40c7ca09-161f-4876-9c69-d590aa8f03ea)
* **Panels:**
    * **Admin Panel:** For system-wide settings, configurations, agent management, SLAs, etc. (Accessed via top-right menu after login).
    * **Agent Panel:** For day-to-day ticket handling, creating users, etc.
### 2. Configure Roles
* Go to Admin Panel -> Agents -> Roles
* Here you can define sets of permissions that can be assigned to Agents. Allows granular control over what different staff members can see and do.
* Click Add Role
* ![image](https://github.com/user-attachments/assets/3189df91-f49d-4ce0-afbc-892c8bf5cdd0)
* Create a "Supreme Admin" role with all permissions
* Title it Supreme Admin and check all boxes for Tickets, Tasks, Knowledgebase

### 3. Configure Departments

* Go to Admin Panel -> Agents -> Departments
* ![image](https://github.com/user-attachments/assets/fcade90c-8d16-4854-ab7b-45056f98168b)
* Click `Add New Deparment` and set parent to Top-Level-Department and name it `SysAdmins`
* This allows us to segregate tickets based on function or responsibility. Controls ticket visibility, auto-assignment rules, and outgoing email settings.
* ![image](https://github.com/user-attachments/assets/7b9c0b4c-e863-43e1-bc53-ba77807267af)
* Leave Access as is, will assign people when we create Agents later
* Next we will configure a Team, which allows us to group agents across different Departments for specific tasks or alerts (e.g., a "Major Incident Team"). Allows flexible collaboration without changing departmental structure.


### 4. Configure Teams

* Go to Admin Panel -> Agents -> Teams
* Click `Add New Team` and just name it "Online Banking". We will use this team later
* ![image](https://github.com/user-attachments/assets/26862a17-0fed-4f3d-8be4-bc1ca82ff36c)

### 5. Configure User Access to Allow Anyone to Create Tickets

* Go to Admin Panel -> Settings -> Users
* **Key Setting:** Registration Required: Require registration and login to create tickets
* Check this box if you want only registered users to submit tickets. Uncheck it to allow anyone (guests) to create tickets via the portal or email.
* For this we will leave it unchecked to allow anyone to make a ticket
* ![image](https://github.com/user-attachments/assets/ad2e9b06-7418-4e92-a7ae-35bccd4d9e58)
* **Consideration:** Public-facing support often allows guest tickets; internal IT support might require registration.

### 6. Configure Agents (Staff)

* *To create an agent go to Admin Panel -> Agents -> Add New Agent
* Create an Agent called `Jane Doe` and assign an Email address(any and remember it) and set Username
* ![image](https://github.com/user-attachments/assets/951b30f1-2bbf-497d-9cbd-27bd87f7d208)
* Click Set Password, uncheck `Send the agent a password reset email` and click set and fill in a password
* ![image](https://github.com/user-attachments/assets/2bfb8aaf-72ef-4bf9-9e59-cfc7f2aef63d)
* Then click Access and assign Jane Doe to the SysAdmins Department under Primary Department and assign her the `Supreme Admin` role
* ![image](https://github.com/user-attachments/assets/3b7cb863-a2de-4c42-8239-6877bf4326a1)
* This will make her the Admin for the project
* Go to the Teams tab and assign her to the `Online Banking Team`
* ![image](https://github.com/user-attachments/assets/9a8c2395-2499-4fff-9fa8-b5abbd5a40ce)
* Now create another Agent called `John Doe` and assign an Email address and Username. He will act as our Support Level Agent
* ![image](https://github.com/user-attachments/assets/0a74e394-34f0-4051-a22b-b3e21000a136)
* Set Password the same way
* Go to Access tab and set his Department as `Support` and Role as `View Only`
* ![image](https://github.com/user-attachments/assets/04635345-b7f0-4778-9e3c-19edfc41d43b)
* Leave the rest of it as is and click create


### 7. Configure Users (Customers/End-Users)

* We will now create a User to create tickets
* Go to Agent Panel -> Users -> Add User
* Set email address and name and `Add User`
* ![image](https://github.com/user-attachments/assets/aaaa3cda-40b1-4b92-83f5-07148bf199ca)
* Note: Can also be created automatically via registration if enabled.

### 8. Configure Service Level Agreements (SLAs):

* Go to Admin Panel -> Manage -> SLA (tab under)
* Define time-based targets for ticket response and resolution. Can trigger alerts or escalations if targets are missed.
* Create these by clicking `Add New SLA Plan`. example on how to do one:
* ![image](https://github.com/user-attachments/assets/0ddf57e8-d16d-48e7-8539-4c69325eb289)
    * Sev-A: 1-hour grace period, 24/7 schedule (critical issues).
    * Sev-B: 4-hour grace period, 24/7 schedule (high priority).
    * Sev-C: 8-hour grace period, Business Hours schedule (normal priority).

### 9. Configure Help Topics (like categories)

* Categorize incoming tickets. Can be used to auto-assign tickets to specific Departments, set priority, or apply SLAs based on the user's selection when creating a ticket.
* Go to Admin Panel -> Manage -> Help Topics
* Click `Add New Help Topic` to create these 5 topics:
   * Topic: "Business Critical Outage", Parent Topic: `Report a Problem`
   * ![image](https://github.com/user-attachments/assets/a24f6071-7aa9-4294-9b1d-130bc832ed12)
   * Topic: "Personal Computer Issues", Parent Topic: `Report a Problem`
   * ![image](https://github.com/user-attachments/assets/a785e5d3-a7ef-449b-bbf6-65386a8dd15d)
   * Topic: "Equipment Request", Parent Topic: `General Inquiry`
   * ![image](https://github.com/user-attachments/assets/fe92c693-5e0c-431c-be90-4505b74fcda1)
   * Topic: "Password Reset", Parent Topic: `Report a Problem`
   * ![image](https://github.com/user-attachments/assets/2f2f328e-72c7-4880-8fca-be1e7f3e4840)
   * Topic: "Other", Parent Topic: `General Inquiry`
   * ![image](https://github.com/user-attachments/assets/db8dca57-8631-49d1-a515-7ac297c5e6ea)
 * **Manage Default "Report a Problem" Department:**
    * Go to `Report a Problem` help topic and open it
    * ![image](https://github.com/user-attachments/assets/8ab6758b-afb0-4c58-bb83-e0cac510af80)
    * Under **New Ticket Options**, review the currently assigned **Department**.
    * If its `Maintenance` click the dropdown menu and select **System Default** and `Save Changes`
    * ![image](https://github.com/user-attachments/assets/4e7842b1-a926-42c0-96df-45588fa6e7b0)
## Takeaways

* Successfully navigated the osTicket Admin Panel to configure essential system settings.
* Created and understood the purpose of Roles for agent permission management.
* Established Departments to organize agents and tickets based on function.
* Configured Teams to enable cross-departmental collaboration.
* Managed user access settings to control ticket creation permissions.
* Created agent accounts and assigned them to appropriate departments and roles.
* Added user accounts to simulate customer interactions.
* Defined Service Level Agreements (SLAs) to enforce support response and resolution targets.
* Configured Help Topics to categorize incoming tickets for efficient routing and management.
