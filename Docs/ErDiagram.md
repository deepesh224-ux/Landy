# Entity Relationship Diagram

This diagram represents the database schema for the Landy platform, showing the relationships between Users, Properties, Tickets, and other core entities.

## Entities Description

*   **User**: Represents both Tenants and Landlords. Roles are managed via the application logic/auth provider.
*   **Property**: The central entity. Belongs to a Landlord and can have multiple Tenants (e.g., roommates).
*   **Ticket**: Maintenance requests linked to a specific Property and the User who created it.
*   **Payment**: Records of rent payments or application fees.
*   **Message**: Chat messages exchanged within the context of a Property.
*   **Document**: Leases, contracts, or other files associated with a Property.

## Diagram

```mermaid
erDiagram
    User ||--o{ Property : "owns (Landlord)"
    User ||--o{ Property : "rents (Tenant)"
    User ||--o{ Ticket : "creates"
    User ||--o{ Message : "sends"
    User ||--o{ Payment : "makes"

    Property ||--o{ Ticket : "has"
    Property ||--o{ Message : "context for"
    Property ||--o{ Document : "contains"
    Property ||--o{ Payment : "associated with"

    User {
        string id PK
        string email
        string name
        string role "Landlord | Tenant"
        string avatarUrl
    }

    Property {
        string id PK
        string ownerId FK
        string address
        string propertyCode "Unique 6-digit"
        boolean isPublic
        float rentAmount
    }

    Ticket {
        string id PK
        string propertyId FK
        string reporterId FK
        string title
        string description
        string status "New | Assigned | Resolved"
        string priority "Low | Normal | Emergency"
        string imageUrl
        datetime createdAt
    }

    Payment {
        string id PK
        string payerId FK
        string propertyId FK
        float amount
        string status
        datetime date
        string stripeId
    }

    Message {
        string id PK
        string senderId FK
        string propertyId FK
        string content
        datetime sentAt
    }

    Document {
        string id PK
        string propertyId FK
        string name
        string fileUrl
        string type "Lease | Inspection"
    }
```
