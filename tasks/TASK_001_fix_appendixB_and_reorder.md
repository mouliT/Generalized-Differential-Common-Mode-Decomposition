# TASK 001 — Fix appendixB.tex and Reorder Appendices

**Assigned to:** MiniMax M2.5
**Verified by:** Claude (mathematical correctness already checked)
**Repo:** `C:\Users\tmouli\Documents\AI_trainig_data\Vignesh\ECCE_2026_repo`

---

## Summary of changes required

1. Clean up `appendixB.tex` standalone-document guards
2. Fix wrong formula in 4 locations in `appendixB.tex`
3. Replace the 3×3 numerical examples (B.6 + B.7) with a correct 2×2 example
4. Remove `\appendix` from `appendixA.tex`
5. Update master file to reorder appendices (B before A) and add `\appendix`
6. Git add, commit, push

---

## CHANGE 1 — Remove standalone guards from `appendixB.tex`

**Delete lines 1–7** (the `\ifdefined` block at the top):
```
\ifdefined\INCLUDEDVIAINPUT
% Already has preamble from main document
\else
  \documentclass{article}
  \usepackage{amsmath,amssymb}
  \begin{document}
\fi
```

**Delete the last 4 lines** (the closing `\ifdefined` block):
```
\ifdefined\INCLUDEDVIAINPUT
\else
  \end{document}
\fi
```

---

## CHANGE 2 — Fix wrong formula in `appendixB.tex` (4 locations)

In every case, replace `(T^v)^{-1} \, Z` or `(T^v)^{-1}Z` with `T^v \, Z` or `T^v Z`.

**Location 1** — in the opening paragraph (was line 15, now earlier after guard removal):

Find:
```
$Z_{\text{new}} = (T^v)^{-1}Z(T^i)^{-1}$.
```
Replace with:
```
$Z_{\text{new}} = T^v Z (T^i)^{-1}$.
```

**Location 2** — in section B.5 body text:

Find:
```
    Z_{\text{new}} = (T^v)^{-1} \, Z \, (T^i)^{-1}
```
Replace with:
```
    Z_{\text{new}} = T^v \, Z \, (T^i)^{-1}
```

**Location 3** — in section B.5 bullet list:

Find:
```
    \item Circuit:   $Z_{\text{new}} = (T^v)^{-1}Z(T^i)^{-1}$ — different matrices!
```
Replace with:
```
    \item Circuit:   $Z_{\text{new}} = T^v Z(T^i)^{-1}$ — different matrices!
```

**Location 4** — in section B.8 summary table:

Find:
```
        \textbf{Formula} & $A_{\text{new}} = P^{-1}AP$ & $Z_{\text{new}} = (T^v)^{-1}Z(T^i)^{-1}$ \\
```
Replace with:
```
        \textbf{Formula} & $A_{\text{new}} = P^{-1}AP$ & $Z_{\text{new}} = T^v Z(T^i)^{-1}$ \\
```

---

## CHANGE 3 — Replace sections B.6 and B.7 with corrected 2×2 example

**Delete everything from `% ---- B.6 ----` through the end of the B.7 content**
(i.e., from `\subsection{Numerical Example: Similarity Transformation` through
the line ending `\noindent\textbf{Key point:} Different matrices...`).

**Replace with the following LaTeX** (paste exactly):

