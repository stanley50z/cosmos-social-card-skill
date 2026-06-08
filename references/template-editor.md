# Template Editor (`assets/cover-text-editor.html`)

The skill's deliverable is **cover text + titles** plus a **self-contained HTML editor** the user opens in a browser to position that text over their own photo. No build step, no dependencies, no Playwright — it opens directly via `file://`.

## What Claude writes vs. what's static

**Claude only edits the `ZUHE` array.** Everything else (drag logic, sliders, safe-zone overlay, copy button, canvas scaling) is static boilerplate that ships unchanged.

```js
const ZUHE = [
  { id:'A', biaoti:'…标题…', zhu:'…主文字 ≤10…', fu:'…副文字 ≤12…' },
  { id:'B', biaoti:'…',     zhu:'…',            fu:'…' },
  { id:'C', biaoti:'…',     zhu:'…',            fu:'…' },
];
```

Schema:
- `biaoti` — 标题, formal/objective, goes to the post body (NOT drawn on the cover). Shown in the panel + copy export.
- `zhu` — 主文字, the big emotional line on the cover, ≤10 字.
- `fu` — 副文字, the specific payoff/keyword, ≤12 字.

Optionally pre-set the `layout` object below `ZUHE` (per-layer x/y/rotation/size/weight/color/opacity/letter/align) to a sensible starting position for the chosen paradigm. The user then fine-tunes by drag + sliders.

## How to deliver it

1. Copy `assets/cover-text-editor.html` into the task folder as `cover-text-editor.html`.
2. Fill the `ZUHE` array with the 3 候选组合.
3. (Optional) tweak the `layout` starting positions to match the chosen 范式 (e.g. 大字报型 → 主文字 large, high; 数字证据型 → big number as 主, small 副 below).
4. Give the user the absolute path and a one-line "open this in your browser, load your photo, drag to taste."

Do **not** render a PNG — the cover image is the user's own photo. The skill stops at text + editor.

## Editor capabilities (already built in)

- **Two draggable text layers** — 主文字 / 副文字, mirrored by sidebar sliders.
- **Per-layer controls** — X, Y, rotation (−30°…30°), font-size (24–180px), font-weight (100–900), color, opacity, letter-spacing, text-align. Layout is shared across all 3 组合.
- **组合 A/B/C switcher** — hot-swaps the text content while keeping the layout, for blind selection.
- **Safe-zone overlay** — dashed lines at 150px top (avatar/handle) and 150px bottom (like/comment buttons); toggle on/off. Keep critical text between them.
- **Load background** — user drops their own cover photo; text composes on top live.
- **Copy 全部** — formats all 3 组合 (标题 + 主 + 副) for one-paste into the WeChat group 盲选 thread.
- **Auto-fit** — canvas scales to viewport height; drag math accounts for the scale so dragging stays 1:1.

## Canvas spec

- 900 × 1200 px (3:4 vertical — 占双列流最大面积).
- `--safe-margin: 150px` top/bottom (edit in CSS if a platform changes its UI overlay).
- Background is the user's photo (`object-fit: cover`) or the theme color when none loaded.

## Why this and not a rendered cover

The conversation's earlier direction rendered HTML→PNG via Playwright. The final direction deliberately **dropped image rendering**: the cover photo must be the user's real artifact (真实感 ＞ 精美感), and the hard problem is *the words and their placement*, not generating pixels. The editor hands placement control to the human while the skill owns the copywriting. See `cover-text.md` for the principles the text obeys.
