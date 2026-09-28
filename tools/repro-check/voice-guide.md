# Voice guide: how I talk upstream

## Who I am in threads

I'm an IT professional with 11 years in help desk, support, and training, and I'm new to contributing to open source. I'm here as a CodePath AI301 student working on Path Review issues. Readers can expect me to report exactly what I ran and what I saw, and to say plainly when I'm unsure.

## Rules I write by

### Rule: promise the investigation, not the fix

I only promise the next thing I will actually do. No fixes, PRs, or dates until I have reproduced the bug.

- Wrong: "I'll have a fix up by Friday."
- Right: "I'll reproduce this on a fresh clone of my fork and post what I find here."

### Rule: name the specific thing

Every comment names the exact function, file, or symptom from the issue, so it could not be pasted onto any other issue.

- Wrong: "Hi, I'd like to work on this issue."
- Right: "I'd like to take this one: StructuralChunker.chunk() returning an empty list for a document with no headings."

### Rule: show the output, don't describe it

When I say something happened, the output that shows it sits right under the sentence.

- Wrong: "Confirmed, it's broken on my machine."
- Right: "Reproduced on Python 3.11.2, Windows 11. Output below."

### Rule: disclose AI help plainly

I say when I used AI tools and what I did myself.

- Wrong: (saying nothing about the tools I used)
- Right: "I used Claude Code to help me read the code and draft this comment. I ran every command myself."

### Rule: say what I don't know

A guess is labeled as a guess.

- Wrong: "The root cause is the heading regex."
- Right: "I suspect the heading split, but I haven't confirmed that yet."

## Things I never post

- A date or deadline for a fix
- "Same as above, can confirm" or any repro that isn't my own
- "This should be a quick fix"
- Output I didn't run myself
- Blame toward maintainers or other contributors
