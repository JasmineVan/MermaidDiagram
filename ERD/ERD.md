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
    USER ||--|| SEASON-BOOKING : pay
    USER {
        string id PK "also user phone number"
        string phoneNumber
        string firstName
        string lastName
        string address
        string email
        string pictureURL
        string passwordHash "hashed in sha256 hash function"
        string type "personal, family"
        string gender "male, female, other"
        date createDate
        date dateOfBirth
        int age
        boolean isActive
    } 

    TEACHER ||--|| ENROLLMENT : teach
    TEACHER ||--o{ NOTE : note
    TEACHER {
        string id PK
        string phoneNumber
        string firstName
        string lastName
        string address
        string email
        string pictureURL
        string passwordHash "hashed in sha256 hash function"
        string gender "male, female, other"
        string position "fresher, intermediate, master"
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
        string type "swimming, adult, training, club, fasttrack"
        string level "depend on each type"
        string pictureURL
        string lessonURL
        double price
    }

    ENROLLMENT ||--|| LESSON : hold
    ENROLLMENT ||--|| PAYMENT : billing
    ENROLLMENT ||--o{ TIMETABLE-DATE : time
    ENROLLMENT{
        string id PK
        string type "standard, trial"
        string lecturer
        string area "pool lane"
        string lessonID
        date startDate "this lesson will begin in this date"
        date endDate "this lesson will end in this date"
    }

    TIMETABLE-DATE {
        string id PK
        date timetableDate "one day in a timetable"
        datetime startTime "the class will start at this time"
        datetime endTime "the class will end at this time"
    }

    PAYMENT {
        string id PK
        string enrollmentID FK
        string userID FK
        string ticketID FK
        string paymentMethod "Cash, ALE, VN"
        string checkoutURL "the redirect URL from payment gateway"
        string status "unpaid, pending, paid, expired"
        double price
        date createDate
        date expireDate
    }

    TICKET ||--o{ TICKET-DATE : time
    TICKET {
        string id PK
        string description
        string userID FK
        string courseID FK
        string type "regular, 10 days, 30 days"
        date startDate "valid from this day"
        date endDate "invalid from this day"
        int count "used time"
    }

    TICKET-DATE {
        string id PK
        date ticketDate "one day in a ticket"
        datetime startTime
        datetime endTime
        datetime visitTime "visit time in real time"
        boolean isVisit
    }

    POOL-LANE {
        string id
        string pictureURL
    }

    RENTAL-POOL-LANE ||--|| POOL-LANE : rented
    RENTAL-POOL-LANE }|--|| USER : rent
    RENTAL-POOL-LANE {
        string id PK
        string userID FK
        string poolID FK
        string paymentMethod "Cash, ALE, VN"
        string checkoutURL "the redirect URL from payment gateway"
        string status "unpaid, pending, paid, expired"
        double price
        date rentalDate
        datetime rentalStartTime
        datetime rentalEndTime
        int duration "in hour"
    }

    SEASON-BOOKING ||--|| TICKET : contain
    SEASON-BOOKING {
        string id PK
        string userID FK
        string ticketID FK
        string paymentMethod "Cash, ALE, VN"
        string checkoutURL "the redirect URL from payment gateway"
        string status "unpaid, pending, paid, expired"
        double price
        date createDate
        date expireDate
        int duration "in hour"
    }
