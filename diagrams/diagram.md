```mermaid
erDiagram
    CONTACT ||--o{ ACCOUNT : has
    CONTACT {
        string id
        string first_name
        string last_name
        string email
        string phone
    }
    ACCOUNT {
        string id
        string name
        string industry
        string owner_id
    }
    OPPORTUNITY ||--|| ACCOUNT : associated_with
    OPPORTUNITY {
        string id
        string name
        string stage
        float amount
        date close_date
    }
    LEAD ||--o{ ACCOUNT : converted_to
    LEAD {
        string id
        string name
        string source
        string status
    }
} 