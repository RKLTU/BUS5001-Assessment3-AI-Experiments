# Q4 : Google NotebookLM Academic Evaluation

**Course:** BUS5001 — Cloud Platforms and Analytics  
**Assessment:** Assessment 3, Question 4  
**Student ID:** 22738404  
**Platform:** Google NotebookLM  
**Notebook:** `22738404_BUS5001_Q4_ESG_Research_Evaluation`

## 1. Research objective

This project evaluates Google NotebookLM as an AI-assisted academic research and study tool. The scenario involves a postgraduate business analytics student studying sustainability reporting requirements under IFRS S1 and IFRS S2.

The evaluation examines whether NotebookLM can summarise complex standards, compare documents, answer source-based questions, recognise unsupported information, create revision materials and generate assessment questions.

## 2. Sources and methodology

Two official IFRS Foundation standards, published in June 2023, were uploaded to NotebookLM:

1. **IFRS S1:** General Requirements for Disclosure of Sustainability-related Financial Information.
2. **IFRS S2:** Climate-related Disclosures.

Five experiments were conducted using the uploaded documents. E1 used IFRS S1 only; E2–E5 used both standards.

The evaluation considers relevance, factual accuracy, source grounding, academic usefulness, limitations and risks of overreliance. Observed outputs are distinguished from critical analysis. The tests provide examples of performance, not a comprehensive accuracy benchmark.

## 3. Experiments

| ID | NotebookLM functionality | Academic scenario | Main observation |
|---|---|---|---|
| E1 | Source-grounded summarisation | Revise IFRS S1 | Structured summary; one materiality citation inspected |
| E2 | Cross-document comparison | Compare IFRS S1 and IFRS S2 | Useful comparison with an overstatement about transition plans |
| E3 | Source-grounded question answering | Research ESG requirements | Answered three standards questions and declined to invent an ASX 200 compliance statistic |
| E4 | Interactive Learning Overview | Prepare postgraduate revision material | Generated a seven-section learning resource |
| E5 | Quiz generation | Test understanding of IFRS standards | Generated ten questions; the first two were examined |

**[Read the full experiment log](experiment-log.md)** for exact prompts, observed responses, evaluations and screenshot references.

## 4. Key findings

NotebookLM was useful for organising complex academic sources into summaries, comparisons, revision material and scenario-based questions.

Its source-focused approach was particularly valuable in E3, where it recognised that the uploaded standards could not establish a requested ASX 200 compliance percentage.

However, the experiments also identified limitations. E2 overstated the transition-plan requirement, while E5 illustrated how quiz explanations may simplify technical measurement issues. E4 also required caution about omitted transitional reliefs.

These findings demonstrate that readable, confident AI-generated content should not automatically be treated as a complete or authoritative interpretation of technical standards.

## 5. Academic implications and limitations

NotebookLM can support initial reading, concept clarification, revision and formative self-assessment. Students should verify important claims against original documents, particularly exceptions, measurement requirements and reporting obligations.

This evaluation used only two standards and five feature experiments. Only selected citations and two of the ten quiz questions were examined. Consequently, the results should not be generalised into an overall accuracy rate or a claim that the platform is free from hallucinations.

## 6. Evidence

Selected screenshots are stored in the `screenshots/` folder when uploaded. They illustrate generated outputs and selected checks; they do not independently verify every claim.

See the [experiment log](experiment-log.md) for experiment-level documentation.

## 7. Source references

IFRS Foundation. (2023). *IFRS S1 General Requirements for Disclosure of Sustainability-related Financial Information*.

IFRS Foundation. (2023). *IFRS S2 Climate-related Disclosures*.

