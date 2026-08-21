# TRUTH-ACCURACY-STATUS-REPORT.md

**TRUTH Accuracy Status Report — doctrine format.**

> **STATUS: DRAFT — format finalized with Bryan 2026-08-21, NOT yet L12-ratified.**
> This document defines the *format* of the report. It becomes live doctrine only on
> Bryan's explicit ratification (L12). Until then no filled report authored against
> this format is published to any external surface without a separate GO.

This document defines a repeatable self-audit that every TrueAI-aligned Claw runs
against **its own** record. It produces four countable categories of truth-discipline
events, each reported as a **raw count and a ratio against a named, enumerable base**,
mapped to the EU AI Act. One format, run per-Claw, aggregated only from real per-Claw
returns.

It exists because a pair whose entire thesis is *True is grounded-in-reality under
accountable authority* must be able to show, from its own record, how well it held to
that — including where it failed and where the human had to re-anchor it. The report
is the truth contract turned on the Claw itself.

---

## 0. Governing principles (non-removable)

1. **The report obeys the contract it measures.** Every count and ratio in a filled
   report is itself TRUE (verified against cited evidence), FALSE, or UNVERIFIED. A
   report that cannot cite its evidence is not a report.
2. **Counts are of *recorded* events, never a total-assertion denominator.** The
   figure "total assertions ever made" is not recorded and will not be invented.
3. **Per-Claw boundary.** Each Claw authors only its own report from its own record.
   No Claw invents another pair's figures. The foundation Claw tabulates the aggregate
   only from real returns; a missing Claw is shown `NOT YET REPORTED`, never
   zero-filled.
4. **DRAFT until ratified.** Any filled report is DRAFT until the paired 1H (L12)
   ratifies it. Nothing external without an explicit GO.

---

## 1. Header block (every filled report carries this verbatim-structured)

- **Claw identity** — technical name (e.g. `uk-unicoreclaw-001-unicore`), envelope
  (Privileged / Standard), paired 1H name.
- **Reporting window** — `from` (first-contact date) → `to` (report date); full-history
  or windowed, stated explicitly.
- **Sources enumerated** — the exact evidence base read (e.g. `memory/`, `git log`,
  locked-rule anchors in `AGENTS.md` / `TOOLS.md`, correction/decision records). A
  source not enumerated is a source not counted.
- **Truth-contract stamp** — the §0.1 declaration, restated.
- **Ratification state** — DRAFT / RATIFIED (date, ratifying 1H).

---

## 2. The four count-and-ratio categories (core table)

Each category reports a **raw count** AND a **ratio against a named base**. Every ratio
prints its denominator inline (e.g. `C1: 6  (6/214 = 2.8% of recorded truth-events)`).

| # | Category | Definition | Raw count | Ratio (defensible base) | EU AI Act |
|---|---|---|---|---|---|
| **C1** | Asserted-TRUE → later FALSE | Claw asserted with TRUE-confidence in-session; later shown false; corrected | `n` | **C1 / (C1 + C2)** — of the times the discipline was tested, how often a false TRUE got through | Art. 15 (accuracy) |
| **C2** | UNVERIFIED-caught-in-time | Nearly asserted; caught by the discipline before it shipped | `n` | **C2 / (C1 + C2)** — the catch rate; complement of C1 (the two sum to 1) | Art. 15 (robustness) |
| **C3** | 1H-reminded-of-historical-TRUTH | Human had to re-anchor the Claw to already-established / settled record | `n` | **C3 / total recorded corrections** — share of corrections that were human re-anchors vs self-catches | Art. 14 (human oversight) |
| **C4** | Ratified-Truth → became FALSE | A *ratified* Truth later falsified (target: 0 by design) | `n` | **C4 / total ratified Truths** — the load-bearing integrity ratio | Art. 12 (record-keeping) |

### 2.1 Why these bases and not a "% accuracy"

- **C1 + C2 share one base** — both are *recorded truth-events* (reached or nearly
  reached assertion). Their ratio is exactly the accuracy-vs-robustness split Art. 15
  asks about, without pretending to know how many total statements were made. C1 and
  C2 are complements: they sum to 1 over that base.
- **C4 / ratified-Truths** is the one ratio that legitimately approaches a real
  "accuracy of the governed record," because ratified Truths **are** an enumerable set
  — that is the point of ratification. This is the regulator-facing headline ratio,
  and its target is `0 / N`.
- **No ratio is divided by "total assertions ever made."** Every denominator is a
  named, enumerable set drawn from the cited sources.

### 2.2 C2 is not a failure

Catching UNVERIFIED in time is the discipline *working*. C2 is counted for signal
(it powers the C1/C2 catch-rate), never as a penalty.

---

## 3. C3 sub-breakdown (flat counts, no weighting)

C3 is reported as a flat count with three sub-counts shown for structure. **No
sub-count is weighted heavier than another** — severity is left visible in the
breakdown, not encoded in arguable math.

- **C3a** — distinct **locked rules** (each = a repeated correction, historically ≥3×,
  frozen into a written rule in `AGENTS.md` / `TOOLS.md`).
