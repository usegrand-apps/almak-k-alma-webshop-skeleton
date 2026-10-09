You are an expert Frontend UI/UX Engineer and AI Coding Assistant. Your objective is to build the user interface exactly as described in the <ui_frames> section below.

<global_context>
Koncepció: Almakék, friss étkezési almák webshopja. Magyar nyelv, HUF. 1440 px desktop, 1200 px tartalomszélesség, 390 px mobil. Fehér és jégkék felületek, királykék CTA, sötét tintakék tipográfia, természetes piros/zöld almák. Sok üres tér, nagy szerkesztőségi címsor, vékony elválasztók. A termékárak illusztratív minták. Nincsenek igazolatlan bio/minősítési vagy szállítási állítások.
</global_context>

<design_tokens>
Colors: background: #F7FAFF, surface: #FFFFFF, ice: #EAF2FF, primary: #245DE8, ink: #12284C, muted: #526581, border: #DCE5F2
Spacing: unit: 8, section: 96, container: 1200
</design_tokens>

<system_instructions>
Csak a specifikált szekciók és pontos magyar szövegek kerüljenek a felületre. Ne használj Apple elektronikai termékeket vagy Apple-logót: az alma gyümölcs. Nincsenek kitalált vélemények, értékelések, kedvezmények vagy tanúsítványok. Reszponzív: 768 px alatt egyoszlopos hero és terméklista, 20 px oldalmargó, minimum 44 px érintési célok, látható fókusz és reduced-motion támogatás. Termékképek természetes almák semleges világos háttéren; a képek beszerzendő assetek, ne találj ki URL-eket.
</system_instructions>

<mandatory_constraints>
CRITICAL: You MUST strictly adhere to the following constraints. Violating any of these rules is considered a failure.
- MUST ALWAYS ensure that all components and layouts are fully responsive. They must adapt gracefully to different screen sizes, providing an optimal user experience on mobile, tablet, and desktop viewports.
- CRITICAL: STRICT SCOPE ADHERENCE. You MUST ONLY generate the UI elements explicitly listed in the <ui_frames> section. DO NOT hallucinate, assume, or add ANY supplementary components, decorative sections, cards, sidebars, or layout blocks (e.g., "features", "testimonials", "lookbooks", "galleries") unless they are explicitly defined as a block within a frame. If a frame only has a heading, subheading, and CTA, your output MUST ONLY contain those three elements and nothing else.
- CRITICAL: NO CREATIVE BLOAT. Do not include unnecessary tilts (rotations), badges, icons, or emojis unless they are explicitly mentioned in the specific frame's block prompts. Maintain a clean, professional execution of the requested structure without 'filling' empty space with unrequested UI elements.
- CRITICAL: NO EMOJI HALLUCINATION. If a screenshot or reference shows an image placeholder (e.g., a broken image icon with alt text, or a generic placeholder shape), you MUST reproduce it as an <img> tag with the corresponding alt text. DO NOT invent, assume, or substitute an emoji or icon to fill that space unless one is clearly visible in the reference or explicitly requested in the prompt.
- CRITICAL: SHAPE IMPLEMENTATION. If shapes (e.g., circles, polygons, abstract decorative paths) are not explicitly mentioned in the instructions, global context, or frame/block prompts, they MUST NOT be implemented.
- CRITICAL: AVOID AI SLOP (VISUAL & COPY). Do NOT use overused AI buzzwords (e.g., "Elevate", "Unleash", "Seamless", "Next-generation", "Synergy", "Empower") in your generated text; use direct, practical, and grounded language. Visually, do NOT add generic "AI" decorations like abstract blurred glowing blobs, random floating geometric elements, or unprompted particle backgrounds. The UI must remain highly intentional, clean, and professional.
</mandatory_constraints>

<design_philosophy>
These are POSITIVE design standards. Apply them unconditionally unless overridden by the visual_profile or a specific ContentSpec.

## TYPOGRAPHY HIERARCHY
- Every section must have exactly ONE typographic focal point. Pick the most important text element and make it clearly dominant.
- Use at least 3 distinct type sizes per page section: a headline, a subhead or label, and body text. Never set all text at the same size.
- Vary font-weight meaningfully: do not use a single weight throughout. Pair weight 700 headlines with weight 400 body text at minimum.
- Apply negative letter-spacing (-0.02em to -0.05em) on all display text above 40px. Tight tracking reads as quality and intentionality.
- Line-height: 0.9–1.1 on display/hero text; 1.5–1.7 on body text. Never use default line-height (1) on large headings.
- Max headline length: 8 words on desktop, 5 words on mobile. If the headline is longer, it must be broken with an intentional line break to control the rag.

