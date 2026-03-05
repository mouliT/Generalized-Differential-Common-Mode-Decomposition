<!--
  PAPER CONTEXT FILE  —  for use with Claude
  ─────────────────────────────────────────────
  How to use:
  1. Attach this file and the PNG images to a Claude conversation.
  2. Say: "Using the context file below, explain [topic] as Feynman
     would — starting from [basic concept] and building up step by step."
  3. The 'Referenced in paper' sentences are the authors' own words
     about each figure — the most reliable guide to its meaning.
-->

# Paper Context: GDCMDMCEAP — Generalized_Differential-Common-Mode_Decomposition_for_Modeling_Conducted_Emissions_in_Asymmetric_Power_Electronic_Systems.pdf

*Generated: 2026-03-05  |  Figures: 7  |  Pages: 6*

---

## Paper Overview

*(Auto-extracted from the first pages — edit for accuracy)*

IEEE TRANSACTIONS ON POWER ELECTRONICS, VOL. 33, NO. 8, AUGUST 2018 6461

Generalized Differential-Common-Mode Decomposition for Modeling

Conducted Emissions in Asymmetric Power Electronic Systems

Aaron D. Brovont , Member, IEEE

Abstract—This paper proposes a generalized approach to decompose mixed-mode (MM) conducted emissions in power electronic systems into their differential and common-mode components and modal couplings. Speciﬁcally, a pair of transformation matrices are deﬁned that map a sys- tem of MM line-to-ground voltage equations to an equivalent decomposed differential-common-mode set. The result provides exact mathematical re- lationships for the modal couplings induced by asymmetries between the lines described by the voltage equations. As an example, the proposed trans- formation is applied to generate two different, but equally valid models for studying the effect of unbalanced parasitic capacitances in a multichip power module on the common-mode (CM) behavior of a half-bridge con- verter. The two models provide different perspectives on the mechanisms driving CM current through the system. It is found that one model is best suited to study leakage current through the module while the other pro- vides greater insight into currents circulating internally and its impact on the larger system.

Index Terms—Electromagnetic compatibility, electromagnetic interfer- ence, modeling, multichip modules, transforms.

MAJOR impediment to the ongoing proliferation of power elec- tronic systems is the spectrally rich emissions produced by high- frequency and high-edge-rate switching. Preventing said emissions— of which common-mode (CM) voltage and current comprise an im- portant subset—from producing electromagnetic interference (EMI) requires dedicated suppression techniques. These include passive solu- tions, such as CM chokes and EMI ﬁlters [1]–[4] as well as active solu- tions such as cancellation circuitry [5]–[7], ad hoc converter topologies [8]–[11], and specialized switching strategies [12]–[14].

CM equivalent circuits [1], [15] have been a powerful tool in inform- ing these mitigation efforts. However, there has been relatively little effort to formalize their derivation or extend their applicability to asym- metric systems in general. Rather, recent studies on the effectiveness of EMI suppression methods in the presence of circuit asymmetries and the transformation of emissions between modes have relied on in- depth analysis and experimentation with mixed-mode (MM) models [11], [16] or limited the scope of their analysis to a particular compo- nent [17].

