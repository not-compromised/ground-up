# Syllabus — concept frontier

Read by the `ground-up` skill at Gate A and when planning study sessions. Evidence
lives in [learning-log.md](learning-log.md); this file only orders what comes next.
"→ next" marks the frontier per track. Tracks advance independently; a next-marker
moves only when the log shows the concept solid. Seeded 2026-08-25 from Odin
Foundations (JS), a Python reading track (the repos are Python-heavy), and the web
layer stack.

## JS — Odin Foundations order (mined, not marched)

Already taught once, re-test due (see log): comments · functions/parameters/return ·
`export` · type annotations · operator precedence · integer money math · basis
points. Solid: `Math.round`.

→ next:
1. variables (`let`/`const`, scope)
2. data types & conditionals
3. loops & arrays
4. objects
5. problem solving, errors, clean code
6. DOM manipulation & events

Each maps to an Odin Foundations lesson; the lesson gets prescribed when a concept
grades partial/gap twice (stuck-twice rule), never walked linearly.

## Python reading — own repos are the material

→ next:
1. functions, modules, imports
2. dicts & lists
3. f-strings
4. exceptions (`try`/`except`)
5. decorators as used in routers (`@app.get`)
6. classes (as the dashboard uses them)
7. context managers (`with`)
8. venvs & pip

## Web layers — tied to the dashboard chunks

→ next:
1. the request path: browser → Caddy → app → SQLite → response
2. routes & handlers
3. JSON APIs
4. sessions, auth, CSRF
5. static files vs rendered pages
6. timers/cron writing files the app reads

Later: Docker/compose internals · TLS and certs (parts already solid — log,
networking section).

## Beyond my stack — the shelf ("explore <topic>" pulls from here)

TypeScript (firepos is repo 3) · pytest and testing properly · git internals ·
React basics · SQL beyond SQLite basics · HTTP caching & headers · CI pipelines
