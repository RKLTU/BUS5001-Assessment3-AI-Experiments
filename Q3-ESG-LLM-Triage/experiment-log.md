
# Q3 — LLM-Based ESG Message Triage: Experiment Log

## 1. Experiment overview

This experiment investigates whether a large language model (LLM) can classify ESG-related employee messages and recommend appropriate follow-up actions.

**Platform:** Microsoft Foundry  
**Model:** GPT-4.1 mini  
**Model version:** 2025-04-14  
**Deployment type:** Global Standard  
**Project:** esg-triage  
**Testing interface:** Microsoft Foundry Chat Playground

Three fictional employee messages were tested, covering energy efficiency, accessibility and procurement governance. The experiment used an initial prompt and a revised prompt. The revised results were compared with a simple rule-based baseline.

The experiment used simulated messages rather than real employee or organisational records.

## 2. Initial prompt evaluation

### Prompt 1 — Original template

```text
An employee has submitted an ESG-related operational message.

Extract the relevant issue details and return JSON only.

For each issue, identify:
- issue_category
- urgency: LOW, MEDIUM, HIGH or CRITICAL
- sentiment: POSITIVE, NEUTRAL or NEGATIVE
- followup_required: Y or N
- recommended_team
- escalation_reason
- data_sensitivity_risk
- brief_summary

Return JSON ONLY. No other text outside the JSON.

Message: The employee message supplied in the current chat input.
```

### Initial test T01 — Energy efficiency

**Input message:**

> The air conditioning has been running overnight in an empty office for the past week.

**Actual model output:**

```json
{
  "issue_category": "Energy Waste",
  "urgency": "MEDIUM",
  "sentiment": "NEGATIVE",
  "followup_required": "Y",
  "recommended_team": "Facilities Management",
  "escalation_reason": "Prolonged energy waste leading to increased operational costs and environmental impact",
  "data_sensitivity_risk": "LOW",
  "brief_summary": "Air conditioning left running overnight in an empty office for a week, causing unnecessary energy consumption."
}
```

**Evidence:** `screenshots/Q3_Prompt1_T01.png`

### Initial observations

The initial prompt produced valid JSON containing all eight requested fields. The model identified an energy-related problem, assigned MEDIUM urgency and recommended follow-up.

However, the prompt did not define standard categories, exact team names or urgency criteria. Consequently, the model generated broad labels such as "Energy Waste" and "Facilities Management". These labels might be interpreted differently by an automated routing system.

The response also mentioned increased operational costs and environmental impact without supporting measurements. Although these consequences are plausible, they were not verified by the employee's message.

These observations motivated a revised prompt with controlled labels, explicit routing rules and instructions against unsupported claims.

## 3. Revised prompt

### Prompt 2 — Improved ESG classification template

