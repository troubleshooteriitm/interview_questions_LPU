# Python & FastAPI Fundamentals (1–10)

1. Why did the instructor choose FastAPI instead of Flask or Django?
  - **Answer:** FastAPI combines high performance (comparable to NodeJS and Go) with built-in async/await support, automatic data validation via Pydantic, and automatic Swagger/OpenAPI documentation. Django is monolithic and heavy, while Flask lacks native async and built-in type validation.
  - **Key Concepts:** ASGI async performance, Pydantic type safety, auto OpenAPI docs, lightweight micro-framework.
  - **Example:** High throughput APIs requiring async database or microservice calls.

2. What are the main advantages of FastAPI?
  - **Answer:**
  1. **Fast:** High performance thanks to Starlette and Pydantic.
  2. **Fast to code:** Reduces development time by 200–300% via type hinting.
  3. **Fewer bugs:** Autocompletion in IDEs and automated runtime type validation.
  4. **Standards-based:** Fully compliant with OpenAPI and JSON Schema.
  - **Example:** IDE autocompletion and instant payload validation out of the box.

3. Explain how FastAPI automatically generates API documentation.
  - **Answer:** FastAPI inspects path operations, Pydantic request models, and response schemas via Python type hints. It compiles them into an OpenAPI standard JSON specification served at `/openapi.json`, rendering interactive **Swagger UI** (`/docs`) and **ReDoc** (`/redoc`) UIs dynamically.
  - **Key Concepts:** Type hint parsing, OpenAPI specification, Swagger UI (`/docs`), ReDoc (`/redoc`).
  - **Example:** Visiting `http://localhost:8000/docs` to test endpoints interactively without manual documentation writing.

4. What is ASGI, and why does FastAPI use it?
  - **Answer:** Asynchronous Server Gateway Interface (ASGI) is the asynchronous standard for Python web servers. FastAPI uses ASGI (via Uvicorn/Starlette) to handle concurrent asynchronous requests, WebSockets, and long-polling without blocking threads.
  - **Key Concepts:** WSGI vs ASGI, async event loop, Uvicorn server, non-blocking I/O.
  - **Example:** Running FastAPI with `uvicorn main:app --reload`.

5. Explain the lifecycle of a FastAPI request.
  - **Answer:**
  1. Client sends HTTP request -> Uvicorn ASGI server receives packets.
  2. Middleware layer executes (CORS, timing, auth headers).
  3. Router matches Path Operation function.
  4. Dependencies (`Depends()`) resolve DB sessions and tokens.
  5. Pydantic validates and parses input parameters.
  6. Endpoint function executes business/DB logic.
  7. Response model serializes output data to JSON and returns HTTP response.
  - **Example:** Request -> Middleware -> Router -> Dependencies -> Pydantic Validation -> Route Handler -> Response Model -> JSON.

6. What are Path Operations in FastAPI?
  - **Answer:** Python functions decorated with HTTP method decorators on the FastAPI app instance (e.g., `@app.get()`, `@app.post()`, `@app.put()`, `@app.delete()`) that handle incoming requests for specific URL path routes.
  - **Key Concepts:** HTTP decorators (`@app.get`), route handlers, path mapping.
  - **Example:**
  ```python
  @app.get("/posts/{id}")
  def get_post(id: int): return {"post_id": id}
  ```

7. How do Path Parameters differ from Query Parameters?
  - **Answer:** **Path Parameters** are variable parts embedded directly inside the URL path (used to locate a specific resource): `/items/{item_id}`. **Query Parameters** are key-value pairs appended after `?` in the URL (used for filtering, sorting, pagination): `/items?skip=0&limit=10`.
  - **Key Concepts:** Embedded URL path variable vs trailing URL key-value string.
  - **Example:** `/users/42` (Path Param `42`) vs `/users?role=admin` (Query Param `role=admin`).

8. Why does the order of routes matter in FastAPI?
  - **Answer:** FastAPI matches path operations sequentially top-to-bottom in the order they are declared in the code. If a generic dynamic path parameter route (`/users/{id}`) is declared *before* a specific static route (`/users/me`), the static route will never be reached because `{id}` intercepts `"me"`.
  - **Key Concepts:** Top-to-bottom sequential route matching, static vs dynamic path resolution.
  - **Example:** Declare `@app.get("/users/me")` **above** `@app.get("/users/{id}")`.

