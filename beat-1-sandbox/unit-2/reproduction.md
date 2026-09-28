# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

grod718

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56#issuecomment-5860796227

Hi, I'd like to take this one. I'm going to reproduce `StructuralChunker.chunk()` silently dropping a document that has no headings (returning no chunks for it) on a fresh clone of my fork. I'll post a repro report here with my environment, the exact steps I ran, and the output I get.

Heads-up: I'm using Claude Code to help me read the code and draft comments. I run every command myself.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56#issuecomment-5860995464

Repro report for #56: I reproduced it.

**Environment**
- Repo: my fork of codepath/pathreview-ai301-fa26-s3, fresh clone, branch `main`, commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088` (Sep 16 2026)
- OS: Microsoft Windows 11 Pro, commands run in PowerShell
- Python 3.11.2 in a fresh venv; pytest 9.1.1; tiktoken 0.14.0
- Setup: I followed the Python install step from the Makefile's `setup` target (`pip install -e ".[dev]"`). I did not start Docker or run migrations, because this bug is in a unit-tested module and `pyproject.toml` marks unit tests as having no external dependencies.

**Steps**
1. `git clone https://github.com/grod718/pathreview-ai301-fa26-s3.git` and `cd pathreview-ai301-fa26-s3`
2. `python -m venv .venv`
3. `.\.venv\Scripts\python.exe -m pip install -e ".[dev]"`
4. `.\.venv\Scripts\python.exe -m pytest tests\unit\test_structural_chunker.py -v -rxX`
5. Called the chunker directly with the same text the test uses, once without and once with a heading (`repro_56.py` in the repo root):

```python
from ingestion.chunking.structural_chunker import StructuralChunker

chunker = StructuralChunker()
body = "This is plain text without any markdown headings. " * 20

no_heading = chunker.chunk(body, {"source": "test"})
with_heading = chunker.chunk("# Title\n" + body, {"source": "test"})

print("no heading   -> chunks:", len(no_heading), no_heading)
print("with heading -> chunks:", len(with_heading))
print("first chunk text starts:", repr(with_heading[0].text[:50]))
```

Run with `.\.venv\Scripts\python.exe repro_56.py`.

**Output**

Step 4:
```
XFAIL tests/unit/test_structural_chunker.py::TestStructuralChunker::test_document_with_no_headings - issue #56: structural chunker drops documents with no headings
====================== 14 passed, 1 xfailed in 7.68s ======================
```

Step 5:
```
no heading   -> chunks: 0 []
with heading -> chunks: 1
first chunk text starts: 'This is plain text without any markdown headings. '
```

**Result**
`StructuralChunker.chunk()` returned an empty list for the document with no headings, so the whole document was dropped with no error. Adding a single `# Title` line to the same text gave one chunk containing that text. This matches the behavior described in the issue.

Reading `_extract_sections()` in `ingestion/chunking/structural_chunker.py`, content lines only appear to be collected after a heading has been seen (`if heading_stack or current_section_lines:`), which would explain it. I haven't changed any code to confirm that yet.

I used Claude Code to help me read the code and draft this report. I ran every command above myself, and the output is copied from my terminal.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. Smoke run, `--limit 3`: `agreement: 3/3 scored items` (pkg-01, pkg-02, pkg-03 all matched gold).
2. Full 20-package run with `--save-run eval-run.txt`: `agreement: 20/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 8/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`. This is the run committed as `eval-run.txt`.

**Package analysis**

Package: `pkg-20` (source `ghostty-org/ghostty#13604`, "Mode 2031 reports do not work unless both a dark and a light theme are configured"). This is the one package in the `disclosure` category.

- My rubric's decision: **reject** (harness line: `pkg-20  reject  reject   yes`).
- Gold label: **reject**.
- Why my rubric read it that way: on the proof checks this package is strong. The repro report records the environment (`ghostty 1.3.1 (release build, Fedora 42 RPM), GTK backend, GNOME 48 (Wayland), dark system scheme`), gives exact launch commands, and shows the issue's own symptom with a control: the single-theme run returns `^[[?997;2n` and the conditional-pair control returns `^[[?997;1n`, matching the issue's `CSI ? 997 ; 2 n` vs `CSI ? 997 ; 1 n`. The claim is specific ("I want to test the draft patch in the issue against both the single-theme and conditional-pair configurations"). What sinks it is my "AI-use policy respected" check. The repo-facts block states: `All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance`. Neither the candidate claim comment nor the candidate repro report mentions AI or any tool, and the course treats these packages as AI-assisted work. So the policy requires disclosure and neither comment discloses, which is my check's fail condition. The harness table does not print per-check grades for packages that agree, so this is my reading of the package against my rubric rather than a quoted per-check result; it is the only required check this package could fail, since every proof check is satisfied by the quotes above.

**Check rationale**

The check, quoted as it reads now in `tools/repro-check/rubric.md`:

```
| AI-use policy respected | The repo-facts block's contribution policy line, read against the claim comment and the repro report | If the policy requires disclosing AI assistance, at least one of the comments discloses it. If the policy bans AI-generated contributions outright, fail. If the policy is silent or sets only other conditions, pass | required |
```

Why it reads that way: the eval README says the `disclosure` category has exactly one package and that a rubric with no conventions check cannot make up that miss on volume, so this check exists to see that surface at all. I wrote it as three outcomes keyed to what the policy line actually says (requires disclosure, bans AI outright, or silent / other conditions) instead of one rule like "comments must disclose AI use", because a blanket rule would wrongly reject packages from repos that never ask for disclosure. The gold note for `pkg-05` says conda's policy is "permissive-with-responsibility, no disclosure requirement", and that package is a clear accept. I made it `required` because the gold note for `pkg-20` calls it "excellent repro on every proof check" and still rejects it: a disclosure wall holds a package no matter how good the proof is.

**Trade-offs**

What this check gives up: it passes if at least one of the two comments discloses, and it only asks whether AI use is disclosed, not whether the disclosure is complete. ghostty's policy asks for "the tool used and the extent of the assistance". A comment that said only "I used AI" would pass my check even though it names neither the tool nor the extent, and a package that disclosed in the claim but not in the repro report would also pass. I accept those misses because the set only tests the "does not disclose" case, and tightening the check to grade disclosure completeness would add a judgment call the evidence rarely supports.

Nothing else changed, and here is how I know: I did not revise this check after running the eval, so there was no loosening to canary. The first full run reported `disclosure 1/1` together with `clear-accept 8/8`, including `pkg-07`, whose gold note says it "discloses AI assistance as p5.js's stated policy requires", and `pkg-05` with conda's no-requirement policy. Both accepted, so the check did not over-reject repos with conditional or permissive policies, and the overall result was `agreement: 20/20 scored items  (bar: 18/20: PASS)`.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
