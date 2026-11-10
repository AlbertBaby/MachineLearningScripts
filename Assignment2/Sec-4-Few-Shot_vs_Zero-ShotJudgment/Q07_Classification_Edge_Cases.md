# Q7 - Classification with Edge Cases

## Zero-shot prompt

```text
Classify each customer complaint into exactly one primary category:
- Billing
- Network
- Device
- Other

Definitions:
- Billing: charges, invoices, payment, refunds, balance, plan pricing, unexpected fees, or billing disputes.
- Network: signal, coverage, mobile data, broadband connectivity, call drops, speed, latency, or service outage.
- Device: handset/router hardware, physical damage, battery, screen, device setup, firmware, or device-specific faults.
- Other: complaints that do not fit the above categories, including account or service issues without a clearer billing, network, or device cause.

Classification rules:
1. Choose the primary issue the customer wants resolved, not every topic mentioned.
2. If there is more than one issue, choose the one that seems most important.
3. Do not guess the cause of the problem.
4. Use Other when the complaint is too vague or does not fit.
5. If two issues are equally important, choose one and mark it as ambiguous.
6. Return JSON with: complaint_id, category, confidence, short_evidence, ambiguous.

Classify the following complaints:
[Paste complaint records]
```

## Few-shot prompt

```text
You are classifying customer complaints into one primary category: Billing, Network, Device, or Other.

Use these definitions:
- Billing: charges, invoices, payments, refunds, balances, plan price, or fees.
- Network: signal, coverage, mobile data, broadband, speed, call drops, or outages.
- Device: handset/router hardware, battery, screen, physical damage, setup, or device-specific faults.
- Other: issues not primarily about billing, network, or device, or too vague to classify.

Follow the labelled examples as demonstrations of the category boundaries. Do not copy their wording; apply the same principles to new cases.

Examples:
1. Complaint: "I was charged twice for the same monthly plan."
   Category: Billing
   Reason: The main issue is a duplicate charge.

2. Complaint: "My phone shows full signal but mobile data keeps disconnecting."
   Category: Network
   Reason: The issue is mobile data connectivity, even though a phone is mentioned.

3. Complaint: "The handset battery drains from 100% to 10% in an hour."
   Category: Device
   Reason: The main issue is device battery performance.

4. Complaint: "The internet is slow and the monthly bill is also higher than expected."
   Category: Network
   Reason: Both issues are mentioned, but the first problem is the internet. Mark it as ambiguous.

5. Complaint: "Please call me. I need help with my account."
   Category: Other
   Reason: No specific billing, network, or device problem is stated.

6. Complaint: "The app says payment failed, but money was deducted from my bank."
   Category: Billing
   Reason: The central issue is payment reconciliation.

For each new complaint, return JSON with: complaint_id, category, confidence, short_evidence, and ambiguous. Do not invent missing context. Use Other if the category is unclear.

COMPLAINTS:
[Paste complaint records]
```

## Why this structure?
Both prompts use the same categories and rules. The few-shot prompt adds examples for confusing cases, such as when a phone is mentioned but the actual problem is the network.

## Prompting technique
**Both zero-shot and few-shot.** Zero-shot is useful when the category definitions are already clear. Few-shot can help when the same confusing cases come up again and again.

## Why few-shot helps (and when it does not)
Few-shot examples demonstrate how to apply category boundaries consistently. They can reduce ambiguity in cases where keywords are misleading. They do not automatically improve performance if examples are unrepresentative, contradictory, too few, or biased toward one category.

## When few-shot breaks
- Examples contain incorrect labels.
- Examples mostly show only one category.
- New complaints are very different from the examples.
- Examples conflict with the definitions.
- The model copies words from an example instead of applying the rule.

## Failure modes prevented
- Classifying every mention of "phone" as Device.
- Classifying every mention of "internet" as Network when the main issue is a bill.
- Forcing a confident label on vague complaints.
- Inconsistent treatment of overlapping issues.
- Unstructured output that is hard to process.

## Alternative prompt design

```text
Act as a complaint-triage classifier. Identify the customer's main requested resolution, map it to Billing, Network, Device, or Other using the supplied definitions, and return one primary label. If two categories are genuinely inseparable, choose the dominant issue only when supported and set ambiguous=true. Include a short evidence phrase and qualitative confidence. Do not infer causes.

TAXONOMY:
[Paste category definitions]

COMPLAINTS:
[Paste records]
```