9. What is dependency injection in FastAPI?
  - **Answer:** A mechanism managed via `Depends()` that allows endpoints to declare required reusable resources (DB connections, security token decoders, shared query params). FastAPI automatically resolves, executes, and passes the return value into the route function parameters.
  - **Key Concepts:** `Depends()`, code reuse, yield teardown, DB session management.
  - **Example:** `def get_db(): ...; @app.get("/") def index(db: Session = Depends(get_db)):`.

10. How does FastAPI perform request validation?
  - **Answer:** FastAPI uses Python type annotations paired with Pydantic. When a request arrives, Pydantic parses headers, path params, query params, and JSON body fields against declared types. If invalid, FastAPI automatically halts execution and returns a structured `422 Unprocessable Entity` JSON response detailing errors.
  - **Key Concepts:** Type hints, Pydantic validation engine, 422 HTTP error response.
  - **Example:** Expecting `age: int` and receiving `age: "thirty"` returns 422 with `"value is not a valid integer"`.

---

# Pydantic & Validation (11–15)

11. What is Pydantic?
  - **Answer:** A data validation and settings management library for Python using standard type annotations. It enforces type hints at runtime, providing user-friendly validation errors and automatic data parsing/coercion.
  - **Key Concepts:** `BaseModel`, type enforcement, runtime validation, Rust-based core (Pydantic V2).
  - **Example:** `class Post(BaseModel): title: str; rating: Optional[int] = None`.

12. Why does FastAPI use Pydantic models?
  - **Answer:** Pydantic provides seamless data validation, automatic string-to-type parsing, serialization of complex Python objects to JSON, and automatic OpenAPI schema generation directly from class declarations.
  - **Key Concepts:** Parsing vs validating, JSON serialization, OpenAPI schema generation.
  - **Example:** Automatic conversion of ISO date strings in JSON to Python `datetime` objects.

13. Difference between request models and response models.
  - **Answer:** **Request Models:** Define and validate incoming client payload structures (e.g., requires `password`). **Response Models (`response_model=...`):** Define outgoing response JSON structure, filtering out internal sensitive attributes (e.g., stripping `hashed_password`).
  - **Key Concepts:** Input payload validation vs Output data filtering & security formatting.
  - **Example:** `@app.post("/users", response_model=UserOut)` hides `hashed_password` from HTTP responses.

14. Explain schema validation with an example.
  - **Answer:** Defining constraints using Pydantic fields (`Field()`, `EmailStr`, `gt`, `le`, regex patterns). If payload violates constraints, Pydantic rejects request.
  - **Example:**
  ```python
  from pydantic import BaseModel, EmailStr, Field

  class UserCreate(BaseModel):
      email: EmailStr
      password: str = Field(min_length=8)
      age: int = Field(gt=0, lt=120)
  ```

15. What is the difference between a Pydantic model and a SQLAlchemy model?
  - **Answer:** **Pydantic Model:** Operates in application memory to validate, serialize, and structure API request/response JSON payloads. **SQLAlchemy Model:** Operates at the database layer to define table columns, primary keys, relationships, and translate Python operations into SQL statements.
  - **Key Concepts:** API payload schema (Pydantic) vs Database table mapping (SQLAlchemy).
  - **Example:** Pydantic `PostCreate` vs SQLAlchemy `class Post(Base): __tablename__ = "posts"`.

---

# REST APIs & CRUD (16–20)

16. Explain CRUD operations in REST APIs.
  - **Answer:**
    - **Create:** `POST /posts` (Creates a new post resource, returns 201 Created).
    - **Read:** `GET /posts` or `GET /posts/{id}` (Retrieves resources, returns 200 OK).
    - **Update:** `PUT /posts/{id}` (Full update) or `PATCH /posts/{id}` (Partial update).
    - **Delete:** `DELETE /posts/{id}` (Removes resource, returns 204 No Content).
  - **Example:** Standard REST API resource design for managing blog posts or users.

