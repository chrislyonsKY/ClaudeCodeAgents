# SKILL.md Template

> **A framework for teaching AI assistants your domain expertise**

When you work with AI assistants like Claude or ChatGPT, they start every conversation as generalists. A SKILL.md file transforms them into specialists—encoding your workflows, terminology, preferences, and hard-won knowledge into a format they can apply immediately.

Think of it as onboarding documentation for your AI collaborator.

---

## Quick Start

1. Copy the template below
2. Fill in your domain expertise
3. Save as `SKILL.md` (or `MY-DOMAIN-SKILL.md`)
4. Upload to conversations or paste into custom instructions

---

## The Template

```markdown
---
name: your-skill-name
description: "A 1-3 sentence description of when to use this skill. Be specific about trigger phrases and contexts. Example: Use this skill when the user asks about [specific domain], mentions [key terminology], or needs help with [specific tasks]. Include edge cases that should trigger this skill even if not explicitly requested."
author: "Your Name (optional)"
version: "1.0 (optional)"
---

# [Skill Name]

## Overview

[2-3 sentences explaining what this skill covers and why it matters. What domain expertise does this encode? What problems does it solve?]

## Core Concepts

[Define the fundamental ideas, terminology, or mental models someone needs to work in this domain. This grounds the AI in your worldview.]

| Term | Definition |
|------|------------|
| [Term 1] | [What it means in your context] |
| [Term 2] | [What it means in your context] |
| [Term 3] | [What it means in your context] |

## Workflows & Patterns

### [Workflow 1 Name]

[Describe when to use this workflow]

**Steps:**
1. [Step one]
2. [Step two]
3. [Step three]

**Example:**
```[language]
[Code, commands, or structured example]
```

**Common pitfalls:**
- [What goes wrong and how to avoid it]

### [Workflow 2 Name]

[Repeat pattern as needed]

## Tools & Technologies

[List the specific tools, platforms, or technologies relevant to this skill. Include version numbers if they matter.]

| Tool | Purpose | Notes |
|------|---------|-------|
| [Tool 1] | [What it's for] | [Version, quirks, preferences] |
| [Tool 2] | [What it's for] | [Version, quirks, preferences] |

## Code Patterns

[Include reusable code snippets, templates, or patterns you frequently use. These give the AI concrete examples to work from.]

### [Pattern Name]
```[language]
[Your code pattern with comments explaining key decisions]
```

## Style & Preferences

[How do you like things done? What conventions do you follow?]

- **Naming:** [Your conventions]
- **Structure:** [How you organize things]
- **Documentation:** [Your standards]
- **Avoid:** [Things you don't want]

## Domain-Specific References

[Links, documentation, or resources the AI should know about. Include internal terminology or project-specific context.]

- [Resource 1]: [Why it matters]
- [Resource 2]: [Why it matters]

## Common Tasks

[Quick reference for frequent requests]

| Task | Approach |
|------|----------|
| [Task 1] | [How to do it] |
| [Task 2] | [How to do it] |
| [Task 3] | [How to do it] |

## What This Skill Does NOT Cover

[Explicitly state boundaries. This prevents the AI from overreaching or applying this skill inappropriately.]

- [Out of scope item 1]
- [Out of scope item 2]
```

---

## How to Use Your SKILL.md

### Claude (claude.ai)
- **Projects:** Paste into project custom instructions
- **Conversations:** Upload the .md file or paste at conversation start
- **Claude Code:** Place in `~/.claude/skills/` directory

### ChatGPT
- **Custom GPTs:** Use as the instruction set when building a GPT
- **Projects:** Add to project instructions
- **Conversations:** Upload or paste as context

### API Usage (Claude/OpenAI)
Include in your system prompt:
```python
system_prompt = f"""
{open('SKILL.md').read()}

You are an assistant with the above expertise.
"""
```

---

## Tips for Effective Skills

### Be Specific, Not Generic
```
❌ "Help with data analysis"
✅ "Analyze permit boundary shapefiles using ArcPy, outputting 
    acreage calculations in the CHIA report format"
```

### Include Real Examples
Abstract instructions are hard to apply. Show don't tell:
```
❌ "Use proper naming conventions"
✅ "Name feature classes as: {Agency}_{DataType}_{Year}
    Example: EEC_PermitBoundaries_2024"
```

### Encode Your Preferences
The AI doesn't know you prefer tabs over spaces unless you say so:
```markdown
## Preferences
- Python: Black formatter, 88 char line length
- SQL: Uppercase keywords, lowercase identifiers  
- Comments: Explain WHY, not WHAT
```

### State What to Avoid
Negative examples are as valuable as positive ones:
```markdown
## Avoid
- Don't use `arcpy.mapping` (that's ArcMap legacy)
- Never hardcode file paths
- Skip the "As an AI assistant..." preamble
```

### Keep It Maintainable
A 50-page skill file becomes stale. Aim for:
- Core skill: 200-500 lines
- Reference docs: Link out, don't embed
- Update quarterly or when workflows change

---

## Example Skills by Domain

| Domain | Key Sections to Include |
|--------|------------------------|
| **Software Development** | Language patterns, framework conventions, testing approach, PR standards |
| **Data Analysis** | Tool stack, visualization preferences, statistical methods, data cleaning patterns |
| **Writing/Content** | Voice & tone, structure templates, publication standards, topic frameworks |
| **Research** | Source evaluation, citation style, methodology, literature review process |
| **Design** | Design system, component patterns, accessibility standards, tool workflows |
| **DevOps/SysAdmin** | Infrastructure patterns, security practices, monitoring approach, runbooks |
| **GIS/Geospatial** | Coordinate systems, data formats, analysis workflows, cartographic standards |

---

## Sharing Your Skills

Consider publishing your SKILL.md files:
- **GitHub:** Version control + collaboration
- **Gists:** Quick sharing of single skills
- **Team wikis:** Internal knowledge base
- **Newsletters/blogs:** Teach others your approach

The best skills are living documents—update them as your workflows evolve.

---

## License

This template is released under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)—use it however you want, no attribution required.

---

*Created for the GIS and GeoAI community. Contributions welcome.*
