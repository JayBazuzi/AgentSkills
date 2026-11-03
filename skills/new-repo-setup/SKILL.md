---
name: new-repo-setup
description: Use this skill whenever initializing a brand-new git repository, or when the user asks to set up/scaffold a new repo or project. Adds Jay's standard baseline files (.gitignore, LICENSE, .gitattributes) so every repo starts with consistent, predictable git behavior. Trigger on phrases like "new repo", "init this project", "set up a new repository", "scaffold a repo", even if the user only asks for one of the pieces (e.g. just a .gitignore) — mention the others are available too.
---

# New Repo Setup

Baseline files Jay wants in every new repository he creates. Not every repo is buildable/CI-able — that's a separate concern (a separate skill), so this one stays scoped to git-level hygiene only.

## 1. `.gitignore`

Generate one appropriate to the repo's language/tooling (standard GitHub templates are a good starting point — e.g. Node, Python, .NET, etc.). Don't guess blindly; look at what's actually in the repo first.

## 2. `LICENSE`

**Always ask Jay which license he wants before adding one** — don't default to MIT or any other license silently. Once he answers, use the standard full text for that license (fill in year and his name/org as copyright holder).

## 3. `.gitattributes`

Use exactly this content as the baseline, then adjust/add lines for any other file types in the repo that need explicit line-ending handling:

```
* -text
*.verified.* text eol=lf
*.cmd text eol=crlf
*.bat text eol=crlf
```

Why: `* -text` turns off Git's automatic text/binary detection and CRLF/LF normalization by default — avoids Git silently rewriting line endings on files it misclassifies. The two overrides below are important special cases: Verify-style snapshot files (`*.verified.*`, e.g. from Verify.NET) must stay LF so diffs don't spuriously flip on different OSes, while Windows batch scripts (`*.cmd`, `*.bat`) require CRLF to run correctly.
