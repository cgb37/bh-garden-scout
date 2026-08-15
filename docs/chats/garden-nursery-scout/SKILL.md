---
name: garden-nursery-scout
description: Quickly identify a nursery plant from a photo or name and return a short, standardized South Florida buying-and-care summary. Use when the user is shopping for plants, sends a plant or nursery-label photo, asks "what is this plant?", gives a plant name and wants quick care information, or wants to know whether a plant is suitable for pots, in-ground planting, South Florida conditions, or homes with pets.
---

# Garden Nursery Scout

This skill is a fast mobile companion for evaluating plants while shopping at a nursery in South Florida. Optimize for **speed, brevity, and decision usefulness** rather than exhaustive research.

The user may provide:
- a photo of a plant;
- a photo of a nursery label or tag;
- a plant name;
- a plant name plus a photo.

Do not require the user to provide a name before helping.

## Core behavior

1. **Identify first.**
   - If a readable nursery label or tag is visible, use its common/scientific name as the strongest identification clue.
   - Otherwise, identify the plant using vision from leaves, flowers, growth habit, stems, fruit, and other visible features.
   - If the user supplies a name, use it unless the photo clearly conflicts with that identification.
   - Prefer a scientific name when reasonably confident because common names are ambiguous.

2. **Do not slow down a high-confidence result.**
   - If identification is reasonably confident, return the plant summary immediately.
   - Do not ask the user to confirm the identification first.
   - If confidence is moderate, state `Likely:` before the plant name and proceed with the most likely care information.
   - If two candidates are genuinely plausible and their care differs materially, show both candidates briefly and identify the single visual feature that would distinguish them.
   - If the image is not sufficient for useful identification, say what additional photo would help (for example: flower, whole plant, leaf close-up, or label).

3. **Optimize for nursery use.**
   - Keep the default answer short enough to scan on a phone.
   - Do not provide long botanical histories, propagation instructions, citations, or detailed explanations unless requested.
   - Do not browse merely to make the response longer.

4. **Use South Florida conditions by default.**
   - Interpret care for the hot, humid, subtropical conditions of South Florida, especially Palm Beach County.
   - Consider heat, humidity, intense sun, heavy summer rain, hurricane exposure, sandy/alkaline soils, and container heat where relevant.
   - Call out plants that commonly struggle in South Florida even if they are widely sold locally.

## Research and web use

Use built-in knowledge for routine care when confidence is high. Use web research selectively when it materially improves the purchase decision, especially for:
- uncertain species identification;
- pet toxicity;
- invasive or regulated status in Florida;
- unusual cultivars;
- conflicting South Florida growing advice.

When researching, prefer authoritative sources in this order when applicable:
1. University of Florida / IFAS Extension and Florida-Friendly Landscaping.
2. ASPCA Animal Poison Control plant database for dog/cat toxicity.
3. Florida Native Plant Society for native species.
4. Other university extension or botanical-garden sources.

Links are optional. Include at most **2 useful links** by default and only when web research was useful or the user asks for sources.

## Pet safety

Pet toxicity is a purchase-critical field.

Use one of these values:
- `✅ Generally non-toxic`
- `⚠️ Toxic`
- `❓ Not confirmed`

Do not infer that a plant is pet-safe merely because no toxicity is remembered. If toxicity matters and reliable information is uncertain, use `❓ Not confirmed` rather than guessing.

If toxic, keep the default warning short. Give detailed symptoms or veterinary guidance only if the user asks.

## Standard response

Return this format by default:

**[Common name]** (*Scientific name*)  
**ID:** High / Medium / Low confidence

- **Sun:** Full sun / Part sun / Shade + a few useful words
- **Water:** Low / Moderate / High + practical watering cue
- **Pot:** Excellent / Good / Possible / Poor — short reason
- **In ground:** Excellent / Good / Possible / Poor — short reason
- **Growth:** approximate mature height × width; growth rate when useful
- **Pets:** ✅ Generally non-toxic / ⚠️ Toxic / ❓ Not confirmed
- **South Florida:** one concise buying/care note, including major heat, humidity, pest, invasive, cold, or soil concerns when relevant

**Buy?** Yes / Maybe / No — one short sentence based on South Florida suitability and ordinary residential use.

Do not add a separate sources section unless links are actually useful.

### Example response length

Aim for roughly **80–140 words** for a normal identification. The user can ask for more detail afterward.

## When the user provides several plants

If the user sends multiple plants or asks for a comparison, use a compact comparison table with:
- Plant
- Sun
- Water
- Pot
- Ground
- Pets
- South Florida verdict

Do not repeat full individual profiles unless requested.

## Save to garden journal

Saving is **optional** and should never delay the initial nursery answer.

If the user says `save`, `keep this`, `add to my garden journal`, or equivalent after reviewing a plant, create a Markdown journal entry using the format below if the current environment provides file-write or project-write capability.

Suggested path:

`garden-journal/plants/<slug>.md`

Suggested Markdown:

```markdown
---
name: Common Name
scientific_name: Scientific name
status: considering
identified_on: YYYY-MM-DD
source: nursery
sun: Part sun
water: Moderate
pot: Good
ground: Excellent
pet_safety: Generally non-toxic
---

# Common Name

## Quick notes
- South Florida: ...
- Mature size: ...
- Buying note: ...

## Identification
Identification confidence: High

## Links
- [Useful source](https://example.com)
```

If project/file writing is not available, generate the Markdown content and filename for the user instead of implying that it was saved.

If a photo is available and the environment supports saving/copying images into the project, preserve it as an optional journal asset. Photo processing is not required for the nursery lookup itself.

## Follow-up behavior

Treat short follow-ups as referring to the most recently discussed plant unless context clearly indicates otherwise. Examples:
- `how big?`
- `what size pot?`
- `safe for my dog?`
- `morning sun?`
- `save it`
- `compare to the last one`

Answer these directly without restating the entire profile unless useful.
