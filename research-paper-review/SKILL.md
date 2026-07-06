---
name: research-paper-review
description: "Review and analyze academic research papers. Use this skill when the user asks to review a paper, analyze a publication, summarize research, critique methodology, extract key findings, compare papers, check for numerical inconsistencies, or assess novelty and contributions of academic work. Also triggers when the user mentions reading a PDF of a paper, wants a literature review, asks about related work, or wants to improve a paper before submission."
---
 
# Research Paper Review
 
Assist researchers in reviewing, analyzing, and critiquing academic papers systematically and thoroughly.
 
## When to Use
 
- User asks to review, summarize, or critique a research paper
- User shares a PDF or link to an academic paper
- User wants to assess methodology, contributions, or novelty
- User needs help writing a peer review
- User wants to compare multiple papers or do a literature survey
- User wants to improve a paper before submission (pre-submission review)
- User wants to check for numerical/statistical inconsistencies
- User wants venue-specific feedback (conference, journal, or preprint)

## Inputs
 
- Paper content: PDF, LaTeX source, or plain text
- Target venue (optional but recommended): conference, journal, or preprint target
               - Example: "Models 2026", "TOSEM", "Sosym", "arXiv preprint"
- Type of paper (optional but recommended): "full research" paper, "short" paper, "new ideas" paper, "tool demo", "poster",...
- Explicit reviewing guidelines (optional): if available, provide a description or URL with the reviewing criteria.

## A note on your knowledge cutoff
 
Research moves faster than your training data, especially in fast-moving fields. A paper you're reviewing may cite work, use terminology, or build on techniques that postdate your training cutoff — that doesn't make them wrong or fabricated. Throughout this workflow, when you're tempted to flag a citation as suspicious or call something novel (or not novel) based on what you personally recognize, search first. Treat "I don't recognize this" as "I need to check," not as evidence of an error. Reserve findings like "this citation appears to not exist" for cases where you've actually searched and come up empty.
 
## Review Workflow
 
### Step 0: Pre-Processing, Venue Context, and Review Mode
 
- Determine the review mode, since it changes how you frame feedback and what the final verdict looks like:
  - **Formal peer review** — the user is an assigned reviewer (or is asking you to act as one). Output should read like a review, ending in an accept/revise/reject-style verdict.
  - **Pre-submission coaching** — the user is an author preparing to submit. They don't need a verdict on whether to accept their own paper; they need a prioritized punch list and an honest readiness assessment. Infer this from phrasing like "help me improve this before I submit" vs. "I need to review this for [venue]," and ask if it's genuinely ambiguous.
- If target venue and/or type of paper are provided, include them as context for all subsequent steps:
> "Review this paper as if it is intended for [TARGET VENUE] as a [TYPE PAPER] submission. Consider typical standards, expectations, page limits, scope, and audience for this venue and type of paper."
 
- Optional: look up the venue's reviewing guidelines on its website — standards for methodology, novelty, rigor, and formatting vary by venue and change from year to year, so don't rely purely on memory here either.

### Step 1: Read the Paper
 
Identify the format and read accordingly:
 
- **PDF**: Use the Read tool with the `pages` parameter for large documents (max 20 pages per request). PDF pages are rendered as images, so actually look at the figures, plots, and tables as they appear rather than only reading captions — this is how you catch mislabeled axes, illegible legends, low-contrast color choices, or a figure that doesn't quite match what the text claims about it.
- **LaTeX source**: Read the main `.tex` file first. Look for `\input{}` or `\include{}` commands to find additional sections, figures, and bibliography files. Use Grep to search for key commands like `\begin{abstract}`, `\section`, `\cite` across all `.tex` files.
- **Multiple files**: Use Glob with `**/*.tex` to find all source files, then read them in logical order (main file → sections → appendix).
- **Multiple papers** (comparison or literature survey): read and complete Steps 1-4 for each paper individually before moving to the synthesis in Step 4b.
In all cases, skim the abstract, introduction, and conclusion first to get the big picture before diving into details.
 
### Step 2: Structured Summary
 
Show that you understand the paper by producing a summary covering:
 
1. **Problem Statement** — What problem does the paper address? Why does it matter?
2. **Contributions** — What are the claimed contributions? (list them)
3. **Approach/Methodology** — How do the authors solve the problem?
4. **Key Results** — What are the main findings/metrics?
5. **Limitations** — What are the acknowledged (and unacknowledged) limitations?

### Step 3: Numerical & Consistency Checks
 
This is where LLM-assisted review adds the most value, catching things humans easily miss during manual review. Run these checks systematically:
 
