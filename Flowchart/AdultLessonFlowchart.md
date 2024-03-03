```mermaid

---
title: Purchase Adult Lesson
---
%%{init: {'theme':'neutral'}}%%

flowchart TD
    A:::startclass
    G:::conditionClass
    H:::conditionClass
    M:::endClass
    classDef startclass fill:#114232
    classDef conditionClass fill:#FAA300
    classDef endClass fill:#EE4266

    A([Start]) --> B[Book now]
    B --> C[Go to Adult section]
    C --> D[Choose a class]
    D --> E[Selected class detail screen]
    E --> F[Book a class]
    F --> G{Log in?}
    G ---->|TRUE| H{Already book?}
    G -->|FALSE| I[Direct to login page]
    I --> H
    H -->|TRUE| K[Class learning page]
    H -->|FALSE| L[Checkout page]
    L --> M([End])
    K --> M([End])
    