# NOVA: Natural Ordered Verbal Architecture

> **Read code like a book. Write code like a story. Debug code like a proofreader.**

NOVA is a structured, metaphor-driven coding framework that treats every codebase as a **library of books**. It replaces chaotic LLM interactions with a disciplined, chapter-by-chapter compilation process — eliminating hallucinations, saving tokens, and producing deterministic output.

---

## Quick Start

```
1. Place skill.md in your .nova/ directory
2. Fill in the PREFACE with your tech stack (there is NO default — you decide)
3. Write your chapters and compile
```

That's it. NOVA enforces structure. You provide the content.

---

## Core Philosophy

### Token Saving
Every interaction is scoped to a single chapter. NOVA never loads the entire codebase into context. You work on one chapter at a time, and the compiler only reads what it needs.

### Hallucination Removal
NOVA's syntax is deterministic. Every output maps to a declared structure in the Table of Contents. If it's not in the TOC, it doesn't exist. The LLM cannot invent files, functions, or modules that weren't declared.

### Controlled LLM Environment — The LLM Cage
The LLM operates inside a strict cage:
- It **cannot** decide the tech stack (you declare it in PREFACE).
- It **cannot** skip chapters or reorder sections.
- It **cannot** modify source files directly (read-only access to existing code).
- It **must** follow the TOC as the single source of truth.

---

## The 5 Unbreakable Rules

| Rule | Name | Description |
|------|------|-------------|
| **Rule 0** | Book Rule | The TOC (`TOC.md`) is compiled first. It is the skeleton. Everything references it. |
| **Rule 1** | Silent Mode | The LLM outputs **only** code and NOVA syntax. No explanations, no commentary, no markdown fences unless instructed. |
| **Rule 2** | Read-Only Source | Existing source files are **never** modified directly. All changes are expressed as NOVA chapters that compile to new output. |
| **Rule 3** | Context Limiting | Only the current chapter and its declared `CITES` are loaded into context. Nothing else. |
| **Rule 4** | Chapter-Wise Only | Compilation proceeds one chapter at a time, in order. No skipping. No parallel chapters. |

---

## The Complete Book ↔ Programming Metaphor

| Programming Concept | Book Metaphor | NOVA Syntax |
|---------------------|---------------|-------------|
| Codebase | Library | Library |
| Domain | Volume | Volume |
| Tech Stack | Language the Book Speaks | `PREFACE` |
| Module | Chapter | `CHAPTER` |
| Class | Section | `SECTION` |
| Property | Character Sheet | `FIELD` |
| Function | Paragraph | `PARAGRAPH` |
| Type | Glossary Entry | `GLOSSARY` |
| Object | Character Appearance | Character Appearance |
| Enum | Vocabulary | `VOCABULARY` |
| Constant | Axiom | `AXIOM` |
| Import | Citation | `CITES` |
| Config | Preface | `PREFACE` |
| Comment | Footnote | *italic* |
| Test | Proofreading Note | Proofreading Note |
| Error | Errata | Errata |
| Middleware | Editor's Note | Editor's Note |
| Event | Plot Twist | Plot Twist |
| State | Narrator's Memory | Narrator's Memory |
| Route | Index Entry | Index Entry |
| API | Published Letter | Published Letter |
| DB Model | Blueprint | Blueprint |
| UI Component | Illustration | Illustration |
| Source Map | INDEX in TOC.md | `INDEX` |

---

## 4 Operating Modes

### 1. Write Mode (Author)
You are **writing new code**. The LLM acts as a co-author, generating chapters from the TOC skeleton. Every output is a new file.

### 2. Read Mode (Reader)
You are **understanding existing code**. The LLM reads source files and translates them into NOVA book metaphors for comprehension. No files are created or modified.

### 3. Debug Mode (Proofreader)
You are **finding and fixing errors**. The LLM acts as a proofreader, scanning chapters for errata (bugs), inconsistencies, and structural issues. Fixes are expressed as revised paragraphs.

### 4. Migrate Mode (Librarian)
You are **converting an existing codebase** into NOVA format. The LLM acts as a librarian, cataloguing existing files into chapters, sections, and paragraphs — building a TOC from existing source.

---

## Navigation Patterns

