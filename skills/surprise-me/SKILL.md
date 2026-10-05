---
name: surprise-me
description: Max visual acuity mode. Triggers on "/surprise-me", "surprise me", "/surprise-me [target]". Flips the session into extreme-capability visual work - full creative freedom (NOT locked to the user's house style), a mixture of advanced techniques per build, real generated/sourced assets, a dice roll that picks the creative direction, and a MANDATORY loop of 3+ screenshot-critique-improve passes before anything is shown. Use for websites, landing pages, decks, or any visual where the user wants to be blown away rather than served the default style.
---

# /surprise-me — max visual acuity mode

The point: produce work that demonstrates extreme capability, taste, and artistic flavor — the kind of output that makes someone stop scrolling. It works because of five mechanics. Run all five, every time.

Backed by the impeccable.style research (impeccable.style/research): models are deterministic where it matters. Asking yourself to "be creative" changes the wording, not the concept, and when you pick from your own list you always pick the same favourite. So this skill uses mechanical fixes: **a dice roll picks the direction, a written contract locks it, and the critique passes audit the render against the contract.**

## The five mechanics (why this works)

1. **Ambition is stated up front.** The brief is "demonstrate extreme capability, taste, artistic flavor" — not "make a page". Aim every decision at *showcase*, not *adequate*.
2. **Fundamentally different, advanced techniques.** Each build commits to a MIXTURE of at least 3: high-quality 3D, otherworldly animation, exceptional color palette, novel typography, scroll choreography, shader/canvas effects, unusual layout systems. Never one gimmick on a plain page.
3. **Real assets, many workflows.** Don't fake it with CSS gradients. Pull references, generate images (whatever image model is available — GPT Image, Nano Banana, Flux, …), animate stills (Higgsfield, Kling, Runway, …) if a video tool is available, and study advanced motion-design sites. Assets are half the wow. If no generation tool is available, say so in the heads-up and compensate with procedural art (SVG, canvas, WebGL shaders) — never flat placeholders.
4. **Creative freedom — but the dice pick the lane.** `/surprise-me` OVERRIDES the user's default house style — don't fall back to it unless the user names it. You author the candidate directions; the roll (workflow step 3) decides which one gets built, because left to choose you'd build the same favourite every time. Within the rolled lane, full freedom: pick a palette and type pairing that fits the concept and make them exceptional.
5. **Iteration is mandatory, and it's VISUAL.** Nothing ships on pass 1. Minimum 3 passes, each one starts by LOOKING at a rendered screenshot, not the code.

## Workflow

1. **Heads-up** — one line on what you're about to build and the techniques you'll mix. Don't ask for permission; this mode is the permission.

2. **Write the candidates.** Write 6 numbered creative directions for the target. Each is one line: a concept + a mood + the signature technique. Make them *fundamentally* different from each other — different eras, materials, metaphors, color temperatures, layout systems. If two feel like siblings, replace one. Show the list.

3. **Roll the dice.** Pick with a real random source, never by judgment:

   ```bash
   echo $(( RANDOM % 6 + 1 ))  # bash/zsh — works on macOS and Linux
   shuf -i 1-6 -n 1            # alternative where coreutils is installed
   ```

   Report the roll. The rolled direction is the one you build — no re-rolls because you prefer another one. (Re-roll only if the rolled direction is genuinely impossible with the available stack, and say why.)

4. **Write the contract.** Save `surprise-contract.md` next to the build (or in a scratch dir if the project shouldn't contain it). It locks:
   - **Concept** — one sentence; the feeling a viewer should have in the first 3 seconds.
   - **Palette** — 4–6 named hex values with roles (ground, ink, accent, glow, …).
   - **Type pairing** — display + text faces (real fonts, e.g. from Google Fonts or a CDN), with sizes for the hero.
   - **Techniques** — the 3+ advanced techniques from mechanic 2, each with *where* it appears.
   - **Assets** — what will be generated/sourced and how.
   - **Hero moment** — the single thing someone will screenshot and send to a friend.
   - **Bans** — 3+ things this build must NOT do (e.g. "no centered-card-on-gradient hero", "no default system font", "no emoji icons").

5. **Build pass 1.** Implement the whole thing against the contract with real assets. Prefer a stack that renders standalone (single HTML file with CDN libs, or the project's existing framework). Respect `prefers-reduced-motion` and keep it working at phone width.

6. **Critique loop — minimum 3 passes.** Each pass:
   1. **Render and screenshot.** Desktop (~1440px) and mobile (~390px), plus mid-scroll / mid-animation frames when motion matters. Use whatever is available: Playwright (`npx playwright screenshot --viewport-size=1440,900 <url> shot.png`), a headless browser, the agent's built-in browser tool, or a browser-automation MCP.
   2. **Look at the screenshots first, not the code.** Open the images.
   3. **Audit against the contract.** Score each contract line ✅ / ⚠️ / ❌, then answer bluntly: *Would this stop someone scrolling? What looks generic? What's the weakest region of the screen?*
   4. **Fix the top 3 problems**, biggest visual impact first.

   Passes 2 and 3 must each produce a visible improvement in the screenshot. If the work still looks "nice but expected" after pass 3, keep going.

7. **Present.** Show the final screenshot(s), the rolled direction and roll number, how to open/run it, and one line per pass on what changed. Mention what you'd push further with more time or tools.

## Rules of thumb

- Nothing is shown to the user before pass 3 is done.
- Placeholder text like "Lorem ipsum" or "Your Title Here" is a failure — write real copy that fits the concept.
- Every technique must earn its place in the concept; three unrelated effects stacked on top of each other is a gimmick, not a mixture.
- Performance still matters: lazy-load heavy assets, cap canvas/WebGL resolution on mobile, and never block first paint on a 3D scene.
- With a `[target]` argument, the target defines *what* is built (a page, a deck, a component); the dice still pick *how* it looks.
