# Class Diagram

This diagram illustrates the high-level system architecture and the relationships between the main service classes and controllers in the Landy backend.

## Architecture Overview

The backend is structured around modular services that handle specific domains:
*   **Authentication**: Managed by `AuthService` (wrapping Clerk/NextAuth).
*   **Property Management**: `PropertyManager` handles listings, portfolio views, and code generation.
*   **Maintenance**: `TicketService` manages the lifecycle of maintenance requests.
*   **Communication**: `ChatService` handles real-time messaging.
*   **Financials**: `PaymentService` integrates with Stripe.

## Diagram

```mermaid
classDiagram
    class AuthService {
        +login(credentials)
        +logout()
        +getCurrentUser() User
    }

    class PropertyManager {
        +createProperty(details)
        +getPropertiesByLandlord(landlordId)
        +toggleVisibility(propertyId, isPublic)
        +generatePropertyCode(propertyId) string
        +getTenantList(propertyId) User[]
        +removeTenant(propertyId, tenantId)
    }

    class TicketService {
        +createTicket(ticketData)
        +updateStatus(ticketId, status)
        +assignTicket(ticketId, staffId)
        +getTicketsByProperty(propertyId) Ticket[]
    }

    class PaymentService {
        +processRentPayment(paymentDetails)
        +getPaymentHistory(propertyId) Payment[]
        +generateFinancialReport(landlordId) Report
    }

    class ChatService {
        +sendMessage(senderId, propertyId, content)
        +getHistory(propertyId) Message[]
        +subscribeToUpdates(propertyId)
    }

    class CloudStorageService {
        +uploadImage(file) string
        +uploadDocument(file) string
        +getFileUrl(fileId) string
    }

    PropertyManager --> "1" AuthService : validates
    TicketService --> "1" PropertyManager : references
    PaymentService --> "1" PropertyManager : references
    ChatService --> "1" PropertyManager : scoped to
    TicketService ..> CloudStorageService : uses
    PropertyManager ..> CloudStorageService : uses for leases
```
