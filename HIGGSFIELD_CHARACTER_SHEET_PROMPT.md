# Higgsfield Character Sheet Prompt — Authentic Self

Built from the user's own reference photo (shirtless standing shot in the home gym rack). Follows Higgsfield's `character-sheet` workflow: split-screen composition, `photoreal-unretouched` preset, slot-by-slot, anti-AI realism engine, mature adult structure, and the hard framing negatives that stop split-screen breakage.

Attach the reference photo when you generate so identity locks. Aspect ratio: **16:9** (split-screen). Recommended: try Seedream / Nano-Banana / SD-family photoreal models; if unsure, call `models_explore(action:"recommend")`.

---

## Copy-paste prompt (photoreal, split-screen)

Split-screen character sheet composition, left side a full-body shot of the character standing upright in a neutral straight standing pose facing the camera with both feet flat on the ground and arms relaxed at the sides, full head-to-toe framing with the whole body and both feet visible, right side a tight close-up chest-up portrait of the same character, identical original male character on both sides with the exact same face, hair, beard, body, and wardrobe carried across both panels, pure white seamless studio background, professional character sheet presentation, adult man in his mid-forties, fair-to-light olive Mediterranean skin with warm undertones and a natural sun-touched tan across the chest and shoulders, mature masculine face with defined angular structure, a strong straight jawline with visible bone edge along the mandible, high flat cheekbones, slightly hollow lower cheeks, mid-length straight nose with a subtly defined bridge and narrow tip, thin-to-medium lips with a natural muted rosy tone and a soft matte finish, mature adult facial proportions with longer facial thirds and a defined chin, warm hazel-brown deep-set eyes with a slight almond tilt and naturally muted catchlights, no oversized specular glare in the iris, eye color muted rather than glowing, dark eyebrows lightly threaded with silver and a natural arch, short salt-and-pepper hair predominantly silver-gray with darker charcoal roots, cropped short and tight on the sides and back with a slightly longer textured spiky top styled naturally up and slightly forward with a matte finish and no product shine, short well-groomed salt-and-pepper stubble beard mostly silver-gray with a darker mustache area following the jawline and chin cleanly, faint natural crow's-feet at the outer corners of the eyes and subtle forehead expression lines consistent with a man in his forties, visible fine skin texture with natural pores, subtle asymmetries and texture irregularities, faint sun freckles across the shoulders and upper chest, no digital smoothing, no beauty filter, no AI-airbrushed look, skin completely free of artificial glare, shine or highlight blooms, matte-to-natural complexion, lean athletic middle-aged runner-and-lifter physique, moderate defined musculature that reads natural rather than bodybuilder, visible upper chest separation, clearly defined but not exaggerated four-pack abs with a visible linea alba, defined serratus and oblique lines, lean forearms and calves, narrow waist with balanced shoulder-to-hip proportions, approximately average adult male height with slim-athletic build, wearing a fitted matte black athletic shorts sitting at the natural waist with a mid-thigh inseam and a subtle elastic drawstring waistband in a lightweight technical fabric, no shirt, low-profile black athletic training sneakers with a thin sole and minimal branding, a thin delicate gold chain necklace resting flat against the collarbone, a black rectangular smartwatch on the left wrist with a black sport band, a slim fitness tracker band on the right wrist with a small dark green sensor face, no bag, natural anatomy, high-end but unretouched commercial photography style, soft diffused studio lighting without harsh reflections, even soft key from the front with gentle fill so the physique reads without dramatic shadow, cinematic realism, clean white background, 4K quality, sharp focus on skin texture and beard detail, single subject only, exactly one person, only the character in frame, no other people, no duplicate figures, no mannequin, no reflections, no props, no furniture, no background objects, empty seamless studio, left panel standing full-body head-to-toe not cropped not sitting, right panel tight chest-up close-up not full body, no babyface, no overly youthful rounded proportions, no beauty filter, no digital smoothing, no airbrushing, no plastic skin, no glossy skin, no oiled bodybuilder shine, no exaggerated muscle mass, no fake tan, no gym equipment, no text, no watermark, no logos, no frame borders.

---

## What each block does (so you can tweak safely)

- **Composition clause** — locks split-screen: left = standing head-to-toe, right = chest-up close-up. Do not remove; this is the piece that breaks most.
- **Identity (age + heritage + skin)** — mid-forties, olive Mediterranean, sun-touched. Swap age band or heritage if you want a different read.
- **Face** — angular jaw, high flat cheekbones, straight nose, thin-medium lips. The "mature adult structure" clause is what stops Higgsfield from softening you into a babyface — keep it.
- **Eyes + anti-glare clause** — muted catchlights, no glowing iris. Required for photoreal.
- **Hair + beard** — salt-and-pepper, short sides, textured spiky top, matte finish; groomed silver stubble. Change length/style here to try variations.
- **Skin / anti-AI realism engine** — the whole "kills the plastic look" block: pores, asymmetry, no airbrushing, matte-to-natural. Do not soften.
- **Body** — lean athletic, moderate definition, four-pack, natural proportions. If you want a fuller/leaner read, adjust this line and the negative "no exaggerated muscle mass".
- **Wardrobe** — black shorts, no shirt, low-profile black sneakers, thin gold chain, Apple-Watch-style black smartwatch on left, green-faced fitness tracker on right. Swap wardrobe here.
- **Lighting + quality tail** — soft diffused studio, matte, 4K, sharp on texture.
- **Negative tail** — the hard framing rules + adult-structure + photoreal negatives + no gym equipment (since the sheet is on white, not on your rack).

---

## Variations you may want

- **Turnaround model sheet** (front / 3/4 / side / back, all standing): replace the composition clause with
  `Character turnaround model sheet, four consistent full-body views in a row — front view, 3/4 view, side profile, and back view, evenly spaced,` and remove the "right panel tight chest-up" negative.
- **Expression sheet** (one full-body + grid of head-and-shoulders portraits with different expressions):
  `Character expression sheet, one full-body reference on the left and a grid of head-and-shoulders portraits on the right showing varied expressions (neutral, smiling, serious, focused, mid-lift grimace),`
- **Wardrobe sheet** (same face, multiple gym fits): keep identity + face + hair + beard + skin blocks verbatim, swap composition clause to
  `Character wardrobe sheet, the same character shown full-body in four different athletic outfits side by side,` and replace the wardrobe slot with the four outfits.
- **Shirt on** — replace the "no shirt" line with a specific top, e.g. `fitted charcoal heather short-sleeve technical training tee with a crew neck and a subtle moisture-wicking texture,`

---

## Generation call (when you're ready)

Send the prompt above to `generate_image` with aspect ratio `16:9`, and attach the reference photo as a character reference so the face locks to yours (this is what makes it *authentically you* rather than a generic mid-forties athlete). Ask explicitly to generate — I won't run it without your say-so.