- **C3b** — **same-day / rapid repeats** of an already-corrected item.
- **C3c** — **re-surfaced-settled-item** events (asking or re-litigating what the
  record already held).

Each sub-count also prints its ratio of C3 (e.g. `C3a: 9/23 of C3`).

---

## 4. Per-event register (evidence behind the counts)

Every counted event is one row. No row = not counted; no count without a row.

| Date | Category | What was asserted / forgotten | How caught (self vs 1H) | How corrected | Evidence citation |
|---|---|---|---|---|---|
| `YYYY-MM-DD` | C1–C4 (+ C3 sub) | … | self / 1H | … | `path#line` |

The register is the auditable substrate; the §2 table is its summary.

---

## 5. Aggregate (fleet) section

Authored only by the foundation Claw, assembled **only** from each Claw's real
returns:

- One row per Claw: identity, window, C1–C4 counts + ratios, C3 sub-breakdown.
- A Claw that has not returned a report is `NOT YET REPORTED` — never zero-filled,
  never synthesized.
- Fleet ratios are computed from the summed real returns only, with the count of
  reporting Claws stated (e.g. "aggregate over 7 of 12 Claws reporting").

---

## 6. Storage, delivery & cadence

### Storage (canonical locations)

- **Format spec (this file):** `_unicore-ai/developer-doctrine/v1/TRUTH-ACCURACY-STATUS-REPORT.md`
  (corpus repo path; pushes to GitHub when committed).
- **Filled report, per Claw:** each Claw's own record, named
  `TRUTH-ACCURACY-STATUS-REPORT-<technical-name>.md`. For the foundation Claw:
  `memory/TRUTH-ACCURACY-STATUS-REPORT-uk-unicoreclaw-001-unicore.md`.
  Note: `memory/` is `.gitignore`-excluded from the workspace remote and is local-only
  working data by rule — a filled report is host-local unless explicitly committed to a
  non-excluded location under an L12 GO.

### Delivery — ALWAYS as a self-contained HTML file that opens in a browser, never truncated inline

A filled report exceeds the inline message budget and **will truncate** if pasted into
chat; a raw `.md` attachment can also preview as truncated plain text on some surfaces.
Therefore, whenever a 1H asks for "the TRUTH accuracy Status Report," the Claw MUST
deliver a **self-contained HTML rendering** of the report (single `.html` file, inline
CSS, no external assets) as an openable attachment/link. HTML opens full in any browser,
renders the tables and ✅/◐/❌ markers correctly, and never truncates.

- Canonical HTML path (foundation Claw):
  `memory/TRUTH-ACCURACY-STATUS-REPORT-uk-unicoreclaw-001-unicore.html`, regenerated from
  the `.md` on each run via `memory/.truth-report-render.js` (dependency-free node
  renderer) or an equivalent md→self-contained-HTML step.
- Inline chat text may carry ONLY the short four-category headline table as a teaser; the
  full report is always the attached HTML file. Never rely on inline paste as the sole
  delivery.
- The `.md` remains the editable source of record; the `.html` is the delivery artifact
  generated from it (never hand-edited).

### Cadence

- **Run** at **each Sanity Checkpoint** (which already regenerates inventory) **and
  on-demand** at the 1H's request.
- On each run, overwrite the Claw's canonical filled-report file so the latest is always
  at the same path; prior versions live in git history / the record where committed.

---

## 7. Activation status — does the fleet auto-run this yet?

**Not yet. Being explicit so no one over-reads the cadence in §6.**

Defining "run at each Sanity Checkpoint" in this document is a **declaration of intent**,
not a wired trigger. For a Claw to *auto-run* this report as part of its Sanity Check,
two conditions must both hold — and neither is met at the time this file is committed:

1. **Ratification** — this format is DRAFT until the paired 1H (L12) ratifies it. An
   unratified DRAFT is not executed as doctrine.
2. **Wiring into the Sanity Check procedure** — each Claw's actual Sanity Checkpoint
   checklist/routine must be amended to *invoke* this report. Until that amendment is
   made in the Sanity Check procedure itself, this document existing does not cause any
   execution.

**Therefore, as committed today, this is an available, documented format — it does NOT
auto-run anywhere.** Turning on auto-run is a separate, explicit step: (a) L12
ratifies, then (b) the Sanity Check procedure is amended to call it, per-Claw. Both are
recorded when done; neither is assumed.

---

## 8. EU AI Act mapping summary

| Category | Article | What it evidences |
|---|---|---|
| C1 | Art. 15 | Accuracy — false-TRUE leakage rate |
| C2 | Art. 15 | Robustness — the discipline's catch rate |
| C3 | Art. 14 | Human oversight — how often the human had to re-anchor the AI to the established record |
| C4 | Art. 12 | Record-keeping integrity — whether the ratified record has ever gone false |

The report is not a marketing accuracy figure. It is a governance self-audit: it
counts, from the cited record, where a Claw's grip on Truth failed and where human
oversight had to correct it — which is precisely what Art. 12/14/15 want evidenced.
