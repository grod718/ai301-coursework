# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment recorded | The repro report's environment record, read against the issue's stated target (version, platform) in the issue context | A stranger could recreate the starting state: the report names the project version, commit, or install source, and the runtime or OS version wherever the issue depends on one. If the issue targets a specific version or platform, the report matches it or says plainly that it differs | required |
| Steps followable | The repro report's steps, from the stated starting state to the trigger | A stranger could run them without guessing: every command, input, config value, or file needed to trigger the behavior is given literally or linked. Fails if a step says "do the usual setup", skips how the trigger input was made, or depends on something never stated | required |
| Behavior matches the issue | The repro report's artifacts (output excerpts, logs, tracebacks, described screenshots) read against the behavior the issue title and body describe | The artifact shows the same symptom in the same component the issue describes (same error type or message, same wrong output). An artifact showing a different error, a different code path, or a setup failure fails. If the report honestly says it could not reproduce, this check passes when the report does not claim otherwise | required |
| Outcome backed by evidence | The repro report's stated outcome read against its artifacts | The report states an outcome (reproduced, could not reproduce, or partial) and every claim in it is backed by an artifact shown in the report. Fails if it says "reproduced" or "confirmed" with no output shown, or claims more than the artifact shows. An evidenced cannot-reproduce, with the steps run and the observed output, passes | required |
| Claim is specific and honest | The claim comment read against the issue context | The claim names something specific to this issue (its symptom, component, file, or error) and says what the author will do next. Fails only if it is boilerplate that would fit any issue unchanged ("I'd like to work on this", "can I take this?") | required |
| AI-use policy respected | The repo-facts block's contribution policy line, read against the claim comment and the repro report | If the policy requires disclosing AI assistance, at least one of the comments discloses it. If the policy bans AI-generated contributions outright, fail. If the policy is silent or sets only other conditions, pass | required |
| Template asks answered | The repo-facts block's bug-report template asks, read against the repro report | The report supplies what the template asks for, or says why an item does not apply | preferred |

## Verdict rule

Accept if every required check passes. Otherwise reject. Preferred checks never change the verdict. A check that does not apply yet (for example the repro checks on a claim-only draft in live mode) counts as pass. `unclear` on a required check counts as fail.
