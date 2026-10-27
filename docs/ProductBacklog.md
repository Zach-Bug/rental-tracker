# Product Backlog

**Project:** Rental Tracker | **Estimation:** Fibonacci story points (1, 2, 3, 5, 8) | **Priority:** MoSCoW (Must / Should / Could)

Each item links to the requirement(s) in [RequirementsSpecification.md](RequirementsSpecification.md). Acceptance criteria are listed in the details section below the summary table.

## Summary

| ID | User Story (short) | Requirement(s) | Priority | Points | Sprint |
|----|--------------------|----------------|----------|--------|--------|
| PB-01 | Add and edit rental items | FR-1.1, FR-1.2 | Must | 3 | 1 |
| PB-02 | View item list with status | FR-1.3 | Must | 3 | 1 |
| PB-03 | Persist data between sessions | FR-6.1, NFR-2.1 | Must | 5 | 1 |
| PB-04 | Create a renter record | FR-3.1, FR-3.2 | Must | 3 | 2 |
| PB-05 | Search renters and view contact list | FR-3.3, FR-3.4 | Must | 3 | 2 |
| PB-06 | Create a rental with conflict detection | FR-2.1, FR-2.2, FR-1.6, NFR-2.2 | Must | 8 | 2 |
| PB-07 | Check out and check in items | FR-2.5 | Must | 5 | 2 |
| PB-08 | Rental calendar view | FR-2.3 | Must | 8 | 3 |
| PB-09 | Modify or cancel a future rental | FR-2.4 | Must | 3 | 3 |
| PB-10 | Manage accessory inventory | FR-4.1 | Must | 3 | 3 |
| PB-11 | Attach accessories to a rental | FR-4.2, FR-4.3, FR-4.4, FR-4.5 | Must | 5 | 3 |
| PB-12 | Automatic overdue flagging and dashboard | FR-5.1, FR-5.2, NFR-3.3 | Must | 5 | 4 |
| PB-13 | "Currently out" safety report | FR-5.5 | Must | 3 | 4 |
| PB-14 | Filter and search items | FR-1.4, FR-1.5 | Should | 3 | 4 |
| PB-15 | Compose and log change notices | FR-5.3, FR-5.4 | Should | 5 | 4 |
| PB-16 | Staff login | FR-6.2, NFR-5.1, NFR-5.2 | Should | 5 | 5 |
| PB-17 | Record accessory condition at check-in | FR-4.6 | Should | 2 | 5 |
| PB-18 | Rental history per item | FR-2.7 | Should | 2 | 5 |
| PB-19 | Utilization summary report | FR-5.6 | Could | 5 | Backlog |
| PB-20 | Export rentals to CSV | FR-6.3 | Could | 2 | Backlog |
| PB-21 | Emergency contact for renters | FR-3.5 | Could | 1 | Backlog |
| PB-22 | Accessibility pass (keyboard, contrast) | NFR-6.1, NFR-6.2, NFR-6.3 | Should | 3 | 5 |

**Total estimated effort:** 87 points.

## Item Details

### PB-01: Add and edit rental items
**Story:** As a staff member, I want to add and edit kayaks and bikes so that the inventory reflects what we own.
**Requirements:** FR-1.1, FR-1.2
**Acceptance criteria:**
- Given valid ID, type, model, size, and condition, when I save, the item appears in the system.
- Duplicate IDs are rejected with a clear message.
- I can retire an item, and it no longer appears as bookable.

### PB-02: View item list with status
**Story:** As a staff member, I want to see all items and whether each is available or not so I can answer customers quickly.
**Requirements:** FR-1.3
**Acceptance criteria:**
- The list shows every active item with status Available, Rented, or Unavailable.
- Status text is shown (not color only).
- The list loads in under 2 seconds with 500 items.

