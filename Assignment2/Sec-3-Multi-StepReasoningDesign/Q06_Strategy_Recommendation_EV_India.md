# Q6 - Strategy Recommendation Under Uncertainty

## Full usable prompt

```text
Act as a strategy consultant helping a client think about entering the electric vehicle (EV) market in India. Give a practical recommendation, not only general facts.

First, identify the decision that must be made and the client facts that are missing. Do not assume the client's budget, capabilities, target segment, time horizon, risk appetite, manufacturing capacity, brand, or distribution network.

Evidence rules:
1. Separate facts, assumptions, and possible ideas.
2. Do not make up market size, growth, policy details, costs, or forecasts.
3. Mark current market information as unknown if no source is given.
4. Use clear decision criteria and compare the options.
5. Include reasons why the recommendation may not work.

Structure the analysis:

A. Decision framing
- Define what "enter the EV market" could mean: vehicle segment, value-chain role, geography, and entry mode.
- List client-specific information required before a final investment decision.

B. Decision criteria
Use criteria such as demand, competition, government rules, cost, company capability, and risk. Mark the most important ones.

C. Strategic options
Compare at least three options where relevant: no entry / wait, partnership or pilot, and direct scaled entry. Add segment-specific options only if supported by the client's context.

D. Scenarios
Assess a base, positive, and negative scenario. State the main assumption and what could change each scenario. Do not invent numbers.

E. Option comparison
Table: Option | Company fit | Main requirement | Investment level | Main benefit | Main risk.

F. Counterarguments
Give a real reason against the leading option and say what information could change the recommendation.

G. Recommendation
Give a provisional recommendation and confidence level. If there is not enough information, suggest a small first step instead of pretending to be certain.

H. Next steps
List the next steps, such as market research, talking to partners, or trying a small pilot.

I. Executive conclusion
State: recommended option, why, biggest uncertainty, strongest counterargument, and next decision gate.

CLIENT CONTEXT:
[Describe the client, capabilities, target customer, budget, objectives, and risk appetite if known]
```

## Why this structure?
The question is too broad for only a yes or no answer. I broke it into criteria, options, possible situations, and arguments against the recommendation. This should make the answer more balanced.

## Prompting technique
**Zero-shot with a structured answer.** The right answer depends on the client, so I did not use one fixed example. The headings guide the model through the main things to consider.

## Failure modes prevented
- Assuming all EV segments and business models are equivalent.
- Inventing market data or client capabilities.
- Giving a one-sided recommendation.
- Hiding assumptions inside forecasts.
- Ignoring downside scenarios and reversibility.
- Making a final investment recommendation when key inputs are missing.

## Alternative prompt design

```text
Evaluate an India EV entry decision as a stage-gated investment choice. Compare (1) do not enter, (2) run a limited pilot or partnership, and (3) invest for direct scale. Score each against client-defined strategic fit, economics, capabilities, risk, and reversibility. Show evidence, assumptions, counterarguments, and the facts needed to change the ranking. If client context or current market evidence is missing, request it and make only a provisional recommendation.

CLIENT CONTEXT:
[Paste details]
```
