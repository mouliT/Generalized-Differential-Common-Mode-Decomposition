# TASK 002 — Add Three TikZ Figures to appendixA.tex

**Assigned to:** MiniMax M2.5
**Verified by:** Claude (all coordinates and LaTeX code pre-checked)
**File to edit:** `appendixA.tex`

---

## Overview

Insert **three TikZ figures** into `appendixA.tex` at three specific locations.
Do NOT change any existing text — only INSERT the code blocks below at the
specified anchor points.

---

## FIGURE 1 — "Same vector, two coordinate systems" (goes in §A.1)

**Location:** Insert BEFORE this exact line:

```
\begin{statebox}[Strang's Framing, Applied Here]
```

**Code to insert** (paste the entire block):

```latex
% --- Figure: change of basis (same vector, two coordinate systems) ---
\begin{figure}[H]
\centering
\begin{tikzpicture}[>=Stealth, font=\small, scale=0.85]

  %=== Left panel: per-line coordinate system ===
  \begin{scope}
    \draw[->] (-0.3,0) -- (4.2,0) node[right] {$i_1$\,(A)};
    \draw[->] (0,-0.3) -- (0,2.6) node[above] {$i_2$\,(A)};
    \foreach \x in {1,2,3}
      \draw (\x,3pt)--(\x,-3pt) node[below,font=\scriptsize] {\x};
    \foreach \y in {1,2}
      \draw (3pt,\y)--(-3pt,\y) node[left,font=\scriptsize] {\y};
    % Current vector
    \draw[->, very thick, red!80!black] (0,0) -- (3,1)
      node[above right] {$\mathbf{i}$};
    % Projection dashes
    \draw[dashed,gray!70] (3,0)--(3,1)--(0,1);
    % Coordinate annotation
    \node[blue!70!black, font=\scriptsize\bfseries] at (1.5,-0.8)
      {per-line: $(i_1,\,i_2)=(3,\,1)$};
    \node[font=\bfseries\footnotesize, emidark] at (1.8, 2.8)
      {Original basis};
  \end{scope}

  %=== Arrow between panels ===
  \draw[->, very thick, blue!70!black]
    (4.5,1.2) -- (6.0,1.2)
    node[midway,above,font=\scriptsize] {$\TiN$}
    node[midway,below,font=\scriptsize\itshape] {change basis};

  %=== Right panel: DM-CM coordinate system ===
  \begin{scope}[shift={(6.5,0)}]
    \draw[->] (-0.3,0) -- (2.5,0) node[right] {$i_{\mathrm{DM}}$\,(A)};
    \draw[->] (0,-0.3) -- (0,4.8) node[above] {$i_{\mathrm{CM}}$\,(A)};
    \foreach \x in {1,2}
      \draw (\x,3pt)--(\x,-3pt) node[below,font=\scriptsize] {\x};
    \foreach \y in {1,2,3,4}
      \draw (3pt,\y)--(-3pt,\y) node[left,font=\scriptsize] {\y};
    % Same physical current, new coordinates
    \draw[->, very thick, red!80!black] (0,0) -- (1,4)
      node[right] {$\mathbf{i}$};
    % Projection dashes
    \draw[dashed,gray!70] (1,0)--(1,4)--(0,4);
    % Coordinate annotation
    \node[blue!70!black, font=\scriptsize\bfseries] at (0.8,-0.8)
      {DM-CM: $(i_{\mathrm{DM}},\,i_{\mathrm{CM}})=(1,\,4)$};
    \node[font=\bfseries\footnotesize, emidark] at (0.8, 5.2)
      {New basis};
  \end{scope}

\end{tikzpicture}
\caption{The same physical current state — line~1 carries $3\,\mathrm{A}$,
line~2 carries $1\,\mathrm{A}$ — expressed in two coordinate systems.
Left: per-line basis, coordinates $(3,\,1)$.
Right: DM-CM basis, $i_{\mathrm{DM}}=(3-1)/2=1\,\mathrm{A}$
and $i_{\mathrm{CM}}=3+1=4\,\mathrm{A}$.
The red arrow is the same physical current; only the numbers change.}
\label{fig:appA_basis_change}
\end{figure}
% -------------------------------------------------------------------

```

---

## FIGURE 2 — Commutative diagram (goes in §A.1, after the statebox)

**Location:** Insert AFTER this exact line:

```
\end{statebox}

% ---- A.2 ----
```

