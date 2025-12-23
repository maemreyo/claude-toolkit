# structure.md

Batch process English grammar structure files with `status: pending`. Uses internal knowledge only.

## ⛔ CRITICAL: NO WEB SEARCH

**DISABLED TOOLS:** `web_search`, `web_fetch` - NEVER use under ANY circumstances.

**WHY:** Grammar structure analysis must be consistent. You are an expert linguist.

**IF UNSURE:**
- Use best linguistic judgment
- Provide approximations for dates, levels
- Use placeholder: `[context-dependent]`
- NEVER attempt to search

---

## Steps

### 1. Discovery
Find the structure directory:
1. Check: `glean/30_Structures` (preferred)
2. Fallback: Search for `*Structure*` folder
3. If not found: Ask user for path

### 2. Scan Pending Files
```bash
find '<directory_path>' -name '*.md' -exec grep -l '^status: pending' {} \;
```
- Use single quotes for paths with spaces
- Optional: Add `| head -n <limit>` to limit files

### 3. Batch Processing (Concurrent Agents)

Group files into batches of **10-15 files** per agent.

**For each batch, spawn a parallel agent with these instructions:**

```markdown
Process these grammar structure files CONCURRENTLY:

FILES TO PROCESS:
<list of absolute paths>

RULES:
- Use internal knowledge only (NO web search)
- Read each file → Extract structure from filename
- Select hierarchical tag from commented options
- Remove HTML comment block after selecting tag
- Populate aliases: [variations, alternative names]
- Fill ALL 11 flashcards as defined below
- Update status: pending → done
- Write content back to file

LINK FORMATTING:
- Use | instead of / inside links: [[take sb|st around]]
- Relations MUST be 2+ words: [[make sense]], NOT [[make]]

FLASHCARD REQUIREMENTS (11 cards):
1. Quick Recall (Pattern → Formula)
2. Logic & Vibe (include 🧠 Logic and 💡 Core Vibe)
3. Trigger Signal (include 🚦 Signal: when to use)
4. Example & Analysis (include 🔍 Analysis)
5. Error Correction (include Trap and Why)
6. Comparison (include 🧱 The Barrier)
7. Fill-in-the-Blank
8. Writer's Rewrite (include Effect)
9. Metaphor Deconstruction (analyze imagery)
10. Scenario Reaction (include 👨‍🎨 Director's Note)
11. Common Mistake Hunter

FORMAT RULES:
- Keep callout format: > [!info], > [!question]-, etc.
- Mandatory: Include `?` separator between Q&A
- Fill [[ structure ]] with actual Obsidian links
- Write all content in English
```

### 4. Validation
After all batches complete:
```bash
# Check for web traces
grep -r "web_search\|http://" glean/30_Structures/ | grep "status: done"

# Check link formatting (should use | not /)
grep -r "\[\[[^]]*\/[^]]*\]\]" glean/30_Structures/ | grep "status: done"

# Check card counts
for f in glean/30_Structures/*.md; do
  grep -q "status: done" "$f" && echo "$f: $(grep -c '#### Card' "$f") cards"
done
```

### 5. Report Summary
```
✅ Processed X/Y files successfully
📦 Batches executed: N
❌ Failed files: [list if any]
⚠️ Link format warnings: [if any]
```

---

## Usage Examples

```
# Process all pending files
/structure.md

# With custom path
Process structures in workspace/english/30_Structures

# Dry run (list only)
Show pending structure files without processing
```

## Success Criteria

- [x] All `status: pending` → `status: done`
- [x] 11 flashcards per file
- [x] Aliases populated
- [x] Links use `|` not `/`
- [x] Relations are 2+ words
- [x] No web search traces
