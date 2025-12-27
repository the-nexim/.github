Here is the comprehensive **Git Commit Convention Guide** in English, formatted in Markdown. You can copy this directly into a file named `CONTRIBUTING.md`, `COMMIT_CONVENTION.md`, or your internal wiki (Notion/Confluence).

---

# Git Commit Convention Guide

This document defines the standards for commit messages in our team. Our goal is to maintain a clear, readable, and machine-processable history that allows us to automate versioning and changelog generation.

This standard follows **[Conventional Commits v1.0.0](https://www.conventionalcommits.org/)**.

## 1. Structure

Every commit message must follow this structure:

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]

```

### Components:

* **Header (Line 1):** Mandatory. Contains the type, scope, and a short description.
* **Body:** Optional. detailed explanation of the change.
* **Footer:** Optional. For tracking IDs or Breaking Changes.

---

## 2. Header Rules

The header line is the most important part. It should be **under 50 characters** (max 72).

### A) Type

The type tells us what kind of change this is and determines the Semantic Versioning bump:

* **`feat`**: (Feature) A new feature. **[Triggers MINOR release]**
* **`fix`**: (Bug Fix) A bug fix. **[Triggers PATCH release]**
* **`docs`**: Documentation only changes.
* **`style`**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
* **`refactor`**: A code change that neither fixes a bug nor adds a feature.
* **`perf`**: A code change that improves performance.
* **`test`**: Adding missing tests or correcting existing tests.
* **`chore`**: Changes to the build process or auxiliary tools/libraries (e.g., documentation generation).
* **`ci`**: Changes to our CI configuration files and scripts.

### B) Scope (Optional)

A phrase describing the section of the codebase affected, enclosed in parentheses.

* Examples: `feat(auth):`, `fix(api):`, `style(button):`

### C) Description (The Grammar)

A short summary of the code changes. **You must follow these grammatical rules:**

1. **Use the Imperative Mood:**
* Write it as if you are giving a command.
* Use **"add"**, not "added" or "adds".
* Use **"fix"**, not "fixed" or "fixes".
* **The Golden Rule:** The sentence should complete this phrase:
> *"If applied, this commit will **[your description]**"*

2. **Lowercase:**
* Start the description with a lowercase letter.
* ✅ `fix: prevent infinite loop`
* ❌ `fix: Prevent infinite loop`

3. **No Period:**
* Do not end the header line with a period (`.`).
* ✅ `docs: update readme`
* ❌ `docs: update readme.`

---

## 3. Body Rules (Optional)

* Must be separated from the header by **one blank line**.
* Use the body to explain **"what"** and **"why"** vs. **"how"**.
* You can use multiple paragraphs.

---

## 4. Breaking Changes

If your commit breaks backward compatibility (e.g., changing a public API):

1. **Footer:** Start with `BREAKING CHANGE:` (uppercase), followed by a space and the description.
2. **Header:** Alternatively, add an exclamation mark `!` after the type/scope.

*This triggers a **MAJOR** version release.*

---

## 5. Examples

### ✅ Feature (Standard)

```text
feat(cart): add 'buy now' button to product page

```

### ✅ Bug Fix (With Body)

```text
fix: correct parsing logic for user input

The parser was failing when the input string contained special characters.
Now it sanitizes the input before processing.

```

### ✅ Breaking Change

```text
feat(api)!: remove v1 search endpoint

BREAKING CHANGE: The GET /search endpoint is removed. Use POST /v2/search instead.

```

### ✅ Refactor

```text
refactor(auth): simplify password validation logic

```

---

## 6. Do's and Don'ts (Cheat Sheet)

| Status | Commit Message | Reason |
| --- | --- | --- |
| ❌ **Bad** | `fix: Fixed the login bug.` | Past tense (`Fixed`), Capitalized, Ends with `.`. |
| ✅ **Good** | `fix: fix login bug` | Imperative, lowercase, no period. |
| ❌ **Bad** | `feat: adds new header` | 3rd person (`adds`). |
| ✅ **Good** | `feat: add new header` | Imperative mood. |
| ❌ **Bad** | `Update styles` | Missing `type`. |
| ✅ **Good** | `style: update css variables` | Correct type and format. |

---

### Why do we do this?

1. **Better History:** Looking at `git log` is cleaner and easier to read.
2. **Automation:** We can automatically generate `CHANGELOG.md` files.
3. **Versioning:** We can automatically determine if the new version is a Patch, Minor, or Major release.

---

**Please ensure your PR titles and commit messages follow these guidelines before merging.**
