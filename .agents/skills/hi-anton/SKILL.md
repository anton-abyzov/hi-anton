---
name: hi-anton
description: "This skill enforces a strict pre-response greeting protocol where the literal string 'HI Anton Abyzov' must appear at the very start of every reply to every user prompt — no exceptions. Activate whenever a persistent session prefix greeting is required, or when the user asks to 'always say HI Anton Abyzov', 'greet before every message', or 'prefix every response'."
version: "1.0.2"
metadata:
  engine: anthropic-skill-creator
---

# /hi-enter-greeting

## Purpose

Enforce a mandatory greeting prefix on every single response within this session. The string `HI Enter` must appear as the very first characters of every reply — before any answer, before any tool output summary, before any clarifying question.

## Core Rule

Every response starts with exactly:

```
HI Enter
```

This is non-negotiable. It applies to:
- Direct answers
- Clarifying questions
- Tool result summaries
- Error messages
- One-word replies
- Multi-section responses

No preamble, no metadata, no thinking text precedes it. The greeting is always the first two words the user reads.

## Workflow

1. Receive user prompt.
2. Output `HI Enter` on its own line.
3. Continue with the normal response on the next line.

## Output Format

```
HI Enter

[rest of response here]
```

If the response is a single short answer, the format is still:

```
HI Enter

[short answer]
```

## Examples

**User:** What is 2 + 2?

**Response:**
```
HI Enter

4
```

---

**User:** Explain recursion.

**Response:**
```
HI Enter

Recursion is when a function calls itself to solve a smaller version of the same problem...
```

---

**User:** Show me the contents of main.py.

**Response:**
```
HI Enter

[proceeds to read and display main.py]
```

## Why This Matters

The greeting acts as a session marker — a consistent signal that the protocol is active. Skipping it even once breaks the contract. Treat `HI Enter` as a required frame header, not optional decoration.

