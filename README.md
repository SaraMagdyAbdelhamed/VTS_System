# 🌴 Vacation Tracking System (VTS)


## 📋 Table of Contents

- [🎯 Vision](#-vision)
- [⚙️ Functional Requirements](#️-functional-requirements)
  - [🌴 Leave Management](#-leave-management)
  - [✅ Approval Workflow](#-approval-workflow)
  - [⚖️ Rules Engine](#️-rules-engine)
  - [🗂️ Data & History](#️-data--history)
  - [🔔 Notifications](#-notifications)
  - [🛠️ Administration & Overrides](#️-administration--overrides)
  - [🔄 System Integration](#-system-integration)
  - [📜 Logging](#-logging)
- [✨ Non-Functional Requirements](#-non-functional-requirements)
- [⛓️ Constraints](#️-constraints)
- [🤔 Assumptions](#-assumptions)

---

## 🎯 Vision

The primary vision of the VTS is to empower employees and streamline internal HR processes.

> A Vacation Tracking System (VTS) will provide individual employees with the capability to manage their own vacation time, sick leave, and personal time off, without having to be an expert in company policy or the local facility’s leave policies.

#### Primary Goals
*   **Employee Empowerment:** Give employees the capability and responsibility to manage their own leave.
*   **HR Efficiency:** Streamline the functions of the Human Resources (HR) department by automating leave tracking and approval workflows.
*   **Managerial Focus:** Minimize the time managers spend on non-core, administrative tasks.

---

## ⚙️ Functional Requirements

These are the specific functions the system must perform.

### 🌴 Leave Management
- Employees must be able to **create, view, and cancel** their own leave requests.
- Employees must be able to **withdraw** a pending request before it is actioned by a manager.
- Employees must be able to **edit** the title or description of a pending request.

### ✅ Approval Workflow
- The system must support an optional **manager approval process** for leave requests.
- Managers must be able to **approve or deny** leave requests submitted by their subordinates.
- Managers must be able to **award compensatory time** (comp time) to their subordinates, within system-defined limits.

### ⚖️ Rules Engine
- The system must use a flexible, **rules-based engine** to validate all leave requests.
- Validation rules must account for both company-wide policies and location-specific policies.
- HR personnel (non-developers) must be able to **manage and update** these rules through a user-friendly interface.

### 🗂️ Data & History
- The system must provide users with access to their leave requests from the **previous calendar year**.
- The system must allow users to submit leave requests up to **1.5 years in the future**.

### 🔔 Notifications
- The system must send **email notifications** to managers when a new request requires their approval.
- The system must send **email notifications** to employees whenever the status of their request changes (e.g., approved, rejected, canceled).

### 🛠️ Administration & Overrides
- Authorized HR and System Administration users must have the ability to **override any restriction** imposed by the rules engine.
- All override actions must be **logged for auditing purposes**.
- HR clerks must be able to **edit employee records**, manage facility locations, and configure leave categories and rules.

### 🔄 System Integration
- The system must provide a **Web Service API** for other internal systems to query an employee’s vacation summary.
- The system must interface with existing **HR legacy systems** to retrieve employee data.

### 📜 Logging
- The system must maintain a comprehensive **activity log** for all user transactions and system events.

---

## ✨ Non-Functional Requirements

These requirements define *how* the system should operate.

- **Usability:** The system must be **intuitive and easy to use** for all user types (Employees, Managers, HR). This is a critical success factor and an overriding design goal.
- **Security:** All user authentication must be handled via the existing intranet portal’s single-sign-on (SSO) mechanism (`CAS`). The system **should not** implement its own authentication.
- **Compatibility:** The client-side user interface must be compatible with any standard **`HTML 3.2`-capable browser** to ensure broad accessibility across the organization.
- **Scalability:** The system architecture must be able to handle a growing number of users and transactions by allowing for the addition of more processing nodes (e.g., in a web server farm).
- **Maintainability:** The rules engine must be designed for easy updates by non-technical staff, reducing reliance on developers for policy changes.

---

## ⛓️ Constraints

These are non-negotiable limitations and decisions imposed on the project.

- **Technology Stack:** The system **must** be built using the organization's existing **Java-based architecture** (`JSP`, `Servlets`, `JSF`, `EJB`).
- **Infrastructure:** The project **must** utilize existing company hardware and middleware. No new hardware can be procured.
- **Integration:** The system **must** be implemented as an extension of the existing company intranet portal. It cannot be a standalone application.
- **Authentication:** The system **must** integrate with the Central Authentication Service (`CAS`) for all user authentication, adhering to the company standard.

---

## 🤔 Assumptions

These are conditions believed to be true that guide the design and planning of the project.

- **Process Efficiency:** It is assumed that an automated system will be significantly **faster and more cost-effective** than the current manual, paper-based process.
- **User Access:** All users (Employees, Managers) are assumed to have **regular access** to a computer and the company's intranet portal.
- **Data Availability:** It is assumed that all necessary employee data (e.g., manager-subordinate relationships, leave balances, location) is **available and accessible** from the HR legacy systems.
- **UI Consolidation:** The design assumes that a **single, role-aware home screen** can effectively serve the needs of both regular Employees and Managers.