## SPACING AND RHYTHM
- Whitespace is a design element, not an absence of design. When in doubt, add more vertical padding to sections.
- Use an 8px base grid: all spacing values (padding, margin, gap) must be multiples of 8 (8, 16, 24, 32, 48, 64, 96, 128).
- Asymmetry signals intent. Prefer unequal column widths (e.g., 5/7 split) over exact 50/50 splits where the design allows.
- Internal component spacing must be tighter than inter-component spacing. A button's internal padding should be smaller than the gap between the button and its neighboring element.

## COLOR DISCIPLINE
- Neutral-first: page background, surfaces, and text colors should be neutral. Color accent is reserved for maximum 2 roles: the primary interactive color (buttons, links) and an optional brand accent.
- Never use more than 2 named brand colors in a single section.
- Do NOT use gradients on text or as section backgrounds unless they are extracted from the design_tokens. Gradients are earned, not assumed.
- Surface hierarchy: use color or shadow to create depth between layers (background → surface → elevated surface). A minimum of 2 distinct surface levels must exist.

## VISUAL HIERARCHY PER SECTION
- Every section has exactly one focal point. The focal point must be immediately obvious at a glance — largest, boldest, or most visually distinct element.
- All other elements in the section radiate from the focal point in decreasing visual weight.
- Avoid visual ties: never size two elements the same when one is semantically more important than the other.

## INTERACTION QUALITY
- EVERY interactive element (button, link, input, card) MUST have a visible hover state. Default browser hover states are not acceptable.
- Hover states must communicate affordance: a button that changes background color on hover signals it is clickable. A card that lifts (shadow increase) signals it is navigable.
- Focus-visible states are REQUIRED on all interactive elements for keyboard accessibility. Use a 2px ring offset from the element, in the accent color.
- All transitions must have timing: use transition-duration of 150–200ms with ease-out easing as the default.

## ANTI-SLOP LAYOUT PATTERNS (FORBIDDEN DEFAULTS)
The following layout compositions are BANNED unless explicitly specified in a frame block:
- BANNED: "Centered hero on gradient background with a large headline, short subtext, and two CTA buttons below." Use left-aligned layouts, real backgrounds, or image backdrops instead.
- BANNED: "Three equal-width columns with an icon at the top, bold title, and two-line paragraph." Use unequal columns, list-based layouts, or single-column with strong dividers instead.
- BANNED: "White cards with drop shadow on a light gray (#F5F5F5 or #F9F9F9) background with identical internal structure." Use borders instead of shadows, vary card heights, or use no cards at all.
- BANNED: "Full-width section with centered headline, centered two-line subtext, centered CTA button, then a content grid below." Break this generic SaaS template at every step.
- BANNED: "Pricing table with three plans where the middle one is highlighted." Use real pricing, real feature names, and an intentional layout that fits the product.
- BANNED: Generic testimonial carousels with circular avatar, star rating, quote, and name. Use pull-quotes, case studies, or conversation-format testimonials instead.

## COPY QUALITY STANDARDS
- SPECIFIC beats VAGUE: "Deploys to 30 global regions" beats "Deploy anywhere, anytime". Every claim must be concretely anchored.
- ACTIVE VOICE: Subject performs the action. "Your team ships 3x faster" not "3x faster shipping is enabled for your team".
- NUMBERS OVER ABSTRACTIONS: Cite actual numbers, timeframes, or quantities. "Loads in under 200ms" beats "lightning fast".
- HEADLINE = ONE CLAIM: A headline makes one clear claim. It does not try to cover everything.
- CTA TEXT: Action verbs only. "Start building", "See the demo", "Get early access". Never "Learn more" or "Click here".
</design_philosophy>

<visual_profile>
Apply these visual profile specifications. They take precedence over design_philosophy defaults where they conflict.
AESTHETIC: Minimal — maximum whitespace, single accent color, no decorative elements whatsoever.
Use a neutral base (white or very light gray surface, near-black text).
Remove all drop shadows; use 1px borders at 10% opacity instead.
Zero decorative icons, badges, or illustration unless explicitly in the frame spec.
DENSITY: Sparse — section vertical padding 120–200px; internal component gaps 24–32px; let content breathe.
CORNER RADIUS: Rounded — border-radius 8–12px on cards, 6–8px on buttons and inputs.
SHADOWS: None — use 1px borders for surface separation instead of drop shadows.
ANIMATION: Subtle — transitions at 150–200ms ease-out; hover states use background-color and box-shadow changes; no scale or translate transforms.
COPY VOICE: Friendly — second person (you/your); contractions allowed; conversational; short sentences; exclamation point max once per page.
</visual_profile>

