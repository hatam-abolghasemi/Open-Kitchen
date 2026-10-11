# DevOps Manifesto

*A sample of team standards for Open Kitchen.*

These are the beliefs of Hatam Abolghasemi, learned over four years of DevOps work. They are one team's answer to what good work means, not part of the [model](../MODEL.md). A team can adopt them as they are, change them, or write its own. The [principles](PRINCIPLES.md) explain each belief and how it shows up in daily work.

1. **Incidents are inevitable. Slow recovery is not.** Post-mortems exist to find ways to minimize MTTR.
2. **`print` before `return`.** Metrics and measurement before production.
3. **Mistakes are signals, not sins.** No incident is `rm -rf /`. Blame hides mistakes, and hidden mistakes repeat.
4. **Automation speeds up the manual, it doesn't replace it.** If nobody can do it by hand, the automation is a SPOF.
5. **X as Git.** If it isn't in Git, it didn't happen.
6. **Default is not for production.** Every value that affects behavior we care about is set on purpose.
7. **Every translation has a daily cost.** Bad names, needless abstractions and variable hells are paid for every day.
8. **A name is a self-documenting identifier.** Not a metadata paragraph.
9. **One thing, one name, everywhere.** When forced to rename, rename everywhere. Express different aspects in different views, not in identifiers.
10. **Failure blast radius decides how much is enough.** What breaks, for whom, and at what cost.
11. **Environments exist to separate the different classes of failure blast radius.** Each one must name the failure it keeps away from production.
12. **Idle is waste.** Slow startup is a bug to fix, not a reason to stay warm.
13. **Solve real current vital problems.** A flaw that exists today is current, even if its failure hasn't happened yet; a problem a new tool invents is not.
14. **Requirements choose tools, not the other way around.** Need a small slice of a big tool? Build it, cleanly. Need most of a flawed tool? Keep it.
15. **Greater pain now is better than gradual pain forever.** Don't carry corpses around: burn them to the ground or bring them back to life.
16. **Marketing brings the users. Tech keeps them.** Every decision ends in money, time, risk or customer experience, and every action translates into business metrics.
17. **Nothing is frozen, this repo included.** Every decision carries a date to check it again.

*Recovery first, predictability second, efficiency third.*