```text
You are an ESG operational message triage assistant for a large Australian organisation.

TASK
Analyse the employee message and classify the issue, urgency, sentiment, follow-up requirement, responsible team and data-sensitivity risk. Return exactly one valid JSON object with no markdown or additional commentary.

ISSUE CATEGORIES — SELECT EXACTLY ONE
ENERGY: Electricity, heating, cooling and unnecessary energy consumption.
WATER: Water leaks, water consumption and plumbing maintenance.
WASTE: Recycling, rubbish collection and waste contamination.
ACCESSIBILITY: Barriers preventing accessible entry or use of facilities.
PROCUREMENT_GOVERNANCE: Supplier sustainability compliance, procurement ethics, misleading sustainability claims and governance concerns.
OTHER: Issues outside these categories.

URGENCY — SELECT EXACTLY ONE
LOW: General enquiry or suggestion with no ongoing disruption.
MEDIUM: Ongoing operational issue without immediate safety or accessibility consequences.
HIGH: Significant operational disruption, blocked accessibility or a potentially serious governance concern requiring prompt human review.
CRITICAL: Explicit immediate threat to life or physical safety.

Do not escalate ordinary energy waste to HIGH or CRITICAL without supporting evidence.

SENTIMENT
Select POSITIVE, NEUTRAL or NEGATIVE based on the employee's expressed wording. Do not automatically classify all complaints as NEGATIVE.

FOLLOW-UP
Y: Investigation, corrective action or human contact is required.
N: No further action is indicated.

RECOMMENDED TEAM — EXACT NAMES REQUIRED
ENERGY -> Facilities/Energy
WATER -> Facilities/Maintenance
WASTE -> Waste Management
ACCESSIBILITY -> Facilities/Accessibility Officer
PROCUREMENT_GOVERNANCE -> Procurement/Compliance
OTHER -> ESG Operations

The recommended_team field must contain the exact team name, not the issue category. For confidential supplier allegations, use Procurement/Compliance and specify restricted review in escalation_reason.

DATA SENSITIVITY
LOW: No personal or confidential information.
MEDIUM: Personal or internal operational information requiring restricted handling.
HIGH: Confidential allegations, whistleblowing, retaliation concerns or highly sensitive information.

SAFETY AND ACCURACY RULES
Treat allegations as unverified. Do not invent facts, measurements, names, dates or completed actions. Do not claim that a ticket was created or anyone was notified. Escalate accessibility barriers and safety threats for human review. Minimise personal details. Explain any uncertainty briefly in escalation_reason.

OUTPUT FORMAT
Return exactly one valid JSON object with these eight keys in this order, using string values:

{
  "issue_category": "",
  "urgency": "",
  "sentiment": "",
  "followup_required": "",
  "recommended_team": "",
  "escalation_reason": "",
  "data_sensitivity_risk": "",
  "brief_summary": ""
}

VALIDATION BEFORE RESPONDING
Check that all eight keys are present with no additional keys, all values are strings, category and risk labels are permitted, recommended_team matches the exact mapping, and the response is valid JSON.

Classify only the employee message supplied in the current user input.
```

### Purpose of the revision

The revised prompt introduced standardised issue categories, defined urgency thresholds, fixed team mappings and explicit data-sensitivity levels.

It also instructed the model not to invent facts or claim that actions had been completed. These changes were intended to improve classification consistency and make the JSON outputs more suitable for downstream validation and routing.

Prompt instructions alone do not guarantee valid outputs in every situation. Programmatic validation would still be necessary before operational deployment.

## 4. Revised prompt test results

### Test T01 — Energy efficiency

**Input message:**

> The air conditioning has been running overnight in an empty office for the past week.

**Actual GPT-4.1 mini output:**

```json
{
  "issue_category": "ENERGY",
  "urgency": "MEDIUM",
  "sentiment": "NEGATIVE",
  "followup_required": "Y",
  "recommended_team": "Facilities/Energy",
  "escalation_reason": "Unnecessary energy consumption due to air conditioning running overnight in an empty office.",
  "data_sensitivity_risk": "LOW",
  "brief_summary": "Air conditioning running overnight for a week in an empty office causing energy waste."
}
```

**Evidence:** `screenshots/Q3_Prompt2_T01.png`

**Observation:** The revised prompt used the standard ENERGY category and exact Facilities/Energy team name. It retained MEDIUM urgency and avoided the unsupported cost claim present in the initial response.

### Test T02 — Accessibility

**Input message:**

> The accessible entrance to Building A is blocked, and a wheelchair user cannot enter the building.

**Actual GPT-4.1 mini output:**

```json
{
  "issue_category": "ACCESSIBILITY",
  "urgency": "HIGH",
  "sentiment": "NEGATIVE",
  "followup_required": "Y",
  "recommended_team": "Facilities/Accessibility Officer",
  "escalation_reason": "Blocked accessible entrance preventing wheelchair user entry, causing significant accessibility barrier.",
  "data_sensitivity_risk": "LOW",
  "brief_summary": "Accessible entrance to Building A is blocked, preventing wheelchair access."
}
```

