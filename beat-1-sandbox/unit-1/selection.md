# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

\---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56

**Verdict output**

Live-mode run of my installed `issue-select` skill on three Path Review candidates (#56, #68, #60). The verdict for #56 is the first entry in the JSON block and records `accept`.

```
 issue-select: grade these candidate first issues:
  https://github.com/codepath/pathreview-ai301-fa26-s3/issues/68
  https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56
  https://github.com/codepath/pathreview-ai301-fa26-s3/issues/60

● Skill(issue-select)
  ⎿  Successfully loaded skill

  Read 2 files (ctrl+o to expand)

● Bash(gh --version 2>\&1 | head -1)
  ⎿  gh version 2.92.0 (2026-04-28)

● Bash(gh repo view codepath/pathreview-ai301-fa26-s3 --json
      isArchived,pushedAt,latestRelease 2>\&1
      echo "---"…)
  ⎿  {
       "isArchived": false,
       "latestRelease": null,
     … +59 lines (ctrl+o to expand)

● Repo-level facts pass: not archived, pushed 2026-09-16 (recent),
  maintainer active (commits 2026-09-16 and 2026-08-24 by Aburke225, human
  account). Now let's fetch each issue.

● Bash(for n in 68 56 60; do
      echo "=== ISSUE $n ==="…)
  ⎿  === ISSUE 68 ===
     {
       "assignees": \[],
     … +62 lines (ctrl+o to expand)

● Bash(gh api
      repos/codepath/pathreview-ai301-fa26-s3/contents/docs/CONTRIBUTING.md
      --jq '.content' | base64 -d 2>/dev/null | grep -i -A3 -B3
      "AI\\|generated" | head -8…)
  ⎿  # Contributing to PathReview

     Thank you for contributing to PathReview! This guide explains our
     … +58 lines (ctrl+o to expand)

● No explicit AI ban found — silence passes per rubric. All three issues
  look clean and structurally similar (seeded bugs, good first issue label,
  no assignee, no PR). Let me confirm no open PRs and check no-headings test
  / abandoned attempts via PR search.

● Bash(for n in 68 56 60; do
      echo "=== $n PRs ==="…)
  ⎿  === 68 PRs ===
     === 56 PRs ===
     === 60 PRs ===

● No PRs tied to any of these issues. All checks pass for all three; none
  have real blockers (claim comments are from students, ignored per house
  rule).

  Issue #68: KeywordSearcher.index() raises ZeroDivisionError on empty
  corpus
  Issue #56: StructuralChunker.chunk() drops documents without headings
  Issue #60: FaithfulnessChecker crashes on chunk text: None

  All three: bounded scope (single bug, named files), contribution not
  support, no abandoned PRs, no assignee, no open PR, no AI ban, maintainer
  responsive (opener is Aburke225, COLLABORATOR), good-first-issue label
  present, repo active.

  Fit ranking: user's profile is Python/Flask/SQLAlchemy/RAG pipelines with
  ChromaDB \& sentence-transformers, wants more RAG/agentic practice. All
  three are Python RAG-adjacent bugs of similar tiny scope. #56 and #68 are
  core RAG retrieval/chunking components (closer to "RAG pipelines"
  experience); #60 is an evaluator utility. #68 (BM25 keyword search) and
  #56 (chunking) most directly match "RAG pipelines" experience; #56
  involves a chunker (very RAG-pipeline-specific, ingestion) — rank #56 top
  for direct fit to chunking/RAG-pipeline work, then #68 (retrieval), then
  #60 (evaluator, still fine but slightly less central to stated interests).

● Code review(review · 0 findings)

● Summary: All three pass every required check (repo active/not archived,
  maintainer human \& recent commits, bounded single-file bug scope, code
  contribution not support, no abandoned PRs, no assignee, no open PR, no
  real claim block per Path Review house rule — student claim comments don't
  count, no AI ban in CONTRIBUTING.md). All three carry the good first
  issue label and were opened by a collaborator, so preferred checks pass
  too.

  Ranked by fit to your Python/RAG background:
  1. #56 (structural chunker drops heading-less docs) — ingestion/chunking
  is core RAG-pipeline work, closest to your ChromaDB/sentence-transformers
  experience.
  2. #68 (BM25 keyword search ZeroDivisionError on empty index) —
  retrieval-side RAG bug, same fit tier.
  3. #60 (faithfulness checker crashes on None chunk text) — RAG-adjacent
  but an evaluation utility rather than pipeline core.

  \[
    {
      "item":
  "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56",
      "checks": \[
        {"name": "Repo not archived", "grade": "pass", "evidence":
  "isArchived: false"},
        {"name": "Repo in use", "grade": "pass", "evidence": "pushedAt
  2026-09-16, within 180 days of 2026-09-21"},
        {"name": "Maintainer alive", "grade": "pass", "evidence": "commit by
  Aburke225 on 2026-09-16, human account"},
        {"name": "Bounded scope", "grade": "pass", "evidence": "Single bug:
  StructuralChunker.chunk() returns empty list for heading-less docs, one
  file + one test"},
        {"name": "Is a contribution, not support", "grade": "pass",
  "evidence": "Body describes a code defect with repro steps, not a usage
  question"},
        {"name": "No abandoned attempts", "grade": "pass", "evidence": "No
  PRs found referencing issue #56"},
        {"name": "No assignee", "grade": "pass", "evidence": "assignees:
  \[]"},
        {"name": "No open pull request", "grade": "pass", "evidence": "No
  PRs found referencing #56"},
        {"name": "No active claim", "grade": "pass", "evidence": "No
  comments on this issue at all"},
        {"name": "No AI ban", "grade": "pass", "evidence": "CONTRIBUTING.md
  has no AI-generated-content ban; silence passes per rubric"},
        {"name": "Maintainer responsive", "grade": "pass", "evidence":
  "Opener Aburke225 has author\_association COLLABORATOR"},
        {"name": "Friendly signal", "grade": "pass", "evidence": "Labels
  include 'good first issue'; opened by Aburke225 (maintainer)"}
      ],
      "verdict": "accept"
    },
    {
      "item":
  "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/68",
      "checks": \[
        {"name": "Repo not archived", "grade": "pass", "evidence":
  "isArchived: false"},
        {"name": "Repo in use", "grade": "pass", "evidence": "pushedAt
  2026-09-16, within 180 days of 2026-09-21"},
        {"name": "Maintainer alive", "grade": "pass", "evidence": "commit by
  Aburke225 on 2026-09-16, human account"},
        {"name": "Bounded scope", "grade": "pass", "evidence": "Single bug
  in KeywordSearcher.index(), named files, remove one xfail marker"},
        {"name": "Is a contribution, not support", "grade": "pass",
  "evidence": "Body describes a ZeroDivisionError defect and fix
  expectation"},
        {"name": "No abandoned attempts", "grade": "pass", "evidence": "No
  PRs found referencing issue #68"},
        {"name": "No assignee", "grade": "pass", "evidence": "assignees:
  \[]"},
        {"name": "No open pull request", "grade": "pass", "evidence": "No
  PRs found referencing #68"},
        {"name": "No active claim", "grade": "pass", "evidence": "Only a
  student claim comment (acordero4852, NONE association), ignored per Path
  Review house rule"},
        {"name": "No AI ban", "grade": "pass", "evidence": "CONTRIBUTING.md
  has no AI-generated-content ban; silence passes per rubric"},
        {"name": "Maintainer responsive", "grade": "pass", "evidence":
  "Opener Aburke225 has author\_association COLLABORATOR"},
        {"name": "Friendly signal", "grade": "pass", "evidence": "Labels
  include 'good first issue'; opened by Aburke225 (maintainer)"}
      ],
      "verdict": "accept"
    },
    {
      "item":
  "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/60",
      "checks": \[
        {"name": "Repo not archived", "grade": "pass", "evidence":
  "isArchived: false"},
        {"name": "Repo in use", "grade": "pass", "evidence": "pushedAt
  2026-09-16, within 180 days of 2026-09-21"},
        {"name": "Maintainer alive", "grade": "pass", "evidence": "commit by
  Aburke225 on 2026-09-16, human account"},
        {"name": "Bounded scope", "grade": "pass", "evidence": "Single bug
  in FaithfulnessChecker.check(), named file + repro"},
        {"name": "Is a contribution, not support", "grade": "pass",
  "evidence": "Body describes a TypeError defect with repro steps"},
        {"name": "No abandoned attempts", "grade": "pass", "evidence": "No
  PRs found referencing issue #60"},
        {"name": "No assignee", "grade": "pass", "evidence": "assignees:
  \[]"},
        {"name": "No open pull request", "grade": "pass", "evidence": "No
  PRs found referencing #60"},
        {"name": "No active claim", "grade": "pass", "evidence": "Only a
  student claim comment (pkmaster21, NONE association) dated 2026-09-21,
  ignored per Path Review house rule"},
        {"name": "No AI ban", "grade": "pass", "evidence": "CONTRIBUTING.md
  has no AI-generated-content ban; silence passes per rubric"},
        {"name": "Maintainer responsive", "grade": "pass", "evidence":
  "Opener Aburke225 has author\_association COLLABORATOR"},
        {"name": "Friendly signal", "grade": "pass", "evidence": "Labels
  include 'good first issue'; opened by Aburke225 (maintainer)"}
      ],
      "verdict": "accept"
    }
  ]
```

\---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

1. Smoke run, `--limit 3`: `agreement: 2/3 scored items`. The harness line for the miss was `issue-01  accept  reject   NO     failed: Bounded scope, Maintainer responsive (preferred), Friendly signal (preferred)`. (Two earlier attempts errored before grading anything and produced no score: a Windows `UnicodeEncodeError` fixed by running `python -X utf8`, then `claude exited 1` because my Claude Code login had expired.)
2. `--only issue-01`, after rewriting the Bounded scope check: `agreement: 1/1 scored items`, with the line `issue-01  accept  accept   yes`.
3. Full 20-issue run with `--save-run eval-run.txt`: `agreement: 20/20 scored items  (bar: 18/20: PASS)`. This is the run committed as `eval-run.txt`.

**Issue analysis**

Issue analyzed: `issue-01` (source `conda/conda#16475`, "Add permanent docs for installing PyPI packages with `conda install`").

* My rubric's first decision: **reject**, failing the required check Bounded scope. The two other failed checks were tagged `(preferred)`, and the eval README says preferred checks never change a verdict, so Bounded scope alone caused the reject.
* Gold label: **accept**.
* Why my first rubric read it that way: the issue body has a `## Proposed changes` section with five sub-headings: `### Add a new task page`, `### Update `manage-pkgs.rst`, `### Update `pip-interoperability.rst`, `### Update `new-features.md``, and `### Consider a global `troubleshooting.rst` entry`. My first Bounded scope check said `Not an umbrella or tracking issue (a list of sub-items meant to be split)`, and that list of five items matches that wording. The harness note only names the check, so this is my reading; it is supported by the re-run, because changing only that one row flipped the verdict to accept.
* Why the gold label is still right: the evidence guide says scope fails when the issue is `explicitly an umbrella or tracking issue (a list of sub-items meant to be split into separate work)`. My check had dropped the word "explicitly". Issue-01 never calls itself an umbrella or tracking issue, nobody asks for it to be split, the bundle shows `Comments (0 total, first 0 shown)`, and it is one documentation feature spread across a few pages. The guide also says `Grade the size of the work being asked for, not the polish of the writeup.`

**Check rationale**

The check quoted as it is currently written in `tools/issue-select/rubric.md`:

```
| Bounded scope | Issue body and Comments | Fails only if (a) the issue calls itself an umbrella, tracking, or epic issue, or the opener or a maintainer says it should be split into separate issues or PRs; (b) a maintainer says the fix touches core internals; or (c) the thread shows the design is still being debated with no maintainer decision. One coherent change that touches several files or sections (for example one documentation feature spread across a few pages) passes. A short body or missing repro steps is NOT a failure | required |
```

Reasoning behind its current form: the first version failed on the shape of the issue (a list of sub-items). The evidence guide fails scope only on explicit signals, so the rewrite requires one: (a) an umbrella, tracking, or epic label or a request to split, (b) a maintainer saying the fix touches core internals, or (c) an unsettled design debate. The last two sentences keep the guide's line `Short is not the same as unscoped.` and add that one coherent change across several files or sections passes, which is exactly what issue-01 was.

**Trade-offs**

* What this check gives up: an umbrella issue that never says it is one. A long list of loosely related sub-items with no "tracking" or "split" wording and no maintainer comment now passes Bounded scope, and a genuinely large change that touches many files also passes if it reads as one coherent change. I accept that miss because the other required checks (no open PR, no assignee, no active claim, and so on) still apply, and because failing on the shape of a list is what wrongly rejected a good first issue.
* Nothing else changed, and here is how I know: I did not re-run individual canaries with `--only`. I ran the full 20-issue eval after the change, and it reported `categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 4/4` and `agreement: 20/20 scored items  (bar: 18/20: PASS)`. All four scope issues still matched their gold labels after I loosened the check.

\---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. Fit to my interests and the time available:

WRITE YOUR ANSWER HERE I want to get better at RAG and agentic systems, and chunking is a core part of a RAG pipeline. I have built a RAG pipeline with ChromaDB and sentence-transformers, so I know what a chunker feeds into, but I have not fixed a bug inside one. The skill I found is one bug in Structural Chunker. chunk(), with one file and one test, which fits around my full-time job. I can realistically give it \[YOUR HOURS, for example "a few evenings a week"]..

2. What the verdict identified correctly, and what I weighed that the rubric could not:

The verdict correctly found that the repo is active (last push 2026-09-16), that the issue has no assignee, no linked PRs and no comments, and that CONTRIBUTING.md has no AI ban. What the rubric could not weigh was fit and competition. All three candidates passed every check, so I compared them myself. #68 and #60 already have student claim comments, and #60's is dated today, while #56 has none. Chunking also matches my RAG experience more closely than the evaluator utility in #60.

3. Anticipated difficulty in claiming it:

Other students may claim it too, since it is a good first issue and the Path Review house rule allows shared issues. I would not race them. I would claim early with a clear comment and put my effort into a solid fix with a test. I have not read the code yet, so the fix may turn out bigger than the issue suggests. If that happens, I would read the existing tests first and ask a question in the issue thread before changing anything..

\---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.

