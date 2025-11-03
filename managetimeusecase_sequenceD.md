sequenceDiagram
    participant Employee
    participant System as Time Management System
    participant DB as Database
    participant Manager
    participant Notifier as Notification Service

    %% Step 1: Employee Submits Timesheet
    Employee->>+System: Submits Timesheet (hours, project codes)
    System->>System: Validate input data
    System->>+DB: Save Timesheet data (status: 'Pending')
    note over DB: Timesheet is stored with a<br/>'Pending' status until reviewed.
    DB-->>-System: Confirm data saved

    %% Step 2: System Notifies Manager
    System->>+Notifier: Request notification for Manager
    Notifier->>Manager: Email: "Timesheet requires approval"
    Notifier-->>-System: Confirm notification sent
    System-->>-Employee: Show "Submission successful" message

    %% Step 3: Manager Reviews and Acts on the Timesheet
    Manager->>+System: Views pending timesheets
    System->>+DB: Fetch Timesheet data for Manager
    DB-->>-System: Return Timesheet data
    System-->>-Manager: Display Timesheet for review

    alt Approve Timesheet
        Manager->>+System: Approves Timesheet
        System->>+DB: Update Timesheet (status: 'Approved')
        DB-->>-System: Confirm update
        System->>+Notifier: Request approval notification for Employee
        Notifier->>Employee: Email: "Your timesheet has been approved"
        Notifier-->>-System: Confirm notification sent
        System-->>-Manager: Show confirmation message

    else Reject Timesheet
        Manager->>+System: Rejects Timesheet (with comments)
        System->>+DB: Update Timesheet (status: 'Rejected', comments)
        DB-->>-System: Confirm update
        System->>+Notifier: Request rejection notification for Employee
        Notifier->>Employee: Email: "Your timesheet was rejected. Please review."
        Notifier-->>-System: Confirm notification sent
        System-->>-Manager: Show confirmation message
    end
