# Lab 6 Notes — Docker Compose, FastAPI & MongoDB

---

## Part 1.2 — Code Review Questions

**What base image does the `Dockerfile` use?**

> Testing Testing 

**How many services are defined in `docker-compose.yml`? What are their names?**

Testing Testing 

**Which port does FastAPI listen on inside the container, and which host port is it mapped to?**

> Your answer here

**What environment variable tells FastAPI where to find MongoDB?**

> Your answer here

**What do `insert-one.py` and `insert-many.py` do?**

> Your answer here

---

## Part 2 — Bringing the Stack Up

**What output did you see after running `docker compose up -d`?**

> Your answer here

**What does `docker compose ps` show? What is in the STATUS column?**

> Your answer here

---

## Part 3 — Watching Your Containers

**Screenshot #1:** `docker stats --no-stream`
- Which container uses more memory at idle?
- What is the MEM USAGE / LIMIT ratio for each?

> Your answer here

**What log message appears when FastAPI starts successfully?**

> Your answer here

---

## Part 4 — Interacting with the REST API

**Screenshot #2:** `GET /people` response with 3+ documents

**What happens when you run `curl http://localhost:8000/` ?**

> Your answer here

**After running `insert-many.py`, how many documents are in the collection?**

> Your answer here

---

## Part 5 — MongoDB Compass

**Screenshot #3:** Compass showing collection with expanded document

**What is the name of the database and collection the FastAPI app uses?**

> Your answer here

**What does the `_id` field look like in a document? Why does MongoDB add it?**

> Your answer here

---

## Part 6 — Compose Lifecycle

**After running `docker compose stop` and `docker compose start`, is your data still there? Why?**

> Your answer here

---

## Part 7 — GitHub Actions

**Screenshot #4a:** Test workflow green checkmark

**Screenshot #4b:** Build workflow green checkmark + GitHub Packages page

**In your own words, what does the test workflow do step by step?**

> Your answer here

**What is the difference between `push: true` and `push: false` in the build workflow?**

> Your answer here

**What is GHCR and how is it different from Docker Hub?**

> Your answer here

---

## General Notes & Questions

-

