# Evidence Inventory: EAS-Discrete-Continuous-Duality-Proof

*Date: 2026-07-01*

---

## Evidence Block 1: EAS Axiom A1 and Cardinality Constraint

Claim: EAS axiom A1 states that for a finite cognitive system S with representation space R_S embedded in environment E, card(R_S) < card(E) (cardinality constraint) and no dynamical isomorphism exists between R_S and E.
Source: EAS-Single-Axiom-Foundation.md
URL: File: EAS-Single-Axiom-Foundation.md, Section: 3. The Axiom
Date: 2026
Excerpt: "Axiom A1 (Finitude). Let S be a finite cognitive system physically embedded in environment E, with representation space R_S and dynamics T_R... (a) Cardinality constraint: card(R_S) < card(E). (b) Dynamical non-isomorphism: There does not exist a bijection f: R_S → E such that f ∘ T_R = T_E ∘ f."
Context: Foundation axiom of EAS; verified in Lean 4
Confidence: HIGH [FILE-SOURCED]

---

## Evidence Block 2: Epiplexity Decomposition Definition

Claim: Epiplexity decomposes the time-bounded MDL cost as MDL_T(X) = S_T(X) + H_T(X), where S_T(X) = |P*| is the epiplexity (program length of optimal T-bounded model) and H_T(X) = E_X[-log P*(X)] is the time-bounded entropy.
Source: Finzi et al. (2026), arXiv:2601.03220
URL: https://arxiv.org/abs/2601.03220
Date: 2026-01-06
Excerpt: "P* = arg min_{P ∈ P_T} {|P| + E_X[-log₂ P(X)]}. The structural complexity is S_T(X) = |P★|. The entropic component is H_T(X) = E_X[-log₂ P★(X)]."
Context: Core definition of the epiplexity framework
Confidence: HIGH [SEARCH-SOURCED]

---

## Evidence Block 3: Epiplexity Key Properties

Claim: S_T(X) ≥ 0 and H_T(X) ≥ 0 for all X, T. CSPRNG output has near-maximum H_T and low S_T.
Source: Finzi et al. (2026), arXiv:2601.03220
URL: https://arxiv.org/abs/2601.03220
Date: 2026-01-06
Excerpt: "Key Properties (proven in Finzi et al., 2026): ST_nonneg: S_T(X) ≥ 0 for all X, T; HT_nonneg: H_T(X) ≥ 0 for all X, T; csprng_high_epiplexity: CSPRNG output has near-maximum H_T and low S_T"
Context: Proven properties; also verified in Lean 4 by Apoth3osis Labs
Confidence: HIGH [SEARCH-SOURCED]

---

## Evidence Block 4: EAS Theorem T1 Compression

Claim: EAS Theorem T1 states that under Axiom A1, the representation R_S is necessarily a compressed representation of E. The map f: E → R_S is non-injective, so information is necessarily lost.
Source: EAS-Single-Axiom-Foundation.md
URL: File: EAS-Single-Axiom-Foundation.md, Section: 4.2 T1: Compression Theorem
Date: 2026
Excerpt: "Theorem T1. Under Axiom A1, the representation R_S is necessarily a compressed representation of E. Cognitive systems do not reconstruct the world; they compress it."
Context: Direct consequence of A1(a) via pigeonhole principle
Confidence: HIGH [FILE-SOURCED]

---

## Evidence Block 5: Baez-Fritz-Leinster Entropy Characterization

Claim: Shannon entropy is characterized as the unique functor F: FinMeas → R_+ that is functorial (F(f∘g) = F(f) + F(g)), convex-linear, and continuous. The information loss F(f) = c(H(p) - H(q)).
Source: Baez, Fritz & Leinster (2011)
URL: http://escholarship.org/uc/item/82c9t7gk.pdf
Date: 2011-11-24
Excerpt: "We show that Shannon entropy gives the only concept of information loss that is functorial, convex-linear and continuous. F(f ∘ g) = F(f) + F(g)... F(f) = c(H(p) − H(q))"
Context: Category-theoretic characterization of entropy; foundational for our functor construction
Confidence: HIGH [SEARCH-SOURCED]

---

## Evidence Block 6: Li's Universal Entropy as Natural Transformation

