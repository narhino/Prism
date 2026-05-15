# Scene format

Output one block per scene. The narration text comes FIRST, then the prompt to draw that scene comes BELOW it.

Each scene block:

```
---
**SCENE N — m:ss to m:ss**

[Narration text, verbatim from the script, 1–3 sentences]

**Prompt:**
[A single self-contained description of what is drawn on the whiteboard for this scene. Pure observation: a person, an object, a map, a chart, a label. No style notes — no mentions of color, palette, marker, line weight, animation, camera moves, software, or transitions. The user handles style separately.]
---
```

## Rules

1. **One scene = one drawn image.** No animation. The channel works by drawing each scene on a whiteboard, holding it, then moving to the next.
2. **One image per narration moment.** Each ~10–25 seconds of narration gets its own scene.
3. **Two places in one scene is allowed when the narration flows that way.** Example: "A factory in Germany. A power plant in India." can be one scene with both places drawn side-by-side. Keep the flow over a rigid one-subject-per-scene rule.
4. **Recurring characters get canonical descriptions.** When the same person appears across multiple scenes, write the canonical description once in a "Character library" section at the top of the file, then paste that exact description into every scene's prompt that includes them. The image generator has no memory across prompts.
5. **Prompts must be self-contained.** Each prompt should make sense to an image generator that has never seen the previous prompts. Repeat character descriptions, repeat key labels.
6. **No style notes in prompts.** Do not write "white line on dark charcoal" or "marker on whiteboard" or color references. The user applies style separately at generation time.
7. **Describe WHAT, not HOW.** No camera moves, no software references, no transition descriptions.

## Top-of-file character library

Begin every `05-scenes.md` with a Character library section listing each recurring character (someone in 2+ scenes). Format:

```
## Character library

**[Character name]:** [canonical description, 1–2 sentences — physical build, age range, clothing, hair, distinctive features. No facial expression — that gets specified per scene.]

**[Next character]:** [...]
```

When that character appears in a scene, paste the canonical description into the scene's prompt verbatim, then add scene-specific action and expression.
