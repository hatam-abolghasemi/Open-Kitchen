# Adopting Open Kitchen

*From reading the model to running it.*

Decisions happen at two levels: the whole brigade answers the team-level questions once, and the chefs of each counter answer the charter questions for that counter. Record the team answers in your [brigade record](templates/brigade.md).

## Team-level questions

### Size and counters

1. **How many chefs does the brigade have,** and which row of the [scaling table](MODEL.md#scaling) does it start from?
2. **Which counters do we open?** Start from the example concerns and adapt them to your repositories.
3. **How many counters does each chef serve at?** The same number for everyone, or does it vary?
4. **Which defaults do we change?** See [Core rules and defaults](MODEL.md#core-rules-and-defaults).

### House standards and the test kitchen

5. **Which house standards do we adopt?** Our own, the [sample](house-standards/MANIFESTO.md), or the sample with our changes, and which version?
6. **How much room does the test kitchen get?** A kitchen-wide rule, such as a share of each week, or each counter's choice?
7. **Who decides an experiment is proven** before it reaches production: the counter alone, or with the counters it touches?

### Minimum output

8. **What counts as output?** Each counter's choice, or brigade-wide rules such as "a planned task, not only incident work"?
9. **What happens when a counter misses its minimum?** Is the changelog showing it enough, or does a miss trigger something?
10. **What stops a counter from setting its minimum too low?** Is the happiness vote the only check?
11. **Does incident work count** toward the minimum in a bad week?

### Ownership

12. **Where does a tool that spans two concerns belong?** A service mesh enforces security policy; a log store behaves like a data store. Is it always where its repository sits, with the other counter consulted?
13. **Who serves at Others?** Chefs like any counter, or one named chef per tool until it is promoted?
14. **When is a concern promoted out of Others,** and who decides?
15. **Who owns the repository structure itself?** One counter, or the whole brigade?
16. **Which teams have regulars at our counters?** DBAs, network, security or QA engineers outside the brigade.

### Chefs

17. **How are the first assignments made?** Self-selection, current expertise, or a team agreement?
18. **How does the rotation scheme work?** Which counter changes for a chef, and where the chef goes.
19. **What if a counter has too few chefs** to deliver its minimum after a rotation?

### Happiness signal

20. **Who votes?** Everyone, or only people who don't work that counter: regulars and product teams?
21. **Where do votes happen,** and who counts them?
22. **In the last-resort step, who writes the rules,** and when does the counter get its autonomy back?

### Measuring

23. **Which deployments count for DORA?** Developers' application deploys, the brigade's infrastructure changes, or both, reported separately?
24. **Which maturity framework do we use?** See [Maturity](MEASURING.md#maturity).
25. **Which chef builds the monthly value report** with the organization's planners: a rotating chef, or each gateway in turn?
26. **What do our peers need** from the value report to use it in their own planning and reviews?

## Charter questions

The chefs of each counter answer these in its [charter](templates/charter.md). The suggestions are a starting point to take, change or ignore.

| # | Question | Suggested answer |
| --- | --- | --- |
| 1 | Which chefs serve at our counter? | (must be filled) |
| 2 | Which tools do we serve? | (must be filled) |
| 3 | What is our minimum weekly output? | (must be filled) |
| 4 | Do we have a head chef? If yes, who, and why? | No. A majority of the counter's chefs decides. |
| 5 | How do we break a tie? | This week's gateway decides. |
| 6 | Which changes need a group decision? | Production and disaster-recovery changes. Any chef may change other environments. |
| 7 | How do we share the weekly work? | Each chef picks tasks at the start of the week. |
| 8 | Who is our gateway? | Weekly round-robin. |
| 9 | Who writes the weekly changelog, and when? | This week's gateway, by the end of the work week. |
| 10 | What do we promise the teams we work with? | Acknowledge requests within 1 working day. |
| 11 | How do we build our monthly on-call list? | Round-robin, published before the month starts. |
| 12 | Where are our runbooks? | In each tool's repository, as `RUNBOOK.md`. |
| 13 | How does a chef new to our counter get up to speed? | Read the charter and runbooks, then shadow one gateway week. |
| 14 | What if one chef blocks every decision? | The majority decides, and the blocking is noted in the changelog. |
| 15 | When may an outsider make an emergency change to our tools? | The [model default](MODEL.md#emergency-changes-from-outside). |
| 16 | How do we make room for the test kitchen? | One experiment in progress at all times. |
| 17 | Where do we keep our standards gap? | Issues labeled `standards-gap` in our repositories. |
| 18 | Who are our regulars, and how do we work with them? | Name them, invite them to open sessions, and discuss changes that affect their work with them first. |

## Rollout

A suggested shape. Adjust durations to your brigade; small brigades can skip the pilot.

| Phase | Duration | What happens |
| --- | --- | --- |
| Decide | About 2 weeks | Answer the team-level questions, choose house standards and a maturity framework, open counters, assign chefs, name regulars, write charters. |
| Pilot | About 8 weeks | Two counters run the full model. Start measuring by hand ([Starting from nothing](MEASURING.md#starting-from-nothing)). |
| Review | 1 week | Adjust the brigade record and charters from what the pilot showed. |
| Go live | About 6 weeks | Every counter runs the model. The first value report goes out. |
| First rotation | At the rotation point | One counter changes per chef, and every charter is renewed. |
