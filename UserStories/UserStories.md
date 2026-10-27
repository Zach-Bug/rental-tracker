# User Stories

**Project:** Rental Tracker (Kayak & Mountain Bike Rental Management)

User stories follow the format **"As a ... I want ... so that ..."**. Each story is traced to the requirements in [RequirementsSpecification.md](../docs/RequirementsSpecification.md) and the items in [ProductBacklog.md](../docs/ProductBacklog.md). Use case names in the [use case diagram](../Diagrams/UseCaseDiagram.drawio) mirror the story titles below.

## Actors

| Actor | Description |
|-------|-------------|
| Staff Member | Rental shop employee who handles bookings, check-out/check-in, and renter records |
| Manager | A Staff Member with additional rights to manage inventory and monitor the business (inherits all Staff Member use cases) |
| Safety Coordinator | Person responsible for knowing who is out on the water or trails and for responding to incidents |
| Renter | Customer who rents equipment; receives change notices (does not use the software directly) |
| System Clock | Timer that triggers the automatic overdue check |

## Summary

| ID | Title | Primary Actor | Priority | Points | Requirements | Backlog | Activity Diagram |
|----|-------|---------------|----------|--------|--------------|---------|------------------|
| US-01 | Log In | Staff Member | Should | 5 | FR-6.2, NFR-5.1, NFR-5.2 | PB-16 | |
| US-02 | Manage Rental Items | Manager | Must | 3 | FR-1.1, FR-1.2 | PB-01 | |
| US-03 | View Item Availability | Staff Member | Must | 5 | FR-1.3, FR-1.4, FR-1.5 | PB-02, PB-14 | |
| US-04 | Register Renter | Staff Member | Must | 3 | FR-3.1, FR-3.2 | PB-04 | |
| US-05 | Search Renters and View Contact Details | Staff Member | Must | 3 | FR-3.3, FR-3.4 | PB-05 | |
| US-06 | Create Rental Booking | Staff Member | Must | 8 | FR-2.1, FR-2.2, FR-1.6, NFR-2.2 | PB-06 | [AD-01](../Diagrams/ActivityDiagrams/AD-01_CreateRentalBooking.drawio) |
| US-07 | Modify or Cancel Rental | Staff Member | Must | 3 | FR-2.4 | PB-09 | |
| US-08 | View Rental Calendar | Staff Member | Must | 8 | FR-2.3 | PB-08 | |
| US-09 | Check Out Rental | Staff Member | Must | 5 | FR-2.5, FR-4.4 | PB-07 | [AD-02](../Diagrams/ActivityDiagrams/AD-02_CheckOutRental.drawio) |
| US-10 | Attach Accessories to Rental | Staff Member | Must | 5 | FR-4.2, FR-4.3, FR-4.4, FR-4.5 | PB-11 | [AD-02](../Diagrams/ActivityDiagrams/AD-02_CheckOutRental.drawio) |
| US-11 | Check In Rental | Staff Member | Must | 5 | FR-2.5, FR-4.6 | PB-07, PB-17 | [AD-03](../Diagrams/ActivityDiagrams/AD-03_CheckInRental.drawio) |
| US-12 | Manage Accessory Inventory | Manager | Must | 3 | FR-4.1 | PB-10 | |
| US-13 | Monitor Overdue Rentals | Manager | Must | 5 | FR-5.1, FR-5.2, NFR-3.3 | PB-12 | [AD-04](../Diagrams/ActivityDiagrams/AD-04_MonitorOverdueRentals.drawio) |
| US-14 | View Currently Out Report | Safety Coordinator | Must | 3 | FR-5.5 | PB-13 | |
| US-15 | Send Change Notice | Staff Member | Should | 5 | FR-5.3, FR-5.4 | PB-15 | [AD-05](../Diagrams/ActivityDiagrams/AD-05_SendChangeNotice.drawio) |

---

## US-01: Log In
**As a** staff member,
**I want** to log in with my username and password,
**so that** only authorized people can see renter information and change rental data.

**Acceptance Criteria**
1. Given valid credentials, when I log in, then I am taken to the main screen.
2. Given invalid credentials, when I log in, then I see an error message and remain on the login screen.
3. Given three consecutive failed attempts, then a warning message is displayed.
4. Passwords are stored hashed and never displayed in plain text.
5. No data screens can be reached without logging in.

## US-02: Manage Rental Items
**As a** manager,
**I want** to add, edit, and retire kayaks and mountain bikes,
**so that** the inventory always reflects the equipment the company actually owns.

**Acceptance Criteria**
1. Given a unique ID, type (kayak or bike), model, size, and condition, when I save, then the item appears in the item list.
2. Given an ID that already exists, when I save, then the system rejects it with a clear message.
3. Given an existing item, when I edit and save its details, then the changes are shown in the list.
4. Given an item I retire, then it no longer appears as bookable but its rental history is kept.

## US-03: View Item Availability
**As a** staff member,
**I want** to see a list of all items with their status, and filter or search it,
**so that** I can quickly tell a customer what is available.

**Acceptance Criteria**
1. The list shows every active item with a status of Available, Rented, or Unavailable.
2. Status is shown as text (not by color alone).
3. I can filter by type and by status, and combine both filters.
4. I can search by item ID or description and results appear within 2 seconds for up to 500 items.

## US-04: Register Renter
**As a** staff member,
**I want** to record a renter's name, phone number, and email,
**so that** I can contact them if there is a problem or a change.

