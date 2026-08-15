# Garden Scout Plugin Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Package the supplied Garden Scout skill as a validated personal Codex plugin backed by its private GitHub repository.

**Architecture:** The private repository is the canonical plugin source. A generated personal-marketplace scaffold provides the installed copy, and the canonical skill and manifest metadata are synchronized into both locations before validation.

**Tech Stack:** Markdown, JSON, Python plugin-creator utilities, Git, GitHub CLI/SSH.

---

### Task 1: Scaffold and Populate the Plugin

**Files:**
- Create: `.codex-plugin/plugin.json`
- Create: `skills/garden-scout/SKILL.md`
- Preserve: `docs/`

- [ ] **Step 1:** Run the plugin-creator scaffold for `garden-scout` with skills and the default personal marketplace.
- [ ] **Step 2:** Copy the supplied `garden-scout-SKILL.md` into `skills/garden-scout/SKILL.md` in the repository and installed plugin.
- [ ] **Step 3:** Copy the validated generated manifest into the repository plugin root and tailor its Garden Scout presentation metadata.

### Task 2: Validate Both Copies

**Files:**
- Verify: `.codex-plugin/plugin.json`
- Verify: `skills/garden-scout/SKILL.md`
- Verify: `~/plugins/garden-scout/.codex-plugin/plugin.json`

- [ ] **Step 1:** Run the plugin validator against the repository root and expect a success result.
- [ ] **Step 2:** Run the plugin validator against the installed personal plugin and expect a success result.
- [ ] **Step 3:** Confirm the personal marketplace entry includes the normalized name, local path, default policy fields, and category.

### Task 3: Publish the Private Repository

**Files:**
- Add: all current repository files, including `docs/`

- [ ] **Step 1:** Review repository status and confirm no unrelated files are excluded.
- [ ] **Step 2:** Commit the initial plugin and documentation on `main` with message `feat: add Garden Scout plugin`.
- [ ] **Step 3:** Push `main` to the existing private `origin` and verify the upstream branch.
