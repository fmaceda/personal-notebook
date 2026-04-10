# Maintainability

Over time, many different people will work on the system — engineers building new features, and operations teams keeping it running — and they should all be able to do their work productively.

Maintaining a system costs more than building it. Most of a system's lifetime is spent being operated and extended, not written from scratch. For this reason, it's worth designing systems that are easy to work on. Three design principles help with this:

* **Operability:** Make it easy for operations teams to keep the system running smoothly and to quickly identify and fix problems when they occur.
* **Simplicity:** Keep the system as simple as possible while still meeting its requirements. Avoid unnecessary complexity and favor well-understood technologies.
* **Evolvability:** Design the system so it can be adapted to new needs over time, without requiring a complete rewrite.

### Operability: Making Life Easy for Operations

Operations teams are responsible for:

* Monitoring the health of the system and quickly identifying problems when they occur.
* Investigating the root cause of problems and fixing them.
* Keeping the system running smoothly despite hardware failures, software bugs, and human mistakes.
* Deploying new versions of the software and rolling back changes when something goes wrong.
* Maintaining security and protecting user data from loss or corruption.
* Documenting how the system works and helping new team members get up to speed.

Good operability means making routine tasks easy, so the team can focus on meaningful work rather than firefighting. Some practical ways to achieve this:

* **Good monitoring and alerting** surfaces problems early, so the team can respond before users are affected.
* **Clear documentation and a learning culture** preserve knowledge about the system and make onboarding new team members easier.
* **Staging environments and rollback mechanisms** let teams test changes safely and recover quickly if something goes wrong in production.

### Simplicity: Managing Complexity

As a system grows, it can become harder to understand and work with. Complexity sneaks in gradually, and left unchecked it makes the system fragile and slow to change.

Some signs that a system has become too complex:

* It's not clear how the different parts of the system interact with each other.
* Technologies and design patterns were added without a clear reason, and nobody remembers why.
* There are too many configuration options, and it's unclear which ones matter.

Complexity causes real problems:

* Developers have a harder time understanding the system, which leads to more bugs.
* Operations teams struggle to maintain something they don't fully understand, which leads to more downtime.

One of the most effective tools for fighting complexity is **abstraction** — the idea of hiding messy, low-level details behind a clean, simple interface. For instance, a well-designed database library lets a developer save and retrieve data without needing to know how the database engine works internally. The complexity is still there, but it's hidden behind a simple surface that's easy to use correctly.

### Evolvability: Making Change Easy

Requirements change. New features get added, old ones get removed, and the business evolves in ways nobody predicted at the start. A system that is hard to change becomes a liability over time.

Designing for evolvability means building the system in a way that makes future changes manageable. One approach is **modular design** — breaking the system into independent components with clear boundaries between them. This way, a change to one part doesn't ripple unpredictably through everything else. For example, a **microservices architecture** (where the system is made up of many small, independently deployable services instead of one large application) allows individual pieces to be updated, replaced, or scaled without touching the rest of the system.

On the process side, **Agile** working practices support evolvability by encouraging small, frequent releases and regular feedback from users. Combined with a **CI/CD pipeline** (a set of automated tools that test and deploy code changes quickly and safely), teams can ship improvements continuously and catch problems early, rather than waiting for a big release that's hard to roll back.

### References

M. Kleppmann, "Foundations of Data Systems," in _Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems_, 1st ed. Sebastopol, CA, USA: O'Reilly Media, 2017, ch. 1, pp. 18–22.
