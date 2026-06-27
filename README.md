# GU Source Action

> **Working name — pending confirmation before this becomes a public repo.**

**An open theoretical-construction program: build the one object that `gu-formalization` proved is missing.**

This repo is the CHILD of [`gu-formalization`](../gu-formalization). That repo is a finished,
adversarially-audited reconstruction of Geometric Unity; its capstone
(`gu-formalization/WHERE-GU-STANDS-AND-THE-MISSING-OBJECT-2026-06-27.md`) proved GU does not close on the
existing material and pinned the single missing object — the stabilized **RS/IG source action** — down to a
precise, buildable spec.

This repo has ONE job: try to construct that object. The target is `SPEC.md`.

## Honest framing (read this first)

This is **open invention, not audit.** It is **expected to mostly fail.** The parent repo earns trust by
keeping only what survives adversarial checking; this repo earns trust by being relentlessly honest about
what it has **not** achieved. A beautiful idea here is worth nothing until it is computed and survives attack.
"It fits beautifully" is a warning sign, not evidence — the parent repo was repeatedly burned by exactly that
(see `DEAD-ENDS.md`). **Never import the answer** (no `24/8`, no assumed-K3, no fitting to the target).

## Dependency

Requires `gu-formalization` checked out as a sibling directory (`../gu-formalization`), or set the env var
`GU_FORMALIZATION_PATH`. The verified machinery — the Cl(9,5)=M(64,H) representation, the gamma-trace
constraint, the obstruction C2, the BV bicomplex — is **imported** via `lib/gu_bridge.py`, never re-derived.
Smoke test: `python tests/test_bridge.py` (reproduces the anchors C2 = 155.36, ||[Pi_RS, M_D]|| = 58.72).

## Start here

`Agents Start Here.md` — the discipline, the spec, the dead-ends not to re-walk, and how to use the bridge.
`DERIVATION-PROGRESS.md` — the running ledger (same compute -> adversarially-verify -> land discipline as the
parent).
