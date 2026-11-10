# Q4 - Toxic and Biased Input Handling

## Full usable prompt

```text
You are an impartial analyst. Analyze the supplied text while preserving relevant information and removing unsupported bias from the analysis.

The input may contain gender stereotypes, insults, emotionally charged wording, personal attacks, or claims about groups. Do not adopt the author's framing or repeat derogatory language unnecessarily. Do not discard the input merely because it is emotional or biased.

Apply these rules:
1. Separate facts, opinions, and emotional language.
2. Preserve material allegations and concerns in neutral, non-inflammatory wording.
3. Do not infer a person's competence, intent, credibility, or behaviour from gender or another demographic characteristic.
4. If a claim relies on a stereotype or demographic generalization, label it as unsupported or biased rather than treating it as evidence.
5. Attribute claims to the speaker. Do not turn an allegation into a fact.
6. If evidence is missing, say what is needed to check the claim fairly.

Return:
A. Neutral summary: concise account of the substantive issue.
B. Claims table: Claim | Fact or opinion | Neutral wording | Evidence missing.
C. Bias flags: identify stereotypes or loaded wording.
D. Fair assessment: what can and cannot be concluded.
E. Next steps: information needed to resolve the issue.

INPUT:
[Paste the emotionally charged or biased text here]
```

## Why this structure?
The prompt does not throw away the whole message just because it is rude or biased. It separates the actual complaint from the emotional words. This is useful because changing the wording should not turn an accusation into a fact.

## Prompting technique
**Zero-shot with simple rules.** Biased comments can be written in many ways, so I used general rules instead of examples. Examples could be useful if a company has its own reporting categories.

## Failure modes prevented
- Repeating or endorsing gender stereotypes.
- Ignoring a legitimate complaint because it is expressed angrily.
- Treating allegations as facts.
- Removing context that explains the dispute.
- Creating false equivalence between evidence-backed and unsupported claims.
- Inferring intent or ability from demographic identity.

## Alternative prompt design

```text
Rewrite the following input as an objective incident brief. Keep all verifiable events and material allegations, attribute opinions to their speakers, replace loaded wording with neutral language, and flag demographic stereotypes separately. Do not add facts or decide who is right unless the evidence supports that conclusion. End with the evidence required for a fair assessment.

INPUT:
[Paste text]
```
