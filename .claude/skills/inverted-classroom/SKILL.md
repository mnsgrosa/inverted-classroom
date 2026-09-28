---
name: inverted-classroom
description: Design and run a learner-led, answer-first course when the user wants to learn a subject through retrieval, Python practice, and Socratic coaching. Use this whenever they ask for a course, curriculum, study plan, or interactive learning workflow, even if they do not name an inverted classroom.
---

# Inverted Classroom

Build a durable course around the learner's goal: the learner attempts retrieval and practice first; the teacher then explains, probes, and schedules targeted revisits. Do not run a course or create files until intake is complete.

## 1. Intake gate

Ask for all of these before writing a learner workspace:

- goal and subject/topic (including the outcome they want);
- baseline: what they can already explain or do, and relevant prerequisites;
- available learning time (per session and overall time horizon);
- desired depth (survey, working competence, or advanced mastery);
- destination: an explicit directory path where course files may be created.

If any answer is missing, state the missing fields, ask focused follow-up questions, and stop. Never infer a subject, schedule, depth, or destination. Confirm the final intake summary and destination before creation. A destination may be an existing directory, but do not overwrite unrelated files; explain any proposed new files first.

## 2. Course workspace and progression

At the confirmed destination, create only a bounded course sized to the time/depth budget:

```
MISSION.md                 # goal, constraints, and success evidence
COURSE.md                  # scope, module order, prerequisites, revisit dates
INDEX.md                   # navigable links and progress/status
RESOURCES.md               # annotated, trusted sources and access dates
modules/                   # one directory per bounded capability
  01-<slug>/
    README.md               # one-command invocation and interpretation
    main.py                 # one-command module entrypoint/checker
    THEORY.html            # questions, then explanation and transfer
    practice/              # learner-authored starter tasks (when relevant)
      README.md            # run/test instructions and examples
      starter.py           # TODO-only starter (no answer code)
      test_starter.py      # executable standard-library checks
learning-records/          # durable records, numbered 0001-*.md
reference/                 # compact, reusable summaries
assets/                    # shared CSS/components, reused by modules
mistakes.md                # misconception index and retry queue
NOTES.md                   # preferences and open questions
```

Create `modules/<nn>-<slug>/` explicitly for every module (including its root `main.py`, HTML theory file, and, when Python is relevant, its `practice/` files). Link every module from `INDEX.md`, and link next/previous modules and exact anchors so the index is a usable course map rather than a directory listing.

Make every module have one concrete capability, a prerequisite, a short estimate, and a completion check. Every generated module must have a discoverable root `main.py` and a module-level `README.md` documenting its one-command invocation, working directory, and result interpretation; for coding tasks link to `practice/README.md` for details. For coding modules, `main.py` runs explicit meaningful tests against the learner's `practice/starter.py`: wrong, incomplete/TODO, or broken checker exits nonzero; zero is reserved for all checks passing. It must contain no implementation or hidden answer file. A passing suite verifies only the tested behavior, not full correctness or conceptual mastery; require dialogue and transfer checks before marking a module complete. Use the budget to choose a realistic number of modules rather than promising exhaustive coverage. Start from the mission and baseline; adapt order, difficulty, and later modules based on demonstrated understanding, not exposure or page completion. Keep `INDEX.md`, learning records, and mistake links current after each session. Cite sources in `RESOURCES.md` and link to them from lessons; prefer authoritative primary sources and label uncertainty.

## 3. Question-first lesson artifacts

Each module's theory file is a small, printable, linked HTML document. Begin with a brief objective, then theory retrieval questions and prediction tasks **before** explanation. Require the learner to record an answer (for example, a textarea or plain-text prompt). Static HTML cannot hide source content before an attempt: for genuine answer-first behavior, put questions in `THEORY.html` and explanations in a separate `EXPLANATION.html` (or deliver explanation only in later agent feedback), linked/revealed after an attempt. Follow attempts with concise explanation, worked *reasoning* (not a completed learner exercise), citation, and a second transfer question. Link exact anchors to related modules and references, and include a shared stylesheet from `assets/`.

HTML must remain useful without JavaScript: provide semantic headings, labels, keyboard-accessible controls, readable print styles, and a no-JS path where the learner writes/saves an attempt, then follows an explicit `Continue to explanation` link or asks the agent for feedback. State that static HTML cannot enforce sequence or grade free text; the agent reviews attempts and gives feedback, hints first, and classification in dialogue. Never claim a browser widget proves mastery. Theory-only modules cannot machine-grade free text: their `main.py` must print that manual dialogue review is required and exit nonzero (for example, status 2), never report a false passing result.

For Python-capable topics, create each relevant task under its module's `practice/`: `README.md` states the bounded prompt, working directory and commands (`python3 main.py` from the module root; `python3 -m unittest -v test_starter.py` from `practice/`), and non-solving input/output examples; `starter.py` contains explicit `TODO` markers and a failing placeholder such as `raise NotImplementedError`, not a solution; `test_starter.py` contains executable checks without answer code. Use stdlib `unittest` by default; pytest is optional only when explicitly declared with setup and command. Have `main.py` run the suite from the correct directory and propagate its exit status; test normal and edge cases, and return nonzero for failing tests or checker errors. Tell the learner to edit the starter, run the commands locally, and author the solution. Do not put completed solutions, answer keys, hidden solution files, or learner-facing implementation snippets in the workspace. If a task is not Python-relevant, use an equivalent learner-authored artifact instead of forcing code.

## 4. Grill, feedback, and remediation

After each attempt, ask the learner to explain why their answer or program works, predict an unseen case, compare a near-miss, and transfer the idea to a changed context. Ask one question at a time and give a small hint before an explanation. Distinguish `correct`, `uncertain/incomplete`, and `wrong`; request revision for the latter two. Do not advance merely because the learner viewed material.

When an error or fragile explanation appears, append an entry to `mistakes.md` with:

- stable ID, date, module, and the learner's observable symptom;
- misconception/hypothesis (without shaming or asserting intent);
- exact remediation target: `modules/<nn>-<slug>/EXPLANATION.html#<anchor>` or `reference/<file>.html#<anchor>` (create the target if absent), plus the cited resource;
- a hint-first remediation prompt and a fresh retry question;
- status (`open`, `retry-due`, or `resolved`) and next revisit date.

A retry must test the same concept in a new example. Mark resolved only after explanation and transfer are both sound; otherwise keep it open and adjust the next module. Space and interleave retries using the available schedule. Record evidence and learner questions in numbered learning records, and revisit the index at the next session before introducing new material.

## Session protocol

1. Load `MISSION.md`, `COURSE.md`, `INDEX.md`, recent learning records, `mistakes.md`, and the relevant lesson/resources.
2. Run retrieval questions before showing explanations; collect the learner's attempt.
3. Grill reasoning and transfer, give hint then explanation, and classify evidence.
4. Assign or inspect the learner-authored task; run only the stated tests/instructions, without supplying its solution.
5. Update records, misconception anchors, retry dates, and index status; propose the next bounded revisit.

If the destination is unavailable or the learner asks for a full answer, pause: offer a hint, test interpretation, or conceptual explanation instead, and request a safe destination or clarification. Never create a subject-specific course during skill authoring or from incomplete intake.