```latex
% ---- B.6 ----
\subsection{Numerical Example: Similarity Transformation ($A: V \to V$)}
\label{sec:numerical-similarity}

For a linear map within a single space, use the same $P$ on both sides.

\bigskip
\noindent\textbf{Setup:} $V = \mathbb{R}^2$, standard basis.
\[
    A = \begin{bmatrix} 3 & 1 \\ 0 & 2 \end{bmatrix}, \qquad
    P = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}, \qquad
    P^{-1} = \begin{bmatrix} 1 & -1 \\ 0 & 1 \end{bmatrix}.
\]

\noindent\textbf{Similarity transform (same $P$ on both sides):}
\[
    A_{\text{new}} = P^{-1} A P
    = \begin{bmatrix} 1 & -1 \\ 0 & 1 \end{bmatrix}
      \begin{bmatrix} 3 & 1 \\ 0 & 2 \end{bmatrix}
      \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}
    = \begin{bmatrix} 3 & 2 \\ 0 & 2 \end{bmatrix}.
\]

\noindent\textbf{Key point:} Same $P$ on both sides because domain and
codomain are the same space $\mathbb{R}^2$.

% ---- B.7 ----
\subsection{Numerical Example: Circuit Transformation ($Z: V_i \to V_v$)}
\label{sec:numerical-circuit}

For impedance, domain $\neq$ codomain, so we need two different matrices.
We use $N = 2$ lines with the paper's actual definitions.

\bigskip
\noindent\textbf{Setup:}
\begin{itemize}
    \item Impedance matrix (line 1: $2\,\Omega$, line 2: $6\,\Omega$, asymmetric):
        \[
            Z = \begin{bmatrix} 2 & 0 \\ 0 & 6 \end{bmatrix}\ \Omega
        \]
    \item Current transformation $T^i$ (KCL: half-differences and sum):
        \[
            T^i = \begin{bmatrix} \tfrac{1}{2} & -\tfrac{1}{2} \\[4pt] 1 & 1 \end{bmatrix},
            \qquad
            (T^i)^{-1} = \begin{bmatrix} 1 & \tfrac{1}{2} \\[4pt] -1 & \tfrac{1}{2} \end{bmatrix}
        \]
    \item Voltage transformation $T^v$ (KVL: full difference and average):
        \[
            T^v = \begin{bmatrix} 1 & -1 \\[4pt] \tfrac{1}{2} & \tfrac{1}{2} \end{bmatrix}
        \]
\end{itemize}

\bigskip
\noindent\textbf{Step 1 — compute $Z\,(T^i)^{-1}$:}
\[
    Z\,(T^i)^{-1}
    = \begin{bmatrix} 2 & 0 \\ 0 & 6 \end{bmatrix}
      \begin{bmatrix} 1 & \tfrac{1}{2} \\ -1 & \tfrac{1}{2} \end{bmatrix}
    = \begin{bmatrix} 2 & 1 \\ -6 & 3 \end{bmatrix}
\]

\bigskip
\noindent\textbf{Step 2 — apply $T^v$ on the left:}
\[
    Z_{\text{DCM}} = T^v \, Z \, (T^i)^{-1}
    = \begin{bmatrix} 1 & -1 \\ \tfrac{1}{2} & \tfrac{1}{2} \end{bmatrix}
      \begin{bmatrix} 2 & 1 \\ -6 & 3 \end{bmatrix}
    = \begin{bmatrix} 8 & -2 \\ -2 & 2 \end{bmatrix}\ \Omega
\]

\noindent\textbf{Reading the result:}
\begin{itemize}
    \item Diagonal entries: DM impedance $= 8\,\Omega$, CM impedance $= 2\,\Omega$.
    \item Off-diagonal entry $-2\,\Omega \neq 0$ — DM and CM are coupled because
          $Z_1 \neq Z_2$ (asymmetric circuit).
\end{itemize}

\bigskip
\noindent\textbf{Sanity check — symmetric case ($Z_1 = Z_2 = 2\,\Omega$):}
\[
    Z_{\text{DCM}}^{\text{sym}}
    = \begin{bmatrix} 1 & -1 \\ \tfrac{1}{2} & \tfrac{1}{2} \end{bmatrix}
      \begin{bmatrix} 2 & 0 \\ 0 & 2 \end{bmatrix}
      \begin{bmatrix} 1 & \tfrac{1}{2} \\ -1 & \tfrac{1}{2} \end{bmatrix}
    = \begin{bmatrix} 4 & 0 \\ 0 & 1 \end{bmatrix}\ \Omega \quad \checkmark
\]
Diagonal — no coupling when the circuit is symmetric.

\noindent\textbf{Key point:} Different matrices $T^i$ and $T^v$ because
currents and voltages live in different physical spaces (KCL vs.\ KVL).
```

---

## CHANGE 4 — Remove `\appendix` from `appendixA.tex`

In `appendixA.tex`, **delete lines 1–2**:
```
% ============================================================
\appendix
```
So the file now begins with:
```
\section{The DM--CM Transformation Through the Lens of Linear Algebra}
```

---

## CHANGE 5 — Update master file `EMI_DM_CM_Decomposition_Tutorial.tex`

Find:
```
\input{sec2}

\input{appendixA}

\end{document}
```

Replace with:
```
\input{sec2}

\appendix
\input{appendixB}
\input{appendixA}

\end{document}
```

---

## CHANGE 6 — Git commit and push

Run these commands in the repo folder:
```bash
git add appendixA.tex appendixB.tex EMI_DM_CM_Decomposition_Tutorial.tex
git commit -m "Fix appendixB formula + replace 3x3 with 2x2 example + reorder appendices (B before A)"
git push
```

---

## Verification checklist (Claude will check these)
- [ ] No occurrence of `(T^v)^{-1} Z` or `(T^v)^{-1}Z` remains in appendixB
- [ ] B.7 result matrix is `[[8,-2],[-2,2]]`
- [ ] Symmetric sanity check shows `[[4,0],[0,1]]`
- [ ] appendixA has no `\appendix` command at its top
- [ ] Master file has `\appendix` before `\input{appendixB}`
- [ ] Document compiles cleanly on Overleaf
