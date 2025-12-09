erDiagram

    USER {
        string id PK
        string name
        string email
        string role
        string passwordHash
    }

    PET {
        string id PK
        string userId FK
        string name
        string breed
        int age
        float weight
    }

    MEDICAL_RECORD {
        string id PK
        string petId FK
        string type
        string notes
        date date
        string fileUrl
    }

    PRODUCT {
        string id PK
        string sellerId FK
        string name
        string category
        float price
        int stock
        float rating
    }

    REVIEW {
        string id PK
        string userId FK
        string productId FK
        int rating
        string comment
    }

    CART {
        string id PK
        string userId FK
    }

    CART_ITEM {
        string id PK
        string cartId FK
        string productId FK
        int quantity
    }

    ORDER {
        string id PK
        string userId FK
        float total
        string status
        string address
        string paymentStatus
    }

    ORDER_ITEM {
        string id PK
        string orderId FK
        string productId FK
        int quantity
        float price
    }

    VET {
        string id PK
        string userId FK
        string specialty
        string location
        float rating
    }

    APPOINTMENT {
        string id PK
        string vetId FK
        string userId FK
        date date
        string time
        string type
        string status
    }

    LOST_FOUND {
        string id PK
        string userId FK
        string type
        string description
        string imageUrl
        float lat
        float lng
    }

    SHELTER {
        string id PK
        string name
        string address
        float lat
        float lng
        string contact
    }

    USER ||--o{ PET : owns
    PET ||--o{ MEDICAL_RECORD : has
    USER ||--o{ REVIEW : writes
    USER ||--o{ CART : has
    CART ||--o{ CART_ITEM : contains
    PRODUCT ||--o{ CART_ITEM : listed_in
    USER ||--o{ ORDER : places
    ORDER ||--o{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : purchased
    USER ||--o{ LOST_FOUND : reports
    USER ||--o{ VET : may_be
    VET ||--o{ APPOINTMENT : has
    USER ||--o{ APPOINTMENT : books
