# Evidence guide: where proof lives in a reproduction package

## Environment

- Where it lives: in an eval package, the repro report's environment record (versions, OS, install method, commit), read against the issue context and the repo-facts block's bug-report template asks. In live mode, the environment section of my draft repro comment, read against the issue body and the repo's setup docs (README, CONTRIBUTING.md, docker-compose or pyproject files).
- What good looks like: someone else could rebuild the same starting state. The report names the project version or commit (or the branch it was cloned from) and the runtime and OS versions. If the issue names a target version or platform, the report either matches it or says plainly that it differs. A report that says only "latest" or "my machine" is not a record.

## Steps

- Where it lives: the repro report's steps section, from setup to trigger. In live mode, the numbered steps in my draft repro comment.
- What good looks like: a stranger could run them in order without guessing. Every command, input value, config setting, and test file needed to trigger the behavior is written out literally or linked. The starting state is stated (fresh clone, which branch, which install command). A step like "set up the environment as usual" or "run it on a bad file" without saying how the file was made fails. The number of steps does not matter; completeness does.

## Behavior shown

- Where it lives: the repro report's artifacts: pasted output, logs, tracebacks, test results, and described screenshots. Read them against the issue title and body (the symptom the issue describes: error type, message, wrong value, component).
- What good looks like: the artifact shows the issue's own symptom in the issue's own component: the same exception type or message, the same wrong output, from the code path the issue names. An artifact showing a different error (an import error, a setup failure, a crash in another module) is an adjacent behavior, not this one, even if the report calls it a reproduction.

## Honesty

- Where it lives: the repro report's outcome statement ("reproduced", "could not reproduce", "partially reproduced") read against its own artifacts.
- What good looks like: every claim has an artifact behind it. "Reproduced" needs output showing the behavior. "Could not reproduce" needs the steps that were run and the output observed instead; that is an honest, passing outcome. A report that says "confirmed, same as the issue" with no output, or claims a root cause the artifacts never show, claims more than its evidence and fails.

## Comms

- Where it lives: the claim comment read against the issue; both comments read against the repo-facts block's contribution policy line (including any AI-use policy) and bug-report template asks. In live mode, the repo's CONTRIBUTING.md, any AI policy file, issue templates, and the issue thread.
- What good looks like: the claim names something only this issue has (its symptom, component, file, or error) and says what the author will do next; a line that would fit any issue unchanged is boilerplate. If the policy requires disclosing AI assistance, at least one of the comments discloses it; a package whose comments stay silent under a disclosure requirement fails. An outright AI ban fails. Silence in the policy passes.
