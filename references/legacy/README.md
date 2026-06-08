# Legacy: carousel image-rendering pipeline

These files belong to the skill's **previous** direction — a full carousel/social-card image generator that rendered finished PNGs (covers + content pages, WeChat pairs, screenshots, maps) via HTML→Playwright in Editorial and Swiss visual systems.

The skill has since **pivoted** to generating *cover text + titles* and a draggable HTML text-editor template (see the top-level `SKILL.md`). It no longer renders cover images — the cover photo is the user's own artifact.

Nothing here is part of the active workflow. It is retained for reference and in case a future task needs the image-rendering machinery again. Do **not** wire these back into the active `SKILL.md` flow without an explicit decision to un-pivot.

Files: `background-systems.md`, `image-overlay.md`, `screenshot-treatment.md`, `map-component.md`, `portrait-fill.md`, `layout-recipes.md`, `theme-presets.md`, `components.md`, `production-workflow.md`, `style-system.md`, `qa-checklist.md`, and in `assets/legacy/`: the two seed templates, `magazine-bg-webgl.js`, `screenshot-backgrounds/`, `validate-social-deck.mjs`.
