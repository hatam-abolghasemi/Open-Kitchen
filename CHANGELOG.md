# Changelog

All notable changes to Open Kitchen are documented here. Versions follow the [versioning policy](CONTRIBUTING.md#versioning).

## [Unreleased]

## [1.0.2] - 2026-10-28

### Added

- Ranked values replace the goals: reliability, happiness, action, distribution, low maintenance. The higher one wins a collision.
- Rotation cohorts: engineers rotate in different months, and moves balance inside each cohort.
- Rotation rankings: engineers rank the groups they'd like to join.
- Handover window and newcomer on-call wait.
- Borrowing: a short-handed group can borrow an engineer for up to 4 weeks with both gateways' agreement.
- Work spanning several groups is owned by whoever starts it.
- People section: changelog items name who did them, a paragraph per engineer leaving a group, and a monthly one-question team pulse.
- Minimum turnout for votes; only people a group's work affects vote.
- Templates: objection field in change requests, cohorts in the team record, handover in the recipe, SLOs, turnout, pulse and borrowing in the weekly summary.

### Changed

- Core rule: sustained unreliability (missed SLOs or a repeated incident) now forces a review, like sustained unhappiness.
- Between groups: the owning group decides change requests within 3 working days, and no answer means agreed. The team vote is removed.
- Recipes are renewed once a year instead of every rotation.
- No rotation happens during a change freeze.
- Releases are cut from this file: renaming `[Unreleased]` to `[X.Y.Z] - YYYY-MM-DD` and pushing to main runs the docs checks, then tags `vX.Y.Z` and creates the GitHub release with that section as notes.
- Docs checks run only on pushes to main, not on pull requests.
- Renamed counters to groups.
- Renamed charters to recipes, and `templates/charter.md` to `templates/recipe.md`.

## [1.0.1] - 2026-10-11

Plain language. No change in behavior.

### Changed

- Dropped the kitchen metaphor everywhere except the name and the counters: the brigade is now the DevOps team, chefs are engineers, regulars are partners, the family meal is internal work, the test kitchen is R&D, and house standards are standards.
- Removed the kitchen-to-model mapping table and the kitchen column from the concerns table.
- Renamed `templates/brigade.md` to `templates/team.md` (the team record) and `house-standards/` to `standards/`.
- Shortened all docs.

## [1.0.0] - 2026-10-11

First public version.

### Added

- The model: the tech organization as one kitchen, product teams cooking the dishes, and the DevOps team as the brigade running the counters every dish passes through; scope, goal, principles, counters and concerns, chefs and rotation, regulars, Rules 1–4, between counters, on-call, emergency changes, change freezes, the manager.
- Who the counters work for: every dish, and the brigade itself through the family meal.
- House standards and the test kitchen: every kitchen names its manifesto, every counter keeps its standards gap visible, and R&D works to close it.
- Scaling: how chefs spread across counters in small, medium and large brigades, when a crowded counter splits, and how a short-handed counter gets chefs.
- Core rules and defaults, separated so brigades know what they may tune.
- Measuring value: brigade health, DORA delivery metrics and business value in four currencies, a reporting rhythm for the manager and peers, and how the model pairs with the adidas DevOps Maturity Framework and the CNCF Platform Engineering Maturity Model.
- Adoption guide: team-level questions, charter questions with suggested answers, rollout plan.
- Questions and open challenges.
- Sample house standards: the author's DevOps manifesto (17 beliefs) and principles.
- Templates: brigade record, counter charter, weekly changelog, weekly manager summary, monthly value report, change request.

[1.0.2]: https://github.com/hatam-abolghasemi/open-kitchen/releases/tag/v1.0.2
[1.0.1]: https://github.com/hatam-abolghasemi/open-kitchen/releases/tag/v1.0.1
[1.0.0]: https://github.com/hatam-abolghasemi/open-kitchen/releases/tag/v1.0.0