Insert BEFORE `% ---- A.2 ----`, i.e. between `\end{statebox}` and `% ---- A.2 ----`.

**Code to insert:**

```latex
% --- Figure: commutative diagram showing Q*A*P^{-1} ---
\begin{figure}[H]
\centering
\begin{tikzpicture}[>=Stealth, font=\small,
  mybox/.style={draw=#1, fill=#1!15, rounded corners=5pt,
                minimum width=3.4cm, minimum height=1.1cm, align=center}]

  % Four corner nodes (explicit positions)
  \node[mybox=blue!60!black] (TL) at (0,   0)
    {Per-line currents\\[2pt]$[i_1,\ldots,i_N]^T$};
  \node[mybox=orange!80!black] (TR) at (8,   0)
    {Per-line voltages\\[2pt]$[v_{1P},\ldots,v_{NP}]^T$};
  \node[mybox=blue!60!black] (BL) at (0,  -3.8)
    {DM-CM currents\\[2pt]$[i_{\mathrm{DM}},\ldots,i_{\mathrm{CM}}]^T$};
  \node[mybox=orange!80!black] (BR) at (8,  -3.8)
    {DM-CM voltages\\[2pt]$[v_{\mathrm{DM}},\ldots,v_{\mathrm{CM}}]^T$};

  % Top: Z (per-line impedance)
  \draw[->, thick] (TL) -- (TR)
    node[midway, above] {$\mathbf{Z}$\quad(per-line basis)};

  % Bottom: Z_DCM (our goal)
  \draw[->, thick, red!70!black, line width=1.2pt] (BL) -- (BR)
    node[midway, below] {$\mathbf{Z}_{\mathrm{DCM}}$\quad(DM-CM basis)};

  % Left: T^i_N (current basis change)
  \draw[->, thick, blue!70!black] (TL) -- (BL)
    node[midway, left] {$\TiN$\quad};

  % Right: T^v_N (voltage basis change)
  \draw[->, thick, olive!80!black] (TR) -- (BR)
    node[midway, right] {\quad$\TvN$};

  % Result formula in a box below
  \node[draw=red!50!black, fill=red!5, rounded corners=4pt,
        font=\small, align=center] at (4, -5.6)
    {$\mathbf{Z}_{\mathrm{DCM}}
       = \underbrace{\TvN}_{\text{codomain}} \mathbf{Z}
         \underbrace{(\TiN)^{-1}}_{\text{domain}}$
     \quad (two \emph{different} matrices — not $P^{-1}AP$)};

\end{tikzpicture}
\caption{Commutative diagram for the DM-CM change of basis.
Following the top path and then the right arrow
($\TvN \circ \mathbf{Z} \circ (\TiN)^{-1}$) must give the same
result as following the bottom arrow ($\mathbf{Z}_{\mathrm{DCM}}$).
Because current space and voltage space are \emph{different physical
spaces}, they need \emph{independent} basis-change matrices —
unlike the similarity transform $P^{-1}AP$, which uses the same
$P$ on both sides.}
\label{fig:appA_commutative}
\end{figure}
% -------------------------------------------------------------------

```

---

## FIGURE 3 — DM-CM coupling block diagram (goes in §A.3)

**Location:** Insert BEFORE this exact line:

```
\begin{eqnbox}[Strang's Lesson, Inverted]
```

**Code to insert:**