Recently, a systematic CM modeling approach was proposed wherein the key insight was deﬁning CM voltage with respect to an ar- bitrary reference that is distinct from ground [18]. This “extra” ﬂoating reference facilitates the piecemeal transformation of MM system com- ponents (i.e., electric machines, transmission lines, passive loads, etc.,

Manuscript received September 24, 2017; revised November 23, 2017; ac- cepted December 21, 2017. Date of publication January 10, 2018; date of current version April 20, 2018.

The author is with the Department …

---

## Figure Index

| Figure | Page | File | Section |
|--------|------|------|---------|
| Fig. 1 | 1 | `GDCMDMCEAP_Fig1_page01.png` | IEEE TRANSACTIONS ON POWER ELECTRONICS, VOL. 33, NO. 8, AUGUST 2018 |
| Fig. 2 | 3 | `GDCMDMCEAP_Fig2_page03.png` | T = |
| Fig. 3 | 3 | `GDCMDMCEAP_Fig3_page03.png` | T = |
| Fig. 4 | 4 | `GDCMDMCEAP_Fig4_page04.png` | TABLE II |
| Fig. 5 | 4 | `GDCMDMCEAP_Fig5_page04.png` | TABLE I |
| Fig. 6 | 5 | `GDCMDMCEAP_Fig6_page05.png` | TABLE III |
| Fig. 7 | 5 | `GDCMDMCEAP_Fig7_page05.png` | TABLE III |

---

## Figure 1 — Page 1

**File:** `GDCMDMCEAP_Fig1_page01.png`  
**Dimensions:** 1416 x 756 px  
**Section:** IEEE TRANSACTIONS ON POWER ELECTRONICS, VOL. 33, NO. 8, AUGUST 2018

**Caption:**
> Fig. 1. Diagram for DM and CM deﬁnitions and decomposition demonstra- tion.

**Referenced in paper:** *(none found — may be a scanned PDF)*

**Feynman entry point:** *(Claude: fill in)*
> What is the simplest real-world analogy for what this figure shows?
> What single concept does it primarily illustrate,
> and what prerequisite knowledge does a reader need?

---

## Figure 2 — Page 3

**File:** `GDCMDMCEAP_Fig2_page03.png`  
**Dimensions:** 1530 x 955 px  
**Section:** T =

**Caption:**
> Fig. 2. Half-bridge testbed for SiC MCPM EMI characterization with unbal- anced parasitic capacitors.

**Referenced in paper:** *(none found — may be a scanned PDF)*

**Feynman entry point:** *(Claude: fill in)*
> What is the simplest real-world analogy for what this figure shows?
> What single concept does it primarily illustrate,
> and what prerequisite knowledge does a reader need?

---

## Figure 3 — Page 3

**File:** `GDCMDMCEAP_Fig3_page03.png`  
**Dimensions:** 1530 x 941 px  
**Section:** T =

**Caption:**
> Fig. 3. Three sections and voltage deﬁnitions for generating the CEM of the half-bridge converter.

**Referenced in paper:** *(none found — may be a scanned PDF)*

**Feynman entry point:** *(Claude: fill in)*
> What is the simplest real-world analogy for what this figure shows?
> What single concept does it primarily illustrate,
> and what prerequisite knowledge does a reader need?

---

## Figure 4 — Page 4

**File:** `GDCMDMCEAP_Fig4_page04.png`  
**Dimensions:** 1375 x 817 px  
**Section:** TABLE II

**Caption:**
> Fig. 4. CEM of the half-bridge testbed.

**Referenced in paper:** *(none found — may be a scanned PDF)*

**Feynman entry point:** *(Claude: fill in)*
> What is the simplest real-world analogy for what this figure shows?
> What single concept does it primarily illustrate,
> and what prerequisite knowledge does a reader need?

---

## Figure 5 — Page 4

**File:** `GDCMDMCEAP_Fig5_page04.png`  
**Dimensions:** 1454 x 1838 px  
**Section:** TABLE I

**Caption:**
> Fig. 5. Simulated current through the module baseplate using the detailed MM model and the approximate CEM for (a) k = 1 and Cp,tot = 200 pF, (b) k = 0.4 and Cp,tot = 200 pF, and (c) k = 0.4 and Cp,tot = 500 pF. The waveforms are overlaid.

**Referenced in paper:** *(none found — may be a scanned PDF)*

**Feynman entry point:** *(Claude: fill in)*
> What is the simplest real-world analogy for what this figure shows?
> What single concept does it primarily illustrate,
> and what prerequisite knowledge does a reader need?

---

## Figure 6 — Page 5

**File:** `GDCMDMCEAP_Fig6_page05.png`  
**Dimensions:** 1430 x 942 px  
**Section:** TABLE III

**Caption:**
> Fig. 6. Two sections and voltage deﬁnitions for generating the alternative CEM of the half-bridge converter.

**Referenced in paper:** *(none found — may be a scanned PDF)*

**Feynman entry point:** *(Claude: fill in)*
> What is the simplest real-world analogy for what this figure shows?
> What single concept does it primarily illustrate,
> and what prerequisite knowledge does a reader need?

---

## Figure 7 — Page 5

**File:** `GDCMDMCEAP_Fig7_page05.png`  
**Dimensions:** 1418 x 816 px  
**Section:** TABLE III

**Caption:**
> Fig. 7. Alternative CEM of the half-bridge testbed.

**Referenced in paper:** *(none found — may be a scanned PDF)*

**Feynman entry point:** *(Claude: fill in)*
> What is the simplest real-world analogy for what this figure shows?
> What single concept does it primarily illustrate,
> and what prerequisite knowledge does a reader need?

---
