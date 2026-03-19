---
mode: agent
description: Scan for new st-learning-* repos and update the index README and JSON
---

You are updating the `st-learning` index repository. Your job is to discover any `st-learning-*` repositories owned by `bhf` that are not yet listed in `st-learning-index.json`, fetch their READMEs, and update both index files accordingly.

## Steps

1. **Discover all repos** by running:
   ```
   gh repo list bhf --limit 100 --json name,description,url,isPrivate
   ```
   Filter to those whose `name` starts with `st-learning-`.

2. **Compare against the current index** by reading `st-learning-index.json`. Identify any repos present in GitHub but absent from the JSON — these are new repos to add.

3. **For each new repo**, fetch its README:
   ```
   gh api repos/bhf/<name>/readme --jq '.content' | base64 -d
   ```
   Read the README to understand: what the repo demonstrates, its key classes/packages/examples, and any notable requirements (e.g. JDK version).

4. **Update `st-learning-index.json`** — append a new object for each new repo following this schema:
   ```json
   {
     "name": "st-learning-<topic>",
     "url": "https://github.com/bhf/st-learning-<topic>",
     "topics": ["java", "<topic>", "..."],
     "private": <true|false>
   }
   ```

5. **Update `README.md`** — for each new repo add:
   - A **ToC entry** under the appropriate heading in `## Table of Contents`
   - A **`###` section** under `## Repository Index` following this pattern:
     ```markdown
     ### [st-learning-<topic>](https://github.com/bhf/st-learning-<topic>)

     **Topics:** `java` `<topic>` `...`

     One-paragraph description of what is demonstrated.

     **Key classes / examples:** (table or bullet list derived from the repo README)

     ---
     ```
   - A **row** in the `## Quick Reference` table

## Constraints

- Do **not** add run/build command blocks to README entries — those belong in the individual repo READMEs.
- README and `st-learning-index.json` must list exactly the same repos with matching `private` flags.
- Preserve the existing section order in `README.md` (see `.github/copilot-instructions.md`).
- If no new repos are found, report that the index is already up to date and make no changes.
