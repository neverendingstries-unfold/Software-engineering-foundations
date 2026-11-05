Phase 1: Software Engineering Foundations (Weeks 1–8)
Outcome: Build, test, document, and release a small API that another person can run using only your README.

Use a small public automation or data-validation requirement. Write acceptance criteria before coding. Do not add an LLM unless deterministic code cannot solve the problem well.
Phase overview
Week	Focus	Required output
1	Python refresh, repository, virtual environment	Employee Record Validator with tests
2	Data structures, mutability, exceptions, generators	10 exercises with mistake notes
3	Modules, composition, type hints, configuration	Separate validation, logic, and I/O layers; mypy passes
4	Git branches, merge conflicts, code review	Review one public pull request; write a clear PR description
5	Testing, fixtures, mocks, logging, debugging	Tests for malformed input, duplicate IDs, and unexpected failures
6	HTTP, REST, JSON schemas, predictable errors	FastAPI service with validated requests and useful error responses
7	SQL, transactions, indexes, migrations	PostgreSQL persistence of valid and rejected records
8	Concurrency overview, Dockerfile, packaging, release	Tagged v1.0, container build, clean-machine setup test


Phase 1 topics to learn and practice, week by week
For each week, learn only the listed topics. Use official documentation first: the Python tutorial, pytest documentation, FastAPI tutorial, PostgreSQL documentation, and the free Pro Git book. Then complete the practice list from memory before looking anything up.
Week 1: Python refresh and first project
Learn
- Variables and types
- Control flow
- Functions and f-strings
- File I/O and the csv module
- Virtual environments, pip, and pinned requirements
- Running a first pytest test
- Writing a README
Practice

Build the Employee Record Validator:
- Read a CSV file.
- Check required fields, email format, date format, salary range, and unique employee ID.
- Print a report of rejected rows with the reason for each rejection.
- Write at least five tests.
Week 2: Data structures, errors, and generators
Learn
- Lists, dictionaries, sets, and tuples, and when each is fast
- Mutability and the mutable default-argument trap
- copy vs deepcopy
- try / except / finally
- Custom exceptions
- Comprehensions
- Generators and yield
- Context managers
- itertools basics
Practice

Solve 10 exercises, such as:
- Removing duplicates while keeping order
- Grouping records by department with a dictionary
- Counting word frequency
- Flattening a nested list
- Streaming a large file line by line with a generator
- Defining a custom exception hierarchy
- Reproducing the mutable-default bug on purpose
Write a short mistake note for every exercise you got wrong on the first attempt.
Week 3: Structure, types, and configuration
Learn
- Modules and packages
- Imports
- Separating validation, logic, and I/O
- Dataclasses
- Type hints and mypy
- pathlib
- Reading configuration from environment variables
- A small command-line interface with argparse or typer
Practice
- Split the validator into three modules: validation rules, processing logic, and file I/O.
- Replace loose dictionaries with typed models.
- Move thresholds into configuration.
- Get mypy to pass with no ignores.
Week 4: Git workflow and code review
Learn
- Commits and branches
- Merge vs rebase
- Resolving conflicts
- .gitignore
- Tags and pull requests
- Writing commit messages and PR descriptions
- Giving useful review comments
Practice
- Create a merge conflict on purpose and resolve it.
- Do all further work on a branch with a pull request.
- Read one small public pull request and leave two specific, polite comments (or write notes if you do not post them).
- Write a PR description that states the problem, the change, and how you tested it.
Week 5: Testing, logging, and debugging
Learn
- pytest fixtures and parametrization
- tmp_path, monkeypatch, and mocks
- Arrange–Act–Assert
- Test coverage
- The logging module and log levels
- Debugging with pdb or your editor's debugger
Practice
- Add tests for malformed rows, duplicate IDs, an empty file, and an unexpected exception (inject the failure with a mock).
- Add logging that never prints personal data.
- Set a coverage target and explain any gap.
- Plant a bug in a copy of your code and find it with the debugger, not print statements.
Week 6: HTTP, REST, and a first API
Learn
- HTTP methods and status codes
- Headers
- Which methods are safe and idempotent
- REST resource design
- JSON
- FastAPI routes
- Pydantic request and response models
- Custom error handlers
- The auto-generated OpenAPI page
- Calling APIs with curl and httpx
Practice

Expose the validator as an API with endpoints to:
- Submit records
- Fetch one record
- List rejected rows
Use one consistent error format, write API tests with the test client, and put copy-paste request examples in the README.
Week 7: SQL and persistence
Learn
- Tables
- Primary and foreign keys
- Unique and not-null constraints
- Transactions and the ACID idea
- Indexes and EXPLAIN
- Migrations with Alembic
- Connecting from Python with SQLAlchemy or psycopg
Practice
- Create tables for valid and rejected records through a migration.
- Save each batch inside one transaction so a failure leaves nothing half-written.
- Add a unique constraint and a test that proves duplicates are refused.
- Run EXPLAIN on one query before and after adding an index, and note the difference.
Week 8: Concurrency, packaging, and release
Learn
- Threads vs processes vs asyncio at overview level
- What the GIL means in practice
- Async endpoints in FastAPI
- Writing a Dockerfile
- Docker Compose with PostgreSQL
- pyproject packaging
- Semantic versioning
- A GitHub Actions workflow
Practice
- Make one batch step concurrent and measure whether it actually helps.
- Build a container and run the API plus database with Compose.
- Add CI that runs pytest, ruff, and mypy.
- Tag v1.0.
- Delete your environment and set it up again using only the README.
- Finish with the Phase 1 gate review below.
Project 1: Document-processing API / Employee Record Validator
Publish:
- The project specification
- API examples
- Test report
- CI log
- Release tag
- Code-review notes
Phase gate: do not move on until you can
- [ ] Reproduce the environment on a clean machine using only the README.
- [ ] Show tests for valid input, malformed input, missing fields, duplicates, and unexpected failures.
- [ ] Make a small change without breaking tests.
- [ ] Explain one code-review finding and its fix.