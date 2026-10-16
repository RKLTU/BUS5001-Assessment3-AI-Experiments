# Q4: Google NotebookLM Experiment Log

**Course:** BUS5001 — Cloud Platforms and Analytics  
**Assessment:** Assessment 3, Question 4  
**Student ID:** 22738404  
**Notebook:** `22738404_BUS5001_Q4_ESG_Research_Evaluation`  
**Platform:** Google NotebookLM  
**Research scenario:** A postgraduate business analytics student uses an AI research assistant to understand and compare IFRS sustainability disclosure standards, prepare revision materials, and check source-grounded answers.

## Sources and method

Two official IFRS Foundation standards (June 2023 editions) were uploaded to one NotebookLM notebook:

1. *IFRS S1 — General Requirements for Disclosure of Sustainability-related Financial Information* (`IFRS S1.pdf`).
2. *IFRS S2 — Climate-related Disclosures* (`IFRS S2.pdf`).

Five feature experiments were performed. E1 used IFRS S1 only; E2–E5 used both standards. Prompts were entered once for the reported outputs. The evaluation considers task completion, academic usefulness, accuracy, citation grounding, limitations, and risks of overreliance. Observed results are distinguished from the evaluator's analysis. A screenshot demonstrates only the content visible in that screenshot; it does not validate every claim in a generated response.

## Experiment overview

| ID | Feature | Academic use case | Observed outcome |
|---|---|---|---|
| E1 | Source-grounded summarisation | Revise IFRS S1 | Structured summary covering requested topics; one materiality citation inspected |
| E2 | Cross-document comparison | Compare IFRS S1 and S2 for an ESG briefing | Seven-area comparison and three insights; a transition-plan claim was overstated |
| E3 | Source-grounded Q&A and unsupported-question test | Answer technical questions without inventing external statistics | Answered three standards questions; declined to invent an ASX 200 percentage |
| E4 | Interactive Learning Overview | Prepare postgraduate revision material | Seven-section interactive report with takeaways and misconceptions |
| E5 | Quiz generation | Test applied knowledge through scenario questions | Ten-question quiz generated; first two questions examined, not all ten |

---

## E1 — Source-grounded IFRS S1 summarisation

**Feature:** Chat-based source-grounded summary.  
**Selected source:** IFRS S1 only.  
**Scenario:** A postgraduate student needs an introductory study summary of IFRS S1.

### Exact prompt

> Act as an academic research assistant helping a postgraduate business analytics student understand IFRS S1. Using only the uploaded IFRS S1 document, provide a structured summary of its purpose, scope, four core content areas, materiality requirements and general disclosure principles. Explain each point in clear academic language and include source citations. Distinguish requirements stated in the document from your own explanations. If any requested information is not supported by the source, explicitly state that it is not available. Keep the response within approximately 400 words.

### Actual observed response (transcribed)

**Summary of IFRS S1: General Requirements for Disclosure of Sustainability-related Financial Information**

**Purpose:** IFRS S1 mandates disclosure of sustainability-related risks and opportunities useful to primary users (investors, lenders and creditors) when deciding whether to provide resources. It described effects on cash flows, access to finance and cost of capital over short, medium and long terms.

**Scope:** It described applicability when preparing disclosures under IFRS Sustainability Disclosure Standards, regardless of the GAAP used for related financial statements, and excluded risks and opportunities not reasonably expected to affect financial prospects.

**Four core content areas:** Governance; Strategy; Risk Management; Metrics and Targets. The response explained oversight, business-model and financial effects, identification/monitoring processes, and performance/targets.

**Materiality:** The response defined information as material if omitting, misstating or obscuring it could reasonably influence primary users' decisions, and noted entity-specific qualitative and quantitative considerations.

**General disclosure principles:** Fair presentation; same reporting entity as financial statements; connected information; timing and location; explicit and unreserved compliance statement where all requirements are met.

The response concluded: “All requested topics are fully supported by IFRS S1.”

*Transcription note:* This section condenses the response's wording while preserving its substantive claims; the screenshot records the original on-screen answer. It should not be treated as a verbatim full transcript.

### Evidence and evaluation

- **Strength:** The response followed the requested structure and made a complex standard accessible for initial revision.
- **Citation check:** A materiality citation was clicked in NotebookLM. The opened IFRS S1 source passage matched the definition about omitting, misstating or obscuring information. This verifies that **particular claim**, not the whole summary.
- **Limitation:** The timing statement was expressed without explaining initial-application transition relief; summaries can omit exceptions. Academic users should consult the standard for precise compliance questions.
- **Evidence files (upload if saved):** `screenshots/Q4_E1_IFRS_S1_Summary.png`; `screenshots/Q4_E1_Citation_Verification.png`.

