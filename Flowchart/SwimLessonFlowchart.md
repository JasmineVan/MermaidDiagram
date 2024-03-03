```mermaid

---
title: Purchase School Of Fish
---
%%{init: {'theme':'neutral'}}%%

flowchart TB
    A:::startclass
    G:::conditionClass
    H:::conditionClass
    L:::conditionClass
    P:::conditionClass
    M:::endClass
    classDef startclass fill:#114232
    classDef conditionClass fill:#FAA300
    classDef endClass fill:#EE4266

    A([Start]) --> B[Book now]
    B --> C[Go to SOF section]
    C --> D[Choose a class]
    D --> E[Selected class detail screen]
    E --> F[Book a class]
    F --> G{Log in?}
    G ---->|TRUE| H{Already book?}
    G -->|FALSE| I[Direct to login page]
    I --> H
    H -->|TRUE| K[Class learning page]
    H -->|FALSE| L{Account type?}
    K --> M([End])
    L ---->|Personal| P
    L -->|Family| O[Choose member]
    subgraph " "
    N --> U[Complete checkout]
    end
    O --> P{Check old}
    U --> K
    P -->|Valid| N[Checkout page]
    P -->|Invalid| R[Show error message]
    R --> M
    