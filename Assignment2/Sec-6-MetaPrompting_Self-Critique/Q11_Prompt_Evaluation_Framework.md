# Q11 - Prompt Evaluation Framework

## Full usable prompt

```text
You are checking the quality of a prompt. Evaluate the prompt below for clarity and robustness. Judge the prompt itself, not only the answer it may produce.

CANDIDATE PROMPT:
[Paste prompt here]

Evaluation rules:
1. Score only what is written in the prompt.
2. Give a score from 1 to 5, where 1 is poor and 5 is excellent.
3. Give a short reason for each score.
4. Point out the most important weakness first.
5. A longer prompt should not automatically get a higher score.

Score these dimensions:

A. Clarity
Assess whether the task, audience, inputs, terminology, constraints, and success criteria are understandable and unambiguous.

B. Robustness
Assess whether the prompt handles incomplete, contradictory, malformed, adversarial, or out-of-scope inputs; prevents unsupported assumptions; and defines fallback behaviour.

Return:
1. Scorecard table: Dimension | Score (1-5) | Evidence | Main weakness.
2. Overall assessment: concise summary of strengths and limitations.
3. Failure scenarios: up to three inputs that may cause the prompt to fail.
4. Recommended changes: specific edits.
5. Revised prompt: provide one if enough information exists.

Do not claim that a prompt is secure or reliable merely because it contains words such as "accurate", "robust", or "do not hallucinate".
```

## Why this structure?
The rubric defines what clarity and robustness mean and requires evidence for each score. Failure scenarios test the prompt against realistic conditions rather than relying on vague impressions.

## Prompting technique
**Zero-shot with a scoring guide.** The score descriptions give the model something clear to follow. Examples may help later if many people need to score prompts in the same way.

## Failure modes prevented
- Scores based only on a general impression.
- Evaluating the answer instead of the prompt.
- Ignoring unusual or misleading inputs.
- Giving vague improvement advice.

## Alternative prompt design

```text
Act as a reviewer of the prompt below. Identify unclear parts, missing constraints, unsupported assumptions, injection weaknesses, and missing fallback behaviour. Score clarity and robustness from 1-5 with evidence. Then suggest a few useful edits. Do not rewrite unrelated parts.

PROMPT:
[Paste candidate]
```
