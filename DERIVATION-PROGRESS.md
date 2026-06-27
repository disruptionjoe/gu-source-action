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

---

### LENS-01 - Cryptoeconomic security-budget source action (2026-06-27)

Added `CRYPTOECONOMIC-SOURCE-ACTION.md` as the current front-door candidate lens. The idea:

```text
source action = adversarially priced rule for finalizing admissible geometric extensions
```

This does not claim a construction. It gives the search a concrete minimax normal form:

```text
Score(phi) = GrowthValue(phi)
             - ValidationCost(phi)
             - FinalizationCost(phi)
             - WorstCaseAdversarialLoss(phi)
```

where the adversary is the space of rival GU completions, not a human attacker. Added
`lib/security_budget.py` and `tests/test_security_budget.py` as a small executable scaffold for candidate
selection surfaces. The hard next step is to replace toy loss channels with GU-native computable channels
from the parent repo objects.

---

### LENS-02 - 25-persona divergent lens vote (2026-06-27)

Added `PERSONA-LENS-VOTE-2026-06-27.md` and `tests/test_persona_lens_vote.py`. The exercise forced 25
different lenses to make independent top-3 recommendations, then used a 3/2/1 vote to prioritize the
workstreams.

Vote result:

```text
1. B - GU-native minimax loss channels        20 points
2. C - boundary spectral-section/finality     18 points
3. A - BV-to-boundary-Dirac carrier           17 points
4. I - anti-import adversarial oracle         14 points
5. D - families pushforward/cobordism index   12 points
```

The actionable consensus is a triad:

```text
source-action search = GU-native minimax loss channels
                       + boundary finality carrier
                       + adversarial anti-import oracle
```

This does not supersede `SPEC.md`; it sets the next prioritization rule for construction attempts.

---

### CONSTRUCT-01 - first 5 construction steps: the BV-to-boundary-Dirac MAP holds (M_KT = N*D_Sigma^2), but the index half is forced shut (eta=0); a new obstruction-theorem (2026-06-27)

First concrete construction work: 5 SEQUENTIAL steps on workstream A (BV-to-boundary-Dirac = SPEC item 5(iii) = persona-vote #3), each computed on the explicit Cl(9,5) rep via `lib/gu_bridge.py` and adversarially framed. (The orchestration crashed near the end but wrote all 5 step tests; re-run + verified in the main loop. Step 1's heavy 196-pair Gram loop was made exact-but-fast via the Frobenius inner product.) Genuine mixed result: half built, half forced shut, plus a sharp new theorem. Guards held throughout (bare commutator 58.72 untouched; no target import).

**ADVANCE - the bridge holds at the operator level.**
- Step 1 (`tests/step1_c2_dirac_symbol.py`): C2's escape E(xi) = sum_a xi_a E_a, E_a = (I-Pi_RS)(id_14(x)e_a)Pi_RS, is a genuine first-order symbol; its Frobenius Gram M_ab = <E_a,E_b> is EXACTLY Euclidean (kappa*I, kappa=33.96, residual 0.0 -- NOT the (9,5)-Lorentzian kappa*diag(ETA), rel resid 0.96), and C2(xi) = K*|xi| is PERFECTLY ISOTROPIC (K=21.80, 0.0% directional spread, C2(2xi)/C2(xi)=2.000000). So the boundary symbol is Euclidean-ELLIPTIC and C2 is a pure scalar-magnitude first-order symbol.
- Step 2 (`tests/step2_boundary_dirac.py`): the boundary Dirac D_Sigma is EXACTLY self-adjoint (0.0e+00), full rank 128, Euclidean-elliptic (sigma_min=0.4949 bounded from 0 over all directions), and it does NOT degenerate on the (9,5) physical light cone - it is Euclidean-elliptic, not Lorentzian-hyperbolic.
- Step 4 (`tests/step4_mkt_vs_dirac_square.py`): **M_KT = N*(D_Sigma^2)|_surface EXACTLY** (rel 8.6e-16; N=14 = Gamma Gamma^dag tight-frame constant, a-priori, not fitted), and trace(M_KT) = C2^2 => sqrt(trace) = 155.3625 = C2. So D_Sigma is the square-ROOT of the Koszul-Tate Hessian: the BV-to-boundary-Dirac MAP (SPEC 5(iii), first half) is genuinely built at the full OPERATOR level, beyond Step 1's symbol level.

**HONEST NEGATIVE - the index half is forced shut.**
- Step 3 (`tests/step3_spectral_section.py`): eta(D_Sigma) = 0, FORCED by the anticommuting chiral grading G = Pi_RS - Q ({G, D_Sigma} = 0 to 5.5e-14); spectrum mirrored about 0; eta = 0 over all 20 tested xi (12 random + 8 null-cone). The spectral section is TRIVIAL (symmetric +/-), exactly as the parent flat operator.
- Step 5 (`tests/step5_synthesis.py`): SPEC 5(iii)'s required clause "APS spectral section connects to C2 (eta != 0)" FAILS. C2 is a degree-1 SYMBOL norm (a magnitude = sqrt(trace M_KT)), living in the singular-value SCALE of D_Sigma, NOT a sign-asymmetry / index.

**NEW OBSTRUCTION-THEOREM (the genuine product).** Any boundary Dirac whose square is the (positive) Koszul-Tate Hessian inherits an anticommuting chiral grading, hence eta = 0, so C2 can NEVER be its APS index. This independently re-derives the parent's "C2 is not an index" BY CONSTRUCTION and with the MECHANISM, and converts SPEC 5(iii) from open to a precise theorem-shaped wall.

**NEXT:** break the grading - a curvature/connection term that fails to anticommute with G, or a non-self-adjoint / non-chiral boundary operator - OR abandon the index reading and pursue C2 as a genuine first-order SYMBOL invariant (its natural home per steps 1+4). The latter is workstream A converging toward C (the boundary-symbol carrier), consistent with the persona vote.
