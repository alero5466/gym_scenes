# Structure 2: Seedance 2.5 Prompt Template
## Subject + Action + Setting + Camera + Style + Audio (+ optional References)
> Instructions for the LLM: The user wants to generate a Seedance 2.5 video prompt. Seedance 2.5 supports single-pass generation up to 30 seconds, staged timeline blocks, multi-reference inputs (up to 30 images, 10 videos, 10 audio clips), and dedicated audio bracket syntax. Guide the user through each field one at a time. Only Subject and Action are strictly required — the other fields sharpen the result. Ask the user to pick a duration mode first (short single-shot 4-8s, or staged 10-30s) because staged prompts require timestamped blocks. If any required field is missing or unclear, do not proceed to the next one. Once all confirmed fields are filled, combine them into a single clean plain-text prompt ready to paste into Seedance 2.5 or any compatible AI video generator. No markdown, no headers, no field labels in the output.
---
## Step 0: Duration Mode
Before touching any field, ask the user which mode they want:
- **Short single-shot (4-8 seconds):** one continuous action, no timestamps needed. Prompt reads as one flowing paragraph.
- **Staged sequence (10-30 seconds):** multi-beat action, requires timestamped blocks on their own lines inside the Action field (e.g. `0-5s: …`, `5-15s: …`, `15-30s: …`). Each block should cover one clean beat.
> If the user leaves this blank: Ask them: "How long should this clip be? A short single-shot (4-8s, one continuous action) or a staged sequence (10-30s, multiple beats with timestamps)?"
User input: [DURATION_MODE]
---
## Realism defaults (always applied unless the user overrides)
Seedance 2.5 tends to over-perform facial effort and audible breathing, which reads as unnatural in most footage. Bake these defaults into every prompt automatically — mention them explicitly in the relevant fields — unless the user asks for the opposite (e.g. "he's mid-sprint, gasping"):
- **Facial expression:** natural, calm, and subtle. Micro-expressions only (soft focus, small eyebrow shift, subtle nod). No dramatic squinting, jaw clenching, gritted teeth, cheek-puffing, or grimacing. No visible strain unless the user explicitly asks for it.
- **Lip and jaw movement:** minimal and closed-mouth by default. Lips stay lightly closed or barely parted. No visible chewing, mouthing, or exaggerated jaw drop. The only exception is dialogue, where lip-sync should be natural and precise.
- **Breathing:** quiet and internal. No heavy inhales, no audible panting, no chest-heaving. If breath is mentioned in audio, wrap it as `<very quiet controlled nasal breathing barely audible in the background>` or omit entirely. No open-mouth breathing unless the user asks for it.
> When these defaults conflict with the requested action (e.g. a max-effort deadlift, sprint, or fight scene), ask the user: "This action would normally involve visible strain and heavier breathing. Do you want to keep the subtle-expression / quiet-breath default, or should I let the effort show?"
---
## The six fields
### Field 1: Subject
Describe exactly who or what is in the shot. Think about:
- Who is the main character or object (appearance, clothing, age, build, distinctive features)
- If a reference image is attached, name it here and describe what it shows
- Avoid vague descriptions like "a person" — be specific
- One primary subject only. Secondary elements belong in the Setting field.
> If the user leaves this blank: Ask them: "Who or what is the main subject of this shot? Describe them in as much detail as you can, or attach a reference image. Would you like me to suggest a subject based on what you have described so far?"
User input: [SUBJECT]
---
### Field 2: Action
Describe exactly what the subject is doing. Think about:
- **Short mode:** one single continuous action. No sequences.
- **Staged mode:** break the action into timestamped blocks, each block one clean beat, written as plain time ranges on their own lines:
  ```
  0-5s: The chef sets an empty plate on the counter and picks up a spoon.
  5-15s: Slow push in as sauce is drizzled across the plate in one line.
  15-30s: Close-up as a single microgreen is placed at center.
  ```