<ui_frames>
# 01 — Navigáció [order: 0]

- **Almakék márkajel** [x: 120, y: 28, order: 0]
  - **Type:** default
  - **Prompt:** Szöveges logó: Almakék. 28 px semibold, tintakék. Kis egyszerű körvonalas gyümölcsalma jel; ne Apple-logó.
  - **Exact Copy:** Almakék
  - **Forbidden Patterns:** Apple márkajel
  - **Interaction States Required:**
    - Visszagörget az oldal tetejére.
- **Almáink** [x: 560, y: 24, order: 1]
  - **Type:** default
  - **Prompt:** Görgetés az almaválogatáshoz.
  - **Exact Copy:** Almáink
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** Görgetés az almaválogatáshoz.
- **Válogatásdoboz** [x: 688, y: 24, order: 2]
  - **Type:** default
  - **Prompt:** Görgetés a dobozajánlathoz.
  - **Exact Copy:** Válogatásdoboz
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** Görgetés a dobozajánlathoz.
- **Kosár** [x: 1176, y: 24, order: 3]
  - **Type:** default
  - **Prompt:** Körvonalas kék gomb; kosárpanel megnyitása. Dinamikus darabszám. Mobilon a két középső link elrejtve.
  - **Exact Copy:** Kosár (0)
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** Körvonalas kék gomb; kosárpanel megnyitása. Dinamikus darabszám. Mobilon a két középső link elrejtve.

# 02 — Nyitó szekció [order: 1]

- **Bevezető** [x: 120, y: 80, order: 0]
  - **Type:** default
  - **Prompt:** 12 px nagybetű, 0.14em betűköz, kék.
  - **Exact Copy:** EGYSZERŰEN ALMA.
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** 12 px nagybetű, 0.14em betűköz, kék.
- **Főcím** [x: 120, y: 128, order: 1]
  - **Type:** default
  - **Prompt:** H1 80/84 px, -0.05em; mobilon 48/52 px.
  - **Exact Copy:** Egy harapásnyi
jókedv.
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** H1 80/84 px, -0.05em; mobilon 48/52 px.
- **Hero leírás** [x: 120, y: 360, order: 2]
  - **Type:** default
  - **Prompt:** 18/28 px halvány tintakék.
  - **Exact Copy:** Ropogós kedvencek a mindennapokra.
Válassz almát ízlésed szerint.
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** 18/28 px halvány tintakék.
- **Vásárlás CTA** [x: 120, y: 464, order: 3]
  - **Type:** default
  - **Prompt:** Tömör királykék, fehér felirat; termékrácshoz görget.
  - **Exact Copy:** Megnézem az almákat
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** Tömör királykék, fehér felirat; termékrácshoz görget.
- **Hero almafotó** [x: 744, y: 48, order: 4]
  - **Type:** default
  - **Prompt:** Nagy természetes piros és zöld almák csendéletben, matt jégkék talajon; enyhe valódi árnyék, levegős kép. Alt: Piros és zöld almák világoskék háttéren. Mobilon szöveg alatt 350×340. Nem generikus ikon vagy emoji.
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** Nagy természetes piros és zöld almák csendéletben, matt jégkék talajon; enyhe valódi árnyék, levegős kép. Alt: Piros és zöld almák világoskék háttéren. Mobilon szöveg alatt 350×340. Nem generikus ikon vagy emoji.

# 03 — Almaválogatás [order: 2]

- **Választék cím** [x: 120, y: 56, order: 0]
  - **Type:** default
  - **Prompt:** H2 40/48 px.
  - **Exact Copy:** Találd meg a kedvenced.
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** H2 40/48 px.
- **Választék leírás** [x: 120, y: 128, order: 1]
  - **Type:** default
  - **Prompt:** 18 px.
  - **Exact Copy:** Édes, savanykás vagy valahol a kettő között.
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** 18 px.
- **Íz szűrő** [x: 1040, y: 112, order: 2]
  - **Type:** default
  - **Prompt:** Opciók: Minden íz; Édes; Savanykás. Kliensoldali szűrés, üres állapot: Nincs ilyen alma a válogatásban.
  - **Exact Copy:** Minden íz
  - **Forbidden Patterns:** Nem specifikált szöveg vagy extra díszítés, Lila gradiens, Kitalált értékelések
  - **Layout Hint:** Opciók: Minden íz; Édes; Savanykás. Kliensoldali szűrés, üres állapot: Nincs ilyen alma a válogatásban.
