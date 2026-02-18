# Landy (Small Landlord & Tenant Portal)

## 🏡 Core Concept
Landy is a comprehensive "PropTech" platform designed to bridge the gap between small landlords and tenants. It facilitates the entire rental lifecycle, from property discovery in a public marketplace to ongoing management tasks like maintenance requests and rent payments. A key differentiator is its unique **Property Code system**, which simplifies tenant onboarding and ensures secure access to property-specific data.

## 👥 The User Journeys

### 1. The Tenant Journey
The tenant experience is designed to be seamless, moving from discovery to living in the property.

*   **Screen A: The Public Marketplace**
    *   **Feature:** A searchable list of available rental properties.
    *   **Options:** Tenants can filter listings by price, location, and desired amenities.
    *   **Action:** An "Apply Now" button allows prospective tenants to submit a digital profile directly to the landlord for review.

*   **Screen B: The Onboarding (Your Image)**
    *   **Feature:** The "Join Your Home" portal.
    *   **Action:** This is where the unique **6-digit Property Code** comes into play. The landlord provides this code to the tenant.
    *   **Benefit:** Entering this code instantly links the tenant's account to the specific property, unlocking access to the correct lease, chat channels, and payment portal.

*   **Screen C: The Tenant Dashboard**
    *   **Maintenance:** A dedicated "Ticket" system allows tenants to report issues with photos, descriptions, and urgency levels (Low, Normal, Emergency).
    *   **Finances:** A clear view of rent due dates with a "Pay Now" button powered by Stripe integration.
    *   **Chat:** A private, direct messaging thread with the landlord for quick communication.
    *   **Documents:** digital access to important files like the lease agreement and move-in inspection photos.

### 2. The Landlord Journey
Landlords are provided with tools to manage their portfolio efficiently and communicate effectively.

*   **Screen A: The Portfolio Overview**
    *   **Feature:** A card-based dashboard displaying all owned properties.
    *   **Options:** Properties can be toggled between "Private" (Managed state) and "Public" (Listed on Marketplace).
    *   **Stats:** High-level financial metrics showing total monthly rent collected and a count of open maintenance tickets.

*   **Screen B: Property Deep-Dive**
    *   When a specific property is selected (e.g., "742 Evergreen Terrace"), the landlord gains access to:
        *   **Maintenance Kanban:** A visual board to manage tickets, dragging them from *New* ➔ *Assigned* ➔ *Resolved*.
        *   **Tenant Management:** A list of currently linked tenants, with options to Reset the Property Code or remove a tenant if necessary.
        *   **Financials:** A log of expenses (repairs, utilities) to assist with tax reporting and profitability tracking.
        *   **Chat Center:** A history of all messages exchanged regarding that specific property.

## 🛠️ Technical Architecture

| Feature | Implementation | Benefit |
| :--- | :--- | :--- |
| **Logic** | Next.js + TypeScript | Ensures type safety and provides fast, server-side rendered routing for distinct Landlord and Tenant views. |
| **Database** | PostgreSQL (Supabase/Prisma) | Maintains robust relational links between Users, Properties, and Tickets. |
| **Auth** | Clerk / NextAuth | Manages secure authentication and "Role-Based Access Control" (RBAC) related flows. |
| **Real-time** | Pusher / Ably | Powers instant delivery of chat messages and updates to ticket statuses. |
| **Payments** | Stripe API | Facilitates secure rent collection and processing of application fees. |
| **Media** | Cloudinary / AWS S3 | Optimized storage for maintenance photos and PDF lease documents. |
