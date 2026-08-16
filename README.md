# Garden Scout

Garden Scout is a fast plant-identification and nursery decision assistant for South Florida, with guidance tuned for Palm Beach County conditions. It helps turn a nursery stop into a clear, practical buying decision.

## What you can send

Use Garden Scout with any of the following:

- A plant photo
- A nursery label or tag photo
- A plant name
- A plant name plus a photo

It responds with a compact card designed for quick scanning while you shop:

- **Common name** and **scientific name**
- **ID confidence**
- **Sun** and **water** needs
- **Pot** and **in-ground** suitability
- **Growth** (mature size and pace)
- **Pets** safety status
- **South Florida** fit
- **Buy?** verdict with a short reason

Garden Scout assumes South Florida / Palm Beach County conditions unless you say otherwise: heat, humidity, seasonal rain, strong sun, and mild winters.

## Example prompts

Attach a photo or label and ask:

> Identify this plant and tell me whether I should buy it.

> Is this suitable for a large patio pot in Palm Beach County?

> Is this safe around dogs and cats?

> Compare this with the last plant for a sunny, low-maintenance spot.

After a result, ask follow-ups naturally: “What size pot?”, “How fast does it grow?”, or “Full sun?” To keep a research record, say **“save it”** or **“save this”**. For a comparison, say **“compare it to the last one”**; Garden Scout focuses on the decision-relevant differences.

## Install and use

This repository is a Codex marketplace containing one plugin: **Garden Scout**. Anyone may download, install, and use unmodified copies of the plugin for personal or commercial use without written permission.

1. Clone the repository locally:

   ```sh
   git clone https://github.com/cgb37/bh-garden-scout.git
   ```

2. Add the cloned repository as the non-default Codex marketplace, replacing the path with its local location:

   ```sh
   codex plugin marketplace add <path-to-cloned-repository>
   ```

3. Install the plugin from that marketplace:

   ```sh
   codex plugin add garden-scout@bh-garden-scout
   ```

4. Start a fresh Codex task, attach a plant or nursery-label photo if useful, and ask a buying question.

Publishing this repository on GitHub does not itself install or synchronize the plugin to ChatGPT or an iPhone. This README documents only the tested local Codex workflow above.

## Privacy and limitations

Submitted plant and label photos are processed by your OpenAI product/session. Before sharing an image, avoid including people, addresses, receipts, or other sensitive details.

Plant identification can be wrong, especially when images are unclear or species and cultivars look alike. Cultivar-level identification may be ambiguous. Pet-toxicity information should be verified with an authoritative veterinary or toxicology source before it guides a safety decision; Garden Scout does not provide medical or veterinary advice. Local microclimates, drainage, salt exposure, maintenance, and nursery growing conditions can change how a plant performs.

## Production layout

```text
.
├── .agents/plugins/marketplace.json     # Marketplace listing
├── .gitignore
├── plugins/
│   └── garden-scout/
│       ├── .codex-plugin/plugin.json    # Plugin manifest
│       └── skills/garden-scout/          # Garden Scout behavior
├── LICENSE
└── README.md
```

## License, feedback, and contributions

Garden Scout is proprietary software. Public visibility, including on GitHub, and this license permit only the express right to download, install, and use unmodified copies. Modifying, creating derivative works, redistributing, sublicensing, or selling the software or substantial portions of it requires prior written permission from CGB37. All rights not expressly granted are reserved. See [LICENSE](LICENSE).

Feedback and issue reports are welcome where the repository host supports them. They do not grant permission to contribute, modify, or submit code or other changes; contact CGB37 for written permission before doing so.