17. Why should POST return **201 Created** instead of **200 OK**?
  - **Answer:** HTTP status code 201 explicitly signals to client applications that a **new resource has been successfully created** on the server (often accompanied by a `Location` header or the created resource object), differentiating it from general successful requests (200 OK).
  - **Key Concepts:** HTTP status code semantics, explicit resource creation confirmation.
  - **Example:** `status_code=status.HTTP_201_CREATED` in FastAPI decorators.

18. Explain idempotent HTTP methods.
  - **Answer:** An HTTP method is idempotent if executing it multiple times produces the exact same server state as executing it once. `GET`, `PUT`, `DELETE`, `HEAD`, `OPTIONS` are idempotent; `POST` is non-idempotent (retrying creates duplicates).
  - **Key Concepts:** Retry safety, identical server state side-effects.
  - **Example:** Sending `DELETE /posts/5` 5 times results in post 5 being deleted without secondary side effects.

19. Difference between PUT and PATCH.
  - **Answer:** **PUT:** Overwrites the **entire** target resource object (missing fields are reset to default/null). **PATCH:** Updates only the **specified fields** included in the request body, leaving unmentioned fields untouched.
  - **Key Concepts:** Complete replacement (PUT) vs Partial update (PATCH).
  - **Example:** `PATCH` updating only a user's email address while leaving name and password intact.

20. How should API error responses be designed?
  - **Answer:** Error responses should return appropriate standard HTTP status codes (4xx client error, 5xx server error) with a consistent, structured JSON payload describing the error message.
  - **Key Concepts:** `HTTPException`, consistent error schema, clear diagnostic messages.
  - **Example:** `raise HTTPException(status_code=404, detail="Post with id 5 not found")`.

---

# PostgreSQL & SQL (21–28)

21. Why use PostgreSQL instead of SQLite for production?
  - **Answer:** SQLite stores database data in a single local file (lacks high-concurrency write support, locking whole file on write). PostgreSQL is a robust client-server database supporting concurrent multi-connection writes, ACID compliance, advanced indexing, JSONB support, and replication.
  - **Key Concepts:** Client-server vs single-file storage, concurrent write throughput, enterprise production readiness.
  - **Example:** PostgreSQL handling thousands of simultaneous concurrent web app transactions.

22. Explain primary keys and foreign keys.
  - **Answer:** **Primary Key (PK):** A unique identifier column for each row in a database table (cannot be NULL). **Foreign Key (FK):** A column in one table referencing the Primary Key of another table to establish relational constraints between records.
  - **Key Concepts:** Unique row identity (PK), referential constraint link (FK).
  - **Example:** `users.id` (PK) referenced by `posts.owner_id` (FK).

23. What are database constraints?
  - **Answer:** Rules enforced on table columns to restrict allowable data types and ensure data integrity.
  - **Key Concepts:** `NOT NULL`, `UNIQUE`, `PRIMARY KEY`, `FOREIGN KEY`, `CHECK`.
  - **Example:** `email VARCHAR UNIQUE NOT NULL`.

24. Difference between WHERE, LIKE, and IN.
  - **Answer:**
    - `WHERE`: Filters records based on exact equality or comparison expressions (`WHERE age >= 18`).
    - `LIKE`: Performs wildcard pattern matching (`WHERE name LIKE 'John%'`).
    - `IN`: Checks if a column value matches any value in a specified list (`WHERE id IN (1, 2, 3)`).
  - **Example:** Filtering queries based on exact match, pattern searching, or set inclusion.

25. Explain ORDER BY, LIMIT, and OFFSET.
  - **Answer:** `ORDER BY` sorts result sets by columns (`ASC` or `DESC`). `LIMIT` restricts max number of returned rows. `OFFSET` skips $N$ initial rows before returning results (used for pagination).
  - **Key Concepts:** Sorting, result slicing, pagination implementation.
  - **Example:** `SELECT * FROM posts ORDER BY created_at DESC LIMIT 10 OFFSET 20;` (Page 3).

26. What are SQL joins, and when would you use them?
  - **Answer:** Clause used to query and combine columns from two or more relational tables in a single query by matching common foreign key columns.
  - **Key Concepts:** Relational query aggregation, normalized schema stitching.
  - **Example:** Joining `posts` table with `users` table to fetch post titles alongside author names.

