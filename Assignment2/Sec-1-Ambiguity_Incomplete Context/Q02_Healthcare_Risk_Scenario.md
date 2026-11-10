# Q2 - Healthcare Risk Scenario

## Full usable prompt

```text
You are helping to organise a rough patient summary for a doctor to review. You are not diagnosing the patient, so do not present any condition as confirmed.

Safety and evidence rules:
1. Do not give a definite diagnosis, treatment, or medicine advice.
2. Use only what is written in the summary. Do not make up test results, history, or timelines.
3. Point out details that do not match.
4. Possible conditions must be labelled as things for a clinician to check, not as diagnoses.
5. Include unknown information. If there may be an urgent warning sign, say that urgent in-person care may be needed.

Return:

A. Structured patient summary
- Presenting concern
- Symptoms and onset/duration
- Important symptoms and findings
- Medical history, medicines, and tests if given

B. Inconsistencies
Table: Conflicting details | Where they appear | Why clinically relevant | Clarification needed.

C. Possible diagnoses / differential considerations
Table: Possibility to assess | Details that support it | Missing details | Confidence (Low / Moderate / Higher).
Do not rank a possibility as confirmed.

D. Risky assumptions
List assumptions that could be unsafe, especially treating missing information as normal.

E. Unknowns and missing information
List important unknowns and questions the doctor should ask.

F. Safety flags
Identify any documented red flags. If none are documented, say "No red flags are explicitly documented in the supplied summary"; do not say that red flags are absent.

G. Clinician handoff
Provide a concise neutral handoff summary and a short list of clarification questions.

PATIENT SUMMARY:
[Paste rough patient summary here]
```

## Why this structure?
The prompt keeps facts, possible conditions, contradictions, and missing details in separate sections. I think this is important because a messy note should not suddenly look complete. The safety section can point out possible urgent issues without saying everything is safe.

## Prompting technique
**Zero-shot with a fixed format.** Patient cases can vary a lot, so examples may not fit. I used Low, Moderate, and Higher confidence instead of made-up percentages.

## Failure modes prevented
- A possible diagnosis being written as a confirmed diagnosis.
- Missing information being treated as a normal finding.
- Invented clinical history, examination results, or test values.
- False precision in confidence scores.
- Contradictions being silently reconciled.
- Unsafe reassurance when emergency information is incomplete.

## Alternative prompt design

```text
Convert the following rough patient note into a clinician-review worksheet. First extract the documented facts verbatim or faithfully. Then list up to five differential considerations only where supported, with evidence for, evidence against, and information still needed. Mark all uncertain or contradictory details. Never diagnose, prescribe, or infer that an undocumented symptom is absent. Finish with safety concerns and questions for the treating clinician.

NOTE:
[Paste patient summary]
```
