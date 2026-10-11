# US-GAAP-Prompt-Library-for-LLM-Evaluation




US GAAP Prompt Library for LLM Evaluation
A prompt bank for training and evaluating large language models on US GAAP accounting: standalone companies, parent and subsidiary, and full consolidation. Each prompt has a checkpoint of what a correct answer must show and the common trap models fall into.

Keywords: US GAAP, FASB ASC, ASC 606, ASC 842, ASC 326 CECL, ASC 740, ASC 805, ASC 810 consolidation, non-controlling interest, intercompany eliminations, LLM evaluation, prompt engineering, RLHF, data annotation, accounting AI, red-teaming, reference answers.
Contents
File
What it covers
01-standalone-company.md
Part A: prompts for a single company across ASC 100 to 900 (general, assets, liabilities, equity, revenue, expenses, broad transactions, industry)
02-parent-subsidiary.md
Part B: control, intercompany transactions, ownership changes, deconsolidation, step acquisitions
03-consolidation.md
Part C: consolidation workflow, VIE, goodwill, NCI, translation, deferred taxes, EPS, cash flow
04-master-case-and-rubric.md
Part D: multi-step master case with answer key; Part E: scoring rubric and prompt-writing guide
prompts.jsonl
Every table row as JSON Lines for datasets and eval harnesses
scripts/build_jsonl.py
Rebuilds prompts.jsonl from the Markdown tables

JSONL format
{"id": "A2-17", "source_file": "01-standalone-company.md", "asc": "606", "prompt": "...", "correct_answer_must_show": "...", "common_trap": "..."}

Rebuild after editing any table:

python scripts/build_jsonl.py
How to use
Give the model the prompt unchanged and ask it to "show journal entries, calculations and the ASC reference."
Compare to correct_answer_must_show and record the trap if one appears.
Score with the rubric in 04-master-case-and-rubric.md; grade reasoning separately from the final number.
Change one fact in the prompt and check that the answer changes correctly.
Important notes
All numbers are illustrative. Verify every answer key against the current FASB Codification and recent ASUs (for example ASU 2023-07, ASU 2023-09, and any amendments to ASC 350-40) before using it as a gold answer.
Tax-law items change; mark them "verify current law" in reference answers.
This is educational material, not accounting, tax or legal advice.
Contributing
Pull requests are welcome: add prompts, fix answer keys with an ASC citation, or add new traps. Keep one row per prompt and keep the five-column table format so the script can parse it.
License
MIT, see LICENSE.