- Physical movement: direction, speed, body position, what triggers it, what results
- Keep each block to what happens in that window — no overflow between blocks
- **Facial expression default:** always describe it as natural, calm, and subtle with micro-expressions only. Explicitly say "no visible strain, no jaw clenching, no cheek-puffing, mouth lightly closed" unless the user asks for visible effort. See Realism defaults above.
> If the user leaves this blank: Ask them: "What is the subject doing? For short mode: one single action. For staged mode: give me the beats with rough timing and I'll format them as timestamped blocks. Or want me to suggest based on the subject and setting?"
User input: [ACTION]
---
### Field 3: Setting
Describe the full location and setting. Think about:
- Where the scene takes place (interior or exterior, specific location type)
- Time of day and weather conditions
- Surfaces, textures, and materials visible in the shot
- Background elements and depth
- Light sources (natural light, artificial, neon, fire, practical lights)
- Atmosphere (smoke, fog, dust, rain, heat haze)
- Any important foreground or background objects
> If the user leaves this blank: Ask them: "Where does this scene take place? Describe the location, time of day, weather, and any important background details. Or want me to suggest a setting that fits the subject and action?"
User input: [SETTING]
---
### Field 4: Camera
Describe the camera work as its own field (Seedance 2.5 splits this out from Style). Think about:
- Shot type (wide, medium, close-up, extreme close-up, POV, over-the-shoulder)
- Camera angle (eye level, low angle, high angle, overhead, Dutch tilt)
- Lens character (wide angle, telephoto, fish-eye, anamorphic, macro)
- Camera movement (static locked-off, slow push in, tracking, handheld, orbit, crane, snap zoom, gimbal glide)
- Framing continuity across staged blocks (does the camera move between beats or hold?)
> If the user leaves this blank: Ask them: "What shot type, angle, lens, and movement should this be? If it's staged, does the camera hold across beats or move between them?"
User input: [CAMERA]
---
### Field 5: Style
Describe the visual and technical character — everything except the camera itself. Think about:
- Film stock or digital look (35mm, 16mm, VHS, digital cinema, camcorder)
- Color grade and contrast (warm, cold, desaturated, high contrast, bleach bypass, teal-and-orange)
- Grain, texture, or visual artifacts
- Lighting quality (soft, hard, high-key, low-key, chiaroscuro)
- Any specific cinematographer, film, or era references
- Note: Do not use vague words like "cinematic" or "high quality" — describe the actual visual tone
> If the user leaves this blank: Ask them: "How should this look and feel — film stock, color grade, lighting quality, era or director reference? Or want me to suggest a style based on subject, action, setting, and camera?"
User input: [STYLE]
---
### Field 6: Audio
Describe exactly what we hear. Seedance 2.5 uses **explicit bracket syntax** to keep audio channels separated — use them so dialogue doesn't get drawn as captions and SFX aren't read aloud:
- `( … )` — **music** (genre, tempo, instruments, mood)
- `< … >` — **sound effects** (ambient and action-driven)
- `{ … }` — **spoken dialogue** (the actual line, in quotes if desired)
- `【 … 】` — **on-screen subtitles / captions** (only if the user explicitly wants text burned in)
Think about:
- Ambient sounds from the setting (rain, traffic, wind, crowd, machinery) → `< >`
- Sounds produced by the action (footsteps, impact, breathing, engine) → `< >`
- Music or score (genre, tempo, instruments, mood) → `( )`
- Dialogue if applicable → `{ }`
- Order and layering of sounds (what comes first, what builds, what fades)
- Be specific: `<footsteps on wet pavement>` beats `<walking sounds>`
- **Breathing default:** keep any breath sound quiet and internal. Default phrasing: `<very quiet controlled nasal breathing barely audible in the background>`. Never include heavy exhales, grunts, panting, or gasping unless the user explicitly asks for visible effort. See Realism defaults above.
> If the user leaves this blank: Ask them: "What do we hear? Ambient sounds, action sounds, any music or dialogue? I'll wrap each in the right brackets."
User input: [AUDIO]
---
### Optional Field 7: References
If the user is attaching reference files, assign each one an explicit job. Seedance 2.5 accepts up to **30 images, 10 videos, 10 audio clips** per generation, and coherence improves when every ref has a stated role. Formats:
- `Reference image 1: character face and wardrobe lock`
- `Reference image 2: environment / set design cue`
- `Reference video 1: motion direction for the pull-up phase`
- `Reference audio 1: voice timbre for the dialogue`
> If the user attaches references without labeling: Ask them: "What is each reference file's job? Character lock, environment cue, motion direction, or something else?"
User input: [REFERENCES]
---
### Optional Anchors: "What must not change"
Seedance 2.5 responds strongly to an explicit anchor line stating what stays fixed across the whole clip. State it *before* variable elements. Examples:
- "Maintain identical face, hair, and wardrobe from Reference image 1 for the entire clip."
- "Bar height, plate color, and floor material remain constant across all beats."
- "The red bicycle helmet stays in the left hand throughout."
> If the subject or setting has identity-critical details: Ask the user: "Is there anything that absolutely must not drift across the clip — face, wardrobe, prop, color, position? I'll add it as an anchor line."
User input: [ANCHORS]
---
## Validation checklist
Before generating the output, confirm each required field is filled and specific:
- [ ] Duration mode: Is it short single-shot or staged? If staged, does the Action field use timestamped blocks?
- [ ] Subject: Is there a clear, specific description of who or what is in the shot? (REQUIRED)
- [ ] Action: For short mode, one clean action? For staged mode, timestamped blocks that cover the full duration? (REQUIRED)
- [ ] Setting: Location, time of day, atmosphere, and light sources described?
- [ ] Camera: Shot type, angle, and movement stated? If staged, is camera continuity across beats clear?
- [ ] Style: Concrete visual tone described (not just "cinematic" or "professional")?
- [ ] Audio: At least one specific sound described, wrapped in the correct bracket type?
- [ ] References (if attached): Every ref has an assigned job?
- [ ] Anchors (if identity matters): The must-not-change list is stated before variable elements?
If any required field fails the check, ask the user to clarify before proceeding.
---
## Output format
Combine all fields into a single clean plain-text block. **No markdown, no field labels, no headers.** The final prompt should read as one production brief.
### Structure for short single-shot mode
One flowing paragraph: `[SUBJECT]. [ACTION]. [SETTING]. [CAMERA]. [STYLE]. [AUDIO with brackets].` Anchors line first if used.
### Structure for staged mode
Anchors first, then references (if any), then the staged action as timestamped blocks on their own lines, then Setting / Camera / Style as continuing paragraph, then Audio last with brackets:
```
Maintain identical face and wardrobe from Reference image 1 throughout. Reference image 1: character lock.

[SUBJECT paragraph]

0-5s: [action beat one]
5-15s: [action beat two]
15-30s: [action beat three]

[SETTING paragraph]. [CAMERA paragraph]. [STYLE paragraph].

<ambient sfx>, <action sfx>, (music description), {dialogue if any}.
```
---
## Example outputs
### Short single-shot example (6 seconds)
A teenager in a bright neon jacket and vintage sneakers. Skateboarding fast past an old 80s mall storefront, board wheels catching the pavement. 1980s suburban strip in golden hour, parked cars along the curb, heat shimmer rising off the asphalt. Extreme low-angle tracking shot from a handheld camcorder gliding alongside at wheel height, fish-eye lens. Heavy 35mm grain, warm golden hour color grade with amber highlights and deep magenta shadows. <skateboard wheels rolling on pavement>, <distant traffic hum>, (synthwave arpeggio at 110 bpm building over the shot).
### Staged 30-second example
Maintain identical face, wardrobe, and the red bicycle helmet in the left hand from Reference image 1 for the entire clip. Reference image 1: character and prop lock. Reference video 1: motion reference for the messenger's stride.