- **Gala fotó** [x: 120, y: 208, order: 3]
  - **Type:** default
  - **Prompt:** Piros-sárga Gala almák fehér stúdióháttéren. 12 px sarok, körülötte sok levegő. Alt: Piros-sárga Gala almák.
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** Piros-sárga Gala almák fehér stúdióháttéren. 12 px sarok, körülötte sok levegő. Alt: Piros-sárga Gala almák.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Gala név** [x: 120, y: 504, order: 4]
  - **Type:** default
  - **Prompt:** H3 24 px tintakék.
  - **Exact Copy:** Gala
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** H3 24 px tintakék.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Gala íz** [x: 120, y: 544, order: 5]
  - **Type:** default
  - **Prompt:** 14 px másodlagos szöveg.
  - **Exact Copy:** Édes · lédús
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 14 px másodlagos szöveg.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Gala ár** [x: 120, y: 592, order: 6]
  - **Type:** default
  - **Prompt:** 22 px semibold. Illusztratív mintaár.
  - **Exact Copy:** 890 Ft / kg
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 22 px semibold. Illusztratív mintaár.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Gala kosárgomb** [x: 120, y: 648, order: 7]
  - **Type:** default
  - **Prompt:** 1 kg Gala hozzáadása a kosárhoz; ismétlés növeli a mennyiséget. Kék szegélyes gomb, hover halványkék háttér, siker aria-live: A kosárba került.
  - **Exact Copy:** Kosárba · 1 kg
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 1 kg Gala hozzáadása a kosárhoz; ismétlés növeli a mennyiséget. Kék szegélyes gomb, hover halványkék háttér, siker aria-live: A kosárba került.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Granny Smith fotó** [x: 528, y: 208, order: 8]
  - **Type:** default
  - **Prompt:** Élénkzöld Granny Smith almák fehér stúdióháttéren. 12 px sarok, körülötte sok levegő. Alt: Élénkzöld Granny Smith almák.
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** Élénkzöld Granny Smith almák fehér stúdióháttéren. 12 px sarok, körülötte sok levegő. Alt: Élénkzöld Granny Smith almák.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Granny Smith név** [x: 528, y: 504, order: 9]
  - **Type:** default
  - **Prompt:** H3 24 px tintakék.
  - **Exact Copy:** Granny Smith
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** H3 24 px tintakék.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Granny Smith íz** [x: 528, y: 544, order: 10]
  - **Type:** default
  - **Prompt:** 14 px másodlagos szöveg.
  - **Exact Copy:** Savanykás · roppanós
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 14 px másodlagos szöveg.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Granny Smith ár** [x: 528, y: 592, order: 11]
  - **Type:** default
  - **Prompt:** 22 px semibold. Illusztratív mintaár.
  - **Exact Copy:** 990 Ft / kg
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 22 px semibold. Illusztratív mintaár.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Granny Smith kosárgomb** [x: 528, y: 648, order: 12]
  - **Type:** default
  - **Prompt:** 1 kg Granny Smith hozzáadása a kosárhoz; ismétlés növeli a mennyiséget. Kék szegélyes gomb, hover halványkék háttér, siker aria-live: A kosárba került.
  - **Exact Copy:** Kosárba · 1 kg
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 1 kg Granny Smith hozzáadása a kosárhoz; ismétlés növeli a mennyiséget. Kék szegélyes gomb, hover halványkék háttér, siker aria-live: A kosárba került.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Golden Delicious fotó** [x: 936, y: 208, order: 13]
  - **Type:** default
  - **Prompt:** Sárga Golden Delicious almák fehér stúdióháttéren. 12 px sarok, körülötte sok levegő. Alt: Sárga Golden Delicious almák.
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** Sárga Golden Delicious almák fehér stúdióháttéren. 12 px sarok, körülötte sok levegő. Alt: Sárga Golden Delicious almák.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Golden Delicious név** [x: 936, y: 504, order: 14]
  - **Type:** default
  - **Prompt:** H3 24 px tintakék.
  - **Exact Copy:** Golden Delicious
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** H3 24 px tintakék.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Golden Delicious íz** [x: 936, y: 544, order: 15]
  - **Type:** default
  - **Prompt:** 14 px másodlagos szöveg.
  - **Exact Copy:** Édes · lágy
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 14 px másodlagos szöveg.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Golden Delicious ár** [x: 936, y: 592, order: 16]
  - **Type:** default
  - **Prompt:** 22 px semibold. Illusztratív mintaár.
  - **Exact Copy:** 850 Ft / kg
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 22 px semibold. Illusztratív mintaár.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.
- **Golden Delicious kosárgomb** [x: 936, y: 648, order: 17]
  - **Type:** default
  - **Prompt:** 1 kg Golden Delicious hozzáadása a kosárhoz; ismétlés növeli a mennyiséget. Kék szegélyes gomb, hover halványkék háttér, siker aria-live: A kosárba került.
  - **Exact Copy:** Kosárba · 1 kg
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 1 kg Golden Delicious hozzáadása a kosárhoz; ismétlés növeli a mennyiséget. Kék szegélyes gomb, hover halványkék háttér, siker aria-live: A kosárba került.
  - **Interaction States Required:**
    - Mobilon egy oszlop, kép és hozzá tartozó adatok/gomb egy kártyában; minden termék külön article.

