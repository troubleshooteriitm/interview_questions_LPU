
## 1. Explain how Python memory management works.

**Answer:**
Python manages memory automatically using:
- **Private Heap:** Stores all Python objects.
- **Reference Counting:** Frees objects when their reference count becomes zero.
- **Garbage Collector (`gc`):** Detects and removes cyclic references.
- **pymalloc:** Efficiently allocates memory for small objects.

---

## 2. What is the Global Interpreter Lock (GIL)?

**Answer:**
The GIL is a mutex in CPython that allows only one thread to execute Python bytecode at a time. It simplifies memory management but prevents true parallel execution of CPU-bound threads.

---

## 3. When does the GIL become a bottleneck?

**Answer:**
The GIL becomes a bottleneck in **CPU-bound** multithreaded applications because only one thread can execute Python bytecode at a time. It is usually not a problem for **I/O-bound** tasks, where threads release the GIL while waiting.

---

## 4. Difference between multiprocessing, threading, and asyncio.

**Answer:**

| Threading | Multiprocessing | asyncio |
|-----------|-----------------|----------|
| Uses threads | Uses separate processes | Uses coroutines |
| Shared memory | Separate memory | Single-threaded |
| Affected by GIL | Not affected by GIL | Single-threaded |
| Best for I/O-bound tasks | Best for CPU-bound tasks | Best for high-concurrency I/O |

---

## 5. Explain generators and `yield`.

**Answer:**
A generator is a function that returns values one at a time using the `yield` keyword instead of returning all values at once. It pauses after each `yield` and resumes when `next()` is called, making it memory-efficient.

---

## 6. Generator vs Iterator.

**Answer:**

| Generator | Iterator |
|-----------|----------|
| Created using `yield` | Created by implementing `__iter__()` and `__next__()` |
| Easier to write | Requires more code |
| Memory efficient | Memory efficient |
| Every generator is an iterator | Not every iterator is a generator |

---

## 7. Explain mutable vs immutable objects.

**Answer:**
Mutable objects can be changed after creation, while immutable objects cannot.

**Mutable:**
- `list`
- `dict`
- `set`
- `bytearray`

**Immutable:**
- `int`
- `float`
- `bool`
- `str`
- `tuple`
- `frozenset`
- `bytes`

---

## 8. Why FastAPI over Flask?

**Answer:**
FastAPI provides better performance, built-in data validation with Pydantic, automatic OpenAPI/Swagger documentation, native async support, and dependency injection. Flask is simpler but requires additional libraries for many of these features.

---

## 9. Explain ASGI.

**Answer:**
ASGI (Asynchronous Server Gateway Interface) is the successor to WSGI. It supports asynchronous programming, WebSockets, HTTP, and long-lived connections, making it suitable for modern Python web applications like FastAPI.

---

## 10. Difference between ASGI and WSGI.

**Answer:**

| WSGI | ASGI |
|------|------|
| Synchronous | Asynchronous |
| Handles HTTP only | Handles HTTP, WebSockets, and other protocols |
| Used by Flask, Django (traditional) | Used by FastAPI, Starlette, modern Django |
| Not suitable for real-time applications | Ideal for real-time and async applications |

## 11. How does Python import work?

**Answer:**
When Python imports a module:
1. Checks if it is already loaded in `sys.modules`.
2. Searches the directories listed in `sys.path`.
3. Compiles the module to bytecode (`.pyc`) if needed.
4. Executes the module once.
5. Caches the loaded module in `sys.modules` for future imports.

---

## 12. Explain `__new__` vs `__init__`.

**Answer:**

| `__new__` | `__init__` |
|------------|------------|
| Creates the object | Initializes the object |
| Runs first | Runs after `__new__` |
| Returns the instance | Returns `None` |
| Used for controlling object creation | Used for initializing object attributes |

---

## 13. Explain descriptors.

**Answer:**
A descriptor is an object that controls attribute access by implementing one or more of these methods:
- `__get__`
- `__set__`
- `__delete__`

Descriptors are used internally by features like `property`, `classmethod`, and `staticmethod`.

---

## 14. Explain metaclasses.

**Answer:**
A metaclass is the class of a class. Just as classes create objects, metaclasses create classes. Python uses `type` as the default metaclass. Metaclasses are commonly used to customize class creation in frameworks.

---

## 15. How would you optimize Python code handling millions of records?

**Answer:**
- Use generators instead of loading everything into memory.
- Process data in batches (chunking).
- Use efficient data structures like dictionaries and sets.
- Avoid unnecessary object creation.
- Use NumPy or Pandas for numerical operations.
- Profile code using `cProfile` to identify bottlenecks.
- Use multiprocessing for CPU-bound tasks and asyncio/threading for I/O-bound tasks.

---

## 16. Explain middleware.

**Answer:**
Middleware is code that runs before and/or after a request reaches the application. It is commonly used for:
- Authentication
- Logging
- CORS
- Compression
- Request/response modification
- Rate limiting

---

## 17. How would you implement authentication?

