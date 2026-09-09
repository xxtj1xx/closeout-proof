# Case study — From van notes to an auditable closeout

**Claim:** I can translate a messy field closeout into a structured, verifiable packet without inventing job data or pretending a model is in the loop.

**Lane:** AI-enabled telecom / field operations and implementation. The “AI” here is a deterministic reviewer plus a next-missing-field assistant. That is honest. A hosted LLM can sit on top later; the checklist is the product.

## Problem

Overnight OSP closeouts fail in the office for boring reasons: no after photo, no test reading, fiber count that does not match the sheath, a timestamp that never got written down. The tech already did the work. The packet is incomplete. Someone re-enters it in the morning.

## Constraints

- Public portfolio cannot use real employer, customer, engineer, town, job, or cable IDs.
- Measurement has to be repeatable by a stranger with this repo.
- Field usability: a 12-item gate is small enough to finish in a van.
- No network required.

## System design

1. One frozen checklist of 12 required items.
2. Two synthetic packets that share the same site fiction (`SYN-SITE-14`, 432-count enclosure).
3. A scorer that only counts checklist keys. No vibes.
4. A reviewer that flags missing required items, count mismatches, and “photo claimed but not attached.”
5. An assistant that names the next missing field — the same move an implementation specialist would ship before wiring an LLM.

## Implementation

`index.html` loads both fixtures, scores them, and lets you toggle packets. `fixtures/*.json` are the source of truth. Changing a fixture changes the bench. That is the point.

## Verification

Open the page. Click **Run bench**. You should see:

- Baseline present 6 / 12, missing 6, flags 8, re-entry 3
- Structured present 12 / 12, missing 0, flags 0, re-entry 0

If those numbers drift, the fixtures or the scorer changed. Do not round them.

## Outcome

On synthetic packets, the gated workflow removes every checklist miss that the messy notes left open. That supports the hiring sentence *“I design closeouts that fail closed.”* It does **not** support a claim about minutes saved on a real Crown Castle or contractor form. Timed field runs are still TBD.

## Lessons

- The valuable layer is the checklist and the fail-closed gate, not a chatbot wrapper.
- Public proof has to be synthetic or the packet cannot ship.
- Resume language stays qualitative until a timed, permission-cleared field run exists.

## Privacy

All names, IDs, and photos in this repo are invented. Do not paste production closeouts into this demo.