# 04 — Válogatásdoboz [order: 3]

- **Dobozfotó** [x: 120, y: 48, order: 0]
  - **Type:** default
  - **Prompt:** Nyitott natúr papírdoboz piros, zöld és sárga almákkal, halványkék háttéren. Alt: Három almafajtából összeállított válogatásdoboz.
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** Nyitott natúr papírdoboz piros, zöld és sárga almákkal, halványkék háttéren. Alt: Három almafajtából összeállított válogatásdoboz.
- **Doboz felirat** [x: 744, y: 64, order: 1]
  - **Type:** default
  - **Prompt:** 12 px kék nagybetű.
  - **Exact Copy:** HÁROM FAJTA. EGY DOBOZ.
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 12 px kék nagybetű.
- **Doboz cím** [x: 744, y: 112, order: 2]
  - **Type:** default
  - **Prompt:** 40/46 px H2; egész szekció jégkék háttér.
  - **Exact Copy:** Miért választanál
csak egyet?
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 40/46 px H2; egész szekció jégkék háttér.
- **Doboz leírás** [x: 744, y: 236, order: 3]
  - **Type:** default
  - **Prompt:** 18/28 px.
  - **Exact Copy:** 1 kg Gala, 1 kg Granny Smith és 1 kg Golden Delicious egy válogatásban.
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 18/28 px.
- **Doboz ár** [x: 744, y: 312, order: 4]
  - **Type:** default
  - **Prompt:** 24 px semibold. Összetevők árának összege, nem akció.
  - **Exact Copy:** 2 730 Ft / 3 kg
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** 24 px semibold. Összetevők árának összege, nem akció.
- **Doboz CTA** [x: 984, y: 308, order: 5]
  - **Type:** default
  - **Prompt:** Egy 3 kg-os válogatásdoboz hozzáadása a kosárhoz; nincs átirányítás vagy valódi rendelés.
  - **Exact Copy:** Kérem a válogatást
  - **Forbidden Patterns:** Kitalált kedvezmény vagy minősítés, Extra termékkártyák
  - **Layout Hint:** Egy 3 kg-os válogatásdoboz hozzáadása a kosárhoz; nincs átirányítás vagy valódi rendelés.

# 05 — Lábléc [order: 4]

- **Lábléc logó** [x: 120, y: 48, order: 0]
  - **Type:** default
  - **Prompt:** 28 px tintakék, fehér háttér, felső 1 px szegély.
  - **Exact Copy:** Almakék
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** 28 px tintakék, fehér háttér, felső 1 px szegély.
- **Lábléc szlogen** [x: 120, y: 104, order: 1]
  - **Type:** default
  - **Prompt:** 16 px másodlagos.
  - **Exact Copy:** Egy kis roppanás a mindennapokba.
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** 16 px másodlagos.
- **Vissza fel** [x: 1104, y: 48, order: 2]
  - **Type:** default
  - **Prompt:** Oldal tetejére görgetés; reduced-motion esetén azonnal.
  - **Exact Copy:** Vissza az elejére ↑
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Oldal tetejére görgetés; reduced-motion esetén azonnal.
- **Koncepció jelzés** [x: 120, y: 184, order: 3]
  - **Type:** default
  - **Prompt:** 12 px visszafogott szöveg.
  - **Exact Copy:** Webshopkoncepció · Az árak illusztrációk.
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** 12 px visszafogott szöveg.