NOVA enforces structured navigation through the codebase-as-book:

### Zoom-In
Move from a higher level of abstraction to a lower one.
```
Library → Volume → Chapter → Section → Paragraph
```

### Zoom-Out
Move from a lower level to a higher one.
```
Paragraph → Section → Chapter → Volume → Library
```

### Stay Level
Navigate between peers at the same level of abstraction.
```
Chapter 3 → Chapter 4 → Chapter 5
```

### Reverse Lookup
Find all references to a specific element across the entire library.
```
"Where is this FIELD used?" → Search all CITES and PARAGRAPHS
```

### Decision Tree
```
Need more detail?        → Zoom-In
Need broader context?    → Zoom-Out
Need the next piece?     → Stay Level
Need to find references? → Reverse Lookup
```

---

## NOVA Syntax Dictionary (Essential Elements)

| Syntax | Purpose | Example |
|--------|---------|---------|
| `PREFACE` | Declares tech stack, language, framework | `PREFACE: TypeScript, Next.js 14, Prisma` |
| `CHAPTER [name]` | Defines a module/file boundary | `CHAPTER auth-service` |
| `SECTION [name]` | Defines a class or logical group | `SECTION UserAuthHandler` |
| `PARAGRAPH [name]` | Defines a function or method | `PARAGRAPH validateToken` |
| `FIELD [name]` | Defines a property or variable | `FIELD accessToken: string` |
| `CITES [ref]` | Declares a dependency/import | `CITES ../utils/hash` |
| `GLOSSARY [name]` | Defines a type or interface | `GLOSSARY UserRole` |
| `VOCABULARY [name]` | Defines an enum | `VOCABULARY Status { ACTIVE, INACTIVE }` |
| `AXIOM [name]` | Defines a constant | `AXIOM MAX_RETRIES = 3` |
| `INDEX` | Source map in TOC.md | `INDEX: src/auth/service.ts` |
| `FOOTNOTE` | Inline comment or annotation | *rendered as italic* |

---

## Anti-Hallucination Shield

NOVA prevents LLM hallucinations through structural enforcement:

1. **TOC-First Compilation** — The Table of Contents is the single source of truth. If a chapter isn't declared in the TOC, the LLM cannot generate it.

2. **Explicit Tech Stack** — There is **no default tech stack**. The user must declare every technology in the `PREFACE`. The LLM cannot assume React, Node, Python, or anything else.

3. **Scoped Context** — Rule 3 ensures the LLM only sees the current chapter and its citations. It cannot hallucinate based on unloaded context.

4. **Silent Mode** — Rule 1 prevents the LLM from generating explanatory text that could contain fabricated information. Output is code only.

5. **Deterministic Mapping** — Every programming concept maps to exactly one book metaphor. There is no ambiguity in what the LLM should produce.

---

## Project Architecture

```
.nova/
├── skill.md              # The NOVA Compiler Directive (main instruction file)
├── TOC.md                # Table of Contents — the skeleton of your project
├── PREFACE.md            # Tech stack declaration (YOU fill this in)
├── chapters/             # Individual chapter files
│   ├── chapter-01.md
│   ├── chapter-02.md
│   └── ...
├── glossary/             # Type definitions and interfaces
│   └── types.md
├── index/                # Source maps and cross-references
│   └── source-map.md
└── errata/               # Known issues and bug tracking
    └── bugs.md
```

> **Note:** The `.nova/` directory is the heart of your project. The root `skill.md` is a pointer to `.nova/skill.md`.

---

## Important: No Default Tech Stack

NOVA does **not** assume any technology. You must explicitly declare your stack in the `PREFACE`:

```
PREFACE:
  Language: TypeScript
  Runtime: Node.js 20
  Framework: Next.js 14 (App Router)
  Database: PostgreSQL + Prisma
  Auth: NextAuth.js v5
  Styling: Tailwind CSS v3
```

If you don't declare it, it doesn't exist. This is by design.

---

## License

This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

See [LICENSE](LICENSE) for details.

---

<p align="center">
  <strong>NOVA: Natural Ordered Verbal Architecture</strong><br/>
  © 2026 NOVA Contributors. All rights reserved.<br/>
  Licensed under AGPL-3.0.
</p>
