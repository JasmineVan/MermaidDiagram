```mermaid

---
title: Aquatic Hubs
---
%%{init: {'theme':'base'}}%%

erDiagram
    USER }|--|{ USER : relation
    USER }o--o{ ENROLLMENT : attend
    USER ||--|| PAYMENT : pay
    USER ||--o{ TICKET : own
    USER {
        string id
        string phoneNumber
        string firstName
        string lastName
        string address
        string email
        string pictureURL
        string passwordHash
        string type
        string gender
        date createDate
        date dateOfBirth
        int age
        boolean isActive
    }

    TEACHER ||--|| ENROLLMENT : teach
    TEACHER ||--o{ NOTE : note
    TEACHER {
        string id
        string phoneNumber
        string firstName
        string lastName
        string address
        string email
        string pictureURL
        string passwordHash
        string type
        string gender
        string position
        date createDate
        date dateOfBirth
        int age
        boolean isActive
    }

    NOTE {
        string id
        string title
        string content
        datetime createDate
    }

    LESSON{
        string id
        string description
        string detail
        string type
        string level
        string pictureURL
        string lessonURL
        double price
    }

    ENROLLMENT ||--|| LESSON : hold
    ENROLLMENT ||--|| PAYMENT : billing
    ENROLLMENT ||--o{ TIMETABLE-DATE : time
    ENROLLMENT{
        string id
        string type
        string lecture
        string area
        string lessonID
        date startDate
        date endDate
    }

    TIMETABLE-DATE {
        string id
        date timetableDate
        datetime startTime
        datetime endTime
    }

    PAYMENT {
        string id
        string enrollmentID
        string userID
        string ticketID
        string paymentMethod
        string checkoutURL
        string status
        double price
        date createDate
        date expireDate
    }

    TICKET ||--o{ TICKET-DATE : time
    TICKET {
        string id
        string description
        string userID
        string courseID
        string type
        date startDate
        date endDate
        int count
    }

    TICKET-DATE {
        string id
        date ticketDate
        datetime startTime
        datetime endTime
        datetime visitTime
        boolean isVisit
    }

    POOL-LANE {
        string id
        string pictureURL
    }
