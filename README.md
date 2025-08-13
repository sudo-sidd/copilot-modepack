# Copilot Mode Pack

Lightweight behavioral overlays for GitHub Copilot Chat. Instead of creating custom chat modes (`.chatmode.md`), you temporarily attach an `*.instructions.md` file as context to an existing built‑in mode (Ask, Edit, Agent) to shape its behavior for that conversation.

## Why & How I Use These Modes

Different cognitive goals → different pairing & tooling posture:

### 1. Learning a concept or exploring an unfamiliar project

- Mode: Ask + Tutor
- Editor Setup: Turn OFF inline code completions (VS Code Settings → GitHub Copilot: Inline Suggest Disabled, or run the Copilot command to disable for workspace).
- Rationale: Forces active recall and reasoning instead of passive acceptance of AI completions; prevents "autopilot" coding where you end up with working code you don't understand.
- Practice: Ask conceptual, architecture, and debugging questions; request small hints instead of solutions; only invoke override keyword when you intentionally want a concrete code reference.

### 2. Productive grind in a familiar stack

- Mode: Edit + Assist (keep completions ON).
- Use Case: Offload repetitive / low-complexity tasks: boilerplate, documentation blocks, comments, test scaffolding, simple refactors.
- Rationale: Maximizes velocity while you still review and control scope; avoids context switching fatigue.
- Prompt Style: Be specific (files / functions / acceptance criteria) so Assist generates minimal, clean diffs.

### 3. Creative or "vibe" prototyping session

- Mode: Agent + Hands-Off
- Goal: Rapidly manifest experimental ideas / throwaway prototypes by iterating with high-level prompts.
- Rationale: Embraces speed & exploration; you can later formalize or harden promising results using Assist mode.
- Safeguard: Don't ship Hands-Off output to production without a manual review pass (security, performance, style).

### Benefits of This Discipline

- Preserves deep learning (less over-reliance on completion noise).
- Channels AI strength (speed on rote tasks, broad exploration) without eroding core skill acquisition.
- Reduces cognitive overload by aligning tool behavior with intent.
- Improves security & correctness via explicit scope (Hands-Off) and reasoning-first (Tutor).

## Instruction Files & Pairing

| Instruction File              | Pair With Base Mode | Intent                                                                                               |
| ----------------------------- | ------------------- | ---------------------------------------------------------------------------------------------------- |
| `Tutor.instructions.md`     | Ask                 | Socratic tutoring, conceptual clarity, no full runnable code unless override keyword explicitly used |
| `Assist.instructions.md`    | Edit                | Implementation helper for incremental edits, boilerplate, tests, docs                                |
| `Hands-Off.instructions.md` | Agent               | Full execution of a clearly scoped task with security & maintainability guardrails                   |

(Ensure file names match exactly those in this repository.)

## Where to Put Them

You have two non-exclusive options:

1. In this repository (project-local) so teammates share the same rules , and rules apply only for that workspace
2. In your user data prompts folder (e.g. `~/.config/Code/User/prompts/`) for reuse across projects

## Attaching an Instruction File

1. Open Copilot Chat.
2. Select the base mode (Ask / Edit / Agent).
3. Open the Add Context panel:
   - UI: Click "Add context" → choose "Add instructions".
   - Shortcut : Press the sequence shown in your environment (you mentioned: `Ctrl+A`, then `t`, then `/`). Keybindings may vary—adjust if customized.
4. Paste the full contents of the chosen `*.instructions.md` file .
5. Send your prompt—behavior now follows the attached instructions.
6. To switch: remove that instruction context and attach a different file.

Nothing persists globally; each chat thread can have its own active instruction file.

## Override Keyword (Tutor Mode)

`Tutor.instructions.md` deliberately blocks full runnable code. To allow it in a specific answer, include the override phrase in your prompt (keyword documented inside the file: "CODE REQUEST OVERRIDE"). Omit the phrase for conceptual guidance only.

Example:

- Concept-only: "Explain why my DFS blows the call stack."
- With override: "CODE REQUEST OVERRIDE: Show a tail-recursive alternative." (Now Tutor may produce runnable code.)

## Recommended Workflow

1. Ask + Tutor: Refine requirements, validate understanding, surface risks.
2. Edit + Assist: Generate boilerplate, tests, configs, small focused changes.
3. Agent + Hands-Off: Execute a well-bounded implementation task end‑to‑end.
4. (Optional) Return to Ask + Tutor for post-implementation review or refactor planning.

## Quick Reference Matrix

| Goal                     | Mode + Instructions          |
| ------------------------ | ---------------------------- |
| Clarify / learn concept  | Ask + Tutor                  |
| Add tests / boilerplate  | Edit + Assist                |
| Implement scoped feature | Agent + Hands-Off            |
| Refactor planning        | Ask + Tutor, then Edit/Agent |

## Troubleshooting

| Symptom                                      | Likely Cause                                 | Resolution                                               |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------------------- |
| Copilot ignores constraints                  | File not actually attached                   | Re-attach via Add context → Add instructions            |
| Full code appears in Tutor mode unexpectedly | Override phrase present or ambiguous request | Remove phrase; restate conceptual intent                 |
| Hands-Off refuses to proceed                 | Scope ambiguous / missing constraints        | Provide explicit boundaries, inputs, acceptance criteria |
| Edit mode changes too broad                  | Vague edit prompt                            | Narrow prompt; specify files/functions                   |

## Security & Scope Notes

- Instruction files discourage leaking secrets or using unsafe shortcuts.
- Hands-Off mode should not invent architecture—supply scope explicitly.
- Tutor mode enforces reasoning-before-code to reduce shallow copy/paste.

## Contributing

1. Open an issue describing proposed behavioral adjustment.
2. Provide rationale and minimal diff.
3. Keep language directive and unambiguous; avoid large unrelated edits.

## Repository Structure

```text
Assist.instructions.md
Hands-Off.instructions.md
Tutor.instructions.md
README.md
```
