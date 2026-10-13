# Generate → Verify → Repair for motion

Adapted from the example supplied by the user, credited there to @shmidtdq and ideas attributed to Andrej Karpathy. This is a local working guide, not a verified quotation or endorsement. The example's timing numbers are optional design starting points, not universal constraints.

## Define the target

Record the target renderer, viewport, frame rate where relevant, moving elements, and observable pass criteria. For each meaningful beat, record start, duration, easing, overlap/stagger, travel, allowed overshoot, and resting state. Set tolerances before measuring. Use the user's brief and existing design system; do not impose arbitrary duration ratios or a fixed stagger ceiling.

Follow the user's chosen approval checkpoints. Otherwise proceed with authorized reversible work without adding a new approval gate. Keep GPT-6.1 Sol low for routine work and Astra low for difficult reasoning under LOW_TOKEN_RULES.md.

## Generate

Implement one independently checkable beat or short sequence. Keep animation state repeatable from time and input where practical. Preserve the existing architecture and use the renderer's supported timing APIs. Avoid unrelated elements, speculative effects, and refactoring for its own sake.

## Verify

- Drive the real animation with available, supported tools. Use a deterministic clock or timeline seek when supported; otherwise record playback and measure actual timestamps.
- Inspect start, transition boundaries, peak overshoot, and resting frames. Check timing, continuity, unintended simultaneous starts, order, displacement, clipping, and final state against the beat table.
- Capture a labeled contact sheet when comparing several beats. For a frame-exact brief, capture the requested frame sequence and compare within the predefined tolerance. Screenshots alone do not prove event handling or frame-rate performance.
- Respect reduced-motion preferences. Reduce or remove nonessential movement, retain meaning and interaction feedback, and test the resulting state. Do not force a cross-fade if no animation is appropriate.
- Report mismatches with expected and observed values. Do not substitute “looks smooth” for measurement or claim a visual check when only source code was inspected.

## Repair and finish

Change the smallest responsible part, usually timing/easing values. If the evidence identifies a structural bug, fix the structure rather than repeatedly tuning numbers. Rerun the affected frames and relevant interaction checks.

Start with one verification pass and up to two focused repair batches. If the same defect survives, reassess the cause. Continue only with a new evidence-backed approach within the agreed budget; report blockers or unmet criteria honestly. Stop once the criteria pass, without extra polish loops.

Deliver the working artifact and concise verification evidence. Include the beat table/contact sheet when useful or requested. Keep a repair log only for substantial or unattended work. Apply the same loop to code using behavior tests and to data analysis using source reconciliation and numerical checks; do not introduce a motion workflow for those tasks.
