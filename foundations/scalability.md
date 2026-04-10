# Scalability

As a system grows — whether in the amount of data it stores, the number of users it serves, or the complexity of what it does — there should be reasonable ways to handle that growth.

**Scalability** is a system's ability to handle increasing load without breaking down or slowing to a crawl.

### Describing Load

Before designing for scalability, it's important to understand what "load" actually means for a given system and how it might grow over time. Load can be measured in different ways depending on the type of system:

* For a **web application**: number of requests per second, or number of users active at the same time.
* For a **database**: number of queries per second, or total amount of data stored.

Understanding load also means recognizing trade-offs. One common example is the choice between **write scaling** and **read scaling**:

* **Write scaling**: adding resources to handle more write operations (e.g., saving new data).
* **Read scaling**: adding resources to handle more read operations (e.g., loading data).

Different systems have different needs here. A social media platform, for example, has many more users reading posts than creating them, so it would prioritize read scaling. An online retailer processing many orders per second might need to prioritize write scaling instead.

### Describing Performance

Once we understand the load, the next question is: what happens to performance when the load increases?

If the load goes up but the hardware resources stay the same (CPU, memory, disk, network), two key metrics tend to suffer:

* **Throughput**: the number of requests the system can handle per unit of time. Under higher load, throughput may drop as the system becomes a bottleneck.
* **Response time**: the total time from when a user sends a request to when they receive a response. This includes network delays, time spent waiting in a queue, and the actual processing time.

It's worth distinguishing **response time** from **latency**. Response time is what the user actually experiences — the full end-to-end time. Latency, more precisely, refers to the time a request spends _waiting_ before it starts being processed. For example, if a server is busy, a new request might sit in a queue for a moment before it's handled — that waiting time is the latency.

Response times aren't constant. The same request made at different times may return at different speeds due to server load, network conditions, or caching. Because of this variability, it's better to look at the **distribution** of response times rather than just the average.

A useful tool for this is **percentiles**. For example, the **p95 (95th percentile)** response time means that 95% of requests complete within that time — and only 5% take longer. This helps identify slow outliers and set realistic performance targets.

### Approaches for Coping with Load

An architecture that works well at one scale may not hold up as load increases. There are two main strategies for scaling a system:

* **Vertical scaling (scaling up)**: making a single server more powerful by adding more CPU, memory, or storage. It's simple and quick to apply, but there's a physical and financial ceiling to how far you can go.
* **Horizontal scaling (scaling out)**: adding more servers and spreading the load across them. This can handle much larger scale and is often more cost-effective over time, but it adds complexity to the system.

Horizontal scaling works easily for **stateless services** — services that don't need to remember anything between requests (each request carries all the information needed to handle it). It gets more complex for **stateful services** — services that need to keep track of ongoing information, like a user's session. In those cases, state needs to be stored somewhere shared (e.g., a database or a distributed cache) so that any server can access it.

Historically, the common approach was to keep the database on a single server and scale it vertically. As data volumes grew, this became impractical, and distributed databases that can scale horizontally have become more common.

There's no single right answer for scalability. The best approach depends on the specific system's needs. A small startup might start with vertical scaling for simplicity, while a large platform might need horizontal scaling from day one.

The key insight is that a scalable architecture is designed around the system's expected usage patterns — specifically, **which operations will be most frequent**. A read-heavy system might add a caching layer to serve common requests faster, while a write-heavy system might use a distributed database optimized for high write throughput.

### References

M. Kleppmann, "Foundations of Data Systems," in _Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems_, 1st ed. Sebastopol, CA, USA: O'Reilly Media, 2017, ch. 1, pp. 10–18.
