# Measuring Value

Three layers, each for a different audience.

## 1. Team health

| Signal | Measure |
| --- | --- |
| Minimum output | Weeks met ÷ weeks |
| Happiness | Thumbs up ÷ cast votes |
| Internal work | Share of output for the team itself |
| R&D | Experiments finished per month |
| Standards gap | Open items per group |
| Gateway response | Time to acknowledge requests |

## 2. Delivery (DORA)

| Metric | Measures |
| --- | --- |
| Deployment frequency | How often changes reach production |
| Change lead time | Commit to production |
| Failed deployment recovery time | Time to recover from a failed deploy |
| Change failure rate | Share of deploys needing a fix |
| Deployment rework rate | Share of deploys that were unplanned fixes |

Add reliability: share of time each service meets its SLOs. Compare a group only with its own past.

## 3. Business value

Every notable change names a currency and a number.

| Currency | Example |
| --- | --- |
| Money | Infrastructure cost, savings |
| Time | Lead time, toil hours removed |
| Risk | Incidents, SLO breaches, single points of failure |
| Customer experience | Availability, user-facing latency |

"Moved old metrics to object storage" is unfinished. "Moved old metrics to object storage: €400/month saved" is done.

## Reports

| Rhythm | Report | Audience |
| --- | --- | --- |
| Weekly | [Changelog](templates/weekly-changelog.md) | Everyone |
| Weekly | [Summary](templates/weekly-summary.md) | Manager |
| Monthly | [Value report](templates/value-report.md) | Manager and peers |
| Quarterly | Maturity review | Team and manager |

## Maturity

Use an existing framework, such as the [adidas DevOps Maturity Framework](https://github.com/adidas/adidas-devops-maturity-framework) or the [CNCF Platform Engineering Maturity Model](https://tag-app-delivery.cncf.io/whitepapers/platform-eng-maturity-model/). Gaps become standards-gap items.

## Starting from nothing

1. Month 1: log deploys, rollbacks, incidents and costs by hand.
2. Month 2: label hotfixes and change-caused incidents.
3. Month 3: automate collection and send the first value report.