---

## E2 — Comparison of IFRS S1 and IFRS S2

**Feature:** Multi-source synthesis and comparison.  
**Selected sources:** IFRS S1 and IFRS S2.  
**Scenario:** A postgraduate student prepares a comparative ESG reporting briefing.

### Exact prompt

> Act as an academic research assistant helping a postgraduate business analytics student compare IFRS S1 and IFRS S2. Using only the two uploaded standards, create a comparison table covering: (1) purpose and scope, (2) sustainability-related versus climate-related risks and opportunities, (3) governance, (4) strategy, (5) risk management, (6) metrics and targets, and (7) materiality and disclosure requirements. For each area, explain the requirements under IFRS S1 and IFRS S2 and identify their similarities and differences. Include source citations from both documents for the main comparisons. Then provide three key insights explaining why the distinction matters for university students studying ESG reporting. Do not invent requirements or assume that IFRS S2 replaces IFRS S1. Clearly identify anything that cannot be verified from the uploaded sources. Keep the response approximately 500–600 words.

### Actual observed output — seven comparison areas

| Area | NotebookLM's reported distinction |
|---|---|
| Purpose and scope | IFRS S1 is the overarching sustainability disclosure framework; IFRS S2 addresses climate-related risks and opportunities. |
| Risks and opportunities | IFRS S1 covers sustainability-related risks and opportunities broadly; IFRS S2 addresses physical and transition climate risks and climate opportunities. |
| Governance | Both require governance disclosures; IFRS S2 concentrates on climate oversight and can avoid unnecessary duplication. |
| Strategy | Both address strategy and resilience; the output stated that IFRS S2 “mandates climate-related scenario analysis and transition plans.” |
| Risk management | Both cover identification, assessment, prioritisation, monitoring and integration into risk management. |
| Metrics and targets | IFRS S1 gives general principles; IFRS S2 includes detailed GHG, cross-industry and industry-based disclosures. |
| Materiality and disclosures | IFRS S1 establishes materiality and general reporting requirements; IFRS S2 applies those principles to climate-related matters. |

**Three generated insights:** (1) S2 builds on rather than replaces S1; (2) S2 increases quantitative analytics demands (GHG emissions, scenario analysis, financial-industry disclosures); (3) both use a primary-user, financially oriented materiality perspective. NotebookLM also stated that the sources could not establish jurisdiction-specific adoption or ASX compliance rates.

### Evidence and evaluation

- **Strength:** The table brought together two lengthy standards and helped distinguish general and topic-specific requirements.
- **Important overstatement:** The E2 strategy row implied that every entity must have a transition plan. IFRS S2 requires disclosure about **any climate-related transition plan the entity has**; this is not a universal requirement to create one. IFRS S2 does require climate-related scenario analysis for climate-resilience assessment, using an approach commensurate with circumstances.
- **Additional qualification:** The output discussed financed emissions without consistently limiting those requirements to relevant financial activities.
- **Source inspection:** The student subsequently located relevant transition-plan wording in IFRS S2. No separate citation-check screenshot was retained, so this inspection is recorded as a user-reported check rather than independently preserved screenshot evidence.
- **Evidence file (upload if saved):** `screenshots/Q4_E2_IFRS_Comparison.png` (or `_1.png` and `_2.png` if split).

---

## E3 — Source-grounded questions and unsupported-statistic test

**Feature:** Document-grounded Q&A and refusal to invent missing information.  
**Selected sources:** IFRS S1 and IFRS S2.  
**Scenario:** A student checks technical standards questions alongside an empirical question that the uploaded documents cannot answer.

### Exact prompt

> Act as an academic research assistant supporting a postgraduate student preparing an ESG reporting assignment. Using only the uploaded IFRS S1 and IFRS S2 documents, answer the following questions:
>
> 1. What are the four core content areas of sustainability-related financial disclosures?
> 2. What are the three categories of greenhouse gas emissions addressed by IFRS S2?
> 3. Does IFRS S2 require every organisation to create a climate transition plan, or does it require disclosure of relevant plans where they exist?
> 4. What percentage of Australian ASX 200 companies fully complied with IFRS S2 in 2025?
>
> For each answer, provide a concise explanation and source citations where available. Clearly distinguish requirements supported by the documents from information that cannot be established using the uploaded sources. Do not estimate, invent statistics, or use external information. Conclude with a brief statement identifying which questions could and could not be answered reliably.

### Actual observed answers

