# Add a Personal Skill to ChatGPT

This is the repeatable workflow for adding a personal `SKILL.md` to
ChatGPT. Use it whenever you create a new lightweight skill such as
**Garden Scout**.

> **Important:** OpenAI currently describes these as **Skills** inside
> the **Plugins** area of ChatGPT. A plugin can contain skills, apps,
> and app templates. For a simple workflow that only needs instructions
> and ChatGPT's built-in capabilities, a Skill is enough.

## 1. Prepare the skill

At minimum, have a valid `SKILL.md`.

Recommended project layout:

``` text
garden-scout/
├── README.md
└── SKILL.md
```

The skill should begin with YAML frontmatter:

``` yaml
---
name: garden-scout
description: Fast nursery plant identification and South Florida growing guidance.
---
```

Then put the workflow instructions below the frontmatter.

### Before uploading

Quick check:

-   The `name` is short and unique.
-   The `description` clearly says **when the skill should be used**.
-   The instructions are self-contained.
-   Keep the skill focused on one workflow.
-   Remove secrets, API keys, passwords, and private credentials.
-   Test examples are useful but optional.

------------------------------------------------------------------------

## 2. Open Skills in ChatGPT

Use the **ChatGPT web or desktop app**.

1.  Open **Plugins** in the ChatGPT sidebar.
2.  Select the **Skills** tab.
3.  Select **Create**.

You should see options including:

-   **Create with chat**
-   **Create with editor**
-   **Upload from your computer**

For an existing GitHub/local skill, use **Upload from your computer**.

------------------------------------------------------------------------

## 3. Upload the skill

1.  Choose **Upload from your computer**.
2.  Select your skill file/package.
3.  Review the skill information ChatGPT detects.
4.  Correct the name, description, or instructions if necessary.
5.  Save/install the skill.

For a simple skill, there is no need to create an app, MCP server, OAuth
connection, or API integration.

------------------------------------------------------------------------

## 4. Confirm installation

Return to:

**Plugins → Skills**

Look under:

**Created by me** or **Installed**

Confirm that the new skill appears there.

Open it once and verify that the displayed description accurately
represents its trigger/use case.

------------------------------------------------------------------------

## 5. Test in a new chat

Always test the skill in a **fresh conversation**.

For Garden Scout, a good first test is:

``` text
[attach plant photo]

What is this?
```

The skill should automatically recognize that the request matches its
workflow.

Then test a follow-up:

``` text
save it
```

Confirm that the result follows the Markdown format defined by the
skill.

### Test the important paths

For an image-based skill, test at least:

1.  Clear plant + readable nursery label
2.  Clear plant without a label
3.  Ambiguous plant photo
4.  Plant name supplied as text
5.  Follow-up question
6.  `save it`

You do not need exhaustive testing before using a personal skill. The
goal is to catch obvious trigger or formatting problems.

------------------------------------------------------------------------

## 6. Use the skill normally

Once installed, ChatGPT can automatically use an installed skill when
your request matches its description.

You can also explicitly select/invoke plugin capabilities from ChatGPT
when needed.

For Garden Scout, the normal nursery workflow should simply be:

``` text
Take photo
    ↓
Attach photo in ChatGPT
    ↓
Ask "What is this?"
    ↓
Review plant card
    ↓
Like it?
    ↓
Say "save it"
    ↓
Continue to next plant
```

Avoid unnecessary prompts. The skill should contain the workflow so you
do not have to explain it each time.

------------------------------------------------------------------------

## 7. Update the skill

Treat GitHub as the **source of truth**.

Recommended workflow:

``` text
GitHub/local repo
      ↓
Edit SKILL.md
      ↓
Commit changes
      ↓
Update/re-upload skill in ChatGPT
      ↓
Test in fresh chat
```

Example:

``` bash
git add SKILL.md
git commit -m "refine plant identification workflow"
git push
```

Do not make substantial changes only in the ChatGPT editor unless you
also copy those changes back into the repository.

------------------------------------------------------------------------

## 8. Web, desktop, and mobile

Skill availability can differ by ChatGPT surface.

OpenAI currently notes that Personal Skills may need to be added
separately between **desktop** and **web/mobile** rather than
automatically syncing everywhere.

After creating a skill, verify it on the device you actually intend to
use.

For Garden Scout, this is especially important because the primary
workflow is likely:

``` text
iPhone → camera/photo → ChatGPT → Garden Scout
```

Test the complete workflow on the iPhone before relying on it at a
nursery.

------------------------------------------------------------------------

## 9. Simple skill vs. app/MCP

Do **not** add an app or MCP server unless the workflow actually needs
access to an external system.

Use only a Skill when the workflow needs things ChatGPT already
provides, such as:

-   instructions
-   vision
-   reasoning
-   web research
-   standardized output
-   file/document creation

Consider adding an app/MCP integration later when ChatGPT needs to
directly:

-   query your own database
-   call your private API
-   modify an external application
-   read/write external records
-   perform authenticated actions

Start simple.

------------------------------------------------------------------------

# Reusable Workflow

For the next personal skill you create:

``` text
1. Create GitHub repo
2. Write SKILL.md
3. Test instructions locally/review manually
4. ChatGPT → Plugins
5. Skills → Create
6. Upload from computer
7. Install/save
8. Test in a fresh chat
9. Test on the intended device
10. Keep GitHub as source of truth
```

## Rule of thumb

**If ChatGPT already has the capabilities required to perform the
workflow, start with a Skill.**

Add an app/MCP integration only when the skill needs access to an
external system or action that ChatGPT cannot perform by itself.

------------------------------------------------------------------------

## Official documentation

-   OpenAI Help Center --- **Skills in ChatGPT**
-   OpenAI Help Center --- **Plugins in ChatGPT and Codex**

Because the Plugins/Skills interface is evolving, check the current
OpenAI documentation if the UI labels differ from this guide.
