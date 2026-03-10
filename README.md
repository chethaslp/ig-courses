# IG Course Content Repository

This repository holds all course content for the IG educational platform. Each course lives on its **own branch** — the branch name is the course slug used in the platform URL (`/classroom/[branch-name]`). The `main` branch contains only this README.

---

## Branch Structure

| Branch | Purpose |
|---|---|
| `main` | This README only. No course content. |
| `web-dev` | Course: "Web Dev Fundamentals" |
| *(one branch per course)* | |

---

## Course Branch File Structure

Every course branch must follow this layout (all content at the **root** of the branch — no top-level course folder):

```
index.json                              # Course metadata (required)
thumbnail.jpeg                          # Course thumbnail (optional)

[section-id]/
  index.json                            # Section metadata (required)

  [module-id]/
    index.json                          # Module metadata (required)
    video.mp4                           # Required for "lecture" type
    guide.md                            # Required for "article" type; optional supplement for lectures
    actions.csv                         # Optional — timed video interactions
    resources.csv                       # Optional — sidebar resources
```

> Folder names must be **kebab-case** with no numeric prefixes (e.g. `getting-started`, `intro-to-hooks`).

---

## File Specifications

### `/index.json` — Course Metadata

```json
{
  "title": "Intro to React",
  "description": "A beginner-friendly introduction to React.",
  "authors": ["Jane Smith"],
  "tags": ["react", "javascript", "frontend"],
  "difficulty": "Beginner",
  "duration": "3 hours",
  "thumbnail": "thumbnail.jpeg",
  "sections": [
    { "id": "getting-started", "order": 1 },
    { "id": "components", "order": 2 },
    { "id": "hooks", "order": 3 }
  ]
}
```

| Field | Required | Description |
|---|---|---|
| `title` | ✅ | Display name of the course |
| `description` | ✅ | Short summary shown on the course card |
| `authors` | ✅ | Array of author names |
| `tags` | ✅ | Array of topic tags |
| `difficulty` | ✅ | `"Beginner"`, `"Intermediate"`, or `"Advanced"` |
| `duration` | ✅ | Approximate total duration (e.g. `"3 hours"`) |
| `thumbnail` | ❌ | Filename of the thumbnail image at the branch root |
| `sections` | ✅ | Ordered array of `{ id, order }` — IDs must match section folder names |

---

### `[section-id]/index.json` — Section Metadata

```json
{
  "title": "Getting Started",
  "modules": ["welcome", "setup-env", "hello-world"]
}
```

| Field | Required | Description |
|---|---|---|
| `title` | ✅ | Display name of the section |
| `modules` | ✅ | Ordered array of module folder names — defines display order |

---

### `[section-id]/[module-id]/index.json` — Module Metadata

```json
{
  "title": "Setting Up Your Environment",
  "description": "Install Node.js and create your first project.",
  "type": "lecture"
}
```

For **exercise** modules:

```json
{
  "title": "Keyword Challenge",
  "description": "Find the secret keyword hidden in the docs.",
  "type": "exercise",
  "exerciseType": "keyword",
  "validation": {
    "keyword": "react-rocks"
  }
}
```

| Field | Required | Description |
|---|---|---|
| `title` | ✅ | Display name of the module |
| `description` | ❌ | Short summary |
| `type` | ✅ | `"lecture"`, `"article"`, or `"exercise"` |
| `exerciseType` | Exercise only | `"keyword"`, `"quiz"`, or `"game"` |
| `validation` | Exercise only | Validation data (e.g. `{ "keyword": "secret" }`) |

---

### `actions.csv` — Timed Video Actions (lectures only)

Columns: `timestamp_ms, action_name, [...args]`

Use `-1` as the timestamp to trigger an action immediately on page load.

```csv
-1,checkpoint,"Start","Welcome to the course!"
-1,maximise
16000,minimise
28000,highlight,chat_window,3000
34000,prompt,text,"Any questions so far?"
40000,prompt,checkbox,"Which topics interest you?","React","Next.js","TypeScript"
50000,text,"Great choice!",3000
60000,task,terminal_window,"Run: npm install"
```

| Action | Arguments | Description |
|---|---|---|
| `maximise` | — | Expand video to full overlay |
| `minimise` | — | Shrink video to sidebar |
| `highlight` | `id, duration_ms` | Highlight a DOM element by id for a duration |
| `switch-theme` | `light\|dark\|system` | Change the app theme |
| `prompt` | `text\|checkbox, question, [...options]` | Pause video and show a prompt |
| `checkpoint` | `buttonText, [description]` | Pause video with a blocking continue button |
| `text` | `text, [duration_ms]` | Show a brief text overlay |
| `task` | `resourceId, instruction` | Highlight a resource and show an instruction |
| `highlight-resource` | `resourceId` | Highlight an item in the resource sidebar |

> `prompt` and `checkpoint` pause the video. Playback resumes after the user interacts.

---

### `resources.csv` — Sidebar Resources (all module types)

Columns: `id, type, content`

```csv
docs_link,link,https://react.dev
install_command,command,npm create vite@latest
code_snippet,code,const App = () => <h1>Hello</h1>
```

| Type | Description |
|---|---|
| `link` | Clickable URL with auto-generated preview |
| `command` | Terminal command with copy button |
| `code` | Code snippet with copy button |

---

## Contributing a New Course

1. **Create a new branch** from `main` — name it using the course slug (kebab-case):
   ```bash
   git checkout main
   git checkout -b my-new-course
   ```

2. **Add your files** following the structure above. Start with `index.json` at the root.

3. **Validate your structure** before pushing:
   - Every section listed in the course `index.json` must have a corresponding folder with its own `index.json`.
   - Every module listed in a section's `modules` array must have a corresponding folder with its own `index.json`.
   - `type` in each module `index.json` must be `"lecture"`, `"article"`, or `"exercise"`.

4. **Push the branch** — the platform will automatically pick it up within 1 hour (or immediately in dev with cache cleared):
   ```bash
   git push origin my-new-course
   ```

5. **Do not merge into `main`** — each course lives permanently on its own branch.

---

## Editing an Existing Course

Check out the course branch directly:

```bash
git checkout intro-to-react
# make changes
git push origin intro-to-react
```

The platform caches GitHub API responses for 1 hour (`revalidate: 3600`). Changes will propagate automatically after the cache expires.
