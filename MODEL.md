# The Open Kitchen Model

*A transparent, self-governing management model for DevOps teams of any size.*

Open Kitchen sees the whole tech organization as one kitchen. Product teams cook the dishes: the apps their users get. Every dish passes through the same stations on its way to the guests: data, security, observability, delivery, orchestration, networking. These stations are the counters, and the DevOps team is the brigade that runs them, side by side with specialists from other teams. Every chef in the brigade works several counters, and that set keeps changing. The brigade governs itself and cooks in plain view.

## The kitchen in one table

| In the kitchen | In the model |
| --- | --- |
| The kitchen | The tech organization: everyone who makes the product |
| Dishes | The products: apps and services, as they reach users |
| Guests | End users and the business's customers |
| Cooks | Everyone making dishes, in their own teams: developers, QA, data engineers and more |
| Counters | Stations every dish passes through, one per concern |
| The brigade | The DevOps team, which runs the counters and Open Kitchen |
| Chefs | Members of the brigade |
| Regulars | Specialists from other teams who work at a counter: DBAs, network or security engineers |
| The family meal | Work for the brigade's own needs: its tooling, automation, runbooks and cleanup |
| The test kitchen | The brigade's R&D: better counters at lower cost |
| House standards | The brigade's chosen manifesto: what good work means here |
| A counter's house rules | The counter's charter, written by its chefs |
| Cooking in plain view | The weekly changelog |
| Everyone judging hygiene | Thumbs up / thumbs down on changelogs |
| The chef at the counter | The gateway |
| The kitchen manager | The DevOps manager |
| Service | Production |

## Scope

Open Kitchen governs the brigade, and only the brigade. Product teams organize themselves their own way, usually by business domain, which is the right shape for cooking dishes. The model asks only that their dishes pass through the counters, and invites everyone to watch and judge.

Who counts as a chef depends on the organization. A DBA inside the DevOps team is a chef; a DBA on a separate team is a regular at the Data counter.

## The goal

In this order:

1. **The system stays up and running.**
2. **Everybody is happy:** chefs, regulars and the cooks whose dishes pass through.
3. **Minimum HR issues:** conflicts are settled by rules the chefs chose, not by force, lobbying or politics.

## Principles

1. Production comes first. No rule may block operations.
2. Every repository and tool belongs to exactly one counter.
3. The chefs of each counter make its rules. Nobody else writes them.
4. Nobody outside a counter dictates to it; they judge, happy or unhappy.
5. Only enough unhappiness can force a counter to review its work.
6. Everything is visible.
7. Every counter delivers every week, no matter what.
8. The brigade feeds itself and keeps improving its recipes, not only its menu.

## Counters

A counter is a station, not a team. Chefs belong to the brigade, not to a counter, and all counters stand in the same room. Splitting a DevOps team into fixed groups would rebuild, inside DevOps, the silos DevOps exists to break.

**Every concern has exactly one counter, and every repository and tool belongs to exactly one counter.** The chefs who work a counter are responsible for everything at it.

### Concerns

A concern is a lasting technical need, defined so any tool can be placed against it. Counters are named after their concerns. An example set:

| Counter | What it handles | In the kitchen | Example tools |
| --- | --- | --- | --- |
| Networking | Traffic at any OSI layer: routing, load balancing, DNS, proxies | Getting plates to the right table | HAProxy, Envoy, CoreDNS |
| Orchestration | Containers, images and orchestrators | The ovens and stations | Kubernetes, KEDA |
| Observability | Metrics, logs, traces and monitoring | Tasting during service | Prometheus, Grafana, Loki |
| Data | Persistent storage and messaging | The pantry | Ceph, Redis, RabbitMQ |
| Security | Secrets, policy, identity and access | Food safety | Vault, Keycloak, Kyverno |
| CI/CD | Build, test, delivery and reconciliation | The line from stove to pass | GitLab, Argo CD, SonarQube |
| Others | Tools that don't fit a concern yet | Whatever has no station yet | Chat, video conferencing |

Concerns stay flat. A repository structure that follows them shows each tool's counter without a lookup: `<team>/<concern>/<tool>-<environment>`, for example `devops/networking/haproxy-prd`.