### PB-03: Persist data between sessions
**Story:** As a staff member, I want my data saved so I do not lose records when the app closes.
**Requirements:** FR-6.1, NFR-2.1
**Acceptance criteria:**
- After closing and reopening, all items, renters, and rentals are present.
- Forced shutdown during a save does not corrupt existing data.

### PB-04: Create a renter record
**Story:** As a staff member, I want to record a renter's contact details so I can reach them if needed.
**Requirements:** FR-3.1, FR-3.2
**Acceptance criteria:**
- Name and phone are required; email is optional.
- Invalid phone or email formats are rejected with an explanatory message.

### PB-05: Search renters and view contact list
**Story:** As a staff member, I want to find a renter and see what they have out so I can contact them.
**Requirements:** FR-3.3, FR-3.4
**Acceptance criteria:**
- Searching by partial name or phone returns matching renters.
- Current renters are listed with phone, email, and items currently held.

### PB-06: Create a rental with conflict detection
**Story:** As a staff member, I want to book items for a date range and be warned about conflicts so I never double-book.
**Requirements:** FR-2.1, FR-2.2, FR-1.6, NFR-2.2
**Acceptance criteria:**
- A rental links a renter, one or more items, a start, and a scheduled end.
- Overlapping bookings for the same item are rejected with a message naming the conflict.
- Back-to-back bookings (end equals start of the next) are allowed.
- Automated tests cover same-day, multi-day, and boundary cases.

### PB-07: Check out and check in items
**Story:** As a staff member, I want to record when equipment leaves and returns so that availability is accurate.
**Requirements:** FR-2.5
**Acceptance criteria:**
- Check-out records the actual time and sets item status to Rented.
- Check-in records the actual time and sets the item to Available.
- A completed rental cannot be checked out again.

### PB-08: Rental calendar view
**Story:** As a staff member, I want a calendar showing which items are rented and for how long so I can plan ahead.
**Requirements:** FR-2.3
**Acceptance criteria:**
- Daily and monthly views are available.
- Each rental displays item, renter, and span of dates.
- Multi-day rentals span all relevant days.

### PB-09: Modify or cancel a future rental
**Story:** As a staff member, I want to change or cancel a booking when customer plans change.
**Requirements:** FR-2.4
**Acceptance criteria:**
- Changes re-run conflict detection.
- Canceled rentals free the item for the dates.
- Rentals already checked out cannot be canceled, only checked in.

### PB-10: Manage accessory inventory
**Story:** As a staff member, I want to track accessory stock so I know what extras are available.
**Requirements:** FR-4.1
**Acceptance criteria:**
- I can add accessory types with quantities and edit quantities.
- The list displays total and currently available counts.

### PB-11: Attach accessories to a rental
**Story:** As a staff member, I want to record which maps, pumps, paddles, and helmets go out with each rental.
**Requirements:** FR-4.2, FR-4.3, FR-4.4, FR-4.5
**Acceptance criteria:**
- Accessories can be added at check-out.
- Available counts decrease at check-out and increase at check-in.
- Requesting more than available is blocked with a message.
- Each active rental shows its accessory list.

### PB-12: Automatic overdue flagging and dashboard
**Story:** As a manager, I want overdue rentals flagged automatically so I can follow up quickly.
**Requirements:** FR-5.1, FR-5.2, NFR-3.3
**Acceptance criteria:**
- Rentals past scheduled return time and not checked in are marked Overdue within 5 minutes.
- The dashboard lists overdue rentals with renter phone, email, and items outstanding.

### PB-13: "Currently out" safety report
**Story:** As safety personnel, I want a list of everyone currently out so I know who to look for if conditions change.
**Requirements:** FR-5.5
**Acceptance criteria:**
- The report lists all checked-out items, renters, accessories, and due-back times.
- The report can be printed or displayed in one screen.

### PB-14: Filter and search items
**Story:** As a staff member, I want to filter by type and status and search by ID so I can find items fast.
**Requirements:** FR-1.4, FR-1.5
**Acceptance criteria:**
- Filtering by type and status can be combined.
- Search by ID or description returns matches in under 2 seconds.