A bike messenger in a yellow rain jacket carrying one red bicycle helmet in the left hand.

0-5s: The bell above the door rings as the messenger enters a small NYC bodega, closes the glass door with the right hand, and shakes rain from the shoulders.
5-15s: Camera follows from behind at chest height as the messenger walks to the drink cooler, opens it with the right hand, removes one clear bottle of seltzer, and closes the door.
15-25s: The messenger walks to the counter, sets the bottle down, and hands cash to the clerk with the right hand.
25-30s: Close-up on the messenger's face as they nod thanks, turn, and step back toward the door.

Interior of a small New York City bodega on a rainy morning, warm tungsten overhead lights, wet linoleum floor, colorful snack shelves, condensation on the cooler glass, gentle rain visible through the front windows. Handheld gimbal shot, medium framing throughout, following behind then arcing to a close-up on the final beat, 35mm equivalent lens, shallow depth of field. Naturalistic digital cinema look, warm interior tungsten balanced against cool blue rain-light from the window, subtle film grain, muted saturation.

<door bell chime at 0s>, <rain shaking off jacket at 3s>, <cooler door thud at 8s>, <bottle setting on counter at 17s>, <ambient rain and refrigerator hum throughout>, (soft lo-fi jazz playing quietly from a radio at the counter), {"Thanks, have a good one," clerk says at 26s}.
---
## Notes for the LLM
- Only Subject and Action are strictly required. The other fields sharpen output but the prompt will still run without them.
- For clips over 8 seconds, always use staged mode with timestamped blocks.
- Every action beat within a staged prompt should be one clean, unambiguous event — timestamps do the sequencing work that a single paragraph cannot.
- Always wrap audio in the correct bracket type. Never use plain descriptions like "footsteps" without `< >` — the model needs the bracket to route it correctly.
- Anchors should be stated once at the top of the prompt, not repeated inside each beat.
- If the user attaches multiple references, assign each an explicit role. Coherence degrades sharply when references have no stated job.
- If the same character or setting appears across several generations, reuse the exact same description verbatim rather than rewording it — Seedance 2.5 rewards description reuse for cross-clip consistency.
- **Always apply the Realism defaults** (subtle facial expression, minimal jaw/lip movement, quiet internal breathing) in every prompt unless the user explicitly asks for visible effort. Weave these into both the Action field's expression description and the Audio field's breath description on every generation — they should not need to be re-requested each turn. Add them to the Anchors block too when identity locking is used.
- After outputting the prompt, ask: "Would you like to adjust anything before using this?"
