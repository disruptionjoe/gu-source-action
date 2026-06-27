---
title: "Source Action Construction — Derivation Progress"
started: 2026-06-27
status: in_progress
parent: ../gu-formalization
target: SPEC.md
---

# Source Action Construction — Derivation Progress

Running ledger for the construction of GU's missing RS/IG source action. Same discipline as the parent
`gu-formalization`: compute -> adversarially verify -> land only what survives; record honest negatives.

> Inherited starting state (from the parent campaign, 2026-06-24..27): the RS BV bicomplex is built and
> verified; the final obstruction C2 (= 155.36, Gamma-independent) is isolated, proven GLOBAL, and proven NOT
> an index; the three missing global objects (families pushforward, boundary holonomy/spectral section,
> BV-to-boundary-Dirac map) are named in SPEC.md section 5. The natural characteristic class is -5376, not 24.

---

### SEED — repo scaffolded (2026-06-27)

Created the construction repo as a child of gu-formalization. Wired `lib/gu_bridge.py` to the verified parent
machinery (the Cl(9,5)=M(64,H) rep, the gamma-trace constraint, C2, the bicomplex); `tests/test_bridge.py`
reproduces the anchors (bare commutator 58.72, C2 155.36). SPEC.md = the target; DEAD-ENDS.md = the killed
approaches not to re-walk. No construction attempted yet.

**Next:** the first genuine construction attempt is SPEC.md item 5(iii) — the BV-to-boundary-Dirac map —
since C2 is proven not-an-index and not-local, this is the structurally-required bridge. Any attempt must
respect the four guards and the DEAD-ENDS list, and must not import the target.
