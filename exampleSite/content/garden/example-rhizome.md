---
title: "Knowledge Graphs and Connected Thinking"
type: garden
date: 2023-12-01
created: 2023-12-01 Fri 3:45pm
updated: 2024-02-15 Thu 11:30am
state: rhizome
tags: ["pkm", "learning", "tools", "systems"]
share: true
---

**Major revision 2024-02-15:** Expanded section on emergence and added practical implementation notes.

---

After years of organizing thoughts in hierarchical folders and linear documents, I've become convinced that **knowledge is fundamentally networked, not hierarchical**.

## The folder problem

Traditional file systems force us to make a choice: does this note go in "Projects" or "Learning"? "Work" or "Personal"? These categories are artificial boundaries we impose, but ideas don't respect them.

Real thoughts are rhizomatic—they spread horizontally, connecting in unexpected ways.

## What makes a good knowledge graph?

I've experimented with Roam, Obsidian, Notion, and plain markdown files with WikiLinks. Here's what I've learned:

### 1. Bidirectional links are essential

When Note A links to Note B, I need to see that connection from both directions. This creates a web rather than a tree.

**Why it matters:** I often rediscover connections while exploring from different starting points. The path from "Digital Gardens" to "Learning in Public" is different than the reverse path, and both are valuable.

### 2. Emergence over planning

Don't start with a grand taxonomy. Start with atomic notes and let structure emerge from connections.

The most valuable insights come from unexpected adjacencies—notes that link together in ways I didn't predict.

### 3. Link types add clarity

Not all connections are the same:
- **Parent/child**: "DevOps" → "CI/CD practices"
- **Related**: "Continuous delivery" ↔ "Trunk-based development"
- **Example of**: "Kubernetes" ← "Container orchestration"
- **Contradicts**: "Perfect code coverage" ⟂ "Pragmatic testing"

Some tools support typed links; most don't. Even implicit types (through context) help.

### 4. Low friction is critical

If it's hard to create a link, I won't do it. This is why plain markdown with `[[WikiLinks]]` works so well—it's fast and portable.

## Digital gardens as public knowledge graphs

This garden is an experiment in making my knowledge graph public. Each post is a node. Tags and internal links are edges. Growth stages indicate confidence/maturity.

**The paradox:** Making it public changes how I think. I'm more careful, but also more willing to share incomplete ideas because the format signals "this is a work in progress."

## Practical implementation

After much experimentation, here's my current setup:

**Tools:**
- Obsidian for private notes (fluid, fast, local-first)
- Hugo for the public garden (static, portable, version controlled)
- Manual syncing between them (keeps me intentional about what to publish)

**Workflow:**
1. Quick capture in Obsidian (seeds everywhere)
2. Weekly review to tend and connect
3. Promote mature notes to the public garden
4. Backlinks from public to private keep them connected

**Key insight:** The friction of manual syncing is actually a feature—it forces me to consciously choose what to share and how to frame it.

## Related explorations

- [[example-seed]] - Why gardens work differently than blogs
- [[example-sprout]] - Learning in public connects to this
- Personal Knowledge Management systems (various notes)
- Zettelkasten method and atomic notes
- Second brain vs. extended mind theories

## Open questions

- How do we visualize emergent structure in a way that's useful?
- What's the right level of granularity for a "node"?
- Can AI help suggest unexpected connections?
- How do community gardens (shared knowledge graphs) differ from personal ones?

---

## Metadata

- [category::systems]
- [confidence::high]
- [last-major-revision::2024-02-15]
