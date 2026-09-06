---
name: cram-notes-creation
description: Creates concise, high-yield exam cram documents from raw study materials (markdown, PDF, text, DOCX, PPTX). Produces structured chapter-by-chapter revision guides with exam tips, tables, and self-test questions.
agent: any
---

# Cram Notes Creation Skill

## Supported Input Formats

| Format | Processing Method |
|--------|------------------|
| `.md` | Native markdown parsing |
| `.pdf` | pdfplumber or PyPDF2 extraction |
| `.txt` | Plain text parsing |
| `.docx` | python-docx extraction |
| `.pptx` | python-pptx extraction |
| Other | Plain text fallback |

## File Naming Convention

Exam cram files follow semantic versioning: `{chapter-name}-exam-cram-v{major}.{minor}.md`

- Start at `v1.0`
- Major bump: Restructuring or removing large sections
- Minor bump: Adding topics, correcting errors, improving clarity
- All chapter crams share the same version number for consistency

## Standard Workflow

### Phase 1: Discovery

1. Scan for source files using glob patterns: `*.md`, `*.txt`, `*.pdf`, `*.docx`, `*.pptx`, `README*`, `Chapter*`
2. Identify primary notes file (README.md, notes.md, etc.)
3. Identify chapter files, slides, or supplementary documents

### Phase 2: Content Extraction

- **Markdown/Text**: Read file directly, parse markdown headings for structure
- **PDF**: Use pdfplumber or PyPDF2, preserve page numbers
- **DOCX**: Use python-docx, skip images
- **PPTX**: Use python-pptx, note slide numbers

### Phase 3: Content Analysis

1. Read complete source material before creating output
2. Identify chapter boundaries from markdown headings, numbered sections, page breaks, topic divisions
3. Fix formatting issues:
   - Incomplete sentences → complete or flag for user
   - Fragment sentences → infer from context or ask user
   - Malformed lists → normalize
   - Inconsistent headings → standardize

### Phase 4: Cram Structure

```markdown
# Chapter {N} - {Title}

**Domain Weight:** {percentage} of {exam}

---

## Section 1: Topic

- Key point 1
- Key point 2

### Subsection

**Exam Tip:** {tricky distinction}

| Table | Col1 | Col2 |
|-------|------|------|
| Data  | A    | B    |

## Section 2: Another Topic

{content}

---

## Quick Check

1. **Question?**
<details><summary>Answer</summary>
Answer text
</details>
```

### Phase 5: Content Prioritization

**High Priority:** Definitions, key terms, use cases, key differentiators, frequently-tested areas

**Medium Priority:** Supporting details, extended explanations

**Lower Priority:** Tangential information, verbose examples

### Phase 6: Exam Tips

Insert for:
- Similar-sounding concepts
- Easy-to-confuse terms
- Common pitfalls
- Tricky distinctions

Format: `**Exam Tip:** {concise explanation}`

### Phase 7: Quick Checks

- 5-10 questions per chapter
- Mix: definition, scenario, comparison questions
- Answers in collapsible `<details>` blocks

```markdown
1. **Question?**
<details><summary>Answer</summary>
Answer text
</details>
```

### Phase 8: Version Management

1. Check for existing crams
2. Increment appropriately:
   - Minor (v1.0 → v1.1): Fixes, additions
   - Major (v1.x → v2.0): Restructuring
3. Apply consistent version across all chapters

## Quality Checklist

- [ ] All source content processed, no hallucinations
- [ ] Grammar/formatting errors fixed
- [ ] Incomplete sentences completed or flagged
- [ ] Exam tips for tricky distinctions
- [ ] Quick Check with collapsible answers
- [ ] Tables properly formatted
- [ ] Version consistent across chapters
- [ ] Files named correctly

## Error Handling

| Issue | Resolution |
|-------|------------|
| Unclear content | Ask user for clarification |
| Missing file | Attempt alternative extensions |
| Corrupt file | Skip, report, continue with others |
| No clear chapters | Ask user how to divide |
| Conflicting info | Trust primary source, flag discrepancy |

## Output

- One exam cram file per chapter
- Naming: `{chapter}-exam-cram-v{major}.{minor}.md`
- Same directory as source or user-specified

## Usage

```
1. Scan working directory for source files
2. Extract content from each file
3. Analyze structure and identify chapters
4. Create exam cram files following structure
5. Report completion with file list
```

## Notes

- Only use content present in source materials
- Do not hallucinate or invent concepts
- Respect source material copyright
- Output is for exam preparation only
