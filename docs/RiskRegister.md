# Risk Register

**Project:** Rental Tracker | **Team:** Zachery Bugden (Project Lead), Chase Caines (Developer) | **Rating scale:** Low / Medium / High for both Probability and Impact

| ID | Category | Risk Description | Probability | Impact | Mitigation Strategy | Owner |
|----|----------|------------------|-------------|--------|---------------------|-------|
| R-01 | Scope | Scope creep: adding features (payments, GPS, web booking) beyond the five core features. | High | High | Maintain a prioritized backlog (MoSCoW); only add items after team review; keep out-of-scope list in the requirements doc. | Zachery |
| R-02 | Technical | Double-booking bugs due to incorrect date-overlap logic. | Medium | High | Implement overlap check early with thorough unit tests (edge cases: same-day, back-to-back, multi-day). | Chase |
| R-03 | Knowledge gap | Team lacks experience with chosen Java UI framework (Swing/JavaFX) or persistence library. | Medium | Medium | Build a small prototype in Sprint 1; assign learning tasks; use official tutorials; choose the simplest suitable technology. | Zachery, Chase |
| R-04 | Schedule | Underestimating effort, so features are not finished by the course deadline. | High | High | Use story points with velocity tracking; plan sprints for a two-person capacity; prioritize Must items first and move Should/Could items out if velocity is low; reserve the last sprint for testing and buffer. | Zachery |
| R-05 | Team coordination | Merge conflicts or unclear responsibilities when several members edit the same code. | Medium | Medium | Use feature branches and pull requests (each person reviews the other's); short-lived branches; assign backlog items to Zachery or Chase; short weekly check-ins. | Zachery, Chase |
| R-06 | Team coordination | One of the two team members becomes unavailable (illness, other course workload). | Medium | High | With only two team members, each person must understand the whole codebase: review each other's pull requests, document design decisions, and keep Must-have items small enough for either person to finish. | Zachery |
| R-07 | Data | Data loss or corruption in the persistence layer. | Low | High | Use transactions or atomic writes; daily backup (NFR-2.3); test forced-shutdown recovery. | Chase |
| R-08 | Security / privacy | Exposure of renters' personal information (name, phone, email). | Low | High | Require login; hash passwords; store only needed data; do not commit real data to the repository. | Chase |
| R-09 | Requirements | Requirements are ambiguous or misunderstood, leading to rework. | Medium | Medium | Review requirements as a team; write acceptance criteria; confirm with instructor/TA or a real rental operator if possible. | Zachery |
| R-10 | Quality | Insufficient testing leads to defects found late. | Medium | High | Write unit tests alongside features; target 70% coverage; define "done" to include tests; set up CI to run tests. | Zachery |
| R-11 | Technical | Notification feature (email/SMS) relies on external services that may be unavailable or complex to integrate. | Medium | Medium | Start with an in-app notice log and "copy message" workflow; add email later as a Could-have using a simple library. | Chase |
| R-12 | Tooling | Build/environment differences across team machines (JDK version, IDE) cause "works on my machine" issues. | Medium | Low | Standardize on JDK 17 and Maven; document setup in README; commit build files. | Zachery, Chase |
| R-13 | Usability | Staff find the UI confusing, reducing real-world value. | Low | Medium | Do early paper/low-fidelity prototypes; run a quick usability test with 3 users before final release. | Zachery |

## Review Process

The register will be reviewed at the start of each sprint. Risks will be re-rated and new risks added as the project progresses.