Claim: Shannon entropy can be characterized as the universal monoidal natural transformation from the under-category functor -/LProb_ρ to Δ_R, providing a succinct characterization as a reflection arrow.
Source: Li, C. T. (2024), arXiv:2308.05742
URL: https://arxiv.org/html/2308.05742v3
Date: 2024-04-14
Excerpt: "the Shannon entropy can be characterized as the universal monoidal natural transformation from -/LProb_ρ to the category of integrally closed partially ordered abelian groups... providing a succinct characterization of Shannon entropy as a reflection arrow"
Context: Extends Baez-Fritz-Leinster; shows entropy across different categories are components of a single natural transformation
Confidence: HIGH [SEARCH-SOURCED]

---

## Evidence Block 7: Gelfand-Naimark Duality as Categorical Equivalence

Claim: The Gelfand-Naimark theorem establishes a categorical equivalence (contravariant) between compact Hausdorff spaces and unital commutative C*-algebras. This connects topological (continuous) and algebraic structures.
Source: Rafkin (2016), Dartmouth thesis; nLab
URL: https://math.dartmouth.edu/theses/undergrad/2016/Rafkin-thesis.pdf
Date: 2016
Excerpt: "Gelfand-Naimark theorem identifies the category of C∗-algebras with the second of the subcategories... categorical equivalence between two subcategories"
Context: Analogous duality structure to EAS-Epiplexity; Stone duality is the zero-dimensional special case
Confidence: HIGH [SEARCH-SOURCED]

---

## Evidence Block 8: Existing EAS-Epiplexity Bridge (Conceptual)

Claim: The existing Static-Statistical Bridge paper proposes a three-link chain m → S_T → d_VC connecting EAS cardinality, epiplexity, and VC dimension, but acknowledges these connections are conceptual rather than proven theorems.
Source: EAS-Static-Statistical-Bridge-v2.md
URL: File: EAS-Static-Statistical-Bridge-v2.md, Section: 3. The Static-Statistical Bridge
Date: 2026-07-01
Excerpt: "We propose a three-link conceptual chain: m (environment cardinality) → S_T (epistemic residue under computational bounds) → h (VC dimension). While the philosophical motivations are clear, we acknowledge that the mathematical connections between these quantities require further rigorous development."
Context: Prior work establishing the conceptual framework; our Proposition 1 proves the first link rigorously
Confidence: HIGH [FILE-SOURCED]

---

## Evidence Block 9: Epiplexity Lean 4 Formalization

Claim: The Epiplexity framework has been formalized in Lean 4 by Apoth3osis Labs with 23 modules, 80+ theorems, and 0 sorry placeholders, including MDL decomposition, CSPRNG high epiplexity, and OWP factorization hardness.
Source: Apoth3osis Labs
URL: https://www.apoth3osis.io/paper-proof-code/epiplexity
Date: 2026
Excerpt: "Machine-checked Lean 4 formalization of Finzi et al.'s Epiplexity framework. Time-bounded complexity via MDL decomposition: S_T(X) measures code length (structure), H_T(X) measures cross-entropy (noise). CSPRNG indistinguishability implies high epiplexity. One-way permutation implies factorization hardness. 23 modules, 0 sorry."
Context: Independent formal verification of epiplexity properties; potential foundation for unified EAS+Epiplexity formalization
Confidence: HIGH [SEARCH-SOURCED]

---

## Evidence Block 10: Kolmogorov Complexity and Time-Bounded Versions

Claim: Time-bounded Kolmogorov complexity K^t(x) = min{|p| : U(p) = x in ≤ t steps} provides a computable approximation to Kolmogorov complexity. As t → ∞, K^t(x) → K(x), but convergence is non-uniform (depends on x).
Source: Allender et al.
URL: https://people.cs.rutgers.edu/~allender/papers/chapter.pdf
Date: N/A
Excerpt: "Complexity theory provides a setting in which one can associate to any recursive set L a function t_L on the natural numbers... we consider a means of using time-bounded Kolmogorov complexity to define a function K_L that measures a different aspect of the complexity of L."
Context: Establishes the time-bounded complexity framework; supports our analysis that S_T → K convergence is non-uniform
Confidence: MEDIUM [SEARCH-SOURCED]
