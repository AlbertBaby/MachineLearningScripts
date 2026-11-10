# Q8 - Executive-Ready Output

## Full usable prompt

```text
You are preparing a short update for senior leaders. Turn the supplied analysis into a clear summary that focuses on action.

Audience: senior leaders with limited time.
Objective: make the decision, risk, and required action immediately clear.

Rules:
1. Lead with the most important conclusion or decision required.
2. Include only insights that affect a decision, outcome, risk, or priority.
3. Keep facts and recommendations separate.
4. Do not make up metrics, owners, dates, or business impact.
5. Avoid jargon, repetition, and long background explanations.
6. Mention important uncertainty briefly.
7. Keep the response under 350 words unless the user gives another limit.

Use this exact structure:

1. Executive takeaway - maximum 2 sentences.
2. Key findings - table with Finding | Business impact | Confidence.
3. Decisions required - numbered list.
4. Top risks - maximum 3.
5. Next actions - table with Action | Owner | Timing. Use "Not specified" if missing.
6. Open question - the main unresolved issue.

INPUT:
[Paste report, analysis, or meeting notes]
```

## Why this structure?
The format starts with the main point and then shows findings, decisions, risks, and actions. The word limit and tables should stop the answer from becoming too long or hiding actions in paragraphs.

## Prompting technique
**Zero-shot with a fixed format.** This is mainly a summarising task, so clear headings are enough. Examples may help if a company has a very specific writing style.

## Failure modes prevented
- Long, unfocused summaries.
- Made-up owners, dates, or financial impact.
- Too much jargon for senior leaders.
- Leaving out risks or open questions.

## Alternative prompt design

```text
Rewrite the input as a one-page leadership memo. Start with "Decision needed". Provide no more than five evidence-backed insights, three risks, and five actions. Each action must have an owner and due date only when these are stated in the source; otherwise mark them "TBD". End with the consequence of delaying the decision. Maximum 250 words.

SOURCE:
[Paste input]
```
