# 🚀 NOVA: Natural Ordered Verbal Architecture

Welcome to **NOVA (Natural Ordered Verbal Architecture)**, a revolutionary paradigm designed to bridge the gap between human intent, natural language, and compiled machine code. 

Rather than writing traditional source code or relying on unpredictable, free-form AI generation, NOVA structures natural language like a **structured book** (Chapters, Sections, and Paragraphs) and compiles it into clean, idiomatic, and highly performant target code (such as React, Tailwind CSS, Python, Swift, etc.) using a set of deterministic, rule-based translations.

---

## 📖 Table of Contents
1. [Overview](#-overview)
2. [Project Architecture](#-project-architecture)
3. [The NOVA Compiler (`skill.md`)](#-the-nova-compiler-skillmd)
4. [Core Concepts & Protocols](#-core-concepts--protocols)
   - [Protocol 1: Auto-TOC Generation](#protocol-1-auto-toc-generation)
   - [Protocol 2: The Hierarchical Zoom-In Protocol](#protocol-2-the-hierarchical-zoom-in-protocol)
   - [Protocol 3: UI & GUI Spatial Translation](#protocol-3-ui--gui-spatial-translation)
   - [Protocol 4: Backend & Data Mapping](#protocol-4-backend--data-mapping)
5. [The NOVA Syntax Dictionary](#-the-nova-syntax-dictionary)
6. [Anti-Hallucination & Safety Shield](#-anti-hallucination--safety-shield)
7. [How to Use This Repository](#-how-to-use-this-repository)

---

## 🌟 Overview

NOVA is built on the principle of **Infinite Scaling under Finite Context Window Limits**. 

Traditional AI-driven development often suffers from "context window explosion" or hallucinations when dealing with large codebases or complex specifications. NOVA solves this by dividing application design and business logic into modular, human-readable markdown files called "chapters".

By using a hierarchical structure and loading only the minimal payload required for any single compilation step, the **NOVA Compiler** can work autonomously, with near-zero hallucinations and maximum token efficiency.

---

## 📁 Project Architecture

A standard NOVA workspace is structured as follows:

```
├── .nova/
│   ├── skill.md               # The Compiler Directive / "The Bible" of NOVA syntax
│   ├── TOC.md                 # Compressed Hierarchical Map of Volumes & Chapters
│   ├── glossary.md            # Strict global data types for backend and business logic
│   └── design_glossary.md     # UI style tokens (colors, spacing, shadows, fonts, etc.)
├── src/                       # Target output directory (where React/Python/etc. is compiled)
├── README.md                  # This guide
└── skill.md                   # Root copy of the NOVA Skill specification
```

---

## 🤖 The NOVA Compiler (`skill.md`)

The file `.nova/skill.md` acts as the **System Directive** for the AI or compilation engine. It transforms a standard language model into a dedicated **NOVA Execution Engine**. 

When activated, the compiler follows three golden rules:
1. **Silent Execution Mode:** Outputs only compilation status updates (e.g., `✅ Compiled [Paragraph] -> [Path]`), suppressing conversational filler and unnecessary explanations.
2. **Read-Only Source:** Treats the human-authored design files (`ch_*.md`, `glossary.md`, etc.) as absolute, unalterable sources of truth.
3. **Hierarchical Loading:** Restricts its file reads to tiny, targeted sections of text to keep context token usage under **2500 tokens** per operation.

---

## ⚙️ Core Concepts & Protocols

### Protocol 1: Auto-TOC Generation
To maintain a high-level view without reading entire books, the compiler generates and maintains `.nova/TOC.md`. It lists Volumes (Domains) and Chapters with ultra-short, 5-8 word summaries:
```markdown
# NOVA MASTER MAP

## VOLUME 1: INFRASTRUCTURE
- [ch1_db.md] Ch 1: Database -> Models, connections, migrations.
```

### Protocol 2: The Hierarchical Zoom-In Protocol
To compile code without exhausting memory, the compiler zooms in sequentially:
1. **Macro Zoom:** Scan the Volume list in `TOC.md` (~100 tokens).
2. **Meso Zoom:** Scan only the section headers of the target chapter file (~300 tokens).
3. **Micro Zoom:** Read only the relevant `#### Paragraph` payload and glossary files (~1500 tokens).
4. **Compile & Write:** Generate and write the output code to `src/`.

### Protocol 3: UI & GUI Spatial Translation
NOVA translates visual spatial layouts into modern CSS/Flexbox (like Tailwind CSS) using natural wording and **ASCII wireframes**:
- **ASCII Box Mapping:** Elements drawn using `┌───┐` and `└───┘` are parsed as containers, maps, or grid layouts.
- **Directional Hints:** "Left side: / Right side:" maps directly to flex alignments.
- **Visual Styles:** Wording like "shadow-soft" or "primary brand color" is looked up in `.nova/design_glossary.md` to output exact production-ready classes or hex codes.

### Protocol 4: Backend & Data Mapping
Paragraphs indicating backend endpoints or database structures compile automatically into database schemas (Mongoose, Prisma, SQLAlchemy) and route handlers (Next.js, Express, FastAPI):
- Handlers include request validation, exact business logic, and standard HTTP return codes.
- Fields compile into strict schema properties with validators, unique flags, and default values.

---

## 📖 The NOVA Syntax Dictionary

The core engine maps natural ordered language symbols into programming logic constructs:

| Symbol / Keyword | Coding Concept / Translation | Example Wording & Output |
| :--- | :--- | :--- |
| **`Period (.)`** | Ends an executable instruction. | `Fetch data from endpoint.` |
| **`?` at end of line** | `if` condition block. | `User is logged in? Show dashboard.` |
| **`Otherwise?`** | `else if` / `else` block. | `Otherwise? Redirect to /login.` |
| **`!` at start of line** | Guard statement / Early return. | `!user must have premium access.` (Throws error if false) |
| **`**BoldText**`** | Variable declaration. | `**token** is response.body.token.` |
| **`->` (Arrow)** | Variable binding / assignment. | `Save session -> sessionData.` |
| **`|` (Pipe)** | Functional method chaining. | `Get users \| filter active \| sort by name` |
| **`"""..."""`** | Structured JSON/Object literal. | Standard JSON object data context |
| **`Repeat for each X in Y:`**| Loops / Array mapping. | `Y.map(X => { ... })` or `for...of` loops |
| **`Try this ... If it fails?`** | Exception handling / Try-catch block. | `try { ... } catch (err) { ... }` |
| **`IN "javascript":` / `END IN.`** | Raw code bypass. | Inserts raw JavaScript code exactly as written |

---

## 🛡️ Anti-Hallucination & Safety Shield

NOVA ensures rigorous, production-grade output by locking down the AI's imagination:
* **Glossary Lock:** The compiler is prohibited from introducing fields or data structures that are not defined in the global `.nova/glossary.md`.
* **One Sentence = One Operation:** Stems over-engineering. The compiler only builds exactly what is specified—no more, no less.
* **Scope Isolation:** Variables cannot be accessed across different code files unless globally available or explicitly passed through parameters.

---

## 🚀 How to Use This Repository

1. **Activate the Skill:** Load the `.nova/skill.md` as custom instructions in your IDE agent, CLI tool, or AI assistant.
2. **Define Your Glossaries:** Create `.nova/glossary.md` and `.nova/design_glossary.md` defining your custom data models and visual style tokens.
3. **Write Your App Story:** Write natural language chapter books inside `.nova/` using NOVA syntax (e.g., `ch1_auth.md`, `ch2_billing.md`).
4. **Trigger Compilation:** Instruct your agent to "compile" any chapter or paragraph. Watch it silently and beautifully translate your prose into real, production-ready code under `src/`!

---

*NOVA represents the future of readable, maintainable, and infinitely scalable AI-assisted software compilation. Welcome to the era of Natural Ordered Verbal Architecture!*
