---
tags:
  - note_taking
source: AI
---

> [!only-in-original] What is it about?
> How the **Credit** column in `Starting Points.base` is calculated.

## Formula

$$
\text{Credit} = 100 \times M \times 2^{-d/H}
$$

Credit goes from **0 to 100** and shows how much I can rely on a note right now.

| Symbol | Meaning |
|---|---|
| **M** | Maturity weight: the highest credit a note can ever have |
| **H** | Half-life in days: every H days without attention, the credit halves |
| **d** | Age in days: average of *days since `updated`* and *days since `viewed`* |

| maturity | M (max credit) | H (half-life) |
|---|---|---|
| baby | 25 | 7 days |
| young | 50 | 30 days |
| adult | 75 | 90 days |
| elderly | 100 | 365 days |

- More mature ideas are more reliable, so they get a higher **M**.
- They also change more slowly, so they get a longer **H**.
- `status: inactive` sets the credit to 0. The note is kept, but it gets no credit.

## Examples

- A baby note seen today has a credit of **25**. One week later it has about **12**, and after a month about **1–2**.
- An elderly note untouched for a year still has a credit of **50**.

## Formulas in the base

| Formula | What it does |
|---|---|
| `du` | Days since `updated`. The date is cut to `YYYY-MM-DD HH:mm:ss` because that's the only format `date()` accepts |
| `dv` | Days since `viewed` (same conversion) |
| `d` | Average of `du` and `dv` |
| `M`, `H` | Picked from `maturity` (table above) |
| `y` | `0.693 × d / H`, because 2^(−d/H) = e^(−y) |
| `decay` | e^(−y) approximated with a short polynomial, because Bases has no power function. Accurate while the credit still matters |
| `credit` | `100 × M × decay`, rounded (0 if inactive) |

## Reading the score

- **Credit below half of its max** (the note is older than H): time to review it. Re-read it, then edit or confirm it.
- **Credit close to 0**: the note is stale. Rework it, raise its maturity, or set it to inactive.
