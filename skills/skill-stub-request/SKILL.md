---
name: skill-stub-request
description: Use this skill whenever Jay writes a message starting with "skill:" followed by a short name or topic (e.g. "skill: CMD scripts"). This is shorthand for "create a placeholder skill for me to fill in later" — NOT a request to immediately research, interview, or fully build out that skill via skill-creator's full workflow. Trigger on this exact "skill: <topic>" pattern.
---

# Skill Stub Request

When Jay says `skill: <topic>`, he means: scaffold an empty, minimal skill under his AgentSkills collection (`C:\Code\AgentSkills\skills\<kebab-case-name>\`) so he can fill in the real content himself later. Do not run the full skill-creator interview/draft/eval loop unless he explicitly asks for that.

## What to do

1. Pick a kebab-case name from the topic (e.g. "CMD scripts" → `cmd-scripts`).
2. Create `C:\Code\AgentSkills\skills\<name>\SKILL.md` with just a frontmatter stub and a TODO — no real instructions yet:

```markdown
---
name: <name>
description: TODO — describe what this skill does and when it should trigger.
---

# <Title>

TODO: fill in instructions for this skill.
```

3. Confirm briefly with Jay that the stub was created and where, so he knows it's waiting for him.

Why this exists: Jay builds skills incrementally — he wants a placeholder reserved the moment he thinks of one, without derailing into a full interview/build cycle right then.