**Answer:**
Authentication is commonly implemented using JWT tokens:
1. User logs in with credentials.
2. Server validates credentials.
3. Server generates a signed JWT.
4. Client sends the JWT in the `Authorization` header.
5. Server verifies the token before processing protected requests.

---

## 18. JWT vs Sessions.

**Answer:**

| JWT | Session |
|-----|---------|
| Stored on client | Stored on server |
| Stateless | Stateful |
| Easily scalable | Requires server-side storage |
| Suitable for APIs | Common in traditional web applications |

---

## 19. What are refresh tokens?

**Answer:**
A refresh token is a long-lived token used to obtain a new access token after the current access token expires, allowing users to stay logged in without repeatedly entering credentials.

---

## 20. How do you secure APIs?

**Answer:**
- Use HTTPS.
- Implement authentication (JWT/OAuth).
- Validate and sanitize input.
- Apply rate limiting.
- Use proper authorization checks.
- Store secrets securely.
- Enable CORS only for trusted origins.
- Log security events and monitor suspicious activity.


## 21. Explain PostgreSQL MVCC.

**Answer:**
MVCC (Multi-Version Concurrency Control) allows multiple transactions to read and write data simultaneously without blocking each other. Instead of modifying rows directly, PostgreSQL creates new versions of rows, allowing readers to access a consistent snapshot of the database.

---

## 22. What are transaction isolation levels?

**Answer:**

| Isolation Level | Description |
|-----------------|-------------|
| Read Uncommitted | Allows dirty reads (not supported in PostgreSQL; treated as Read Committed). |
| Read Committed | Reads only committed data; default level in PostgreSQL. |
| Repeatable Read | Ensures the same query returns consistent results within a transaction. |
| Serializable | Highest isolation level; transactions behave as if executed one after another. |

---

## 23. Explain deadlocks.

**Answer:**
A deadlock occurs when two or more transactions wait indefinitely for each other to release resources.

Example:
- Transaction A locks Row 1 and waits for Row 2.
- Transaction B locks Row 2 and waits for Row 1.

PostgreSQL detects deadlocks automatically and aborts one transaction.

---

## 24. What are indexes in PostgreSQL?

**Answer:**
Indexes improve query performance by allowing PostgreSQL to locate rows quickly instead of scanning the entire table.

Common index types:
- B-tree
- Hash
- GIN
- GiST
- BRIN

Indexes improve read performance but increase storage usage and slightly slow inserts, updates, and deletes.

---

## 25. B-tree vs Hash indexes.

**Answer:**

| B-tree | Hash |
|--------|------|
| Default index type | Specialized index |
| Supports sorting and range queries | Supports equality searches only |
| Most commonly used | Less commonly used |
| Handles `<`, `>`, `BETWEEN`, `ORDER BY` | Best for `=` comparisons |

---

## 26. What are materialized views?

**Answer:**
A materialized view stores the result of a query physically on disk. Unlike a normal view, it does not update automatically and must be refreshed manually or on a schedule. It is useful for improving the performance of expensive queries.

---

## 27. When should you partition tables?

**Answer:**
Partition tables when:
- The table contains millions of rows.
- Queries frequently filter by a column such as date or region.
- Faster maintenance and improved query performance are required.

---

## 28. What does `EXPLAIN ANALYZE` do?

**Answer:**
`EXPLAIN ANALYZE` executes a query and displays the actual execution plan, including:
- Execution time
- Index usage
- Sequential scans
- Number of rows processed
- Cost estimates

It is used to identify performance bottlenecks.

---

## 29. What is connection pooling?

**Answer:**
Connection pooling maintains a pool of reusable database connections instead of creating a new connection for every request. This reduces connection overhead, improves performance, and allows applications to handle more concurrent users.

---

## 30. Explain normalization vs denormalization.

**Answer:**

| Normalization | Denormalization |
|--------------|-----------------|
| Reduces data redundancy | Introduces controlled redundancy |
| Improves data consistency | Improves read performance |
| Requires more joins | Fewer joins |
| Best for transactional systems | Best for reporting and analytics |


## 31. What is the CAP Theorem?

**Answer:**
The CAP Theorem states that a distributed system can guarantee only **two out of three** properties at the same time:
- **Consistency (C):** Every client sees the latest data.
- **Availability (A):** Every request receives a response.
- **Partition Tolerance (P):** The system continues working despite network failures.

Since network partitions are unavoidable, systems usually choose between **Consistency** and **Availability** during a partition.

---

## 32. Consistency vs Availability.

**Answer:**

| Consistency | Availability |
|-------------|--------------|
| Every client gets the latest data | Every request receives a response |
| May reject requests during failures | May return stale data during failures |
| Preferred in banking systems | Preferred in social media and messaging apps |

---

## 33. What is eventual consistency?

**Answer:**
Eventual consistency means that after updates stop, all replicas of the data will eventually become consistent. It is commonly used in distributed databases to improve availability and scalability.

---

## 34. What is idempotency?

**Answer:**
An operation is **idempotent** if performing it multiple times produces the same result as performing it once.

