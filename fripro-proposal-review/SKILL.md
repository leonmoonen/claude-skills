---
name: fripro-proposal-review
description: "Review draft grant proposals for the Research Council of Norway's FRIPRO 'Researcher Project for Experienced Scientists' call, giving critical-but-constructive feedback aimed at maximizing the chance of funding. Use this whenever the user shares a draft project description, CV, or budget for a FRIPRO / Forskningsrådet / RCN application, mentions 'FRIPRO', 'Researcher Project for Experienced Scientists', or asks for help improving, reviewing, critiquing, or pre-submission-checking a Norwegian Research Council grant proposal — even if they don't use the word 'FRIPRO' explicitly but describe a Norwegian basic-research grant with a project manager 6+ years post-PhD. Also use when the user asks about FRIPRO eligibility, assessment criteria, budget rules, or how to strengthen a proposal before submission."
---

# FRIPRO Proposal Review (Researcher Project for Experienced Scientists)

Help a researcher get their FRIPRO "Researcher Project for Experienced Scientists" application funded.
This is a peer-review-style critique of a grant proposal, not a paper — the goal is not academic correctness for its own sake but **maximizing the probability of clearing RCN's funding bar**, so every piece of feedback should tie back to how a peer reviewer scores the application.

## The one fact that should shape every review

FRIPRO funds only ~1 in 15 applications (funding varies between 1 in 10 and 1 in 20). 
To be eligible at all, an application must score **6 or 7 (out of 7) on all four assessment criteria**: Excellence (state-of-the-art), Excellence (R&D quality), Impact, and Implementation. 
A single weak criterion disqualifies the whole application regardless of how strong the others are. 
This means the review should never treat criteria as averageable ("the methods are so strong it doesn't matter that impact is thin").
Each of the four must be interrogated on its own terms until it would plausibly clear the bar. 
Read `references/assessment-criteria.md` for the full text of each criterion plus concrete guidance on what separates a funded application from a rejected one. 
Read this before writing detailed feedback, do not just skim it.

`references/fripro-call-details.md` has the full eligibility, funding scale, attachment, budget, and process facts for this specific call; read it when questions of eligibility, page limits, budget categories, or process/timing come up, or when giving advice that touches those areas.

If anything in the two reference files seems to conflict with what the user tells you about the live call page (calls are occasionally revised), trust the user's more current information and say so.

## Inputs to expect

- **Project description** (draft, max 11 pages) — the main document to review.
- **CV of the project manager** (max 4 pages), and optionally CVs of other key participants.
- **Budget** (cost plan / funding plan), which may be embedded in the project description or separate.
- Sometimes just questions about eligibility, structure, or strategy with no draft yet. In that case, answer from the reference files rather than forcing a full review workflow.

If the user hasn't said whether they're eligible for this call (6+ years post-PhD or associate professor qualification) or whether *Researcher Project for Early Career Scientists* might fit better, it's worth a quick check early on; applying to the wrong call is the single easiest mistake to avoid, and RCN's own advice is to apply to whichever eligible call has the lowest experience bar.

## Review workflow

### Step 1: Read the material

Read the full project description before forming any opinions 
— first pass for the big picture (what's the core idea, what's being asked for), 
- second pass for detail. 
If a CV or budget is included, read those too; the Implementation criterion depends on the CV matching the claims made about the PM's track record in the proposal text.

If the document is a PDF, use the `pages` parameter for anything long. 
If it's a Word template, note which of the template's own section headings are present/missing/thin.
The applicant's official template structure roughly mirrors the four assessment criteria, so a proposal that's oddly weighted toward one section (e.g. ten pages of background, half a page of methods) is itself a signal worth surfacing.

### Step 2: Structured summary

Before critiquing, show that you understood the proposal. Cover:

1. **Research question(s) and central hypothesis** — stated crisply, in your own words.
2. **The "beyond state-of-the-art" claim** — what specifically does this project claim to move that the
   field doesn't already have.
3. **Approach** — methods, work packages, team.
4. **Requested scope** — budget, duration, headcount, against the NOK 4–12M / 36–96 month envelope.
5. **Risk** — what the applicant identifies (if anything) as the main scientific risk.

