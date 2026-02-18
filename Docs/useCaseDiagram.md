# Use Case Diagram

This diagram provides a high-level overview of the functional requirements for the two main actors: **Tenants** and **Landlords**.

## Actors & Goals

### 👤 Tenant
*   **Goal**: Find a place to live and manage their daily rental needs easily.
*   **Key Actions**: Search listings, Apply, Pay Rent, Request Repairs.

### 👤 Landlord
*   **Goal**: Efficiently manage properties and minimize vacancies.
*   **Key Actions**: List properties, Screen tenants, Collect Rent, Track Maintenance.

## Diagram

```mermaid
usecaseDiagram
    actor "Tenant" as T
    actor "Landlord" as L

    package "Marketplace" {
        usecase "Search Properties" as UC1
        usecase "Apply for Property" as UC2
    }

    package "Property Management" {
        usecase "Create Property Listing" as UC3
        usecase "Generate Property Code" as UC4
        usecase "Join via Code" as UC5
        usecase "Toggle Public/Private" as UC6
    }

    package "Daily Operations" {
        usecase "Pay Rent" as UC7
        usecase "Submit Maintenance Ticket" as UC8
        usecase "Resolve Ticket" as UC9
        usecase "View Financial Stats" as UC10
        usecase "Chat with Landlord/Tenant" as UC11
    }

    T --> UC1
    T --> UC2
    L --> UC3
    L --> UC4
    T --> UC5
    L --> UC6

    T --> UC7
    T --> UC8
    L --> UC9
    L --> UC10
    T --> UC11
    L --> UC11
```
