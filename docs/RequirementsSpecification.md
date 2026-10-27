# Requirements Specification

**Project:** Rental Tracker (Kayak & Mountain Bike Rental Management)
**Version:** 1.0 | **Status:** Draft

## 1. Introduction

### 1.1 Problem Statement
Tourism companies offering daily or multi-day kayak and mountain bike rentals need a reliable way to organize and track equipment. Without one, locating equipment, knowing who has it, and communicating changes (weather, closures, late returns) is slow and error-prone, which affects both efficiency and safety.

### 1.2 Scope
**In scope:** equipment inventory, rental booking and calendar, renter contact records, accessory tracking, overdue detection and change notifications, and basic reports.
**Out of scope (initial release):** online payments, customer-facing booking website, GPS hardware integration, multi-company (multi-tenant) hosting.

### 1.3 Stakeholder Analysis

| Stakeholder | Description | Needs |
|-------------|-------------|-------|
| Rental shop staff | Day-to-day users | Fast check-out/check-in, clear availability, easy lookup of renters |
| Owners / managers | Run the rental business | Overview of utilization, overdue items, accessory losses |
| Renters | Customers | Quick contact about changes, smooth rental process |
| Safety / operations staff | Responsible for people on water or trails | Know who is out, what they have, and when they are due back |
| Course instructor / TA | Evaluates the project | Clear, traceable requirements and documented process |

### 1.4 Definitions

| Term | Meaning |
|------|---------|
| Rental item | A kayak or mountain bike tracked by the system |
| Accessory | An extra item rented with an item (map, pump, paddle, helmet, etc.) |
| Rental | A booking linking a renter, one or more items, accessories, and a date range |
| Overdue | A rental still checked out after its scheduled return date/time |

## 2. Functional Requirements

Priority uses MoSCoW: **Must**, **Should**, **Could**.

### FR-1: Rental Item Listings (Feature 1)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-1.1 | The system shall allow staff to add a rental item with: unique ID, type (kayak or mountain bike), description/model, size, and condition. | Must |
| FR-1.2 | The system shall allow staff to edit and retire (deactivate) a rental item. | Must |
| FR-1.3 | The system shall display a list of all items showing a status of **Available**, **Rented**, or **Unavailable** (e.g., maintenance). | Must |
| FR-1.4 | The system shall allow staff to filter the item list by type and status. | Should |
| FR-1.5 | The system shall allow staff to search items by ID or description. | Should |
| FR-1.6 | The system shall prevent an item with status Rented or Unavailable from being assigned to a new overlapping rental. | Must |

### FR-2: Rental Calendar and Booking (Feature 2)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-2.1 | The system shall allow staff to create a rental specifying renter, item(s), start date/time, and scheduled end date/time. | Must |
| FR-2.2 | The system shall reject a rental whose date range overlaps an existing rental for the same item and display a conflict message. | Must |
| FR-2.3 | The system shall display a calendar (daily and monthly view) showing which items are rented on which dates and for how long. | Must |
| FR-2.4 | The system shall allow staff to modify or cancel a future rental. | Must |
| FR-2.5 | The system shall record actual check-out and check-in times and update the item's status accordingly. | Must |
| FR-2.6 | The system shall support multi-day rentals of any length from 1 to 30 days. | Should |
| FR-2.7 | The system shall retain a rental history for each item. | Should |

### FR-3: Renter Information (Feature 3)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-3.1 | The system shall allow staff to create a renter record with name, phone number, and email (email optional). | Must |
| FR-3.2 | The system shall validate phone numbers and email addresses for correct format before saving. | Should |
| FR-3.3 | The system shall display a list of current renters with their contact details and the items they currently hold. | Must |
| FR-3.4 | The system shall allow staff to search renters by name or phone number. | Must |
| FR-3.5 | The system shall allow staff to record an emergency contact for a renter. | Could |
| FR-3.6 | The system shall allow staff to edit and delete renter records, and shall prevent deletion of renters with active rentals. | Should |

### FR-4: Accessory Tracking (Feature 4)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-4.1 | The system shall maintain an accessory inventory with type (map, pump, paddle, helmet, life jacket, lock, etc.) and quantity. | Must |
| FR-4.2 | The system shall allow staff to attach accessories to a rental at check-out. | Must |
| FR-4.3 | The system shall display, for each active rental, the list of accessories taken out. | Must |
| FR-4.4 | The system shall update accessory availability counts at check-out and check-in. | Must |
| FR-4.5 | The system shall prevent assigning more accessories than are available. | Should |
| FR-4.6 | The system shall allow staff to mark accessories as returned, damaged, or missing at check-in. | Should |