# 06 — Kosárpanel [order: 5]

- **Kosár címsor** [x: 960, y: 40, order: 0]
  - **Type:** default
  - **Prompt:** Jobbról nyíló 480 px széles fehér drawer sötétített háttér felett. Mobilon teljes szélesség. H2 28 px. Nem a lábléc alatti szekció; interakciós állapot.
  - **Exact Copy:** Kosarad
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Jobbról nyíló 480 px széles fehér drawer sötétített háttér felett. Mobilon teljes szélesség. H2 28 px. Nem a lábléc alatti szekció; interakciós állapot.
- **Kosár bezárás** [x: 1336, y: 40, order: 1]
  - **Type:** default
  - **Prompt:** Aria-label: Kosár bezárása. Escape bezár, fókuszcsapda, bezáráskor fókusz vissza a megnyitóra.
  - **Exact Copy:** ×
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Aria-label: Kosár bezárása. Escape bezár, fókuszcsapda, bezáráskor fókusz vissza a megnyitóra.
- **Kosártétel kép** [x: 960, y: 136, order: 2]
  - **Type:** default
  - **Prompt:** Gala termékfotó ugyanaz mint a rácson; alt: Gala alma. Példa feltöltött állapot 1 kg Gala.
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Gala termékfotó ugyanaz mint a rácson; alt: Gala alma. Példa feltöltött állapot 1 kg Gala.
- **Kosártétel név** [x: 1072, y: 136, order: 3]
  - **Type:** default
  - **Prompt:** 20 px semibold; tényleges kosárból dinamikus.
  - **Exact Copy:** Gala
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** 20 px semibold; tényleges kosárból dinamikus.
- **Mennyiség** [x: 1072, y: 184, order: 4]
  - **Type:** default
  - **Prompt:** Léptethető mennyiség: mínusz, érték, plusz; egyenként 44 px cél. Terméknél 1 kg lépés; doboznál 1 doboz. Minimum 1, külön eltávolítással.
  - **Exact Copy:** 1 kg
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Léptethető mennyiség: mínusz, érték, plusz; egyenként 44 px cél. Terméknél 1 kg lépés; doboznál 1 doboz. Minimum 1, külön eltávolítással.
- **Tétel törlés** [x: 1248, y: 184, order: 5]
  - **Type:** default
  - **Prompt:** Tétel eltávolítása. Üres kosárban terméksorok és összeg helyett: A kosarad még üres. CTA: Almák böngészése.
  - **Exact Copy:** Eltávolítás
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Tétel eltávolítása. Üres kosárban terméksorok és összeg helyett: A kosarad még üres. CTA: Almák böngészése.
- **Részösszeg cím** [x: 960, y: 520, order: 6]
  - **Type:** default
  - **Prompt:** A kosár aljához rögzített összegblokk.
  - **Exact Copy:** Részösszeg
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** A kosár aljához rögzített összegblokk.
- **Részösszeg érték** [x: 1224, y: 520, order: 7]
  - **Type:** default
  - **Prompt:** Dinamikus összeg, jobbra igazítva, 24 px semibold.
  - **Exact Copy:** 890 Ft
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Dinamikus összeg, jobbra igazítva, 24 px semibold.
- **Szállítás megjegyzés** [x: 960, y: 568, order: 8]
  - **Type:** default
  - **Prompt:** 14/22 px.
  - **Exact Copy:** A szállítás díja a pénztárnál számítódik.
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** 14/22 px.
- **Pénztár gomb** [x: 960, y: 644, order: 9]
  - **Type:** default
  - **Prompt:** Kék elsődleges gomb. Designkoncepció: checkout integráció még nincs; prototípusban kattintásra információ: Ez egy bemutató, rendelést még nem adhatsz le. Nincs fizetés vagy hamis sikerállapot.
  - **Exact Copy:** Tovább a pénztárhoz
  - **Forbidden Patterns:** Nem specifikált szöveg, Hamis rendelési siker
  - **Layout Hint:** Kék elsődleges gomb. Designkoncepció: checkout integráció még nincs; prototípusban kattintásra információ: Ez egy bemutató, rendelést még nem adhatsz le. Nincs fizetés vagy hamis sikerállapot.

</ui_frames>