# Copilot Instructions

## What this repository is

`st-learning` is a **meta/index repository** — it contains no Java source code. Its only artifacts are:

- `README.md` — human- and LLM-readable index of all `st-learning-*` repos
- `st-learning-index.json` — machine-readable repo manifest consumed by MCP tools and agents
- `brain.gif` — header image

Do not add Java files, Gradle build files, or source code here.

## Repository family

All repos are owned by `bhf` and follow the naming convention `st-learning-<topic>`. Discover them via:
- The Quick Reference table in `README.md`
- `st-learning-index.json` (authoritative machine-readable list)
- GitHub search: `user:bhf st-learning`

Two repos are private (`st-learning-jpms`, `st-learning-base`) and require authenticated GitHub access.

## Adding a new repo to the index

When a new `st-learning-*` repo is created, update **both** files consistently:

1. **`README.md`** — add a new `###` section under `## Repository Index` following the existing pattern:
   ```markdown
   ### [st-learning-<topic>](https://github.com/bhf/st-learning-<topic>)

   **Topics:** `java` `<topic>` `...`

   One-paragraph description of what is demonstrated.

   **Key classes / examples:** (table or bullet list)
   ```
   Also add a row to the Quick Reference table and a ToC entry.

2. **`st-learning-index.json`** — add a corresponding object:
   ```json
   {
     "name": "st-learning-<topic>",
     "url": "https://github.com/bhf/st-learning-<topic>",
     "topics": ["java", "<topic>"],
     "private": false
   }
   ```

README and JSON must always be in sync — same repos, same visibility flags.

## Child repo conventions

Every `st-learning-*` example repo follows these conventions:

- **Language:** Java, JDK 21+ (some repos target JDK 24)
- **Build tool:** Gradle (Kotlin DSL preferred; some use Groovy DSL)
- **Standard commands:** `./gradlew build`, `./gradlew test`
- **Package root:** `com.bhf.learning.<topic>`
- **Bootstrap template:** Use `st-learning-base` (private) when creating a new repo

Do not include run instructions in README index entries — link to the individual repo README instead.

Every child repo README must include the StayTuned brand badge as the very first line, before the `#` title:
```markdown
<a id="top"></a>
[![StayTuned](https://img.shields.io/badge/~%24-StayTuned_-000000?style=flat&labelColor=000000&color=000000)](https://sanjeev.pages.dev)
```

## README structure conventions

Section order must be preserved:
1. HTML comment metadata block (front matter for tools)
2. Badge + title + `brain.gif` + tagline
3. Table of Contents
4. How to Use This Index
5. Repository Index (one `###` per repo)
6. Quick Reference (summary table)
7. For LLMs and MCP Tools (link to `st-learning-index.json`)