**Acceptance Criteria**
1. Name and phone number are required; email is optional.
2. Given a phone number or email in an invalid format, when I save, then the system rejects it and explains the expected format.
3. Given valid details, when I save, then the renter can be selected when creating a rental.

## US-05: Search Renters and View Contact Details
**As a** staff member,
**I want** to search for a renter and see their contact details and current items,
**so that** I can reach them quickly when needed.

**Acceptance Criteria**
1. Searching by part of a name or phone number returns all matching renters.
2. The renter's details show phone, email, and any items they currently hold.
3. A list of all current renters with contact details can be displayed.

## US-06: Create Rental Booking
**As a** staff member,
**I want** to book one or more items for a renter for a date range and be warned about conflicts,
**so that** an item is never double-booked.

**Acceptance Criteria**
1. A booking requires a renter, at least one item, a start date/time, and a scheduled end date/time.
2. Given an item with an overlapping booking, when I try to save, then the system rejects it and shows which booking conflicts.
3. Given back-to-back bookings (one ends when the next starts), then both are accepted.
4. Given an item that is Rented or Unavailable, then it cannot be added to an overlapping booking.
5. Rentals from 1 to 30 days are supported.
6. If the renter does not exist yet, I can register them during booking (see US-04).

## US-07: Modify or Cancel Rental
**As a** staff member,
**I want** to change or cancel a future booking,
**so that** the schedule stays accurate when customer plans change.

**Acceptance Criteria**
1. Given a future booking, when I change the dates or items, then conflict detection runs again before saving.
2. Given a canceled booking, then the items become available for those dates.
3. Given a booking already checked out, then it cannot be canceled (it can only be checked in).

## US-08: View Rental Calendar
**As a** staff member,
**I want** a calendar showing which items are rented and for how long,
**so that** I can plan ahead and answer availability questions for future dates.

**Acceptance Criteria**
1. Daily and monthly calendar views are available.
2. Each rental shows the item, the renter, and the dates it spans.
3. Multi-day rentals appear on every day they cover.
4. The calendar loads within 2 seconds with up to 5,000 rentals.

## US-09: Check Out Rental
**As a** staff member,
**I want** to record when equipment leaves the shop,
**so that** the system knows what is out and the item status is correct.

**Acceptance Criteria**
1. Given a booked rental, when I check it out, then the actual check-out time is recorded and each item's status changes to Rented.
2. A rental that is already checked out or completed cannot be checked out again.
3. A standard check-out (existing booking, one item) takes no more than 6 user actions.
4. A confirmation is displayed after a successful check-out.

## US-10: Attach Accessories to Rental
**As a** staff member,
**I want** to record accessories (maps, pumps, paddles, helmets, etc.) taken out with a rental,
**so that** we know what extra equipment each renter has and can get it back.

**Acceptance Criteria**
1. At check-out I can add accessories by type and quantity.
2. Given a quantity greater than what is available, then the system blocks it and displays a shortage message.
3. Available accessory counts decrease when the rental is checked out.
4. Each active rental displays the list of its accessories.

## US-11: Check In Rental
**As a** staff member,
**I want** to record the return of items and accessories and their condition,
**so that** inventory and availability stay accurate.

**Acceptance Criteria**
1. Given an active rental, when I check it in, then the actual check-in time is recorded and each item's status changes to Available.
2. For each accessory I can mark Returned, Damaged, or Missing.
3. Returned accessories are added back to the available counts; damaged or missing ones are not.
4. The rental is marked Completed and is kept in the item's history.

## US-12: Manage Accessory Inventory
**As a** manager,
**I want** to add accessory types and set quantities,
**so that** the system knows how many of each accessory we own.

**Acceptance Criteria**
1. I can add accessory types (e.g., map, pump, paddle, helmet) with a quantity.
2. I can edit quantities and the list shows total and currently available counts.
3. A quantity cannot be set below the number currently out on rentals.

## US-13: Monitor Overdue Rentals
**As a** manager,
**I want** overdue rentals to be flagged automatically and shown on a dashboard,
**so that** I can follow up with renters quickly.

**Acceptance Criteria**
1. The system checks for overdue rentals at least every 5 minutes (triggered by the System Clock).
2. A rental whose scheduled end has passed and which is not checked in is flagged Overdue.
3. The dashboard lists each overdue rental with renter phone, email, and items and accessories outstanding.
4. When a flagged rental is checked in, it is removed from the overdue list.

## US-14: View Currently Out Report
**As a** safety coordinator,
**I want** a list of every item currently out, who has it, and when it is due back,
**so that** I know who to look for if weather or conditions become dangerous.

**Acceptance Criteria**
1. The report lists all checked-out items with renter name, contact number, accessories, and due-back time.
2. The report fits on one screen or can be printed.
3. The report reflects check-outs and check-ins immediately.

## US-15: Send Change Notice
**As a** staff member,
**I want** to select active rentals and send a notice about a change (weather, trail closure, schedule change),
**so that** affected renters are informed quickly and we have a record of it.

**Acceptance Criteria**
1. I can select one or more active rentals and write a message.
2. Before sending, the system shows the recipients and a preview, and I must confirm.
3. After confirmation, the notice is logged with recipient, timestamp, and message.
4. The notice log can be viewed later.

---

## Traceability to Diagrams

- **Use case diagram:** [Diagrams/UseCaseDiagram.drawio](../Diagrams/UseCaseDiagram.drawio) (one diagram covering all 15 stories).
- **Activity diagrams:** see [Diagrams/ActivityDiagrams](../Diagrams/ActivityDiagrams) and the summary table above.