| Question | NotebookLM answer |
|---|---|
| 1. Four content areas | Governance, Strategy, Risk Management, Metrics and Targets, with short explanations. |
| 2. GHG emissions categories | Scope 1 (direct), Scope 2 (indirect purchased energy), Scope 3 (other indirect value-chain emissions). |
| 3. Transition plans | “IFRS S2 does not mandate that every organization create a new climate transition plan”; it requires information about “any climate-related transition plan the entity has.” |
| 4. ASX 200 2025 compliance percentage | “This information cannot be established using the uploaded sources.” The standards do not provide Australian company compliance statistics. |

NotebookLM's answerability summary identified Questions 1–3 as answerable from the standards and Question 4 as not answerable from the supplied documents.

### Evidence and evaluation

- **Strength:** It answered the three standards questions coherently and declined to fabricate a specific ASX 200 statistic.
- **Prompt sensitivity:** E3 accurately distinguished transition-plan disclosure from mandatory plan creation, whereas E2 had overstated the same issue. The quality of an answer can depend on question framing.
- **Limitation:** One successful refusal is not evidence that the system never hallucinates. The copied text did not preserve clickable citation markers, so citation accuracy was not exhaustively verified.
- **Evidence file (upload if saved):** `screenshots/Q4_E3_Source_Grounded_QA.png`.

---

## E4 — Interactive Learning Overview

**Feature:** Studio → Reports → Interactive → Learning Overview (customised).  
**Selected sources:** IFRS S1 and IFRS S2.  
**Language:** English.  
**Scenario:** Generate independent revision material for a postgraduate business analytics examination.

### Exact customisation instruction

> Create an interactive learning overview for a postgraduate Master of Business Analytics student preparing for an examination on sustainability reporting. Using only the uploaded IFRS S1 and IFRS S2 standards, explain the purpose and scope of each standard, the four core disclosure areas, materiality, Scope 1–3 greenhouse gas emissions, climate-related scenario analysis, and transition plan disclosures. Organise the material into clear revision sections, explain complex terminology in accessible academic language, and highlight important differences between the two standards. Include five key takeaways and three common misconceptions students should avoid. Provide source citations where supported and do not invent requirements or examples presented as facts. The learning overview should be suitable for independent university study.

### Actual observed output

**Generated title:** *Mastering Sustainability Reporting: An Academic Guide to IFRS S1 and IFRS S2*.

The interactive report contained **seven navigable sections**:

1. Introduction.
2. Purpose, Scope, and Structural Interplay: IFRS S1 vs. IFRS S2.
3. The Four Core Content Pillars.
4. Materiality, Connected Information, and Guidance Sources.
5. GHG Emissions Accounting: Scope 1, Scope 2, and Scope 3 Deep Dive.
6. Climate Resilience, Scenario Analysis, and Transition Plans.
7. Revision Summary, Key Takeaways, and Misconceptions.

It included a comparative table, conceptual diagrams, IFRS paragraph references, five exam takeaways, three misconceptions, and suggested studio content (e.g., flashcards, quiz, audio, mind map). Suggested items were **not** separately generated or evaluated in E4.

### Evidence and evaluation

- **Strength:** Clear, extensive study structure; helpful navigation and connections between accounting concepts and analytics tasks.
- **Limitation:** The report's broad claim that Scope 3 disclosures are mandatory did not sufficiently explain the **first-year transitional relief** in the original 2023 IFRS S2 text. This matters when students interpret requirements for initial application.
- **Further limitation:** The report was lengthy and some specialised financed-emissions explanations require careful attention to which entities/activities are covered. Generated learning content is not a substitute for the standards.
- **Evidence file:** `screenshots/Q4_E4_Interactive_Learning_Overview.png`.
- **Source output:** The generated report text was copied into the conversation for review; the screenshot captures the title, navigation and introduction.

---

## E5 — Scenario-based quiz generation

**Feature:** Studio → Quiz.  
**Selected sources:** IFRS S1 and IFRS S2.  
**Settings:** Standard number of questions; Hard difficulty; English.  
**Scenario:** Test postgraduate-level applied knowledge of sustainability disclosure standards.

### Exact customisation instruction

> Create a challenging postgraduate-level multiple-choice quiz for a Master of Business Analytics student studying IFRS S1 and IFRS S2. Use only the two uploaded standards. Test understanding and application of financial materiality, the four disclosure pillars, Scope 1–3 greenhouse gas emissions, climate-related scenario analysis, transition plan requirements, and the relationship between IFRS S1 and IFRS S2. Include realistic academic or business scenarios that require reasoning rather than simple memorisation. Provide plausible distractors, one clearly correct answer per question, and explanations grounded in the standards. Include questions about exceptions or transitional relief where relevant. Do not invent requirements or unsupported facts.

### Actual observed output

