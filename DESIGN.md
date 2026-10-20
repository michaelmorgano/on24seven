# Design rules

How color is used on on24seven pages. Tokens live in `:root` in `index.html`.

## Outcome colors

Color says who did the work. Blue means on24seven delivered. Red means money lost. The two cards mirror each other: solid for the strongest outcome, tint for the lesser one.

| Token | Meaning | Use for |
|---|---|---|
| `--outcome-win` | on24seven delivered | Check badge, solid win badges, recovered or captured money |
| `--outcome-win-ink` | Text on `--outcome-win` | White glyphs and labels on solid blue |
| `--outcome-win-soft` / `--outcome-win-soft-ink` | Service resolved | Tinted win badges |
| `--outcome-loss` | Money lost | The X badge and loss money figures |
| `--outcome-loss-strong` | Revenue lost | Solid red badges (Missed), white text via `--outcome-win-ink` |
| `--outcome-loss-soft` / `--outcome-loss-soft-ink` | Deferred, at risk | Tinted red badges (Voicemail) |
| `--outcome-inert` / `-ink` | Absence | "Without" card (off-white `--surface`) and its gray copy |

Rules:

- **Brand blue never appears on a "without" or loss surface.** Use ink for emphasis there.
- **Red marks lost revenue only.** That means the X, loss money, and the loss badges. Copy and counts on the loss side stay gray.
- **Counts are ink, money is semantic.** On both sides, a number like "8 calls" is `--ink`. A dollar figure takes the outcome color.
- **One success color.** Don't introduce green or black for wins.

## Badges

Badge weight follows revenue impact:

| Style | Class | When | Examples |
|---|---|---|---|
| Solid blue | `.tag.win-strong` | Revenue kept or created | Booked, Rescheduled |
| Tinted blue | `.tag.win-soft` | Service resolved, no revenue change | Answered, Handled |
| Solid red | `.tag.loss-strong` | Revenue lost | Missed |
| Tinted red | `.tag.loss-soft` | Deferred, revenue at risk | Voicemail |

For a new badge on an industry page, ask "did this keep or create revenue?" Yes means solid blue. Resolved without revenue means tinted blue. The loss side mirrors this: solid red means revenue was lost, tinted red means it is at risk.

## Contrast

Badges are about 10.5px uppercase mono, so their text needs **4.5:1**. Money figures at 38px and larger need 3:1.

Current measured values:

| Element | Ratio |
|---|---|
| `.tag.loss-strong` | 5.1:1 |
| `.tag.loss-soft` | 4.9:1 |
| `.tag.win-soft` | 5.2:1 |
| `.tag.win-strong` | 5.1:1 |
| Inert copy on `--outcome-inert` (off-white) | 7.7:1 |
| Loss money on `--outcome-inert` (38px) | 4.0:1 |

If you change `--surface`, `--ink`, or `--accent`, re-measure these values on the rendered page. The inert text gray is mixed in oklab from `--ink` and `--surface`, so they follow those changes automatically, but their contrast can still shift.
