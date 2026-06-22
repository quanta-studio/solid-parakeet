# Slide decks

Runnable [Marp](https://marp.app/) decks — a coherent set of seven knowledge-share talks on
running AI-assisted engineering. **Start with the capstone** (`operating-model`); the middle
five each go deep on one layer it introduces; **close with `lessons-learned`** (why each layer
exists).

| Deck | Source | Topic |
|---|---|---|
| **How We Run AI-Assisted Engineering** *(capstone)* | [`operating-model.md`](./operating-model.md) | The operating model the other talks slot into |
| Tiered Agent Memory | [`tiered-agent-memory.md`](./tiered-agent-memory.md) | The durable-knowledge layer: memory tiered + curated |
| The Virtual Engineering Team | [`virtual-engineer-fleet.md`](./virtual-engineer-fleet.md) | The coordination layer: many agents in parallel |
| Trust, but Verify — with a Rival | [`trust-and-verification.md`](./trust-and-verification.md) | The verification layer: cross-vendor adversarial review + evidence |
| How Much Leash? | [`risk-tiered-autonomy.md`](./risk-tiered-autonomy.md) | The governance ring: autonomy routed by blast radius |
| The Repo Is the Onboarding Doc | [`encoding-the-rules.md`](./encoding-the-rules.md) | The authored-rules layer: rules + reusable playbooks |
| **Lessons Learned — Every Control Is a Scar** *(closer)* | [`lessons-learned.md`](./lessons-learned.md) | The retrospective: the failures that forced each control |

Diagrams for all decks live in [`../diagrams/`](../diagrams/) and are embedded as PNGs.
All commands below work for any deck — swap the filename.

## Live preview (auto-reloads on edit)

```bash
cd docs/slides
npx -y @marp-team/marp-cli@latest -p tiered-agent-memory.md
```

Or serve the whole folder: `npx -y @marp-team/marp-cli@latest -s .`

## Export

`--allow-local-files` is required because the deck embeds local PNGs.

```bash
cd docs/slides
# HTML (self-contained, open in any browser)
npx -y @marp-team/marp-cli@latest tiered-agent-memory.md -o tiered-agent-memory.html --allow-local-files
# PDF (print / email)
npx -y @marp-team/marp-cli@latest tiered-agent-memory.md --pdf --allow-local-files
# PowerPoint (editable; speaker notes land in presenter notes)
npx -y @marp-team/marp-cli@latest tiered-agent-memory.md --pptx --allow-local-files
```

The PDF/PPTX exporters drive a headless Chrome. If Marp can't find one, point it at yours:

```bash
export CHROME_PATH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
```

Speaker notes are the `<!-- ... -->` HTML comments in the source; they export into PPTX presenter notes.

## Re-rendering the diagrams

The PNGs are generated from the `.mmd` sources in `../diagrams/`:

```bash
cd docs/diagrams
npx -y @mermaid-js/mermaid-cli@latest -i 01-memory-hierarchy.mmd -o 01-memory-hierarchy.png -b white -s 2 -p puppeteer-config.json
# repeat for each .mmd source:
#   memory deck:  01-memory-hierarchy   02-fact-lifecycle      03-two-channels
#   fleet deck:   04-fleet-topology     05-task-lifecycle      06-coordination-channels
#   capstone:     07-operating-model    08-four-layers
#   trust deck:   09-cross-vendor-review 10-evidence-ladder
#   autonomy:     11-autonomy-spectrum  12-gated-routing
#   rules deck:   13-rules-vs-memory    14-playbook-lifecycle
#   lessons:      15-scar-map           16-lesson-to-control
```

`puppeteer-config.json` pins the Chrome path (machine-specific) — adjust `executablePath` if Chrome lives elsewhere.

## Companion docs

Each deck has a full four-format kit (diagrams + deck outline + one-pager brief + demo talk track):

- [`../operating-model-presentation.md`](../operating-model-presentation.md) *(capstone)*
- [`../tiered-agent-memory-presentation.md`](../tiered-agent-memory-presentation.md)
- [`../virtual-engineer-fleet-presentation.md`](../virtual-engineer-fleet-presentation.md)
- [`../trust-and-verification-presentation.md`](../trust-and-verification-presentation.md)
- [`../risk-tiered-autonomy-presentation.md`](../risk-tiered-autonomy-presentation.md)
- [`../encoding-the-rules-presentation.md`](../encoding-the-rules-presentation.md)
- [`../lessons-learned-presentation.md`](../lessons-learned-presentation.md) *(closer)*