### PB-15: Compose and log change notices
**Story:** As a staff member, I want to send a notice to selected renters (weather, closures) and keep a record of it.
**Requirements:** FR-5.3, FR-5.4
**Acceptance criteria:**
- I can select active rentals and write a message.
- The system shows recipients' contact details for sending and logs recipient, timestamp, and message.
- The notice log is viewable.

### PB-16: Staff login
**Story:** As an owner, I want only authorized staff to access renter data.
**Requirements:** FR-6.2, NFR-5.1, NFR-5.2
**Acceptance criteria:**
- Data screens are inaccessible without valid credentials.
- Passwords are stored hashed.
- Three consecutive failed logins show a warning message.

### PB-17: Record accessory condition at check-in
**Story:** As a staff member, I want to mark accessories returned, damaged, or missing so inventory stays accurate.
**Requirements:** FR-4.6
**Acceptance criteria:**
- At check-in each accessory can be marked Returned, Damaged, or Missing.
- Damaged/missing items are removed from available counts.

### PB-18: Rental history per item
**Story:** As a manager, I want to see an item's rental history to spot heavy use or problems.
**Requirements:** FR-2.7
**Acceptance criteria:**
- Selecting an item shows all past rentals in date order.

### PB-19: Utilization summary report
**Story:** As a manager, I want rental counts and utilization for a date range to guide purchasing decisions.
**Requirements:** FR-5.6
**Acceptance criteria:**
- Given a start and end date, the report shows rentals per item and percentage of days rented.

### PB-20: Export rentals to CSV
**Story:** As a manager, I want to export data for use in spreadsheets.
**Requirements:** FR-6.3
**Acceptance criteria:**
- Export produces a valid CSV opening correctly in a spreadsheet application.

### PB-21: Emergency contact for renters
**Story:** As safety personnel, I want an emergency contact on file in case a renter cannot be reached.
**Requirements:** FR-3.5
**Acceptance criteria:**
- A renter record can store an emergency contact name and phone number, shown on the renter details screen.

### PB-22: Accessibility pass
**Story:** As a staff member with accessibility needs, I want to operate the app by keyboard with readable contrast.
**Requirements:** NFR-6.1, NFR-6.2, NFR-6.3
**Acceptance criteria:**
- All primary workflows can be completed with keyboard only.
- Body text meets 4.5:1 contrast.
- Statuses include text labels.

## Traceability Matrix (Requirement to Backlog)

| Requirement | Backlog Item(s) |
|-------------|-----------------|
| FR-1.1, FR-1.2 | PB-01 |
| FR-1.3 | PB-02 |
| FR-1.4, FR-1.5 | PB-14 |
| FR-1.6 | PB-06 |
| FR-2.1, FR-2.2 | PB-06 |
| FR-2.3 | PB-08 |
| FR-2.4 | PB-09 |
| FR-2.5 | PB-07 |
| FR-2.6 | PB-06 (date range handling) |
| FR-2.7 | PB-18 |
| FR-3.1, FR-3.2 | PB-04 |
| FR-3.3, FR-3.4 | PB-05 |
| FR-3.5 | PB-21 |
| FR-3.6 | PB-04, PB-05 (edit/delete to be split out in a later refinement) |
| FR-4.1 | PB-10 |
| FR-4.2 to FR-4.5 | PB-11 |
| FR-4.6 | PB-17 |
| FR-5.1, FR-5.2 | PB-12 |
| FR-5.3, FR-5.4 | PB-15 |
| FR-5.5 | PB-13 |
| FR-5.6 | PB-19 |
| FR-6.1 | PB-03 |
| FR-6.2 | PB-16 |
| FR-6.3 | PB-20 |
| NFR-2.x | PB-03, PB-06 |
| NFR-5.x | PB-16 |
| NFR-6.x | PB-22 |
