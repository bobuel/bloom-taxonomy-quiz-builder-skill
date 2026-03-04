# 🎓 Bloom's Quiz Builder — Claude Skill

A [Claude Skill](https://claude.ai) that helps teachers generate rigorous, Bloom's Taxonomy-aligned comprehension questions from any educational material.

Upload a document, article, or reading — and Claude will guide you through identifying themes, selecting question types, and building a validated question set across all six cognitive levels.

---

## What it does

1. **Reads your materials** — upload or paste any educational content
2. **Identifies testable themes** — with rationale for why each is a strong assessment candidate
3. **Prompts your preferences** — theme, tone, question type, and any constraints
4. **Builds one question per Bloom's level** — with validation at each step and teacher approval before moving on
5. **Exports a complete JSON question set** — ready for use in quizzes, LMS platforms, or further editing

---

## Bloom's Taxonomy Levels Covered

| Level | Focus |
|-------|-------|
| 1. Remember | Recall facts and basic concepts |
| 2. Understand | Explain ideas or concepts |
| 3. Apply | Use information in new situations |
| 4. Analyze | Draw connections, break things down |
| 5. Evaluate | Justify a decision or course of action |
| 6. Create | Produce new or original work |

---

## Question types supported

- Multiple choice
- Select all that apply
- Finish the sentence
- Matching
- True / False

---

## Example output (per question)

```
Question Set Rationale: Why this question relates to the selected theme
Question Rationale: Why this is a good question and what it tests
Question: The question text
Question Answers:
  1. Option
  2. Option
  3. Option
  4. Option
Question Correct Answer: The correct answer
Question Correct Answer Rationale: Why this is correct
Question Correct Answer Reference: Where in the materials this answer is found
Question Comprehension Reference: How a student would know this answer
Question Difficulty: Easy / Moderate / Hard
Question Bloom's Level: Remember / Understand / Apply / Analyze / Evaluate / Create
```

Final output is a single **JSON object** with all 6 questions, ready to export.

---

## How to install

1. Download [`bloom-quiz-builder.skill`](./bloom-quiz-builder.skill)
2. In Claude, go to **Settings → Skills**
3. Click **Upload Skill** and select the downloaded file
4. Start a new conversation — Claude will automatically use the skill when you ask it to build a quiz or generate comprehension questions

---

## Example prompt to get started

> "Here's a chapter from our biology textbook. Can you help me build a comprehension quiz?"

> "I want to create a question set based on this article for my 8th grade class."

> "Generate Bloom's Taxonomy questions from this PDF."

---

## Files in this repo

| File | Purpose |
|------|---------|
| `bloom-quiz-builder.skill` | Installable skill file for Claude |
| `SKILL.md` | Human-readable skill instructions — the source of truth |
| `README.md` | This file |

---

## Contributing

Found a bug or want to improve the skill? Open an issue or submit a pull request against `SKILL.md`. The `.skill` file is generated from `SKILL.md` and will be updated accordingly.

---

## Requirements

- A Claude account with Skills enabled ([claude.ai](https://claude.ai))
- Claude Pro, Team, or Enterprise plan (Skills is not available on the free tier)
