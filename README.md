# Closeout Proof

**Public-safe artifact.** Synthetic fiber OSP closeout packets only. No employer, customer, job number, street, or cable-span identifiers.

Live demo: https://closeout-proof.vercel.app

What this is: a hiring proof that Taylor Javery can turn a messy overnight closeout into a structured, checkable packet — and that a deterministic reviewer can catch missing fields before the office does.

What this is not: SpliceFlow production. Not a live LLM. Not real job data.

## 90-second story

Overnight OSP work gets rejected when photos, counts, or test readings never make it onto the packet. Paper and free-text notes hide those holes until morning. This tool uses one fixed 12-item checklist, two synthetic packets, and a rule-based reviewer. Same checklist on both packets. Scores are computed in the browser. Anyone can reload the page and get the same numbers.

## Reproducible scores (this repo)

Checklist has 12 required items. Runner: open `index.html`, click **Run bench**.

| Packet | Present / 12 | Missing | Reviewer flags | Implied re-entry |
| --- | ---: | ---: | ---: | ---: |
| Baseline — messy van notes | 6 | 6 | 8 | 3 |
| Structured — gated closeout | 12 | 0 | 0 | 0 |

Implied re-entry on the messy packet: test reading added after first pass, photo labeled after submit, fiber count corrected from 288 → 432.

These numbers come from `fixtures/baseline.json` and `fixtures/structured.json` scored by the same rules in `index.html`. They are lab scores on synthetic data, not field time studies. Do not put a time-saved percentage on a resume from this repo.

## Run locally

Open `index.html` in a browser. No build step.

## Repo layout

- `index.html` — demo + bench
- `fixtures/` — synthetic packets
- `CASE-STUDY.md` — problem → design → verification → lessons
- `LICENSE` — MIT

## Author

Taylor J. Javery · CFOT · Berkley, MA · [github.com/xxtj1xx](https://github.com/xxtj1xx)
