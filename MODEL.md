# The Open Kitchen Model

## Scope

Open Kitchen governs the DevOps team only. Other teams organize themselves their own way.

## Goals

In this order:

1. The system stays up.
2. Everyone is happy: the team and the people it works with.
3. Conflicts are settled by agreed rules, not politics.

## Principles

1. Production comes first. No rule may block operations.
2. Every repository and tool belongs to exactly one group.
3. Each group makes its own rules.
4. Outsiders don't dictate to a group; they vote happy or unhappy.
5. Only sustained unhappiness forces a group to review its work.
6. Everything is visible.
7. Every group delivers every week.
8. The team invests in its own tooling and R&D, not only in requests.

## Groups

A group handles one concern. Engineers belong to the team, not to a group.

| Group | Concern | Example tools |
| --- | --- | --- |
| Networking | Routing, load balancing, DNS, proxies | HAProxy, Envoy, CoreDNS |
| Orchestration | Containers and orchestrators | Kubernetes, KEDA |
| Observability | Metrics, logs, traces | Prometheus, Grafana, Loki |
| Data | Storage and messaging | Ceph, Redis, RabbitMQ |
| Security | Secrets, policy, identity | Vault, Keycloak, Kyverno |
| CI/CD | Build, test, delivery | GitLab, Argo CD, SonarQube |
| Others | Anything without a concern yet | Chat, video conferencing |

Repositories follow concerns: `<team>/<concern>/<tool>-<environment>`, for example `devops/networking/haproxy-prd`.

**Placing a new tool:** if the tool were removed, what need would remain? Place it at that need's group. No match goes to Others. When several tools at Others share a need, it becomes a new group.

## Rotation

- Every engineer works at several groups.
- Each rotation, exactly one of each engineer's groups changes. Everyone rotates.
- A published scheme decides who moves where.
- New engineers join at the rotation point.

## Partners

Partners are specialists from other teams who work at a group, such as a DBA at Data. They read changelogs, vote, and are consulted on changes that affect them. They don't write a group's rules.

## Standards and R&D

The team adopts a written manifesto ([sample](standards/MANIFESTO.md)). Each group keeps a visible list of where it falls short: its **standards gap**. R&D works to close it. Experiments stay out of production until proven, and every result is published.

## Rule 1: Minimum weekly output

Each group sets a weekly minimum in its rules and delivers it no matter what. It decides what counts.

## Rule 2: Each group writes its own rules

Each group writes a [rules](templates/rules.md): how it decides, who leads, how work is shared. Nobody outside approves it. It is renewed every rotation.

## Rule 3: Weekly changelog and voting

Each group publishes a [weekly changelog](templates/weekly-changelog.md). Anyone can vote thumbs up or down. Only cast votes count.

If unhappiness stays above the threshold:

1. The group holds an open session.
2. If it continues, the group reviews its workflow and publishes the changes.
3. If it still continues, the rest of the team writes that group's rules until it recovers.

## Rule 4: One gateway per group

Each group has one contact person, permanent or rotating weekly or monthly, never daily. The gateway takes requests, assigns them and closes them. Requests spanning several groups are split and tracked by the gateway that received them.

## Between groups

Changing another group's tools needs its agreement through a [change request](templates/change-request.md). If groups can't agree, the whole team votes.

## On-call and incidents

- Each group publishes a monthly on-call list.
- Whoever picks up an alert owns the incident and pulls in others as needed.
- Emergency fixes skip the process and appear in the next changelog.
- Outsiders may change a group's tools only during an incident, if its on-call engineer is unreachable. They report it right away, and the group may revert it.

## Change freezes

SRE or the manager can freeze changes before big events. Only incident fixes go to production.

## The manager

Manager decisions are followed; overrides are noted in the changelog. The manager gets a weekly summary and a monthly value report ([MEASURING.md](MEASURING.md)).

## Scaling

| Team size | Groups per engineer | On-call |
| --- | --- | --- |
| Small (2–6) | All | One shared list |
| Medium (7–20) | 2–3 | Per group or shared |
| Large (20+) | 2–3 | Per group |

A group with too many engineers splits into two concerns. A short-handed group gets more engineers. Changes happen at the rotation point.

## Core rules

Changing any of these means you're no longer running Open Kitchen.

- Governs the DevOps team only.
- One group per concern; one group per tool.
- Each group writes its own rules.
- One group per engineer changes each rotation.
- Only sustained unhappiness forces a review.
- Weekly changelog and minimum output.
- One gateway per group.
- Visible standards gap.
- Monthly value report.
- Manager decisions are followed.

## Defaults

Tune these in your [team record](templates/team.md).

| Default | Value |
| --- | --- |
| Rotation period | 6 months |
| Unhappiness threshold | Over 80% thumbs down |
| Trigger period | 3 weeks in a row |
| Emergency wait | 15 minutes |
| Emergency change review | 1 working day |
| Group split size | Over 8 engineers |
