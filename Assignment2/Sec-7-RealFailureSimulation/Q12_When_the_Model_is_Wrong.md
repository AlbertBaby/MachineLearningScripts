# Q12 - When the Model Is Wrong

## Full usable prompt

```text
You are checking a previous answer that may sound confident but could be wrong. Review it again without assuming it is correct just because it was written earlier.

ORIGINAL QUESTION:
[Paste the original question]

PREVIOUS ANSWER:
[Paste the answer being challenged]

AVAILABLE EVIDENCE / SOURCES:
[Paste source material, data, or references. If none are available, write "None supplied".]

Review procedure:
1. Restate the exact claim or conclusion that needs verification.
2. Break the answer into checkable claims.
3. For each claim, label it Supported, Contradicted, Unverified, or Partly supported.
4. Identify missing evidence, unclear words, old information, or calculation mistakes.
5. Check claims against the supplied evidence. Do not make up sources.
6. Correct only what the evidence supports. If it is still uncertain, say so.

Return:
A. Verdict on previous answer: Correct / Partially correct / Incorrect / Cannot verify.
B. Claim audit table: Claim | Status | Evidence | Issue.
C. Weak assumptions and errors: concise list.
D. Corrected answer: answer the original question using supported information only.
E. Remaining uncertainty: what is still unknown.

Be skeptical but fair. The goal is accuracy, not proving the previous answer wrong.
```

## Why this structure?
It checks the old answer claim by claim against the evidence. I included "Cannot verify" because it is better to admit when there is not enough information than to replace one guess with another.

## Prompting technique
**Zero-shot review with evidence checking.** The prompt asks the model to challenge the old answer, but it still has to show evidence. For important or current information, checking reliable sources is better than only trusting the model.

## Failure modes prevented
- Defending an earlier answer because of anchoring.
- Automatically agreeing with the user's assertion that the answer is wrong.
- Replacing one hallucination with another.
- Treating unsupported claims as verified.
- Inventing citations or claiming unavailable research.
- Failing to identify the exact source of an error.

## Alternative prompt design

```text
Act as a fact-checker reviewing the answer below. Extract its factual claims, test each against the supplied sources, and mark unsupported or contradicted statements. Then produce a corrected answer that retains only supported claims. If the sources are insufficient, state what cannot be verified instead of guessing.

QUESTION:
[Paste question]

ANSWER:
[Paste answer]

SOURCES:
[Paste evidence]
```