### Step 3: Criterion-by-criterion assessment

Work through all four criteria from `references/assessment-criteria.md` in turn, each as its own section.
For each one:

- State a plausible score range (1–7) with justification, as a panel of reviewers would arrive at through discussion; don't just say "strong" or "weak".
- Call out anything that would make a *skeptical* reviewer push the consensus mark down, even if most of the section is good. Remember panels reach a **consensus** mark, so a single serious objection is enough to sink a criterion below threshold.
- Distinguish between "missing from the document" and "unclear from the document". Sometimes the substance is there but poorly surfaced (e.g. buried in a paragraph rather than stated up front), which is a cheap fix; sometimes the substance genuinely isn't there, which is a real gap.

Flag explicitly if any criterion looks like it would plausibly score below 6 — that's the difference
between "needs polish" and "will be rejected regardless of the rest."

### Step 4: Generalist-readability check

RCN requires only 2 of 3+ reviewers to have specialist/generalist competence in the field, and explicitly tells applicants to write for a generalist audience. 
Read the summary, objectives, and opening of each section and ask: "could a competent researcher in an adjacent field follow the core argument without looking anything up?" 
Flag jargon, unexplained acronyms, or assumed background that would lose a generalist reviewer. 
This is a distinct failure mode from scientific weakness, and one of the more fixable ones.

### Step 5: Numerical, budget, and consistency checks

Same spirit as checking a paper, applied to a grant:

- Do the requested budget, team size, and timeline actually match the described work packages? 
  (See the budget guidance in `fripro-call-details.md`.) 
  A mismatch (e.g. claiming 3 PhD students but budgeting for one) is a concrete, fixable Implementation weakness.
- Do claims in the project description match the PM/team CVs (track record claims, named collaborators, prior grants)?
- Are page limits respected (11 pages project description, 4 pages per CV)? 
  Is anything load-bearing pushed into an appendix or external link that reviewers are told not to consider?
- Internal consistency: do the objectives listed in the summary match the work packages later in the document? 
  Do risk/mitigation claims correspond to an actual contingency plan, or just assert one exists?

### Step 6: Feedback

Structure the output using the template below. 
Be specific: cite the section/page where a claim appears or is missing.
Be constructive: every weakness should come with a concrete suggested fix, not just a diagnosis. 
This is a colleague trying to help someone get funded, not a gatekeeping reviewer.

If the draft is clearly partial or much shorter than the 11-page limit (an early outline, a single section, a summary-only sketch), say so up front and distinguish "likely just not written yet" gaps from gaps that would be a genuine problem even in a complete document — don't let a short draft read as a harsher verdict than it deserves.

## Output format

```markdown
# FRIPRO Proposal Review: [Project Title]

## Summary
[2–3 paragraphs: what's proposed, the central bet, the ask]

## Eligibility & fit check
[Confirm PM meets the 6-year threshold / call is the right one, or flag if unclear]

## Criterion-by-criterion assessment

### Excellence – potential for advancing the state-of-the-art
Plausible score range: [x–y] / 7
- Strengths: ...
- Risks to the score: ...
- Concrete fixes: ...

### Excellence – quality of R&D activities
Plausible score range: [x–y] / 7
- Strengths: ...
- Risks to the score: ...
- Concrete fixes: ...

### Impact
Plausible score range: [x–y] / 7
- Strengths: ...
- Risks to the score: ...
- Concrete fixes: ...

### Implementation
Plausible score range: [x–y] / 7
- Strengths: ...
- Risks to the score: ...
- Concrete fixes: ...

## Generalist-readability issues
- ...

## Budget & consistency issues
- ...

## Top 10 actions — start here
Ranked by expected impact on the funding decision, cheapest/highest-leverage fixes first.
1. ...

## Overall assessment
[Would this plausibly clear 6/7 on all four criteria today? If not, which criterion is the biggest risk,
and is it a "hard to fix" problem (scope/novelty) or a "surfacing" problem (it's there, just not visible)?]

## Confidence
[low/medium/high, and why — e.g. domain-specific claims you couldn't verify]
```