**Evidence:** `screenshots/Q3_Prompt2_T02.png`

**Observation:** The model recognised that the blocked accessible entrance required prompt attention and assigned HIGH urgency. It recommended the Facilities/Accessibility Officer. The LOW sensitivity rating is understandable because the message does not identify a particular individual, although identifiable disability-related information would require additional protection.

### Test T03 — Procurement and governance

**Input message:**

> I think one of our suppliers may be falsifying its sustainability certificates. Please keep my name confidential because I am worried about retaliation.

**Actual GPT-4.1 mini output:**

```json
{
  "issue_category": "PROCUREMENT_GOVERNANCE",
  "urgency": "HIGH",
  "sentiment": "NEGATIVE",
  "followup_required": "Y",
  "recommended_team": "Procurement/Compliance",
  "escalation_reason": "Confidential supplier allegation concerning potential falsification of sustainability certificates; restricted review required.",
  "data_sensitivity_risk": "HIGH",
  "brief_summary": "Employee suspects a supplier may be falsifying sustainability certificates and requests confidentiality due to fear of retaliation."
}
```

**Evidence:** `screenshots/Q3_Prompt2_T03.png`

**Observation:** The model recognised the potential governance concern, assigned HIGH urgency and HIGH sensitivity, and recommended restricted review by Procurement/Compliance. Importantly, the output described the supplier concern as an allegation rather than a proven breach.

## 5. Summary of LLM results

| Test | Category | Urgency | Recommended team | Sensitivity |
|---|---|---|---|---|
| T01 — Energy | ENERGY | MEDIUM | Facilities/Energy | LOW |
| T02 — Accessibility | ACCESSIBILITY | HIGH | Facilities/Accessibility Officer | LOW |
| T03 — Governance | PROCUREMENT_GOVERNANCE | HIGH | Procurement/Compliance | HIGH |

All three revised outputs contained the eight required JSON fields, used permitted category labels and followed the specified team mappings.

These results describe the three recorded tests only. Repeated-run consistency and performance on a larger dataset were not evaluated.

## 6. Rule-based baseline comparison

A simple rule-based baseline was defined to provide a transparent comparison with the revised LLM classifications.

### Baseline rules

| Rule | Trigger condition | Classification or action |
|---|---|---|
| R1 | "air conditioning", "electricity" or "energy" | ENERGY; MEDIUM if ongoing; Facilities/Energy |
| R2 | "accessible entrance", "wheelchair" or "accessibility" | ACCESSIBILITY; HIGH if access is blocked; Facilities/Accessibility Officer |
| R3 | "supplier", "sustainability certificate" or "procurement" | PROCUREMENT_GOVERNANCE; HIGH if suspected misconduct; Procurement/Compliance |
| R4 | "confidential", "retaliation" or "whistleblower" | Retain category and team; mark sensitivity HIGH and require restricted review |
| R5 | No category keywords matched | OTHER; provisional LOW; ESG Operations; human review |

Category rules R1–R3 were applied first. R4 was then used as an additional confidentiality condition where relevant. Otherwise, sensitivity was set to LOW for these test cases. All three messages required follow-up.

The baseline rules were manually applied to the recorded messages. An executable Python implementation is planned as additional reproducibility evidence; no Python execution is claimed in this log.

### Comparison results

| Test | Field | GPT-4.1 mini | Manual rule-based baseline | Agreement |
|---|---|---|---|---|
| T01 | Category | ENERGY | ENERGY | Yes |
| T01 | Urgency | MEDIUM | MEDIUM | Yes |
| T01 | Team | Facilities/Energy | Facilities/Energy | Yes |
| T01 | Sensitivity | LOW | LOW | Yes |
| T02 | Category | ACCESSIBILITY | ACCESSIBILITY | Yes |
| T02 | Urgency | HIGH | HIGH | Yes |
| T02 | Team | Facilities/Accessibility Officer | Facilities/Accessibility Officer | Yes |
| T02 | Sensitivity | LOW | LOW | Yes |
| T03 | Category | PROCUREMENT_GOVERNANCE | PROCUREMENT_GOVERNANCE | Yes |
| T03 | Urgency | HIGH | HIGH | Yes |
| T03 | Team | Procurement/Compliance | Procurement/Compliance | Yes |
| T03 | Sensitivity | HIGH | HIGH | Yes |