Example:
A payment API uses an **idempotency key** so that repeated requests do not create duplicate payments.

---

## 35. What is a circuit breaker?

**Answer:**
A circuit breaker prevents repeated requests to a failing service.

It has three states:
- **Closed:** Requests pass normally.
- **Open:** Requests are blocked because the service is failing.
- **Half-Open:** A few requests are allowed to test whether the service has recovered.

Circuit breakers improve system reliability and prevent cascading failures.

---

## 36. Explain RAG (Retrieval-Augmented Generation).

**Answer:**
RAG combines a Large Language Model (LLM) with an external knowledge source.

Workflow:
1. Convert documents into embeddings.
2. Store embeddings in a vector database.
3. Convert the user's query into an embedding.
4. Retrieve the most relevant documents.
5. Send the retrieved context along with the prompt to the LLM.
6. The LLM generates an informed response.

RAG improves accuracy and reduces hallucinations.

---

## 37. What are embeddings?

**Answer:**
Embeddings are numerical vector representations of text, images, or other data that capture semantic meaning.

Similar pieces of information have embeddings that are close together in vector space, enabling semantic search and recommendation systems.

---

## 38. What is a vector database?

**Answer:**
A vector database stores and searches embeddings efficiently using similarity search algorithms.

Popular vector databases include:
- Pinecone
- ChromaDB
- Weaviate
- Milvus
- pgvector (PostgreSQL extension)

They are commonly used in RAG systems and semantic search.

---

## 39. What is prompt engineering?

**Answer:**
Prompt engineering is the practice of designing prompts that guide Large Language Models to produce accurate, relevant, and well-structured responses.

Common techniques include:
- Role prompting
- Few-shot prompting
- Chain-of-thought prompting
- Providing clear instructions
- Specifying output format

---

## 40. What is Agentic AI?

**Answer:**
Agentic AI refers to AI systems that can plan, reason, use tools, remember context, and perform multi-step tasks autonomously to achieve a goal.

Unlike a standard chatbot that only answers questions, an AI agent can:
- Break a task into smaller steps.
- Use external tools or APIs.
- Remember previous interactions.
- Make decisions based on intermediate results.
- Continue until the objective is completed.


## 41. What is Docker?

**Answer:**
Docker is a containerization platform that packages an application along with its dependencies into lightweight, portable containers. Containers run consistently across different environments, making deployment easier.

---

## 42. What are Docker layers?

**Answer:**
Docker images are built in layers, where each instruction in a `Dockerfile` creates a new layer. Layers are cached and reused when possible, making image builds faster and reducing storage usage.

---

## 43. What are multi-stage Docker builds?

**Answer:**
Multi-stage builds use multiple `FROM` statements in a Dockerfile. The application is built in one stage and only the required files are copied to the final image, resulting in a smaller, more secure production image.

---

## 44. What is Kubernetes?

**Answer:**
Kubernetes is a container orchestration platform that automates the deployment, scaling, networking, and management of containerized applications across multiple servers.

---

## 45. What is the difference between a Pod and a Container?

**Answer:**

| Pod | Container |
|-----|-----------|
| Smallest deployable unit in Kubernetes | A single running application instance |
| Can contain one or more containers | Contains application code and dependencies |
| Shares networking and storage among its containers | Runs inside a Pod |

---

## 46. What is CI/CD?

**Answer:**
CI/CD stands for:

- **Continuous Integration (CI):** Automatically builds and tests code whenever changes are pushed.
- **Continuous Delivery/Deployment (CD):** Automatically delivers or deploys tested code to staging or production.

It helps reduce manual work and ensures faster, more reliable releases.

---

## 47. What is Blue-Green Deployment?

**Answer:**
Blue-Green Deployment maintains two identical production environments:

- **Blue:** Current live version.
- **Green:** New version.

After testing the Green environment, traffic is switched from Blue to Green. If problems occur, traffic can quickly be switched back.

---

## 48. What is Canary Deployment?

**Answer:**
Canary Deployment releases a new version to a small percentage of users first. If no issues are detected, the rollout gradually expands until all users receive the new version. This minimizes the impact of potential bugs.

---

## 49. What is the difference between OAuth and JWT?

**Answer:**

| OAuth | JWT |
|--------|-----|
| Authorization framework | Token format |
| Used to grant access to resources | Used to securely transmit user information |
| Supports third-party login (e.g., Google Login) | Commonly used for authentication after login |
| Can use JWT as its access token format | Does not provide an authorization flow by itself |

---

## 50. How would you deploy a production AI platform?

**Answer:**
A typical production AI platform includes:
- FastAPI or another backend framework for serving APIs.
- Docker for containerization.
- Kubernetes for orchestration and scaling.
- PostgreSQL for structured data.
- Redis for caching.
- Vector database (e.g., Pinecone, ChromaDB, or pgvector) for semantic search.
- Load balancer for traffic distribution.
- CI/CD pipeline for automated deployments.
- Monitoring with Prometheus and Grafana.
- Logging using ELK Stack or Loki.
- HTTPS, authentication, rate limiting, and secrets management for security.