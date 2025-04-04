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

* **Context:** Log into the Admin Panel (/scp) using the admin credentials created during setup. The following steps tailor osTicket to a specific organizational structure.

* **Understand Panels:**
    * **Admin Panel:** For system-wide settings, configurations, agent management, SLAs, etc. (Accessed via top-right menu after login).
    * **Agent Panel:** For day-to-day ticket handling, creating users, etc. (Default view after agent login).

### 2. Configure Roles

* **Navigation:** Admin Panel -> Agents -> Roles
* **Purpose:** Define sets of permissions that can be assigned to Agents. Allows granular control over what different staff members can see and do.
* **Example:** Create a "Supreme Admin" role with all permissions (usually exists by default), maybe a "Level 1 Support" role with limited permissions.

### 3. Configure Departments

* **Navigation:** Admin Panel -> Agents -> Departments
* **Purpose:** Segregate tickets based on function or responsibility. Controls ticket visibility, auto-assignment rules, and outgoing email settings.
* **Example:** Create "System Administrators", "Network Team", "Help Desk".

### 4. Configure Teams

* **Navigation:** Admin Panel -> Agents -> Teams
* **Purpose:** Group agents across different Departments for specific tasks or alerts (e.g., a "Major Incident Team"). Allows flexible collaboration without changing departmental structure.
* **Example:** Create an "Online Banking Support" team pulling members from Help Desk and SysAdmins.

### 5. Configure User Access

* **Navigation:** Admin Panel -> Settings -> User Settings
* **Key Setting:** Registration Required: Require registration and login to create tickets
* **Action:** Check this box if you want only registered users to submit tickets. Uncheck it to allow anyone (guests) to create tickets via the portal or email.
* **Consideration:** Public-facing support often allows guest tickets; internal IT support might require registration.

### 6. Configure Agents (Staff)

* **Navigation:** Admin Panel -> Agents -> Add New
* **Purpose:** Create accounts for IT staff who will work on tickets. Assign them to Departments and Roles.
* **Example:** Add Agent "Jane Doe" to the "SysAdmins" Department. Add "John Smith" to the "Support" Department.

### 7. Configure Users (Customers/End-Users)

* **Navigation:** Agent Panel -> Users -> Add New (or User Directory)
* **Purpose:** Create accounts for the end-users or customers who will be submitting tickets. Can also be created automatically via registration if enabled.
* **Example:** Add users "Karen" and "Ken".

### 8. Configure Service Level Agreements (SLAs):

* **Navigation:** Admin Panel -> Manage -> SLA Plans
* **Purpose:** Define time-based targets for ticket response and resolution. Can trigger alerts or escalations if targets are missed.
* **Example:**
    * Sev-A: 1-hour grace period, 24/7 schedule (critical issues).
    * Sev-B: 4-hour grace period, 24/7 schedule (high priority).
    * Sev-C: 8-hour grace period, Business Hours schedule (normal priority).

### 9. Configure Help Topics

* **Navigation:** Admin Panel -> Manage -> Help Topics
* **Purpose:** Categorize incoming tickets. Can be used to auto-assign tickets to specific Departments, set priority, or apply SLAs based on the user's selection when creating a ticket.
* **Example:** "Business Critical Outage", "Personal Computer Issues", "New Equipment Request", "Password Reset".
