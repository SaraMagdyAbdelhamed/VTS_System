Vacation Tracking System (VTS) - System Overview
This document provides a comprehensive overview of the Vacation Tracking System as described in the provided architectural text.

1. System Details
Vision
The core vision for the Vacation Tracking System (VTS) is to empower employees and streamline HR processes. The official vision statement is:

A Vacation Tracking System (VTS) will provide individual employees with the capability to manage their own vacation time, sick leave, and personal time off, without having to be an expert in company policy or the local facility’s leave policies.

The primary goals derived from this vision are:

Give employees the capability and responsibility to manage their own leave.
Streamline the functions of the Human Resources (HR) department.
Minimize non-core, business-related activities for managers.
Empower employees.
Functional Requirements
These are the specific functions the system must perform, derived from the "key features" and use case descriptions.

Leave Management:
Employees can create, view, and cancel their own vacation time requests.
Employees can withdraw a pending request before it is approved/denied.
Employees can edit the title or description of a pending request.
Approval Workflow:
The system must support an optional manager approval process for leave requests.
Managers can approve or deny leave requests from their subordinates.
Managers can award personal leave time (comp time) to subordinates, within system-set limits.
Rules Engine:
Must implement a flexible, rules-based system for validating and verifying leave time requests.
Rules should be manageable by HR personnel, not just developers.
Validation must account for company-wide policies and location-specific rules.
Data and History:
The system must provide access to requests from the previous calendar year.
The system must allow requests to be made up to 1.5 years in the future.
Notifications:
The system must use e-mail to notify managers of new requests needing approval.
The system must use e-mail to notify employees of any change in their request's status (e.g., approved, rejected, canceled).
Administration and Overrides:
HR and System Administration personnel must be able to override all actions restricted by the rules engine.
All override actions must be logged.
HR clerks can edit employee records, manage locations and their rules, and manage leave categories.
System Integration:
Must provide a Web service interface for other internal systems to query an employee’s vacation request summary.
Must interface with HR legacy systems to retrieve necessary employee information.
Logging:
The system must keep activity logs for all transactions.
Non-Functional Requirements
These requirements describe how the system should operate, rather than what it should do.

Usability:
"The system must be easy to use." This is stated as an "overriding design goal" and is considered critical to the project's success. It justifies design decisions that favor user experience over technical simplicity (e.g., using a WYSIWYG editor applet).
Security:
The system must use the existing intranet portal’s single-sign-on (SSO) mechanisms (specifically, CAS) for all user authentication.
Compatibility:
The client-side interface must be compatible with any standard HTML 3.2-capable browser, ensuring broad accessibility without requiring the latest browser versions.
Scalability:
The architecture (J2EE) should support scaling by adding additional processing nodes (e.g., a web server farm) to handle changing demand.
Maintainability:
The rules-based system must be flexible and manageable by non-technical HR staff, indicating a need for a user-friendly rule management interface.
Constraints
These are limitations or decisions that are imposed upon the project and restrict design choices.

Technology Stack: The project is constrained to use a Java-based architecture (JSP, Servlets, JSF, EJB) because this matches the organization's existing skill sets, tools, and successful past experiences.
Existing Infrastructure: The system must use existing hardware and middleware.
Integration Mandate: The VTS must be implemented as an extension to the existing intranet portal system.
Authentication Method: The system must use the Central Authentication Service (CAS) for single-sign-on, as it's the standard for the existing portal.
Assumptions
These are conditions accepted as true without proof, which guide the design and analysis.

Automated Efficiency: It is assumed that an automated system will be faster than the manual process and will save time and money for the HR department.
Shared User Interface: The design assumes that a single home screen (VTSHome) can serve the needs of both regular Employees and Managers, even though this was not an explicit requirement.
User Access: It is assumed that all users (Employees, Managers) have access to the company's intranet portal.
ID Generation: During analysis, it is assumed that implementation-specific details like unique identifiers (primary keys) for entities can be added as needed during the design phase without being specified in the initial analysis model.
