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
flowchart TD
    %% Actors
    T[Tenant]
    L[Landlord]

    %% Subsystems
    subgraph Marketplace
        UC1(Search Properties)
        UC2(Apply for Property)
    end

    subgraph Property_Management [Property Management]
        UC3(Create Property Listing)
        UC4(Generate Property Code)
        UC5(Join via Code)
        UC6(Toggle Public/Private)
    end

    subgraph Daily_Operations [Daily Operations]
        UC7(Pay Rent)
        UC8(Submit Maintenance Ticket)
        UC9(Resolve Ticket)
        UC10(View Financial Stats)
        UC11(Chat with Landlord/Tenant)
    end

    %% Relationships
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
