---
name: game-storyboard
description: Plan game storyboards, cutscene shot lists, and gameplay narrative beats for 2D or 3D games. Use for storyboard panels, camera continuity, animatic planning, or transitions between cutscenes and player control.
---

# Game Storyboard

Turn the brief into a small, checkable sequence. Match the user's language and requested fidelity. This is a custom starter-pack skill, not an official OpenAI skill.

## Scope and output

Use existing characters, art direction, engine, and story constraints. Clarify only missing decisions that materially change the sequence; otherwise state a concise assumption and proceed. Distinguish linear cutscenes from interactive beats. Do not expand a storyboard request into building the game.

Before generating, define observable pass criteria: required story beats, approximate duration or panel count, character/location continuity, and when player control begins or ends. Produce only requested deliverables; a text storyboard does not require image generation, Blender, or an animatic.

For each shot, capture the fields that matter:

| ID / branch | Time or trigger | Framing / camera | Action / player goal | Dialogue / audio | Control / exit condition |
|---|---|---|---|---|---|

For timed scenes, give start and duration. For interactive scenes, use triggers and completion conditions instead of inventing fixed timing. Track branches with stable IDs, conditions, destinations, and intended reconvergence or ending. Keep a concise character and prop reference when visual consistency matters.

## Visual panels and 3D staging

When images are requested, use the available image-generation skill/tool and follow its instructions. Reuse approved character and environment references, preserve costume/prop details, screen direction, eyelines, and action continuity. Generate one representative shot first when the visual direction is unresolved; do not add an approval gate if the user already authorized proceeding. Keep labels and exact dialogue in the shot table rather than relying on generated lettering. Inspect the actual panels and report continuity defects; reference reuse is not a guarantee of consistency.

When Blender staging is requested, check available tooling first. Block out simple geometry, camera positions, scale, and lighting before detailed assets. Preserve editable .blend sources and render the requested camera frames. Only export GLB when runtime assets are part of the request. Use the available 3D asset skill for that export step, not as a second mandatory planning workflow. If Blender or rendering is unavailable, provide the staging specification and clearly mark it unverified.

For an animatic, align panels to the shot table and requested audio, then inspect actual playback or rendered frames at repeatable times. Check transitions, pacing, overlap, and the final state. For interactive delivery, specify skip behavior and input handoff; check reduced-motion behavior when implementing motion. Detailed motion checks may use MOTION_VERIFICATION.md from the starter pack if available; static boards do not need that guide.

## Generate → Verify → Repair

Build one useful sequence, then inspect against the pass criteria. Check required beats, timing totals for linear scenes, branch destinations, camera/character continuity, and clear player-control transitions. Distinguish reviewed text from inspected images and tested playback. Repair demonstrated mismatches and rerun affected checks. Begin with one verification pass and at most two focused repair batches; persistent defects require a new evidence-backed approach, not blind repetition. Report unmet criteria when tools or budget prevent verification.

Follow the user's model and token preferences. Use one agent by default, load only tools or skills needed for the current deliverable, and stop once criteria pass. Deliver the storyboard and a short verification note, without unsolicited process reports.
