# DevOps Principles

*A sample of team standards for Open Kitchen.*

The [manifesto](MANIFESTO.md) states what we believe. This document explains each belief and how it shows up in daily work. The examples come from the author's own team; replace them with yours if you adopt these standards.

Every section below has the same shape: the belief, **why** we hold it, and what it looks like **in practice**. Inside "in practice", the rule comes first, then the mechanism, then concrete examples.

---

## Values

Three values sit under everything, in ranked order. When they collide, the higher one wins.

1. **Recovery.** How fast we detect, understand and recover from failure.
2. **Predictability.** The system does only what is written down.
3. **Efficiency.** We pay only for what is needed.

Recovery ranks first because it is bounded and measurable: MTTR is a number. Predictability has no finish line, because the stack and the business keep changing under it. Ranking it first would mean chasing a state we can never reach.

---

## 1. Incidents are inevitable. Slow recovery is not.

**Why:** No system is failure-free, but recovery speed can be engineered. Every incident could have been recovered faster if we had had something. Finding that something is the work, as far as the failure blast radius (#10) justifies; not every gap is worth closing.

**In practice:**

- Every postmortem names what would have made detection or recovery faster, and that becomes work.
- Break-glass is legitimate. If someone had to bypass GitOps to restore service, GitOps failed recovery in that moment.
- We expect anyone to make mistakes within their scope, and guide them to fix what they can detect.

---

## 2. `print` before `return`.

**Why:** We can't recover from what we can't see. Observability comes first in sequence: nothing can be secured, automated or optimized without it.

**In practice:**

- Nothing reaches production without a way to see whether it is healthy.
- Every function, job and tool reports what it received, what it did and what it produced: enough to debug, not everything.
- Before changing anything: observe, verify the observation, dry-run, then change. Before risky changes: back up and prove the restore works.
- Data has four forms: metrics (cheapest, best for monitoring), logs (when cardinality is the point), traces (the path of a request), and records (full state in a database).
- Log levels have definitions. INFO is allowed in production, but not every INFO. DEBUG never.
- node-exporter runs everywhere, with explicit collectors.

---

## 3. Mistakes are signals, not sins.

**Why:** Blame feels satisfying in the moment, but over time it teaches people to hide mistakes, and hidden mistakes repeat. A mistake or a bypass shows where a system failed, not where a person did.

**In practice:**

- We fix systems, not people.
- Single events may be dropped. Patterns may not: the same mistake twice is a guardrail bug.
- Fixing the pain behind a bypass belongs to the whole team.
- We own the changes we make.

---

## 4. Automation speeds up the manual, it doesn't replace it.

**Why:** Automation is a tool for speed and predictability, not a substitute for understanding. When people only know how to run the automation, it becomes a SPOF made of knowledge: if it breaks, nobody can operate the system.

**In practice:**

- Every automated task can still be done by hand, and the team knows how.
- Automation earns its place when its maintenance cost is lower than the manual cost. A handful of machines rarely justifies it; everyday repeated work usually does.
- Automation shows what it does: plain commands, explicit flags (#6), and output of what it received, did and produced (#2), so reading it is reading the runbook.
- "Everything automated" is a mindset, not a value (#7).

---

## 5. X as Git.

**Why:** What isn't tracked can't be reviewed, reverted or explained during an incident.

**In practice:**

- Infrastructure, configuration, documentation and decisions all live in Git.
- No untracked automation runs.
- Desired state lives in Git, and a reconciler converges toward it.
- Tracking and desired state are different. Sudo logs shipped to a repo are history; Git manifests are truth. Both are required.
- No anonymous root: `sudo` per command, never a root shell, so every privileged action is attributable to a person.
- Attribution serves responsibility, never accusation. It tells us who made the last change so we can ask for the reasoning behind it, shows whether someone fits their role, and keeps intruders out.

---

## 6. Default is not for production.

**Why:** Defaults are invisible to whoever reads the config, and they can change silently between versions.

**In practice:**

- Every version, and every config value that affects behavior we care about, is set explicitly in production. Restating harmless defaults is just noise.
- Third-party Helm charts are rendered into manifests and committed. No CRD or operator enters without being understood and pinned.
- Commands use explicit flags (`mkdir -p`, `grep -qxF`). Idempotency is designed into a change, not inherited from a tool.

---

## 7. Every translation has a daily cost.

**Why:** Every translation costs time on every read, every review and every debug, and costs the most during incidents. Ease of maintenance matters much more than ease of setup.

**In practice:**

- A layer must solve something the layer below cannot. Kubernetes earns its place; a module that wraps `cp` does not.
- Mechanisms are tools, not identities. "Everything containerized," "everything as a Helm chart" and "everything automated" are biased mindsets.
- Plain commands beat abstractions that hide them (#6).

---

## 8. A name is a self-documenting identifier.

**Why:** A good name tells you what something is without a lookup. A name stuffed with metadata becomes long, fragile, and wrong when the metadata changes.

**In practice:**

- Names identify. Metadata belongs in labels, tags and docs.
- Example: `devops/networking/haproxy-prd` says what it is, where it belongs, and which environment it serves.

---

## 9. One thing, one name, everywhere.

**Why:** Every mapping between names is a translation and a place where things fall out of sync.

**In practice:**

- No complicated mappings.
- Different aspects are expressed in different views (labels, dashboards, docs), not packed into identifiers.
- When forced to rename, first ask whether the new name can be applied everywhere the identity lives.
- `prod` is `prod` in every repo, cluster, label, dashboard and document.

---

## 10. Failure blast radius decides how much is enough.

**Why:** "Enough" needs a shared reference, or it drifts with whoever decides. Failure blast radius is that reference: what breaks, for whom, and at what cost. It is a judgment built from experience, not a formula, and it differs from company to company and service to service. Writing it down with each decision is what makes it shared and open to challenge.

**In practice:**

- Configure for enough doomsday, not doomsday. The assumed blast radius is written down with the decision.
- Behavior beyond "enough" is defined, not discovered. DevOps owns how the system degrades; business owns trade-offs about what customers get.
- Safety checks scale with failure probability × failure blast radius. Proven, low-blast paths go straight through.
- "Proven" decays, so evidence is kept fresh continuously (e.g. scheduled restore tests), not checked before every change.
- HA is decided per component by failure blast radius. Harbor, HAProxy and Kafka must be HA. A per-service Redis used as a cache, whose loss only sends the app to the database, can run as a single instance.
- Redundancy doesn't have to be identical. A second GitLab server isn't worth it; a Gitea fallback can be.
- Load is distributed horizontally at every level where failure blast radius demands it.
- Security effort scales with failure blast radius. The system runs first, then is secured: a matter of order, not importance.
- The security baseline holds regardless: no container images running as root, no SSH exposed to the world.

---

## 11. Environments exist to separate the different classes of failure blast radius.

**Why:** Each environment holds a different class of failure, so a failure in one doesn't reach the others, and above all doesn't reach production. Each one must name the failure it keeps away from production.

**In practice:**

- Every environment justifies itself by the class of failure it separates.
- The environment is part of a thing's identity: `-prd`, `-stg`, `-uat`, `-dr`.
- Environments live and die with the work. Feature-review environments come up per branch and go down with a TTL or when the branch is deleted.
- Where per-feature environments aren't possible, an environment scales to zero when unused and comes back up when needed.

---

## 12. Idle is waste.

**Why:** Idle resources cost money. Shrinking them is only safe if starting again is fast.

**In practice:**

- Usage follows demand. Anything allocated without demand has a written reason.
- Scaling rules (min, max, thresholds) are explicit and in Git; the current number may move.
- Slow startup gets fixed rather than hidden behind warm capacity.

---

## 13. Solve real current vital problems.

**Why:** Imagined problems cost setup now and maintenance forever. A problem is current when its flaw exists today, whether or not it has failed yet.

**In practice:**

- This is an order, not a ban. Production reliability comes first (a 99.99% success-rate SLA); stack hygiene and technical debt (#12, #15) come right after, not never.
- Nothing is built for features that aren't needed now or soon.
- A single point of failure is a current problem, not an imagined future: the flaw exists today, only the failure hasn't happened yet. A SPOF is a component whose failure stops the primary objective, not everything that runs as one instance.
- A new tool must name what the current one fails at. "Better on paper" is not a reason.
- Current choices stay until a real, current problem proves them wrong. Every choice keeps an exit condition.
- No TLS for node-exporter on a trusted internal network.

---

## 14. Requirements choose tools, not the other way around.

**Why:** The cost of a tool depends on how much of it we actually need. Adopting a whole tool for a small slice of it means carrying everything else; rebuilding a tool that solves many of our problems means paying for all of them again.

**In practice:**

- Tools are pulled in by pain, never pushed in by fashion. Find first; build only when building is worth it.
- A small slice of a big tool gets built, cleanly. Spegel offered far more than we needed, so Angry Duck was built for the part we did.
- Most of a flawed tool gets kept. Sentry has flaws, but it solves too many problems to rebuild.
- Building in-house is only cheap when the code is clean and modular, so people unfamiliar with the language can still work with it, as with our Lua modules.
- AI lowers the cost of writing code, not of understanding it. What we build must be understood by the team, or it becomes a translation paid for at 4 a.m.

---

## 15. Greater pain now is better than gradual pain forever.

**Why:** The pain here is effort, not incidents: fixing technical debt now should not add a single outage. Gradual pain never gets prioritized, so it never ends. A half-dead system keeps costing attention, maintenance and translations long after it stopped giving value.

**In practice:**

- A short, planned, painful change beats a permanent workaround.
- Anything unused or half-alive (a service, a repo, a config, a dashboard) either gets an owner and comes back to life, or gets deleted.
- Migrations are finished, not left halfway with old and new living side by side.

---

## 16. Marketing brings the users. Tech keeps them.

**Why:** Users stay because the product keeps working, and that is the shared job of everyone in tech. Our part of it is invisible only when we fail to translate it into what the business feels.

**In practice:**

- Every decision lands on money, time, risk or customer experience, and every action translates into business metrics. "Less metric storage" is unfinished until it says "€X/month saved."
- DevOps is a translator, not a ticket queue. It reframes every request against these principles and pushes its own concerns back in business terms.

---

## 17. Nothing is frozen, this repo included.

**Why:** The industry moves whether we do or not.

**In practice:**

- Every standard and decision has a re-check date.
- Review is periodic, not only triggered by pain.
- Repeated workarounds around a tool mean it no longer fits.
- This repo changes too.