### Placing a new tool

1. **Ask the substitution question:** if this tool were removed, would the need disappear, or just be served worse? Either way, the surviving need is the concern.
2. **Place the tool** at the counter whose concern matches that need.
3. **No match?** Place it at Others rather than opening a one-tool counter.
4. **Promote** a need to its own concern and counter once enough tools at Others share it.

## Chefs and rotation

- **Every chef works several counters.** The overlap keeps knowledge flowing between counters.
- **Every rotation period, exactly one of each chef's counters changes.** Never more, so chefs keep depth in the rest.
- **Every chef rotates.** Nobody is exempt, so no counter hardens into a silo.
- **A published scheme decides who moves where,** never personal choice or influence.
- **New chefs start at the rotation point,** when every charter is renewed.

## Regulars

Regulars are people from other teams who work at a counter: a DBA at Data, a network engineer at Networking, a QA engineer at CI/CD. The brigade cooks with them, not for them.

- Each charter names its counter's regulars and says how the chefs work with them.
- Regulars read every changelog, vote, and are invited to open sessions.
- Changes that affect a regular's work are discussed with them first.
- Regulars don't write a counter's rules, and the brigade's rules (rotation, minimum output) don't bind them.

## Who the counters work for

- **Every dish:** the cooks bringing their dishes through, and through them, the guests.
- **The brigade itself:** the chefs need their own tooling, automation, runbooks, dashboards and cleanup to work well. Restaurants feed their staff before service and call it the family meal. In Open Kitchen it is real work, not leftovers: planned, delivered and shown separately in the changelog so its share stays visible.

## House standards and the test kitchen

**House standards.** The brigade names a written manifesto of what good work means there. Open Kitchen doesn't prescribe one. This repository ships a sample, the author's [DevOps Manifesto](house-standards/MANIFESTO.md) with its [principles](house-standards/PRINCIPLES.md); a brigade may adopt it, change it, or write its own. Each counter keeps a visible list of where it falls short of the standards: its **standards gap**.

**The test kitchen** finds better ways to serve every dish at lower cost, aimed at closing the standards gap.

- Every counter runs the test kitchen and makes room for it in its charter.
- Experiments stay away from production until proven.
- Every result is published, including failures. A failed experiment is a finding.
- A proven result ships, and the standards gap shrinks.

## Rule 1: Minimum weekly output

The chefs of each counter set its minimum output per week, write it in the charter, and deliver it **no matter what**: vacations, incidents, sick days, busy weeks.

- The counter decides what counts: a change, a fix, a runbook, an upgrade, a cleanup, a family-meal task, a test-kitchen result.
- The weekly changelog shows whether the minimum was met.
- How chefs share the work is the counter's business.

## Rule 2: Each counter writes its own rules

The chefs of each counter write its [charter](templates/charter.md): how they decide, who leads, how work is shared, how they work with regulars, and how they stop one chef from dominating. Most counters either **accept a head chef** whose calls they follow, or **agree on decision rules**.

Nobody outside approves the charter. It is published, and renewed at every rotation point.

## Rule 3: Weekly changelog and the happiness signal

Every counter publishes a [weekly changelog](templates/weekly-changelog.md) to the brigade, its regulars and anyone who cooks with it: what it delivered, what it did for the brigade, what the test kitchen found, decisions, incidents, next week's plan, and whether the minimum was met.

- **Anyone can vote** thumbs up or down, no reason needed. The vote measures happiness, not technical quality.
- **Only cast votes count.** Not voting is neither approval nor rejection.
- **Unhappiness above the threshold for the trigger period:** the counter holds an open session to explain its direction and hear complaints.
- **Still above it for another trigger period:** the counter reviews its decisions and workflow, and publishes what it changed.
- **Still unhappy after the review:** the rest of the brigade writes rules for that counter until it is happy again.

## Rule 4: One gateway per counter

- Cooks and regulars always have one chef to talk to at each counter: the gateway.
- The gateway is a permanent chef or a weekly or monthly rotation, **never daily**. Current gateways are listed on one page.
- The gateway takes requests, assigns them and closes the loop, without doing everything personally.
- A request spanning several counters is split by the gateway that receives it, handed to the other gateways, and followed until every part is done.
- Requests come through one shared intake or directly at a counter.

