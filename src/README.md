# Source Code

Java source lives under `src/main/java/com/rentaltracker/` and tests under `src/test/java/com/rentaltracker/`.

Planned package layout (see NFR-4.1):

- `model`: domain classes (RentalItem, Renter, Rental, Accessory)
- `service`: business logic (booking, conflict detection, overdue checks)
- `repository`: data persistence
- `ui`: user interface

Implementation begins in Sprint 1 (see [Product Backlog](../docs/ProductBacklog.md)).
