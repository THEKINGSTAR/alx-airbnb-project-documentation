# Airbnb Clone Backend - Use Case Diagram

## 📁 Directory: `use-case-diagram/`

## 📄 File: `README.md`

---

## 🎯 Objective

This document accompanies the **Use Case Diagram** for the Airbnb Clone backend system. The diagram visualizes interactions between primary actors and the system to support key backend features and functionalities.

---

## 👥 Actors Involved

1. **Guest**

   * Registers an account
   * Logs in
   * Updates profile
   * Searches for properties
   * Makes bookings
   * Cancels bookings
   * Makes payments
   * Leaves reviews
   * Sends/receives messages

2. **Host**

   * Registers an account
   * Logs in
   * Updates profile
   * Adds/edit/deletes property listings
   * Manages availability
   * Responds to reviews
   * Views payouts
   * Sends/receives messages

3. **Admin**

   * Logs in
   * Monitors platform activity
   * Manages users, properties, payments, reviews, and bookings
   * Sends system notifications

4. **Payment Service** (External Actor)

   * Processes payments
   * Triggers payout to host

5. **Email Service** (External Actor)

   * Sends booking confirmations, cancellations, and notification emails

---

## 🧩 Key Use Cases Covered

* User Registration & Login
* Role-based access (guest, host, admin)
* Profile management
* Property listing management
* Property search and filtering
* Booking workflow (create, cancel)
* Payment handling and confirmation
* Review and rating submissions
* Admin-level control and system monitoring

---

## 📌 Deliverable

**File:** `airbnb-use-case-diagram.png`
**Location:** `use-case-diagram/`

This file is a visual representation created in Draw\.io (or diagrams.net) and illustrates all key interactions across system roles.

---