---
name: english-vocabulary
description: English vocabulary analysis skill. Used when filling content for vocabulary files in Obsidian vault following the standard template.
---

# English Vocabulary Analysis Skill

Guide to analyzing and presenting English vocabulary in Obsidian format.

## ⛔ CRITICAL: Tool Restrictions

> [!CAUTION] Token Optimization
> - **ABSOLUTELY NO WEB SEARCH** - Use internal knowledge only
> - Read template from: `{baseDir}/references/template.md`
> - DO NOT search for files - paths are provided explicitly

## When to Use This Skill

- Analyzing a new vocabulary word
- Filling content into vocabulary template
- Creating flashcards for Spaced Repetition

## Template Location

**Path:** `{baseDir}/references/template.md`

When generating content:
1. Read the template file from the path above
2. Replace `{{WORD}}` with the actual word
3. Fill in all `...` placeholders
4. Update `status: pending` → `status: done`

## Parts of Speech Reference

| Type | Abbreviation | Example |
|------|--------------|---------|
| **Noun** | n. | knowledge |
| **Verb** | v. | learn |
| **Adjective** | adj. | intelligent |
| **Adverb** | adv. | quickly |

## CEFR Level Guidelines

| Level | Characteristics | Example |
|-------|-----------------|---------|
| A1 | Beginner | book, water |
| A2 | Elementary | understand, important |
| B1 | Intermediate | opportunity, consider |
| B2 | Upper Intermediate | emphasize, comprehensive |
| C1 | Advanced | eloquent, meticulous |
| C2 | Proficiency | ostentatious, ephemeral |

## IPA Notation

- Use standard IPA symbols
- British pronunciation preferred: `/ˈnɒlɪdʒ/`
- Include stress markers: `ˈ` (primary), `ˌ` (secondary)

## Output Format

> [!IMPORTANT] Strict Standard Adherence
> You MUST strictly follow the flashcard format defined in `assets/Vocabulary_Flashcard_Standards.md` (which is reflected in the template).
> - Generate exactly **7 Cards** as per the standard.
> - Use the exact icons and formatting (bold headers, empty lines) as specified.

Keep the entire markdown structure of the template, replacing:
- `{{WORD}}` → actual word
- `...` → actual content
- `[[ ]]` → `[[ actual_word ]]`
- `status: pending` → `status: done`