27. Difference between INNER JOIN and LEFT JOIN.
  - **Answer:** **INNER JOIN:** Returns only rows with matching values in both tables. **LEFT JOIN:** Returns all rows from the left table and matching rows from the right table (filling unmatched right columns with `NULL`).
  - **Key Concepts:** Matching intersection (INNER) vs Left table preservation (LEFT).
  - **Example:** `LEFT JOIN` returns all users even if they have not published any posts.

28. How would you optimize a slow SQL query?
  - **Answer:**
  1. Analyze query execution plan via `EXPLAIN ANALYZE`.
  2. Add B-Tree indexes to columns used in `WHERE`, `JOIN`, and `ORDER BY`.
  3. Avoid `SELECT *`; fetch only required columns.
  4. Fix N+1 query loops using SQL `JOIN`s or ORM eager loading.
  - **Example:** Replacing full table scan with an index scan on `user_id`.

---

# SQLAlchemy ORM (29–34)

29. What is an ORM, and why use SQLAlchemy?
  - **Answer:** Object-Relational Mapping (ORM) translates SQL tables into Python object classes. SQLAlchemy allows developers to interact with SQL databases using Python code instead of writing raw SQL strings, providing database abstraction, injection protection, and relationship management.
  - **Key Concepts:** Object-relational abstraction, SQL injection safety, database agnostic queries.
  - **Example:** `db.query(Post).filter(Post.id == 1).first()` instead of raw SQL strings.

30. Difference between raw SQL and SQLAlchemy ORM.
  - **Answer:** **Raw SQL:** High performance, full engine control, but vulnerable to SQL injection if un-parameterized, no auto-completion, database vendor locked. **SQLAlchemy ORM:** Pythonic syntax, database-agnostic, automated model mapping, but introduces slight abstraction overhead on complex queries.
  - **Key Concepts:** Performance vs abstraction, safety, database independence.
  - **Example:** Raw `cursor.execute()` vs SQLAlchemy ORM methods.

31. How are relationships defined in SQLAlchemy?
  - **Answer:** Using `relationship()` helper functions in parent and child models paired with `ForeignKey()` definitions, enabling direct dot-notation access to linked objects (`post.owner`).
  - **Key Concepts:** `ForeignKey`, `relationship()`, `back_populates`.
  - **Example:**
  ```python
  class Post(Base):
      owner_id = Column(Integer, ForeignKey("users.id"))
      owner = relationship("User", back_populates="posts")
  ```

32. Explain one-to-many relationships.
  - **Answer:** A relationship where a single record in Table A (User) can be linked to multiple records in Table B (Posts), but each record in Table B links back to only one record in Table A.
  - **Key Concepts:** Single parent to multiple children, foreign key placed on child table.
  - **Example:** One User has many Posts.

33. How does SQLAlchemy handle database sessions?
  - **Answer:** A `Session` object manages active connections and transaction boundaries for database operations. It tracks loaded object state changes (Unit of Work pattern) and commits changes atomically via `session.commit()` or discards them via `session.rollback()`.
  - **Key Concepts:** Unit of Work pattern, `SessionLocal`, commit/rollback, session closure.
  - **Example:**
  ```python
  db = SessionLocal()
  try:
      db.add(new_post)
      db.commit()
  finally:
      db.close()
  ```

34. What is lazy loading in an ORM?
  - **Answer:** Related child objects are NOT fetched from the database when the parent object is initially loaded. Instead, a secondary SQL query is executed on-demand when the relationship property is first accessed in Python (can cause N+1 query bugs if accessed inside loops).
  - **Key Concepts:** On-demand fetching, N+1 query risk, eager loading alternative (`joinedload`).
  - **Example:** Accessing `user.posts` triggers a secondary database SELECT query.

---

# Authentication & Security (35–40)

