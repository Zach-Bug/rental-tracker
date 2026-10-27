# Diagrams

All diagrams are UML and are saved as draw.io / diagrams.net XML (`.drawio`) so they can be version-controlled and edited.

| File | Type | Covers |
|------|------|--------|
| [UseCaseDiagram.drawio](UseCaseDiagram.drawio) | Use case diagram (one diagram for the whole system) | All 15 stories in [UserStories.md](../UserStories/UserStories.md); use case names match the story titles |
| [ActivityDiagrams/AD-01_CreateRentalBooking.drawio](ActivityDiagrams/AD-01_CreateRentalBooking.drawio) | Activity diagram | US-06 (conflict detection, FR-2.1, FR-2.2, FR-1.6) |
| [ActivityDiagrams/AD-02_CheckOutRental.drawio](ActivityDiagrams/AD-02_CheckOutRental.drawio) | Activity diagram | US-09, US-10 (check-out and accessories, FR-2.5, FR-4.2 to FR-4.5) |
| [ActivityDiagrams/AD-03_CheckInRental.drawio](ActivityDiagrams/AD-03_CheckInRental.drawio) | Activity diagram | US-11 (check-in and accessory condition, FR-2.5, FR-4.6) |
| [ActivityDiagrams/AD-04_MonitorOverdueRentals.drawio](ActivityDiagrams/AD-04_MonitorOverdueRentals.drawio) | Activity diagram | US-13 (overdue flagging, FR-5.1, FR-5.2, NFR-3.3) |
| [ActivityDiagrams/AD-05_SendChangeNotice.drawio](ActivityDiagrams/AD-05_SendChangeNotice.drawio) | Activity diagram | US-15 (change notices, FR-5.3, FR-5.4) |

## Opening and editing

- Go to <https://app.diagrams.net> and choose **Open Existing Diagram**, or use the draw.io extension in VS Code / IntelliJ.
- To add images to a README or report: **File > Export as > PNG** (or SVG/PDF).

## UML notation used

**Use case diagram**
- Stick figures are actors; ovals are use cases; the large rectangle is the system boundary.
- Solid lines are associations; the hollow-triangle arrow is generalization (Manager is a Staff Member).
- Dashed arrows labeled `<<extend>>` point from the optional use case to the base use case.

**Activity diagram**
- Solid black circle = initial node; circle with inner dot = activity final.
- Rounded rectangle = action; diamond = decision (with `[guard]` labels) or merge.
- Thick black bar = fork / join (parallel actions in AD-02).
- Swimlanes show who performs each action.
