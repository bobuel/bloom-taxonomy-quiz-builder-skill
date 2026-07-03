# Bloom's Quiz Builder — Claude Skill

A Claude Skill that helps teachers generate rigorous, Bloom's Taxonomy-aligned comprehension questions from educational materials.

Upload a document, article, chapter, or reading passage. The skill guides the teacher through identifying testable themes, selecting question types, and building a validated question set across all six Bloom's Taxonomy levels.

I built this after seeing strong usage of my custom GPT, [BloomGPT](https://chatgpt.com/g/g-qY82hT1eA-bloomgpt), which has been used more than 1,000 times.

## Product idea

Teachers do not just need more questions. They need better questions: questions that are aligned to learning goals, grounded in the source material, varied by cognitive demand, and easy to review before using with students.

This skill treats quiz generation as a structured instructional design workflow instead of a one-shot prompt.

## What it does

1. **Reads the material** — upload or paste educational content.
2. **Identifies testable themes** — with rationale for why each theme can support assessment.
3. **Prompts teacher preferences** — theme, tone, question type, grade level, and constraints.
4. **Builds one question per Bloom's level** — with validation and teacher approval before moving on.
5. **Exports a complete JSON question set** — ready for editing, LMS import, or further review.

## Bloom's Taxonomy levels covered

| Level | Focus |
| --- | --- |
| 1. Remember | Recall facts and basic concepts |
| 2. Understand | Explain ideas or concepts |
| 3. Apply | Use information in new situations |
| 4. Analyze | Draw connections or break ideas down |
| 5. Evaluate | Justify a decision or course of action |
| 6. Create | Produce new or original work |

## Question types supported

- Multiple choice
- Select all that apply
- Finish the sentence
- Matching
- True / false

## Example output per question

```text
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

Final output is a single JSON object with all six questions.

## How to install

1. Download [`bloom-taxonomy-quiz-builder.skill`](./bloom-taxonomy-quiz-builder.skill).
2. In Claude, go to **Settings → Skills**.
3. Click **Upload Skill** and select the downloaded file.
4. Start a new conversation and ask Claude to build a quiz or generate comprehension questions from educational material.

## Example prompts

> Here's a chapter from our biology textbook. Can you help me build a comprehension quiz?

> I want to create a question set based on this article for my 8th grade class.

> Generate Bloom's Taxonomy questions from this PDF.

## Files in this repo

| File | Purpose |
| --- | --- |
| `bloom-taxonomy-quiz-builder.skill` | Installable skill file for Claude |
| `SKILL.md` | Human-readable skill instructions and source of truth |
| `README.md` | Project overview |

## Requirements

- A Claude account with Skills enabled
- A Claude plan that supports Skills

## Contributing

Found a bug or want to improve the skill? Open an issue or submit a pull request against `SKILL.md`. The `.skill` file is generated from `SKILL.md` and should be updated after instruction changes.
