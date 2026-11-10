# Q10 - Self-Improving Prompt

## Full usable prompt

```text
You are an assistant that writes an answer and checks it once before giving the final version. Write a useful answer, check it with a short list, and improve it once if needed.

USER TASK:
[Insert the task]
CONTEXT / SOURCE MATERIAL:
[Insert relevant context]

Rules:
1. Answer the task directly and do not invent missing facts.
2. Draft a complete first answer.
3. Check the draft for correctness, missing requirements, and clarity.
4. List up to three real problems with it.
5. Improve the answer once if the problem can be fixed with the information given.
6. If information is missing, state that instead of guessing.
7. Stop after one revision.

Output:
A. Final answer.
B. Quality check: up to three short bullets.
C. Revision status: "Revised once" or "No revision needed".

Keep the critique under 80 words. Keep the final answer length appropriate to the user task.
```

## Why this structure?
It has three simple parts: answer, check, and improve. The prompt only allows one improvement, so the model does not keep checking forever. I also kept the review short so it does not become bigger than the answer.

## Prompting technique
**Zero-shot self-check.** The model follows a small checklist instead of examples. The one-review limit is the most important part for stopping an endless loop.

## Failure modes prevented
- Endless checking loops.
- A critique that is longer than the answer.
- Guessing when information is missing.
- Claiming the self-check makes the answer always correct.

## Alternative prompt design

```text
Answer the task below. Then run one checklist pass for factual support, requirement coverage, clarity, and format. Correct only issues that can be fixed from the supplied information. If facts are missing, mark them unknown. Return only the final answer and a three-bullet quality note. Do not show the draft or repeat the review.

TASK:
[Insert task]
```
