# CRM Data Model Blueprint

This repository defines a basic CRM (Customer Relationship Management) data model suitable for a SaaS application. It includes JSON schema definitions for core CRM entities.

## Overview

The data model consists of four main entities:

1.  **Account:** Represents companies or organizations.
2.  **Contact:** Represents individual people associated with Accounts.
3.  **Lead:** Represents potential prospects (individuals or companies).
4.  **Opportunity:** Represents potential sales deals associated with Accounts.

## Schemas

JSON Schemas define the structure, data types, and constraints for each entity. They are located in the `/schemas` directory. Timestamps (`createdAt`, `updatedAt`) are included in all schemas for tracking, although not explicitly shown in the simplified ER diagram.

### `schemas/account.json`

*   **Purpose:** Stores information about companies or organizations.
*   **Key Fields:** `id`, `name`, `industry`, `owner_id`.
*   **Relationships:**
    *   One Account can have many Contacts (`Contact.accountId`).
    *   One Account is associated with one Opportunity (`Opportunity.accountId`).
    *   A Lead can be converted into an Account (`Lead.convertedAccountId`).

### `schemas/contact.json`

*   **Purpose:** Stores information about individual people.
*   **Key Fields:** `id`, `first_name`, `last_name`, `email`, `phone`, `accountId`.
*   **Relationships:**
    *   A Contact belongs to one Account (`accountId`).

### `schemas/lead.json`

*   **Purpose:** Captures information about potential prospects before qualification.
*   **Key Fields:** `id`, `name`, `source`, `status`.
*   **Lifecycle:** A Lead typically moves through `status` values (e.g., New, Qualified). A `Qualified` lead may be converted into an Account.
*   **Conversion Field:** `convertedAccountId` tracks the resulting Account upon conversion.

### `schemas/opportunity.json`

*   **Purpose:** Tracks potential sales deals or revenue opportunities.
*   **Key Fields:** `id`, `name`, `accountId`, `stage`, `amount`, `close_date`.
*   **Relationships:**
    *   An Opportunity is associated with one Account (`accountId`).

## Usage

These schemas can be used for:

*   **Database Design:** As a blueprint for designing relational or NoSQL database tables/collections.
*   **API Development:** Defining request/response payloads for CRM-related API endpoints.
*   **Data Validation:** Validating incoming data against the defined structure.
*   **Integration:** Ensuring consistency when integrating with other systems.

See the `diagrams/diagram.md` file for a visual representation of the entity relationships using Mermaid syntax. You can use online tools or CLI utilities to render this into an image (e.g., PNG). 