## Between counters

- A counter decides freely about what it handles.
- Changing another counter's tools needs that counter's agreement, through a [change request](templates/change-request.md).
- If two counters can't agree, all chefs vote, and the result is final.

## On-call and incidents

- Each counter publishes its on-call list monthly, covering every day of the month.
- Whoever picks up an alert owns the incident end to end, pulling in other counters' on-call chefs, regulars and the cooks of the affected dish as needed.
- Emergency fixes skip the usual process, then appear in the next changelog.

## Emergency changes from outside

Nobody who doesn't work a counter changes its tools by pressure. Each charter says whether, when and how an outsider, regulars included, may make an emergency change. Without an answer, the default applies:

- Only during an active production incident, and only if the counter's on-call chef can't be reached within the emergency wait.
- The change is reported to the counter's on-call chef and gateway right away.
- The counter reviews it within the review window and may keep, adjust or revert it.

## Change freezes

Whoever the organization trusts with freezes, for example SRE or the manager, can freeze changes across all counters before a big event. During a freeze, only incident fixes reach production and disaster recovery.

## The manager

Like a kitchen manager, the manager runs the business side of the brigade without being one of its chefs. Open Kitchen sets order inside the brigade; it doesn't compete with the organization.

- **Manager decisions are followed.** An override of a counter decision is noted in that counter's changelog.
- **The manager receives a weekly summary** of all changelogs, and the monthly value report described in [Measuring value](MEASURING.md).

## Measuring value

The brigade measures its own health, its delivery performance (DORA) and its business value in four currencies: money, time, risk and customer experience. It reports to the manager and its peers on a fixed rhythm, and pairs with an existing maturity framework instead of inventing one. See [MEASURING.md](MEASURING.md).

## Scaling

Counters follow concerns, so they don't depend on headcount. Size changes how many counters each chef works.

| Brigade size | Counters per chef | Gateways | On-call |
| --- | --- | --- | --- |
| Small (2–6 chefs) | All of them | One chef may take requests for several counters | One shared list |
| Medium (7–20 chefs) | 2–3 | One per counter | Per counter, or shared between quiet counters |
| Large (20+ chefs) | 2–3 | One per counter | Per counter |

- **Small brigades** have little to rotate, since every chef works every counter. Changelogs, votes, gateways and reports still apply, so a brigade grows into the full model without switching systems.
- **A crowded counter splits** past the split size, or when its chefs can't follow all its work: its concern is divided into two concerns with their own counters.
- **A short-handed counter gets chefs,** through the rotation scheme or by chefs taking one more counter. Counters don't merge.
- **Splits and staffing changes happen at the rotation point,** unless production needs them sooner.

## Core rules and defaults

Core rules define the model. Changing one means running something other than Open Kitchen, and changing one here is a major version.

- Open Kitchen governs the brigade only.
- Every concern has exactly one counter; every repository and tool belongs to exactly one counter.
- The chefs of each counter write its rules; everyone else only judges.
- Exactly one of each chef's counters changes per rotation, for every chef, by a published scheme.
- Only cast votes count, and only sustained unhappiness forces a review, in the order of Rule 3.
- Every counter publishes a weekly changelog and delivers its minimum output.
- Every counter has one gateway, never rotating daily.
- The brigade names its house standards, and every counter keeps its standards gap visible.
- The brigade reports its value monthly in business terms.
- Manager decisions are followed.

Defaults are starting values. A brigade may tune them in its [brigade record](templates/brigade.md).

| Default | Value |
| --- | --- |
| Rotation period and charter renewal | 6 months |
| Unhappiness threshold | More than 80% thumbs down |
| Trigger period | 3 weeks in a row |
| Emergency wait before an outsider may act | 15 minutes |
| Review window for an outsider's emergency change | 1 working day |
| Counters per chef (medium and large brigades) | 2–3 |
| Split size of a counter | More than 8 chefs |
| Maturity review | Quarterly |