- **Numbers across text, tables, and figures**: Do values reported in the text match what's in the tables? Do figures reflect the data described?
- **Statistical consistency**: Do p-values, confidence intervals, and effect sizes align? Are sample sizes consistent throughout?
- **Calculations**: Verify percentages, averages, sums. Check that reported improvements (e.g., "30% improvement") match the actual numbers. For anything involving multiple steps of arithmetic across tables, consider having a subagent redo the calculation independently from the raw numbers rather than just re-checking your own work — a second pass that isn't anchored on the answer it expects to find catches more.
- **Internal references**: Do all `\ref`, `\cite`, figure/table references resolve? Are there dangling references or wrong numbering?
- **Acronyms**: Are all acronyms defined on first use?
- **Terminology consistency**: Is the same concept always referred to with the same term?
- **Citations**: Is the citation style uniform (e.g., all conference papers cited with the same fields)? Before flagging any citation as suspicious or non-existent, search for it by title/authors/venue or arXiv ID — see the note on knowledge cutoffs above. Only report a citation as an issue once a search actually fails to turn it up.
- **Prior publication**: Search for the paper's title and key phrasing to check whether it (or a close variant) has already appeared elsewhere — as a workshop paper, preprint, or under a different title. Overlapping or duplicate submission is a common venue policy violation and easy to miss without checking.
Even minor errors (typos, broken references, wrong numbering) matter — reviewers often use them as signals that the paper wasn't carefully prepared.
 
### Step 4: Critical Analysis
 
Take real time to reason through this step rather than rushing to a verdict — novelty and soundness judgments are exactly where shallow analysis shows, and they're the parts of a review authors and readers scrutinize most.
 
Evaluate the paper on these dimensions:
 
| Dimension | Questions to Answer |
|-----------|-------------------|
| **Novelty** | Is this genuinely new? How does it differ from prior work? Search for closely related recent work before concluding either way — fast-moving fields routinely outpace your training data, and "I haven't seen this before" is not the same as "this is novel." |
| **Soundness** | Is the methodology rigorous? Are experiments well-designed? |
| **Significance** | Does this advance the field meaningfully? |
| **Clarity** | Is the paper well-written and well-structured? |
| **Reproducibility** | Could someone replicate this work from the paper alone? Is there a code/data availability statement, and if a repository is linked, does it look like it actually contains what's described? |
| **Related Work** | Is the positioning against prior work fair and complete? |
| **Venue Alignment** | Does the paper meet expectations of the target venue (scope, depth, format, length, contribution type)? |
 
### Step 4b: Comparing Multiple Papers
 
If the user provided two or more papers to compare or survey, add this after completing Steps 1-4 for each paper individually:
 
- A synthesis table comparing them across the same dimensions (novelty, methodology, results, limitations), one row per paper.
- A discussion of how the papers relate to each other: do they compete, build on one another, contradict each other's findings, or address non-overlapping aspects of the same problem?
- For a literature survey, group papers thematically rather than just listing them in the order they were provided.

### Step 5: Provide Actionable Feedback
 
Structure feedback as:
 
- **Strengths** — What the paper does well (be specific, cite sections)
- **Weaknesses** — What could be improved (be constructive, suggest fixes)
- **Questions for Authors** — Things that need clarification
- **Minor Issues** — Typos, formatting, citation issues, broken references
- **Venue-Specific Recommendations** — Highlight alignment issues, potential improvements to meet venue expectations

### Step 6: Prioritized Action List
 
Write down the top 10 most immediate actions the author should take.
 
These should be the ones with the best "bang for the buck" — actions that generate the most benefit relative to the cost of implementing them.
 
## Output Format
 
Use this template for the review. The final section changes depending on the review mode from Step 0: a **formal peer review** ends in an accept/revise/reject verdict; **pre-submission coaching** ends in a readiness assessment instead, since the user is the author, not a gatekeeper deciding on their own paper.
 
```markdown
# Paper Review: [Title]
 
## Summary
[2-3 paragraph summary]
 
## Strengths
- S1: ...
- S2: ...
 
## Weaknesses
- W1: ...
- W2: ...
 
## Questions for Authors
- Q1: ...
 
## Minor Issues
- ...
 
## Venue-Specific Recommendations
- V1: ...
- V2: ...
 
## Overall Assessment
[Formal peer review: 1 paragraph verdict — accept/revise/reject with justification]
[Pre-submission coaching: 1 paragraph readiness assessment — what's the biggest gap between this draft and being submission-ready]
 
## Top Actions
- T1: ...
- T2: ...
 
## Confidence
[Your confidence level in this review: low/medium/high, and why]
```