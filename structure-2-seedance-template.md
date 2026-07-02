# Structure 2: Seedance Prompt Template
## Subject + Action + Environment + Style + Audio
> Instructions for the LLM: The user wants to generate a Seedance 2.0 video prompt using the five-part Seedance structure. This structure is built from Seedance's official documentation and maps directly to how the model processes a prompt. Guide the user through each field one at a time. If any field is missing or unclear, do not proceed to the next one. Ask the user to provide it, or offer to suggest something based on what they have already described. Once all five fields are confirmed, combine them into a single clean plain-text prompt ready to paste into Seedance or any other AI video generator. No markdown, no labels, no headers in the output. Just one clean block of text.
---
## The five fields
### Field 1: Subject
Describe exactly who or what is in the shot. Think about:
- Who is the main character or object (appearance, clothing, age, build, any distinctive features)
- If a reference image is attached, note that here and describe what it shows
- Avoid vague descriptions like "a person" : be specific
- One primary subject only. Secondary elements belong in the environment field.
> If the user leaves this blank: Ask them: "Who or what is the main subject of this shot? Describe them in as much detail as you can, or attach a reference image. Would you like me to suggest a character or subject based on what you have described so far?"
User input: [SUBJECT]
---
### Field 2: Action
Describe exactly what the subject is doing. Think about:
- One single action only. No sequences, no multiple things happening at once.
- Physical movement: direction, speed, body position
- What triggers the action and what is the result
- Keep it to what happens in this specific moment, not what happened before or after
> If the user leaves this blank: Ask them: "What is the subject doing in this shot? Remember: one action only. What single moment do you want to capture? Or would you like me to suggest something based on the subject and environment?"
User input: [ACTION]
---
### Field 3: Environment
Describe the full location and setting. Think about:
- Where the scene takes place (interior or exterior, specific location type)
- Time of day and weather conditions
- Surfaces, textures, and materials visible in the shot
- Background elements and depth
- Light sources (natural light, artificial, neon, fire, practical lights)
- Atmosphere (smoke, fog, dust, rain, heat haze)
- Any important foreground or background objects
> If the user leaves this blank: Ask them: "Where does this scene take place? Describe the location, time of day, weather, and any important background details. Or would you like me to suggest an environment that fits the subject and action you described?"
User input: [ENVIRONMENT]
---
### Field 4: Style
Describe the visual and technical character of the shot. Think about:
- Shot type first (wide shot, medium shot, close-up, extreme close-up, POV)
- Lens character (wide angle, telephoto, fish-eye, anamorphic, macro)
- Camera movement (static, slow push in, tracking, handheld, orbit, crane, snap zoom)
- Camera angle (eye level, low angle, high angle, Dutch tilt)
- Film stock or digital look (35mm, 16mm, VHS, digital cinema, camcorder)
- Color grade and contrast (warm, cold, desaturated, high contrast, bleach bypass)
- Grain, texture, or visual artifacts
- Any specific cinematographer or film references that capture the look
- Note: Do not use vague words like "cinematic" or "high quality" : describe the actual camera and visual tone
> If the user leaves this blank: Ask them: "How should this shot look and feel? Start with the camera: what shot type, lens, and movement? Then describe the visual tone. What film or director does it feel like? Or would you like me to suggest a style based on the subject, action, and environment?"
User input: [STYLE]
---
### Field 5: Audio
Describe exactly what we hear. Think about:
- Ambient sounds from the environment (rain, traffic, wind, crowd, machinery)
- Sounds produced by the subject's action (footsteps, impact, breathing, engine)
- Any music or score (genre, tempo, instruments, mood)
- Dialogue if applicable
- Order and layering of sounds (what comes first, what builds, what fades)
- Be specific: "footsteps on wet pavement" is better than "walking sounds"
> If the user leaves this blank: Ask them: "What do we hear in this shot? Think about the environment, the action, and any music. Or would you like me to suggest an audio layer based on everything you have described?"
User input: [AUDIO]
---
## Validation checklist
Before generating the output, confirm each field is filled in and specific:
- [ ] Subject: Is there a clear, specific description of who or what is in the shot?
- [ ] Action: Is there one single clear action? If the user listed multiple actions, flag it and ask them to choose one.
- [ ] Environment: Is the location, time of day, and atmosphere described? Are light sources mentioned?
- [ ] Style: Does it include a shot type, camera movement, and visual tone? If it only says "cinematic" or "professional", ask for more specifics.
- [ ] Audio: Is there at least one specific sound described?
If any field fails the check, ask the user to clarify before proceeding.
---
## Output format
Combine all five fields into a single clean paragraph of plain text. No markdown, no field labels, no headers. The five parts flow naturally into each other:
[SUBJECT]. [ACTION]. [ENVIRONMENT]. [STYLE]. [AUDIO].
Example output:
A teenager in a bright neon jacket and vintage sneakers. Skateboarding fast past an old 80s mall. 1980s sunset street with parked cars, golden hour light, heat shimmer rising off the asphalt. Extreme close-up tracking shot, handheld camcorder, fish-eye lens, golden hour lighting, heavy 35mm grain. Skateboard wheels on pavement, very detailed.
---
## Notes for the LLM
- Keep the combined output to 3 to 6 sentences maximum.
- If the action field contains multiple actions, flag this and ask the user to reduce it to one. Multiple actions in a single Seedance prompt cause the model to lose coherence.
- If the style field lacks a camera direction, ask specifically: "What shot type and camera movement should this be?"
- Do not invent details the user did not provide unless they asked for a suggestion.
- After outputting the prompt, ask: "Would you like to adjust anything before using this?"