35. Explain the complete JWT authentication flow.
  - **Answer:**
  1. Client sends POST `/login` with credentials.
  2. FastAPI verifies credentials against database password hash.
  3. Server creates JWT token (encoded header, payload with `user_id` and `exp`, signed with `SECRET_KEY`).
  4. Server returns JWT token string to client.
  5. Client includes token in subsequent HTTP requests inside header: `Authorization: Bearer <token>`.
  6. FastAPI dependency decodes and verifies token signature to grant access.
  - **Key Concepts:** Header.Payload.Signature, `jose` / `pyjwt`, Bearer token authorization.
  - **Example:** Decoding token in `get_current_user` dependency.

36. Why should passwords never be stored in plain text?
  - **Answer:** If the database is compromised via SQL injection or data breach, plain text passwords expose user accounts across all services where users reuse passwords. Passwords must be cryptographically hashed using key-stretching algorithms.
  - **Key Concepts:** Data breach risk, key stretching, one-way hash functions.
  - **Example:** Passwords compromised in cleartext expose user emails and accounts globally.

37. How does password hashing work?
  - **Answer:** One-way cryptographic transformation (e.g., `bcrypt`, `argon2`) that converts cleartext passwords into fixed-length hashes using a unique random **salt** for every user. Verifying passwords involves hashing the input password with the stored salt and comparing hashes.
  - **Key Concepts:** One-way function, random salt (prevents Rainbow Table attacks), `passlib.context.CryptContext`.
  - **Example:** `pwd_context.hash("secret123")` -> `$2b$12$e8...`.

38. What is OAuth2 PasswordRequestForm?
  - **Answer:** A built-in FastAPI dependency class (`OAuth2PasswordRequestForm = Depends()`) that automatically parses incoming request form data expecting standard fields `username` and `password` sent via `application/x-www-form-urlencoded`.
  - **Key Concepts:** Swagger authentication integration, form-data parsing (`username`, `password`).
  - **Example:** Used inside `/token` login endpoints for direct compatibility with Swagger UI "Authorize" button.

39. How do protected routes work in FastAPI?
  - **Answer:** Protected route functions include a dependency parameter (`current_user: User = Depends(get_current_user)`). The dependency extracts the Bearer token from headers, verifies JWT signature, fetches user state, and rejects unauthorized calls with HTTP 401.
  - **Key Concepts:** Security dependencies, `OAuth2PasswordBearer`, token verification.
  - **Example:** `@app.get("/users/me") def get_me(user: User = Depends(get_current_user)): return user`.

40. What happens when a JWT token expires?
  - **Answer:** The JWT payload contains an `exp` (expiration timestamp) claim. When `jwt.decode()` is called after expiration, the library raises an `ExpiredSignatureError`. FastAPI catches this exception and returns an HTTP `401 Unauthorized` response to client.
  - **Key Concepts:** `exp` claim, token invalidation, 401 Unauthorized redirect to login/refresh.
  - **Example:** Returning `HTTPException(status_code=401, detail="Token has expired")`.

---

# Alembic & Database Migrations (41–43)

41. What problem does Alembic solve?
  - **Answer:** As database schemas evolve over time, Alembic automates tracking, generating, and applying database DDL schema changes (adding tables, altering columns, dropping constraints) across different environments without losing existing database data.
  - **Key Concepts:** Schema version control, auto-generating migration scripts, database evolution.
  - **Example:** Adding a `phone_number` column to existing production `users` table safely.

42. Why are migrations better than recreating the database?
  - **Answer:** `Base.metadata.create_all()` creates tables if they don't exist, but CANNOT modify existing tables or columns, requiring database drop and data loss. Migrations alter live schemas incrementally while preserving production data.
  - **Key Concepts:** Production data preservation, incremental DDL execution, rollback safety.
  - **Example:** Applying `alembic upgrade head` in production CI/CD pipelines.

43. How do you roll back a migration?
  - **Answer:** Execute Alembic downgrade command: `alembic downgrade -1` (rolls back 1 version) or `alembic downgrade <revision_id>` to revert to a specific past schema state.
  - **Key Concepts:** `downgrade()` function execution, revision tracking.
  - **Example:** Reverting a faulty database column migration step.

---

# Docker & Deployment (44–47)

