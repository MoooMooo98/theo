# Storm scene

Standalone Three.js particle scene. Self-contained `index.html` — no build step,
loads Three.js r0.143.0 via an ES-module importmap from unpkg.

## ⚠️ Do not open by double-clicking

`index.html` uses `<script type="module">` with `import` statements. Every
browser blocks module imports when a page is opened via `file://` (CORS) — you
will get a **blank black page**, not an error dialog. This is standard browser
behaviour, not specific to this file (the official three.js examples have the
same restriction).

## Run it

**Option A — this project's dev server** (already running on port 3007 if
`yarn dev` is up):

```
http://localhost:3007/storm-scene/index.html
```

**Option B — standalone, no Next.js needed:**

```bash
cd public/storm-scene
python3 -m http.server 8080
```

Then open <http://localhost:8080>.