### FR-5: Overdue Tracking and Change Notifications (Feature 5)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-5.1 | The system shall automatically flag any rental as **Overdue** when the current time passes its scheduled return time and it is not checked in. | Must |
| FR-5.2 | The system shall display a dashboard listing all overdue rentals with renter contact details and items outstanding. | Must |
| FR-5.3 | The system shall allow staff to select one or more active rentals and compose a change notice (e.g., weather, trail closure) addressed to the affected renters. | Should |
| FR-5.4 | The system shall record each notice sent (recipient, timestamp, message) in a log. | Should |
| FR-5.5 | The system shall provide a "currently out" report listing all items, renters, and due-back times for safety purposes. | Must |
| FR-5.6 | The system shall support a summary report of rental counts and item utilization for a chosen date range. | Could |

### FR-6: General / Data Management

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-6.1 | The system shall persist all data so that it is retained after the application is closed. | Must |
| FR-6.2 | The system shall require staff to log in with a username and password before accessing data. | Should |
| FR-6.3 | The system shall allow staff to export the rental list to a CSV file. | Could |

## 3. Non-Functional Requirements

### 3.1 Usability

| ID | Requirement | Measure |
|----|-------------|---------|
| NFR-1.1 | A new staff member shall be able to complete a rental check-out after 15 minutes of training. | Verified by usability test with at least 3 users |
| NFR-1.2 | A standard check-out (existing renter, one item) shall take no more than 6 user actions (clicks/entries). | Counted in testing |
| NFR-1.3 | Error messages shall state what went wrong and how to fix it. | Reviewed against all validation cases |

### 3.2 Reliability

| ID | Requirement | Measure |
|----|-------------|---------|
| NFR-2.1 | The system shall not lose committed data upon unexpected shutdown. | 0 lost records in 10 forced-shutdown tests |
| NFR-2.2 | The system shall never double-book an item. | 0 overlapping bookings across automated conflict tests |
| NFR-2.3 | The system shall perform automatic data backup at least once per day. | Backup file present with each day's timestamp |

### 3.3 Performance

| ID | Requirement | Measure |
|----|-------------|---------|
| NFR-3.1 | Item list, search, and calendar views shall load within 2 seconds with up to 500 items and 5,000 rentals. | Timed in testing |
| NFR-3.2 | Creating or updating a rental shall complete within 1 second. | Timed in testing |
| NFR-3.3 | The overdue check shall run at least every 5 minutes. | Verified via logs |

### 3.4 Maintainability

| ID | Requirement | Measure |
|----|-------------|---------|
| NFR-4.1 | Code shall be organized into separate layers (UI, business logic, data access). | Verified in code review |
| NFR-4.2 | Core business logic shall have at least 70% unit-test line coverage. | Coverage report |
| NFR-4.3 | All public classes and methods shall have Javadoc comments. | Checked by Javadoc build warnings |
| NFR-4.4 | The codebase shall follow a consistent style guide (e.g., Google Java Style). | Linter reports 0 errors |

### 3.5 Security

| ID | Requirement | Measure |
|----|-------------|---------|
| NFR-5.1 | Passwords shall be stored hashed (never in plain text). | Verified by inspecting stored data |
| NFR-5.2 | Renter personal data (names, phone, email) shall only be accessible to authenticated users. | Verified via access tests |
| NFR-5.3 | The system shall validate and sanitize all user input to prevent injection into stored data or queries. | Injection test cases pass |

### 3.6 Accessibility

| ID | Requirement | Measure |
|----|-------------|---------|
| NFR-6.1 | The UI shall be fully operable with keyboard only. | Manual test of all main workflows |
| NFR-6.2 | Text/background color contrast shall meet WCAG 2.1 AA (4.5:1 for body text). | Contrast checker |
| NFR-6.3 | Status shall not be conveyed by color alone (text label or icon also shown). | Visual review |

### 3.7 Portability and Compatibility

| ID | Requirement | Measure |
|----|-------------|---------|
| NFR-7.1 | The application shall run on Windows, macOS, and Linux with JDK 17 or later. | Run on all three in testing |

## 4. Requirements Traceability Overview

| Key Feature | Requirements |
|-------------|--------------|
| Listings of available/unavailable rentals | FR-1.x |
| Calendar of rentals and durations | FR-2.x |
| Renter information list | FR-3.x |
| Items/accessories on rental | FR-4.x |
| Overdue tracking and communication of changes (safety) | FR-5.x |

Backlog items that implement these requirements are listed in [ProductBacklog.md](ProductBacklog.md).
