# Q1 - Consulting Case: Messy Client Problem

## Full usable prompt

```text
You are helping a telecom strategy analyst. Read the client material between <CLIENT_INPUT> and </CLIENT_INPUT>. It may be messy, incomplete, or contain different opinions.

Turn the material into a short problem-analysis brief. Do not assume a stakeholder is right just because they sound confident.

Rules for evidence and uncertainty:
1. Use only facts stated in the input. Do not make up numbers, dates, causes, or customer groups.
2. Separate facts, stakeholder opinions, and possible reasons.
3. If statements conflict, show both instead of choosing one.
4. Write "Not provided" when information is missing.
5. Do not claim a cause unless the input supports it.

Produce the following sections:

A. Problem statement
- Restate the reported ARPU decline in neutral language.
- Identify the period, geography, product, and customer segment only if provided.
- List any scope details that are unknown.

B. Evidence register
Create a table with columns: Point, Type (fact / opinion / unknown), Source if known, Notes.

C. Structured problem hypotheses
Create a table with columns: Possible reason, Supporting point, Missing information, Confidence (High/Medium/Low).
Give more than one possible reason if the input supports it.

D. Contradictions and unresolved questions
List each material contradiction, the statements in conflict, why it matters, and the clarification required.

E. Missing data
List the main missing data needed to understand the ARPU decline. For example, this could include the time period, plans/prices, churn, customer mix, and promotions. Say why each item matters.

F. Recommended next steps
Give 3 to 5 next steps. Include what should be done and what information is needed.

G. Executive summary
In no more than 120 words, state what is known, what is not known, the leading hypotheses (if any), and the next best action.

<CLIENT_INPUT>
[Paste the messy client paragraph and stakeholder comments here]
</CLIENT_INPUT>
```

## Why this structure?
I used a simple order: first understand the problem, then list the facts, possible reasons, missing information, and next steps. The tables make it easier to see when people are saying different things. The last check is there to reduce guesses.

## Prompting technique
**Zero-shot prompt.** I did not add examples because every client situation can be different. Instead, I gave clear sections for the answer.

## Failure modes prevented
- Hallucinated ARPU values, periods, segments, or root causes.
- Treating stakeholder opinions as verified facts.
- Silently resolving contradictory statements.
- Confusing correlation with causation.
- Producing generic recommendations disconnected from missing evidence.
- Expressing false certainty when the material is insufficient.

## Alternative prompt design

```text
Act as a skeptical consulting analyst. Convert the supplied telecom notes into (1) verified facts, (2) attributed claims, (3) conflicting statements, (4) testable explanations for the ARPU decline, (5) information required to distinguish those explanations, and (6) a prioritized 30-day investigation plan. For every statement, label its evidence status and confidence. Use "unknown" wherever the input is silent. Never infer a cause from the fact that ARPU declined. End with the three questions the client must answer first.

INPUT:
[Paste client material]
```