```latex
% --- Figure: symmetric (decoupled) vs asymmetric (coupled) ---
\begin{figure}[H]
\centering
\begin{tikzpicture}[>=Stealth, font=\small,
  mode/.style={draw=#1, fill=#1!12, rounded corners=4pt,
               minimum width=2.2cm, minimum height=0.9cm,
               align=center, font=\small\bfseries}]

  %=== Left panel: Symmetric k=1 (no coupling) ===
  \begin{scope}[shift={(-4.5, 0)}]
    \node[font=\bfseries\footnotesize, emidark] at (1.0, 2.0)
      {Symmetric ($k = 1$)};

    \node[mode=blue!60!black]   (DM1) at (1.0,  0.9) {DM};
    \node[mode=orange!70!black] (CM1) at (1.0, -0.9) {CM};

    % Input arrows
    \draw[->, thick] (-1.0, 0.9) -- (DM1.west)
      node[midway, above, font=\scriptsize] {$I_{\mathrm{DM}}$};
    \draw[->, thick] (-1.0,-0.9) -- (CM1.west)
      node[midway, below, font=\scriptsize] {$I_{\mathrm{CM}}$};
    % Output arrows
    \draw[->, thick] (DM1.east) -- (3.0, 0.9)
      node[midway, above, font=\scriptsize] {$V_{\mathrm{DM}}$};
    \draw[->, thick] (CM1.east) -- (3.0,-0.9)
      node[midway, below, font=\scriptsize] {$V_{\mathrm{CM}}$};
    % No coupling label
    \node[gray!60!black, font=\scriptsize\itshape] at (1.0, 0)
      {no coupling};
    % Matrix structure
    \node[font=\scriptsize] at (1.0, -2.2)
      {$\mathbf{Z}_{\mathrm{DCM}}=
        \begin{bmatrix} {*} & 0 \\ 0 & {*} \end{bmatrix}$};
  \end{scope}

  %=== Right panel: Asymmetric k≠1 (coupling appears) ===
  \begin{scope}[shift={(3.0, 0)}]
    \node[font=\bfseries\footnotesize, emidark] at (1.0, 2.0)
      {Asymmetric ($k \neq 1$)};

    \node[mode=blue!60!black]   (DM2) at (1.0,  0.9) {DM};
    \node[mode=orange!70!black] (CM2) at (1.0, -0.9) {CM};

    % Input arrows
    \draw[->, thick] (-1.0, 0.9) -- (DM2.west)
      node[midway, above, font=\scriptsize] {$I_{\mathrm{DM}}$};
    \draw[->, thick] (-1.0,-0.9) -- (CM2.west)
      node[midway, below, font=\scriptsize] {$I_{\mathrm{CM}}$};
    % Output arrows
    \draw[->, thick] (DM2.east) -- (3.0, 0.9)
      node[midway, above, font=\scriptsize] {$V_{\mathrm{DM}}$};
    \draw[->, thick] (CM2.east) -- (3.0,-0.9)
      node[midway, below, font=\scriptsize] {$V_{\mathrm{CM}}$};

    % Coupling: DM -> CM (left side, going down)
    \draw[->, thick, red!75!black]
      (DM2.west) -- ++(-0.55,0)
      node[above, font=\scriptsize, red!75!black] {$z_{21}$}
      -- ++(0,-1.8) -- (CM2.west);
    % Coupling: CM -> DM (left side, going up, further left)
    \draw[->, thick, red!75!black]
      (CM2.west) -- ++(-0.95,0)
      node[below, font=\scriptsize, red!75!black] {$z_{12}$}
      -- ++(0,1.8) -- (DM2.west);

    % Matrix structure
    \node[font=\scriptsize] at (1.0, -2.2)
      {$\mathbf{Z}_{\mathrm{DCM}}=
        \begin{bmatrix} {*} & z_{12} \\ z_{21} & {*} \end{bmatrix}$};
  \end{scope}

\end{tikzpicture}
\caption{Effect of the asymmetry parameter $k$ on modal coupling.
\textbf{Left} ($k=1$, symmetric): $\mathbf{Z}_{\mathrm{DCM}}$ is diagonal —
DM and CM equations are fully independent, each mode drives only its
own response.
\textbf{Right} ($k\neq 1$, asymmetric): off-diagonal entries
$z_{12},\,z_{21}\neq 0$ appear — a DM current source produces a CM voltage
and vice versa.
These cross-terms are the DM-to-CM noise injection mechanism that
conducted-emissions standards seek to limit.}
\label{fig:appA_coupling}
\end{figure}
% -------------------------------------------------------------------

```

---

## CHANGE 4 — Git commit and push

After all three insertions:

```bash
cd "C:\Users\tmouli\Documents\AI_trainig_data\Vignesh\ECCE_2026_repo"
git add appendixA.tex
git commit -m "appendixA: add three TikZ figures (basis change, commutative diagram, coupling blocks)"
git push
```

---

## Verification checklist (report back to Claude)
- [ ] Figure 1 appears just before `\begin{statebox}[Strang's Framing`
- [ ] Figure 2 appears between `\end{statebox}` and `% ---- A.2 ----`
- [ ] Figure 3 appears just before `\begin{eqnbox}[Strang's Lesson, Inverted]`
- [ ] No existing text was modified — only insertions
- [ ] Git push succeeded
- [ ] (Optional) Overleaf compiles without errors
