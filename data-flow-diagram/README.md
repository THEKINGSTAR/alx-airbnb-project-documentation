# Data Flow Diagram (DFD) – Airbnb Clone Backend

## 📌 Overview

This diagram visualizes how data moves throughout the Airbnb backend system. It covers the major external entities, internal processes, and data stores. Each process receives input, performs logic, and stores data in the appropriate database.

## 🧩 DFD Level 1 Components

### External Entities
- **User** – Registers, logs in, books listings.
- **Admin** – Manages listings and monitors platform activity.
- **Payment Gateway** – Handles external payment transactions.

### Processes
- **Authenticate User** – Manages registration and login.
- **Manage Listings** – Admins or hosts manage property data.
- **Manage Booking** – Guests create or cancel bookings.
- **Process Payment** – Handles payments and payouts.

### Data Stores
- **User DB** – Stores user credentials and profile info.
- **Property DB** – Stores listing information.
- **Booking DB** – Holds reservation records.
- **Payment DB** – Logs completed payment details.

## 📤 Exported Files
- **data-flow.drawio** – Editable diagram (Draw.io format)
- **data-flow.png** – Image version for documentation