44. What should a production Dockerfile for FastAPI include?
  - **Answer:** Use a slim multi-stage Python base image, set working directory, copy dependencies (`requirements.txt`), run `pip install --no-cache-dir`, copy application code, expose port 8000, and run Uvicorn/Gunicorn as non-root user.
  - **Key Concepts:** Lightweight base image (`python:3.11-slim`), layer caching, non-root user, Uvicorn CMD.
  - **Example:**
  ```dockerfile
  FROM python:3.11-slim
  WORKDIR /app
  COPY requirements.txt .
  RUN pip install --no-cache-dir -r requirements.txt
  COPY . .
  CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
  ```

45. Difference between Docker Image and Docker Container.
  - **Answer:** **Docker Image:** Read-only template file containing Python runtime, app code, and libraries. **Docker Container:** Isolated running process instance executed from a Docker image.
  - **Key Concepts:** Static template (Image) vs Active running process (Container).
  - **Example:** `docker build -t fastapi-app .` creates image; `docker run -p 8000:8000 fastapi-app` launches container.

46. Why use Docker Compose with FastAPI and PostgreSQL?
  - **Answer:** Docker Compose orchestrates running multiple container services (FastAPI web container + PostgreSQL DB container) together, managing shared networks, environment variables, startup order (`depends_on`), and persistent volume storage in one declarative `docker-compose.yml` file.
  - **Key Concepts:** Multi-container management, bridge networking, persistent volume mounts.
  - **Example:** Running `docker-compose up` launches FastAPI and PostgreSQL configured to talk over internal Docker network.

47. Why should environment variables be used instead of hard-coded credentials?
  - **Answer:** Hard-coding database passwords and JWT secrets in code risks leaking sensitive credentials in version control (Git). Environment variables (`pydantic-settings` / `.env`) allow dynamic configuration separation across Dev, Staging, and Production.
  - **Key Concepts:** Security isolation, 12-Factor App methodology, `pydantic-settings`.
  - **Example:** `class Settings(BaseSettings): DATABASE_URL: str; SECRET_KEY: str`.

---

# Testing & CI/CD (48–50)

48. How do you test FastAPI endpoints using `TestClient`?
  - **Answer:** FastAPI provides `TestClient` (built on `httpx` / `starlette`). It simulates HTTP requests against the FastAPI app in-memory without spawning a live network server, allowing assertions on response status codes and JSON payloads using `pytest`.
  - **Key Concepts:** In-memory request testing, `pytest`, status code & payload assertions.
  - **Example:**
  ```python
  from fastapi.testclient import TestClient
  from app.main import app

  client = TestClient(app)

  def test_read_main():
      response = client.get("/")
      assert response.status_code == 200
      assert response.json() == {"msg": "Hello World"}
  ```

49. What are pytest fixtures, and why are they useful?
  - **Answer:** Pytest fixtures (`@pytest.fixture`) are setup and teardown helper functions that supply test dependencies (test database sessions, mocked API tokens, clean dataset states) across test cases, ensuring test isolation and reusable code.
  - **Key Concepts:** Setup/teardown automation, test isolation, database override fixture (`app.dependency_overrides`).
  - **Example:** Creating a clean SQLite test database session fixture before every test function runs.

50. Explain how a GitHub Actions CI/CD pipeline works for a FastAPI application.
  - **Answer:**
  1. Trigger: Developer pushes code or opens Pull Request on `main`.
  2. Runner: GitHub spins up a clean Linux VM runner.
  3. CI: Checks out code, sets up Python, installs dependencies, runs `flake8`/`black` linter, executes `pytest` suite.
  4. CD: If tests pass, builds Docker image, logs into container registry (Docker Hub / AWS ECR), pushes image, and triggers production deployment restart.
  - **Key Concepts:** Automated testing workflow, Docker build & push, CD deployment trigger.
  - **Example:** `.github/workflows/main.yml` running pytest and deploying container automatically.

---

## Interview Follow-up Questions (Very Likely)

After many of the questions above, interviewers may ask:

* Can you explain what happens internally?
* Can you draw the request flow?
* How did you implement this in one of your projects?
* What are the common mistakes?
* What are the security implications?
* How would you scale this in production?
* How would you optimize performance?
* What are the alternatives?
* How would you debug an issue here?
* How would you test this feature?

