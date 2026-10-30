# Rental Tracker: Kayak & Mountain Bike Rental Management

A Java-based management tool that helps tourism companies organize and track kayak and mountain bike rentals, making it safer, easier, and faster to locate equipment, contact renters, and communicate changes.

> **Course:** Software Engineering | **Status:** Planning / Requirements phase

## Team Members

| Name | Role | GitHub |
|------|------|--------|
| Zachery Bugden | Project Lead | @Zach-Bug |
| Chase Caines | Developer | ChaseCCaines |

## Problem Statement

Tourism companies that offer daily or multi-day kayak and mountain bike rentals often track equipment on paper, spreadsheets, or memory. This makes it hard to know what is available, where equipment is, who has it, and who to contact when plans or conditions change (weather, closures, late returns). Rental Tracker centralizes this information to make locating and retrieving equipment safer, easier, and faster.

## Stakeholders

- **Rental shop staff / owners:** primary users who manage inventory, bookings, and returns.
- **Tour and rental company managers:** need an overview of utilization and overdue items.
- **Renters (customers):** benefit indirectly through faster check-out and quick communication about changes or safety issues.
- **Safety / operations personnel:** need to know who is out on the water or trails and when they are due back.

See [docs/RequirementsSpecification.md](docs/RequirementsSpecification.md) for the full stakeholder analysis.

## Key Features

1. **Rental listings:** view all available and unavailable kayaks and bikes.
2. **Rental calendar:** see when items were rented and for how long.
3. **Renter information:** store contact details so renters can be reached when needed.
4. **Accessory tracking:** record extra items taken out (maps, pumps, paddles, helmets, etc.).
5. **Overdue alerts & change notices:** flag late returns and communicate changes to affected renters.

## Technologies

- **Language:** Java (JDK 17+)
- **Build tool:** Maven *(planned)*
- **Testing:** JUnit 5 *(planned)*

## Repository Structure

```
rental-tracker/
├── README.md
├── .gitignore
├── docs/
│   ├── RequirementsSpecification.md   # Functional & non-functional requirements
│   ├── RiskRegister.md                # Project risks and mitigations
│   └── ProductBacklog.md              # Prioritized, traceable backlog
├── UserStories/
│   └── UserStories.md                 # 15 user stories with acceptance criteria
├── Diagrams/
│   ├── UseCaseDiagram.drawio          # UML use case diagram (whole system)
│   └── ActivityDiagrams/              # UML activity diagrams (.drawio)
└── src/
    ├── main/java/com/rentaltracker/   # Application source code
    └── test/java/com/rentaltracker/   # Unit tests
```

## Documentation

| Document | Description |
|----------|-------------|
| [Requirements Specification](docs/RequirementsSpecification.md) | Functional and non-functional requirements |
| [Risk Register](docs/RiskRegister.md) | Identified project risks |
| [Product Backlog](docs/ProductBacklog.md) | Initial backlog linked to requirements |
| [User Stories](UserStories/UserStories.md) | 15 user stories with acceptance criteria |
| [Diagrams](Diagrams/README.md) | Use case diagram and activity diagrams (draw.io XML) |

## Getting Started

Implementation has not started yet. Build and run instructions will be added in `src/` as development begins.
