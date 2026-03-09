# ECCE 2026 EMI Tutorial — Project Instructions

## Project Identity
- **Student:** Vignesh (B.Tech 2nd year, Power Electronics)
- **Paper:** "Generalized Differential-Common-Mode Decomposition for Modeling
  Conducted Emissions in Asymmetric Power Electronic Systems" — Brovont, IEEE TPEL Aug. 2018
- **Repo:** https://github.com/mouliT/Generalized-Differential-Common-Mode-Decomposition
- **Workflow:** edit locally → git commit/push → Overleaf pull → compile → student reads

## File Structure
| File | Lines | Contents |
|---|---|---|
| `EMI_DM_CM_Decomposition_Tutorial.tex` | ~151 | Master file — preamble + `\input` calls only |
| `sec0.tex` | ~248 | §0 Before You Begin |
| `sec1.tex` | ~720 | §1 Defining CM and DM |
| `sec2.tex` | ~1025 | §2 How Asymmetry Couples the Two Modes |
| `appendixA.tex` | ~200 | Appendix A — Strang linear algebra connections |
| `appendixB.tex` | ~350 | Appendix B — Geometric interpretation + numerical examples |
| `tasks/` | — | MiniMax task instruction files |

**Always edit the section file directly, not the master file.**

## Two-Agent Workflow
Claude is the **master agent** — responsible for:
- Mathematical reasoning and correctness checks
- Writing new sections from scratch
- Reviewing MiniMax output for errors
- Creating task instruction files for MiniMax

MiniMax M2.5 is the **executor agent** — handles:
- Mechanical file edits specified precisely in a task `.md` file
- String replacements with exact old/new strings given
- Reordering `\input` lines
- Running git add/commit/push after edits

**Task file protocol:**
1. Claude creates `tasks/TASK_NNN_description.md` with exact instructions
2. User opens that file in MiniMax chat
3. MiniMax executes and reports back
4. Claude reviews the result

## Hard Rules (same as global rules)
1. **One section at a time.** Write one section, stop, wait for green signal.
2. **Commit and push automatically** after every correction or new section.
3. **Never use `\ref` to a label that does not yet exist.**
4. **Read figures before describing them.**

## LaTeX Macros (defined in master preamble)
`\vcm`, `\icm`, `\vdm{m}{n}`, `\idm{m}{n}`, `\TiN`, `\TvN`,
`\iDCM`, `\vDCM`, `\Vdc`, `\Cp`, `\Rh`, `\Ni`, `\figref`,
`\figentry{label}{filename-no-ext}{caption}{width}`

## tcolorbox Styles
`circuitbox` (blue), `statebox` (orange), `eqnbox` (green),
`physbox` (gray), `warningbox` (red)

## Document Progress
| Section | Status |
|---|---|
| §0 Before You Begin | ✅ Complete |
| §1 Defining CM and DM | ✅ Complete |
| §2 How Asymmetry Couples the Two Modes | ✅ Complete |
| §3 Half-Bridge Testbed + MCPM | TODO |
| §4 First CEM Derivation | TODO |
| §5 Alternative CEM | TODO |
| Appendix A (Strang connections) | ✅ Complete — pending reorder to B |
| Appendix B (Geometric interpretation) | ✅ Draft — pending formula fix + reorder to A |

## Key Equations
- Per-line KVL (EMI approx): `v_nP + v_Pg = (R + pL + S_n/p) * i_n`
- Mixed-mode matrix form (Eq.9): `Z * i = v_nP + v_Pg * 1_N`
- DCM transformation: `Z_DCM = T^v_N * Z * (T^i_N)^{-1}` ← use `T^v` NOT `(T^v)^{-1}`
- S_DCM (Eq.11): `S_DCM = T^v_N * S_N * (T^i_N)^{-1}`
- k=1 → S_DCM diagonal (no coupling); k≠1 → off-diagonal entries appear
