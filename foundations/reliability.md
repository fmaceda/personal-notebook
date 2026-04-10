# Reliability

A reliable system keeps working correctly — doing what it's supposed to do, at an acceptable speed — even when things go wrong, such as hardware breaking, software bugs appearing, or people making mistakes.

A reliable system is expected to:

* Do what the user expects, even if the user makes a mistake or uses the app in an unexpected way.
* Stay fast and responsive, even under heavy traffic or when some parts of the system are having trouble.
* Keep data safe and private, even if the system is under attack or has security weaknesses.

In short, reliability is about making sure a system keeps working well for its users, no matter what challenges come up.

It helps to distinguish between two related terms: a **fault** is when one part of the system stops working correctly, while a **failure** is when the whole system stops working. Since it's impossible to prevent every fault, systems should be designed to be **fault-tolerant** — meaning they can keep running even when individual parts break.

### Hardware Faults

Physical components can fail in many ways:

* Hard disks crash
* RAM becomes corrupted
* Power grid goes down
* Network cables get unplugged

The most common way to deal with hardware failures is **redundancy** — having backup components ready to take over if the primary one fails. For example, storing data across multiple hard disks (RAID) means that if one disk fails, no data is lost. Similarly, having multiple servers behind a load balancer means that if one server goes down, others can handle the traffic. Servers can also have dual power supplies for the same reason.

As applications grow and run on more and more machines, hardware failures become more frequent just by the numbers. For example, if a single machine has a 1% chance of a hardware fault in a given period, a cluster of 100 machines would expect about 1 fault in that same period. The more machines, the more faults to deal with.

This is why software-level fault tolerance matters too — things like distributed systems that can automatically detect and recover from hardware failures, or software that retries an operation if it fails due to a hardware problem.

### Software Faults

Unlike hardware faults, which tend to be random and unpredictable, software faults are often **deterministic** — meaning the same input will trigger the same bug every time.

These bugs can be reduced through testing, code reviews, and good engineering practices. However, not every bug will be caught before it reaches production, so it's important to have monitoring and alerting set up to detect problems early and fix them quickly.

When a quick fix isn't available, having a mitigation plan helps. For example, if a bug causes one feature to break, it may be possible to temporarily disable just that feature while a proper fix is developed, rather than letting it affect the whole system.

### Human Errors

People are often the biggest source of reliability problems. A developer might accidentally delete a database, misconfigure a server, or roll out a buggy update.

To reduce the impact of human mistakes, good systems are built with multiple layers of protection:

* **Simple, well-designed interfaces** reduce the chance of mistakes in the first place, and **automating repetitive tasks** removes opportunities for human error.
* **Separate environments** (like staging vs. production) mean that mistakes can be caught before they affect real users. **Rollback mechanisms** let teams quickly undo a bad change.
* **Automated tests** (unit, integration, and end-to-end) catch regressions early, before they reach production.
* **Monitoring and alerting** make it easy to detect when something goes wrong, and help teams respond quickly. Tracking performance metrics and error rates gives everyone visibility into the system's health.
* **Good team practices** — like clear documentation and a culture of learning from mistakes rather than assigning blame — help prevent the same errors from happening twice.

### The importance of reliability

Almost every app we use every day — email, social media, online banking — depends on reliable systems running underneath. Without reliability, we'd face constant outages, lost data, and security breaches.

That said, reliability sometimes has to be balanced against cost or performance. For example, a social media platform might accept slightly delayed posts during peak traffic to avoid overloading servers, or an online store might delay some order processing during a high-traffic event like Black Friday. These are deliberate trade-offs. But in general, reliability should be a priority — users trust the systems they use, and that trust is hard to rebuild once it's broken.

### References

M. Kleppmann, "Foundations of Data Systems," in _Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems_, 1st ed. Sebastopol, CA, USA: O'Reilly Media, 2017, ch. 1, pp. 3–10.
