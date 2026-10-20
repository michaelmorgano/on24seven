# Design rules

How color is used on on24seven pages. Tokens live in `:root` in `index.html`.

## Outcome colors

Color says who did the work. Blue means on24seven delivered. Red means money lost. Gray means nothing happened.

| Token | Meaning | Use for |
|---|---|---|
| `--outcome-win` | on24seven delivered | Check badge, solid win badges, recovered or captured money |
| `--outcome-win-ink` | Text on `--outcome-win` | White glyphs and labels on solid blue |
| `--outcome-win-soft` / `--outcome-win-soft-ink` | Service resolved | Tinted win badges |
| `--outcome-loss` | Money lost | The X badge and loss money figures **only** |
| `--outcome-inert` / `-fill` / `-ink` | Absence: a missed call | "Without" card (plain white), its gray badges and copy |

Rules:

- **Brand blue never appears on a "without" or loss surface.** Use ink for emphasis there.
- **Red is used only for money and the X.** Labels, badges, and counts on the loss side stay gray.
- **Counts are ink, money is semantic.** On both sides, a number like "8 calls" is `--ink`. A dollar figure takes the outcome color.
- **One success color.** Don't introduce green or black for wins.

## Badges

Badge weight follows revenue impact:

| Style | Class | When | Examples |
|---|---|---|---|
| Solid blue | `.tag.win-strong` | Revenue kept or created | Booked, Rescheduled |
| Tinted blue | `.tag.win-soft` | Service resolved, no revenue change | Answered, Handled |
| Gray | `.tag.inert` | Nothing happened | Missed, Voicemail |

For a new badge on an industry page, ask "did this keep or create revenue?" Yes means solid. Resolved without revenue means tint.

## Contrast

Badges are about 10.5px uppercase mono, so their text needs **4.5:1**. Money figures at 38px and larger need 3:1.

Current measured values:

| Element | Ratio |
|---|---|
| `.tag.inert` | 5.7:1 |
| `.tag.win-soft` | 5.2:1 |
| `.tag.win-strong` | 5.1:1 |
| Inert copy on `--outcome-inert` (white) | 8.4:1 |
| Loss money on `--outcome-inert` (38px) | 4.3:1 |

If you change `--surface`, `--ink`, or `--accent`, re-measure these values on the rendered page. The inert pill and text grays are mixed in oklab from `--ink` and `--surface`, so they follow those changes automatically, but their contrast can still shift.