NotebookLM created a **10-question** quiz titled *Sustainability Quiz*. **Only Questions 1 and 2 were examined in this evaluation.**

**Question 1 — Scope 3 supplier-data uncertainty.** The scenario concerned estimating Scope 3 Category 1 emissions for a newly acquired overseas tier-two supplier when direct data could not be obtained. NotebookLM marked **B** correct:

> “The standard presumes that Scope 3 emissions can be estimated reliably using secondary data and industry averages without omitting the metric.”

It explained that IFRS S2 contains a presumption that Scope 3 emissions can be reliably estimated using secondary data and industry averages when direct primary data is unavailable. It also explained why a blanket commercial-sensitivity exemption or missing verified supplier data would not automatically justify omission.

**Question 2 — Applicability under non-IFRS GAAP.** The scenario concerned a private corporation preparing financial statements under local non-IFRS GAAP. NotebookLM marked **C** correct:

> “The corporation may apply IFRS Sustainability Disclosure Standards irrespective of whether its financial statements comply with IFRS Accounting Standards or other GAAP.”

This is consistent with IFRS S1 paragraph 8.

### Evidence and evaluation

- **Strength:** Both inspected questions used realistic business situations and had clearly identifiable intended answers. The system provided immediate feedback; Question 2's result was consistent with IFRS S1.
- **Qualification on Question 1:** The correct-option explanation is directionally consistent with IFRS S2's use of reasonable, supportable estimation inputs, but its wording may encourage overconfidence about the reliability of estimates. Actual data quality and uncertainty still matter.
- **Coverage limit:** The other eight questions, their answer keys and feedback were **not checked**. No claim is made that the entire quiz was accurate.
- **Evidence file:** `screenshots/Q4_E5_Quiz_Answer_Explanation.png`.

---

## Overall critical evaluation

**Academic usefulness:** NotebookLM supported five realistic stages of an ESG research workflow: initial comprehension, cross-standard comparison, targeted fact checking, revision-material generation and self-assessment. Its strongest value was converting two long technical source documents into navigable explanations and practice material.

**Source-grounding and accuracy:** One E1 materiality citation was checked against its source passage. E3 correctly declined an unsupported external statistic. However, E2's transition-plan wording was overbroad, and E4 omitted an important first-year transition qualification. E5's first answer illustrated how plausible feedback can still simplify measurement uncertainty. Therefore, citation markers and polished prose should not be treated as proof of complete accuracy.

**Bias, hallucination and overreliance:** The selected experiments did not reveal a fabricated ASX statistic, but they did reveal oversimplification and inconsistency across prompts. Source selection can constrain responses, but users must still check whether citations support specific claims, whether exceptions apply and whether generated learning material accurately represents the source. The small, non-random test set and partial quiz inspection limit generalisation.

**Practical adoption recommendation:** Use NotebookLM as an **assisted research and revision tool**, not as the final authority for regulatory interpretation or academic citation. Students should upload authoritative documents, ask bounded questions, verify critical passages directly, check transition provisions and technical exceptions, and cite the original IFRS documents in assessed writing. Lecturers could use generated guides or quizzes as drafts, subject to subject-matter review.

## Screenshot index

Store only actual saved screenshots in `screenshots/`. The names below are planned evidence filenames, not a claim that every file has already been uploaded.

| Experiment | Evidence filename | Demonstrates |
|---|---|---|
| E1 | `Q4_E1_IFRS_S1_Summary.png` | Summarisation output |
| E1 | `Q4_E1_Citation_Verification.png` | Materiality source passage opened |
| E2 | `Q4_E2_IFRS_Comparison.png` | Multi-source comparison output (or numbered parts) |
| E3 | `Q4_E3_Source_Grounded_QA.png` | Refusal to invent unsupported ASX statistic |
| E4 | `Q4_E4_Interactive_Learning_Overview.png` | Seven-section interactive report |
| E5 | `Q4_E5_Quiz_Answer_Explanation.png` | Question 1, selected answer and feedback |

## Limitations of this evaluation

- Five purposively selected experiments in one notebook are not a benchmark of overall system performance.
- Only one E1 source citation was visually verified; E2 source inspection was not preserved as separate evidence.
- The full E4 report was reviewed as text, but not all of its technical assertions were independently checked against both PDFs.
- E5 generated ten questions, but only the first two were examined.
- No independent human grading or quantitative accuracy metric was applied.

## Primary sources

IFRS Foundation. (2023). *IFRS S1: General requirements for disclosure of sustainability-related financial information*. International Sustainability Standards Board.

IFRS Foundation. (2023). *IFRS S2: Climate-related disclosures*. International Sustainability Standards Board.
