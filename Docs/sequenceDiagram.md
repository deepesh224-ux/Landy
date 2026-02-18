# Sequence Diagram

This diagram details the core "Tenant Onboarding" flow, illustrating how a tenant joins a property using the unique 6-digit code.

## Flow Description

1.  **Code Distribution**: The Landlord generates a code and shares it with the Tenant off-platform.
2.  **Input**: The Tenant logs in and enters the code in the "Join Your Home" portal.
3.  **Validation**: The System validates the code against the database.
4.  **Linking**: If valid, the System links the Tenant's account to the Property.
5.  **Access**: The Tenant is granted access to the Dashboard, Lease, and Chat.

## Diagram

```mermaid
sequenceDiagram
    actor Tenant
    actor Landlord
    participant Frontend as Web App
    participant Backend as API Server
    participant DB as Database

    Landlord->>Frontend: Request Property Code
    Frontend->>Backend: POST /api/properties/:id/code
    Backend->>DB: Update/Fetch Code
    DB-->>Backend: Return "123456"
    Backend-->>Frontend: Display Code "123456"
    Frontend-->>Landlord: Shows Code

    Note over Landlord, Tenant: Landlord shares code with Tenant (SMS/Email)

    Tenant->>Frontend: Enter Code "123456"
    Frontend->>Backend: POST /api/join-property { code: "123456" }
    Backend->>DB: Query Property by Code
    alt Code Invalid
        DB-->>Backend: null
        Backend-->>Frontend: Error "Invalid Code"
        Frontend-->>Tenant: Show Error Message
    else Code Valid
        DB-->>Backend: Property Object
        Backend->>DB: Link Tenant User ID to Property
        DB-->>Backend: Success
        Backend-->>Frontend: Success (200 OK)
        Frontend-->>Tenant: Redirect to Dashboard
    end
```
