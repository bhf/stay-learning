# Copilot Instructions for `stay-learning` Index Repository

This repository acts as the central meta-index for `stay-learning-*` repositories (owned by `bhf`). It tracks individual, targeted learning repositories across various languages and patterns.

## Repository Architecture & Core Files

- **`README.md`**: The primary human and LLM entry point. It serves as an aggregated index of all known topic repositories.
- **`st-learning-index.json`**: The machine-readable source of truth.
- Both files **must** stay perfectly synchronized. If a repository is added to the generic JSON list, it MUST have a corresponding entry in the `README.md`.

## Naming & Indexing Conventions

- **Repository Naming**: Individual repositories strictly follow the pattern `stay-learning-<topic>`.
- **Delegation of Responsibility**: Do **not** place run, build, or deployment instructions in this meta-index `README.md`. Application-specific commands belong in the individual repo's README.
- **Topics**: Sub-repository topics should be included in `st-learning-index.json` under the `"topics"` array and visualized concisely in the `README.md` as inline code blocks (e.g., `**Topics:** \`java\` \`streams\``).

## Strict `README.md` Structure

When modifying `README.md`, you **must preserve** the following exact section order:

1. **HTML comment metadata block** (for indexing purposes)
2. **Badge + title + `brain.gif` + tagline**
3. **`## Table of Contents`**
4. **`## How to Use This Index`**
5. **`## Repository Index`** (Contains one `###` section per repository)
   - Must use the format: `### [stay-learning-<topic>](https://github.com/bhf/stay-learning-<topic>)`
   - Must include `**Topics:**` followed by a concise description
6. **`## Quick Reference`** (Summary table)
7. **`## For LLMs and MCP Tools`**

## Developer Workflows

- **Updating the Index**: The primary automation workflow relies on `.github/prompts/update-index.prompt.md`. This prompt instructs an AI agent to query GitHub via `gh repo list bhf` and `gh api`, fetch unseen `stay-learning-*` READMEs, and generate the proper entries in both `st-learning-index.json` and `README.md`.
- Ensure changes pass manual inspection to confirm that `private` flags, URIs, and descriptions correctly align between the JSON and Markdown files.