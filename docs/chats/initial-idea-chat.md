I’d make this a skill-first plugin, not an MCP app initially. Your nursery workflow is almost entirely “photo/name → vision identification → short standardized answer,” which is exactly what a skill is good at. Current OpenAI documentation says plugins can package skills and apps together, so we can add a write-capable app later without redesigning the workflow.  

I created a first version based on your attached bh-add-plant skill, but deliberately made it much leaner:

* It accepts photo, label photo, name, or name + photo.
* A readable nursery label takes precedence; otherwise it uses vision.
* No confirmation round-trip for a high-confidence identification.
* The default response is only about 80–140 words, optimized for scanning on an iPhone.
* It assumes South Florida / Palm Beach County conditions.
* Standard fields are Sun, Water, Pot, In-ground, Growth, Pets, South Florida notes, and a simple Buy? Yes / Maybe / No.
* Pet safety uses Generally non-toxic, Toxic, or Not confirmed rather than guessing.
* Web research is selective rather than automatic, with UF/IFAS and ASPCA prioritized when verification matters.
* A later save it can create a standardized Markdown garden-journal entry without slowing the initial nursery lookup.

You can inspect the skill directly or use the ZIP as the starting package:

Download SKILL.md⁠￼

Download garden-nursery-scout.zip⁠￼

What the nursery interaction should feel like

You take a picture and invoke the plugin. Ideally the response is something like:

Firebush (Hamelia patens)
ID: High confidence

* Sun: Full sun to part sun; best flowering in sun
* Water: Moderate until established; then fairly drought tolerant
* Pot: Good — use a large container and prune for size
* In ground: Excellent — very well suited to South Florida
* Growth: ~6–12 ft × 4–8 ft; fast
* Pets: ❓ Not confirmed
* South Florida: Heat-loving and attracts butterflies/hummingbirds; can grow aggressively in good conditions

Buy? Yes — excellent landscape choice for South Florida if you have room.

Then while standing there you can ask:

What size pot?

or:

Compare this to the last one.

or simply:

save it

The skill explicitly treats those short statements as referring to the current plant.

Saving is the only part I would separate

For version 1, I would let the skill create the Markdown file/content when the environment already has project file access. ChatGPT Projects themselves are designed to keep chats, instructions, and files together, so they’re a reasonable place to organize this kind of journal.  

For your actual personal garden application, however, I think the better eventual architecture is:

garden-nursery-scout
│
├── skill
│   └── SKILL.md
│
└── app                 ← add later
    └── MCP
        └── save_plant()

The skill handles intelligence and formatting.

The optional MCP app would do one thing:

save_plant(
    plant_name,
    scientific_name,
    markdown,
    photo?
)

and put the entry into your application’s repository/database. OpenAI’s current app architecture uses MCP for custom integrations and, where write actions are supported, custom MCP apps are the mechanism for creating or modifying data.  

That separation is especially useful here because identifying plants should remain fast even if your garden application or its API is unavailable.

One thing I’d change before calling this finished is the journal schema. The schema I put in SKILL.md is intentionally generic:

garden-journal/
└── plants/
    └── firebush.md

with frontmatter such as:

name: Firebush
scientific_name: Hamelia patens
status: considering
identified_on: 2026-08-15
source: nursery
sun: Full sun
water: Moderate
pot: Good
ground: Excellent
pet_safety: Not confirmed

Since this is meant for another one of your personal apps, I’d next align that save format with the actual application’s directory structure/schema rather than inventing a parallel format. That would leave us with a very small, focused plugin: probably one skill file plus, eventually, one MCP save tool.