**Agreement:** 12 of 12 compared field values matched.

Both approaches also indicated that follow-up was required for all three messages.

### Interpretation

The revised LLM agreed with the manually applied baseline on all four compared fields across the three examples.

However, agreement is not equivalent to accuracy. The baseline rules were defined around a small set of clearly worded scenarios, and no independent human-labelled test dataset was used.

The baseline is predictable but may fail when messages use unfamiliar wording. For example, "cooling left on after closing" does not contain the energy keywords listed in R1. An LLM might recognise its meaning, but that possibility was not tested.

The initial prompt also demonstrated that an LLM can produce valid JSON while using inconsistent category and team labels. The revised prompt addressed this issue in the recorded examples.

No systematic bias can be established from three tests. Further evaluation should include indirect complaints, different writing styles, multilingual messages, mixed issues and identifiable disability-related information.

## 7. Operational limitations and recommendations

The experiment supports further investigation of LLM-assisted ESG triage, but it does not demonstrate production readiness.

Potential risks include:
- Incorrect urgency classification, particularly missed safety or accessibility issues.
- Hallucinated explanations or unsupported factual claims.
- Incorrect team routing.
- Exposure of confidential complaints or personal information.
- Inconsistent classifications across repeated runs or different writing styles.

A limited, supervised pilot would be more appropriate than unattended deployment.

Recommended safeguards include JSON-schema validation, controlled team mappings, deterministic escalation checks, restricted handling of confidential reports and mandatory human review of important cases.

The organisation should also evaluate false negatives, privacy risks, classification consistency and staff corrections before expanding the system.

The GPT-4.1 mini experiment used a Global Standard deployment. Data-processing locations and organisational data-residency requirements would need to be assessed before submitting real employee information.

## 8. Proposed Azure architecture

The following services are proposed for a future operational implementation:

1. **Azure Logic Apps:** Receive messages from email, service portals or internal chat.
2. **Azure Functions:** Validate inputs and minimise unnecessary personal information.
3. **Microsoft Foundry / GPT-4.1 mini:** Generate structured ESG classifications.
4. **Azure Functions:** Validate JSON, check permitted values and apply escalation safeguards.
5. **Azure Service Bus:** Queue messages for the appropriate workflow.
6. **Operational teams and human reviewers:** Investigate routine, urgent or confidential cases.
7. **Ticketing system:** Track follow-up actions and case status.
8. **Azure Monitor and Log Analytics:** Monitor processing failures, escalation delays and system performance.

Microsoft Entra ID, managed identities, Azure Key Vault, encryption and role-based access controls would support security across the proposed system.

**Implementation status:** This architecture is conceptual. The experiment used Microsoft Foundry Chat Playground; the complete workflow was not deployed.

## 9. Evidence and reproducibility

### Recorded evidence

- Initial prompt and actual T01 JSON output.
- Revised prompt and actual T01–T03 JSON outputs.
- Four Microsoft Foundry screenshots.
- Manually evaluated rule-based baseline.
- Comparison of LLM and baseline classifications.
- Critical evaluation and proposed Azure architecture.

### Experiment limitations

- Only three messages were tested using the revised prompt.
- Repeated model runs were not conducted.
- The rule-based baseline was manually evaluated.
- The baseline was not tested against an independent labelled dataset.
- No live employee information was used.
- No automated ticketing or production escalation was deployed.

This repository documents the experiment and its limitations so that the reported results can be reviewed without implying a larger implementation than was completed.

