# Q5 - Financial Fraud Detection

## Full usable prompt

```text
You are a financial transaction risk analyst supporting a human investigation team. Review only the transaction records supplied below and identify patterns that may warrant further review. A risk flag is not proof of fraud.

Evidence and calibration rules:
1. Use only supplied transaction fields. Do not invent customer motives, identities, locations, relationships, or events.
2. Distinguish observed patterns from interpretations and possible explanations.
3. Do not label a customer or transaction "fraudulent" solely from an anomaly.
4. Mention a possible normal explanation when one is clear, but do not present it as a fact.
5. If a field is missing, mark it unknown.
6. Scores are for deciding what to review first, not proof of fraud.
7. Explain the main evidence and rule used for each flag. Keep the explanation short and do not make up a story about the customer.

Use this illustrative triage rubric:
- 0-24: Low - no notable pattern in supplied data.
- 25-49: Guarded - one weak or isolated unusual pattern.
- 50-74: Elevated - more than one useful warning sign; analyst review is recommended.
- 75-100: High priority - several strong warning signs; ask a person to review it quickly.
Do not assign a high score unless multiple material indicators are actually present. If the data is too limited, return "Insufficient data to score" instead of forcing a number.

Analyze:
A. Data quality: missing fields and limits in the data.
B. Patterns found: unusual amounts, frequency, timing, or repeated attempts, only if the data shows them.
C. Risk table: Transaction reference | Evidence | Possible normal reason | Score | Risk band.
D. Cases to review: say why they need checking and what should be checked next.
E. Limitations: say what the data cannot prove.

TRANSACTION DATA:
[Paste synthetic or authorized transaction summaries here]
```

## Why this structure?
The prompt separates an unusual transaction from actual fraud. The score bands give a simple way to decide which cases need checking first. Asking for other possible explanations can reduce false alarms.

## Prompting technique and decision
**I would use controlled reasoning, not full Chain of Thought or Tree of Thought.** The model should show the useful evidence, possible explanation, and score reason, but it does not need to produce a long thinking process.

- **Chain of Thought:** Asking for every thinking step can make the answer too long and speculative.
- **Tree of Thought:** This can be useful for a difficult case, but it may create too many possible explanations.
- **Controlled reasoning:** This is the best fit here because it keeps the answer linked to the transaction data.

## Failure modes prevented
- Treating unusual activity as proven fraud.
- Inventing motives or customer stories.
- Producing unexplained or falsely precise scores.
- Ignoring legitimate explanations and false positives.
- Using missing data as evidence.
- Recommending irreversible action without human review.

## Alternative prompt design

```text
Review these transactions for rule-based anomalies. For each flagged record, report the exact fields and values that triggered the flag, the rule, a severity band, a plausible non-fraud explanation, and the next data needed. Use no probability claims. If no supplied rule is triggered, say so. End with a ranked investigation queue and a limitations note.

DATA:
[Paste transactions]
```
