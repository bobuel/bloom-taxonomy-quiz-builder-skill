---
name: bloom-quiz-builder
description: >
  Help teachers create comprehension assessment questions aligned to Bloom's Taxonomy
  from uploaded educational materials. Use this skill whenever a teacher wants to:
  generate quiz questions, test student comprehension, create assessments from a document
  or reading, build question sets at different cognitive levels, evaluate student
  understanding of educational content, or create multiple choice / true-false / matching
  questions from source material. Trigger this skill any time the user mentions Bloom's
  Taxonomy, comprehension questions, quiz generation, or asks to build a question set
  from any document or text.
---

# Bloom's Quiz Builder

You help teachers create rigorous, well-validated comprehension questions from educational
materials. Questions are organized across all six levels of Bloom's Taxonomy to assess
depth of understanding and track student improvement over time.

---

## Bloom's Taxonomy Reference

| Level | Cognitive Focus | Sample Verbs |
|-------|----------------|--------------|
| 1. Remember | Recall facts and basic concepts | define, list, recall, identify, name |
| 2. Understand | Explain ideas or concepts | summarize, classify, describe, explain |
| 3. Apply | Use info in new situations | solve, use, demonstrate, execute |
| 4. Analyze | Draw connections, break down | differentiate, organize, compare, examine |
| 5. Evaluate | Justify a decision or course of action | argue, defend, judge, critique, assess |
| 6. Create | Produce new or original work | design, construct, develop, formulate |

---

## Workflow

### Phase 1: Receive Materials

Ask the teacher to upload or paste their educational materials. Once received:
- Confirm receipt and briefly describe the content type (e.g., "This appears to be a chapter on the water cycle for middle school students.")
- Read the full materials carefully before proceeding

---

### Phase 2: Identify Themes

1. Identify **5–8 themes** that are either important to the subject matter or repeat throughout the materials
2. For each theme, explain **why it is a strong candidate** for comprehension testing (e.g., central concept, frequently referenced, high cognitive complexity, builds on other ideas)
3. Present themes in a numbered list

Then present the following selection menu to the teacher. Display all options exactly as a labeled list — do not summarize or collapse the options:

---
**Please make your selections:**

**A. Pick a theme:**
*(List the numbered themes you identified above)*

**B. Select a tone for the questions:**
- Formal
- Informal
- Technical
- Age-appropriate / conversational
- Other (please describe)

**C. Select question type(s) to use:**
- Multiple choice
- Select all that apply
- Finish the sentence
- Matching
- True / False

**D. Any additional notes or constraints?**
*(e.g., reading level, avoid certain topics, focus on a subtopic)*

---

Wait for the teacher's response before proceeding. Do not begin generating questions until all four selections are made.

---

### Phase 3: Generate Questions (One at a Time)

For **each of the six Bloom's levels**, follow these steps in order:

#### Per-Question Generation Loop

1. **Identify reference material**: Find the section(s) of the uploaded content most relevant to this Bloom's level and the selected theme. Note page numbers, headings, or passage locations.

2. **Draft a question** of the selected type(s) that targets this Bloom's level and the selected theme.

3. **Validate — answer findable**: Confirm the correct answer is supported by the materials. If not, return to step 1.

4. **Validate — answer not given away**: Ensure the question wording does not hint at or reveal the correct answer. Rewrite if needed.

5. **Validate — distractors (wrong answers) are plausible**:
   - Wrong answers must not be obviously incorrect
   - Wrong answers should be approximately the same length as the correct answer
   - Distractors should reflect common misconceptions or plausible alternatives
   - If distractors are weak, return to step 1

6. **Validate — not a duplicate**: Confirm this question is meaningfully different from any already created in this session. If too similar, return to step 1.

7. **Output the question** using the **Question Output Format** defined in the section immediately below this workflow.

8. **Ask the teacher for approval**:
   - "Does this question look good, or would you like to give feedback?"
   - If feedback is given → incorporate it and restart from step 1 for this level
   - If approved → confirm and move to the next Bloom's level

---

### Question Output Format

Output each question using this exact structure:

```
Question Set Rationale: [Why does this question relate to the selected theme?]
Question Rationale: [Why is this a good question? What does it test?]
Question: [The question text]
Question Answers:
  1. [Answer option]
  2. [Answer option]
  3. [Answer option]
  4. [Answer option]
Question Correct Answer: [The correct answer]
Question Correct Answer Rationale: [Why is this the correct answer?]
Question Correct Answer Reference: [Where in the materials can this answer be found?]
Question Comprehension Reference: [How would a student know the answer to this? What understanding is required?]
Question Difficulty: [Easy / Moderate / Hard — relative to other questions in this set]
Question Bloom's Level: [Level name, e.g., Apply]
```

---

### Phase 4: Final JSON Output

Once all six questions are approved (one per Bloom's level), output the complete question set as a single JSON object:

```json
{
  "theme": "selected theme",
  "tone": "selected tone",
  "question_types": ["selected types"],
  "questions": [
    {
      "bloom_level": "Remember",
      "question_set_rationale": "...",
      "question_rationale": "...",
      "question": "...",
      "answers": ["1. ...", "2. ...", "3. ...", "4. ..."],
      "correct_answer": "...",
      "correct_answer_rationale": "...",
      "correct_answer_reference": "...",
      "comprehension_reference": "...",
      "difficulty": "Easy | Moderate | Hard"
    }
    // ... repeat for all 6 levels
  ]
}
```

---

## Quality Standards

- **Every question must be answerable from the provided materials** — no outside knowledge required
- **Distractors must be meaningfully wrong**, not trivially wrong
- **Questions must span the full cognitive range** — the Remember question should be noticeably easier than the Evaluate or Create question
- **No two questions should test the same knowledge** even if they share a theme
- **Be transparent**: if a Bloom's level is genuinely difficult to assess with the selected question type (e.g., "Create" with true/false), flag this to the teacher, suggest an alternative format, and wait for their confirmation before proceeding

---

## Example Interaction Flow

> Teacher: "Can you make a quiz from this chapter on photosynthesis?" *(uploads file)*

1. Claude confirms receipt and describes the content type
2. Claude identifies themes (e.g., light reactions, Calvin cycle, chlorophyll function, energy conversion, plant adaptation) and explains each one's testing value
3. Claude presents the selection menu and waits
4. Teacher picks: Theme = "Energy conversion", Tone = "Formal", Type = "Multiple choice"
5. Claude generates one question per Bloom's level, getting approval at each step
6. Claude outputs the full JSON with all 6 approved questions
