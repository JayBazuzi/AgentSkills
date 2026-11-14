# Skills and Scripts

This repo uses these words with specific meanings.

## Definitions

A **skill** is Markdown instructions for the agent (a folder with a `SKILL.md`, optionally with supporting files).
It describes *how to approach* a kind of task.
The agent interprets it with judgment, so results can vary.

A **script** is code we write, such as a Bash script or a small C# program.
It *does* a task the same way every time.
It runs without an AI, so people, CI, and other scripts can use it too.

A **tool** keeps its usual agent meaning: a function the agent can call, such as Bash, Read, or Edit.

## Comparison

| | Skill | Script |
|---|---|---|
| Executed by | The agent, interpreting prose | A shell or runtime |
| Deterministic | No, relies on judgment | Yes |
| Token cost per use | Skill body loaded and reasoned through each time | Usually just the command and its output |
| Usable without AI | No | Yes |
| Good for | Decisions, style, conventions, "it depends" | Exact, mechanical, repeatable steps |
| Testability | Hard (needs evals) | Easy (ordinary tests) |

## Using them together

The skill decides *when* and *why*; the script does the *what*.
A skill folder can ship its own scripts (conventionally in a `scripts/` subfolder), so the skill shrinks to "run this, then check X".
That is more reliable and uses fewer tokens than rebuilding the steps from prose each time.

## Choosing

- If the agent would do it the same way every time, make it a **script**, plus a short skill saying when to run it.
- If it depends on context or taste, make it a **skill**.
- If it is mostly mechanical with some judgment, do **both**: the skill handles judgment and calls the script for the mechanical part.

## Triggering

Only a skill's `description` line is always in the agent's context; the body loads when the skill is invoked.
So the `description` is what determines whether a skill gets used, and it should match how tasks are actually phrased.
