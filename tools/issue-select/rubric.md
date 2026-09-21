# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Repo not archived | "archived:" on the repo line | archived is false | required |
| Repo in use | "last push to any branch" and "latest release" under Repo facts | Last push within 180 days of the capture date | required |
| Maintainer alive | "last 5 default-branch commits" under Repo facts | At least 1 commit within 90 days of the capture date, authored by a non-bot account or a bot merge of a human's pull request | required |
| Bounded scope | Issue body and Comments | Fails only if (a) the issue calls itself an umbrella, tracking, or epic issue, or the opener or a maintainer says it should be split into separate issues or PRs; (b) a maintainer says the fix touches core internals; or (c) the thread shows the design is still being debated with no maintainer decision. One coherent change that touches several files or sections (for example one documentation feature spread across a few pages) passes. A short body or missing repro steps is NOT a failure | required |
| Is a contribution, not support | Issue body | Asks for a code, doc, or test change, not "how do I use or configure X" | required |
| No abandoned attempts | "linked PRs:" state, plus PRs mentioned in Comments | Fewer than 3 closed unmerged pull requests tied to this issue | required |
| No assignee | "this issue: assignees:" under Repo facts | Assignees is empty | required |
| No open pull request | "linked PRs:" state, plus PRs mentioned in Comments | No open PR tied to this issue. If the linked list and the thread disagree, believe the thread | required |
| No active claim | Comments section | No claim comment ("I'll take this", "can I work on this", "working on this") dated within 30 days of the capture date that was not withdrawn | required |
| No AI ban | "contribution policy" line under Repo facts | No outright ban on AI-generated contributions. Disclosure, testing, or human-review conditions pass, and so does silence | required |
| Maintainer responsive | "maintainer first-response sample" and author_association in Comments | First maintainer replies within 14 days, or an Owner, Member, or Collaborator has commented in this thread | preferred |
| Friendly signal | Labels and issue opener | Carries a good-first-issue label, or a maintainer opened it | preferred |

## Verdict rule

Reject if any required check fails. Otherwise accept. Preferred checks never change a verdict. A good-first-issue label never rescues a failed required check. Recency thresholds are measured against the capture date in eval mode and against today in live mode.
