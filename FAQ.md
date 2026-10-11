# Questions and Open Challenges

*What people ask about Open Kitchen, and what the model hasn't solved yet.*

Answered questions explain choices the model already makes. Open challenges are known gaps, with current thinking; bring evidence and ideas to [Discussions](https://github.com/hatam-abolghasemi/open-kitchen/discussions).

## Answered

### Does Open Kitchen manage developers, QA or data teams?

No. The whole tech organization is the kitchen, but the model governs only the brigade, the DevOps team. Product teams cook the dishes and organize themselves their own way; their dishes pass through the counters, and they watch and judge like everyone else. Specialists from other teams who work at a counter are regulars. See [Scope](MODEL.md#scope) and [Regulars](MODEL.md#regulars).

### Isn't the brigade just a ticket queue for other teams?

No. The brigade works with product teams and regulars, not for them as customers. Gateways exist so everyone knows whom to talk to, not to turn collaboration into tickets.

### Is Open Kitchen a maturity model?

No. It is a management model: how a DevOps team organizes, decides, delivers and reports. It pairs with an existing maturity framework, such as the adidas DevOps Maturity Framework, and feeds its gaps into the test kitchen. See [Maturity](MEASURING.md#maturity).

### How does it connect DevOps to the business?

Through three layers: brigade health, delivery (DORA) and business value in four currencies: money, time, risk and customer experience. Every notable change is translated into a currency with a number, and a monthly value report goes to the manager and peers. See [MEASURING.md](MEASURING.md).

### Is this DORA the EU regulation?

No. Here DORA means DevOps Research and Assessment and its software delivery metrics, not the EU's Digital Operational Resilience Act for financial entities.

### Does it replace Scrum, Kanban or Team Topologies?

No. Each counter chooses its own workflow in its charter. In Team Topologies terms, product teams are stream-aligned and the brigade acts as a platform team; Open Kitchen describes how that team runs inside.

### Isn't the happiness vote a popularity contest?

It measures happiness, not quality, and that is intended: unhappy chefs, regulars or product teams are a real signal. A single bad week changes nothing. Only sustained unhappiness forces anything, and the first step is a conversation, not a punishment.

### Doesn't rotation destroy expertise?

Only one of a chef's counters changes per rotation, so depth stays in the others. Rotation trades a little short-term speed for knowledge spread across the brigade, which shortens recovery when the usual expert is away.

### Why deliver every week, no matter what?

Because a counter that only delivers in good weeks disappears in bad ones. The counter sets its own minimum, so "no matter what" is a promise the chefs chose, sized to survive vacations and incidents.

### Does a small team need all this?

No. In a small brigade every chef serves every counter, so rotation has little to do. Changelogs, votes, gateways and the value report still work, and the team grows into the rest. See [Scaling](MODEL.md#scaling).

### Do we have to adopt the sample manifesto?

No. Every brigade must name house standards, but they can be its own. The sample is one engineer's lessons, shared as a starting point.

### What happens when the manager disagrees?

The manager's decision is followed and noted in the counter's changelog. Open Kitchen governs the team from inside; it never competes with the organization.

## Open challenges

### Valuing the family meal

Work for the brigade itself serves no dish directly, so its value is indirect: faster recovery, less toil, easier onboarding. *Current thinking:* translate it through time and risk, such as hours of toil removed or recovery time before and after.

### Crediting value that didn't happen

Avoided incidents and prevented outages are real value but hard to prove. *Current thinking:* report exposure before and after, such as open single points of failure or untested restores, never invented savings.

### Thin or skewed voting

Few votes make the signal noisy; organized votes can bend it. *Current thinking:* only cast votes count by design, and escalation needs several weeks in a row, but no participation floor exists yet.

### Rotation versus critical knowledge

A chef rotating away from a counter may hold knowledge nobody else has. *Current thinking:* runbooks and the gateway shadow week are the bridge, but the model has no explicit handover rule.

### Splitting crowded counters

Dividing a concern in two keeps counters flat, but the new boundary can be fuzzy. *Current thinking:* apply the substitution question to each tool, the same way tools are placed.

### Fitting the organization's planning

Many organizations plan in OKRs, quarters or sprints that don't match weekly changelogs and monthly reports. *Current thinking:* the value report is the bridge; how it maps onto each planning system is untested.

### How much voice regulars get

Regulars vote and are consulted, but don't write a counter's rules. A regular who works a counter daily may need more say than that. *Current thinking:* each charter decides how regulars take part; whether the model should set a floor is open.

### Evidence at every size

The model is designed for any size, but each size needs real brigades running it. Reports from small and large brigades are the most useful contribution right now.
