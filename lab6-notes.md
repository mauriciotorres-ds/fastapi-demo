# Lab 6 Notes — Docker Compose, FastAPI & MongoDB

---

## Part 1.2 — Code Review Questions

**What base image does the `Dockerfile` use?**

> The base image is `python:3.11-alpine3.20`
> FROM python:3.11-alpine3.20 - Code used in the Dockerfile
> The base image is the foundation of the container, which is a minimal operating system with Python 3.11 pre-installed, pulled from Docker Hub. main.py and requirements.txt are the app's files that get copied into that base. The base image is what the app lives inside of, not the app itself.




**How many services are defined in `docker-compose.yml`? What are their names?**

>  2 - api and mongodb. Two completely seperate images running as two seperate containers. 

**Which port does FastAPI listen on inside the container, and which host port is it mapped to?**

> Host:container , 8000:80
> FastAPI listens on port 80 inside the container, and Docker maps that to port 8000 on my laptop

**What environment variable tells FastAPI where to find MongoDB?**

>     environment:
>      - MONGO_URI=mongodb://mongodb:27017/ 
> This line tells the FastAPI app, that MongoDB is reachable at this address on the docker network. 

**What do `insert-one.py` and `insert-many.py` do?**

> They're seed scripts for populating the database with fake test data. insert-one.py manually inserts a single hardcoded person record (name + email) into MongoDB. insert-many.py does the same but inserts a batch of records at once 

---

## Part 2 — Bringing the Stack Up
**Side Notes**
> docker compose build reads the Dockerfile and builds the image. It installs Python, copies your code in, sets everything up. But nothing is running yet.
> docker compose up -d takes that image (plus the mongo image) and actually starts the containers. The -d stands for "detached," runs everything in the background so the terminal stays clean and usable instead of being locked up showing a wall of logs. 

**What output did you see after running `docker compose up -d`?**

> [+] Running 4/4

**What does `docker compose ps` show? What is in the STATUS column?**

> NAME                     IMAGE              COMMAND                  SERVICE   CREATED         STATUS         PORTS
> fastapi-demo-api-1       fastapi-demo-api   "fastapi run app/mai…"   api       3 minutes ago   Up 3 minutes   0.0.0.0:8000->80/tcp, [::]:8000->80/tcp 
> fastapi-demo-mongodb-1   mongo:latest       "docker-entrypoint.s…"   mongodb   3 minutes ago   Up 3 minutes   0.0.0.0:27017->27017/tcp, [::]:27017->27017/tcp

---

## Part 3 — Watching Your Containers
**What log message appears when FastAPI starts successfully? What does it tell you about the ASGI server being used?**
>  Asynchronous Server Gateway Interface = ASGI
> Uvicorn (the ASGI server), receives the raw HTTP request, hands it to FastAPI (the framework), FastAPI runs your Python code, sends a response back through Uvicorn

> INFO:     Uvicorn running on http://0.0.0.0:80 
> INFO:     Application startup complete
> This tells you that Uvicorn is the ASGI server being used. Uvicorn acts as the layer between incoming HTTP requests and the FastAPI application — it listens on port 80 inside the container, receives raw requests, and hands them off to FastAPI to process. 



**Screenshot #1:** `docker stats --no-stream`
- Which container uses more memory at idle?
- What is the MEM USAGE / LIMIT ratio for each?

> At Idle, mongodb uses more memory. 
> Mem usage /Limit ratio
> API:  268.8MiB / 7.653GiB, mongodb: 372.3MiB / 7.653GiB   

**What log message appears when FastAPI starts successfully?**

> The log message that appears when FastAPI starts successfully is Uvicorn running on http://0.0.0.0:80 along with Application startup complete. This says thatUvicorn is the ASGI server being used, it's the layer that listens for incoming HTTP requests and hands them off to FastAPI to process.


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

> Your 

---

## Part 6 — Compose Lifecycle

**After running `docker compose stop` and `docker compose start`, is your data still there? Why?**

> Your answer 

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

