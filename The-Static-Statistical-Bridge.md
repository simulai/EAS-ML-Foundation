# The Static-Statistical Bridge: Epiplexity as the Link between Epistemic Axioms and Learning Theory

**Jing Zhang**

*Independent Researcher*

*ORCID: 0009-0008-3136-2457*

---

## Abstract

Information theory has long operated under the implicit assumption of computationally unbounded observers. Shannon entropy measures what *unlimited* observers can transmit; Kolmogorov complexity measures what *unlimited* Turing machines can compress. Neither quantity speaks to what *finite* systems—embedded in physical environments with bounded computational resources—can actually learn. In this paper, we establish the mathematical foundations connecting the Epistemic Axiomatic System (EAS, Zhang 2026) and statistical learning theory through **epiplexity** ($S_T$, Finzi et al. 2026)—a time-bounded information measure quantifying structural information extractable by computationally bounded observers.

We prove three theorems rigorously connecting EAS with Epiplexity. **Theorem A** (Information-Theoretic Lower Bound) establishes that the time-bounded entropy satisfies $H_T(X) \geq \log_2(m/n)$ bits, where $m = \mathrm{card}(E)$ and $n = \mathrm{card}(R_S)$, proving that the EAS cardinality constraint from Axiom A1 imposes a hard information-theoretic floor on epiplexity's entropic component. **Theorem B** (Faithfulness of the Bridge Functor) constructs an explicit functor $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ between the finite-object categories of EAS and Epiplexity, and proves that $\Phi$ is faithful but not full—the Epiplexity category contains morphisms (stochastic maps, approximate simulations) that have no EAS pre-image, reflecting the fact that computationally bounded observers can represent transitions that no deterministic finite system can realize. **Theorem C** (Three-Way Entropy Decomposition) decomposes the information loss $H_T(X) - \log_2(m/n)$ into three non-negative components—distributional distortion $\Delta_{\mathrm{dist}}$, representation indexing cost $\Delta_{\mathrm{index}}$, and computational overhead $\Delta_{\mathrm{comp}}$—each with a precise information-theoretic and operational meaning, with the key finding that $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n$ (a purely combinatorial quantity).

Together, these three theorems upgrade the EAS–Epiplexity connection from a conceptual framework to a rigorous mathematical foundation, establishing the **discrete–continuous duality** (a descriptive term we introduce for the asymmetric faithful-embedding relationship between $\mathbf{EAS}_{\mathbf{Fin}}$ and $\mathbf{Epipl}_{\mathbf{Fin}}$; this is not a duality in the classical mathematical sense of an equivalence of categories) as a structural principle: discrete cardinality constraints set hard information-theoretic floors, the passage from discrete to continuous is faithful but not reversible, and continuous measurements refine discrete bounds by decomposing the residual gap into independently interpretable components.

**Important limitation:** The core quantitative results of this paper—particularly Theorem C's three-way decomposition and the indexing–distortion trade-off $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n$—assume a uniformly distributed environment. Non-uniform distributions introduce additional complexity; see §8.2, Limitation 3.

**Keywords:** epiplexity, epistemic axioms, VC dimension, statistical learning theory, bounded rationality, computational complexity, information theory, category theory, discrete-continuous duality, bridge functor

---

## 1. Introduction

### 1.1 The Information-Theoretic Gap

Since Shannon's seminal 1948 paper, information theory has provided the mathematical framework for understanding communication, compression, and—more recently—learning. The Shannon entropy $H(X)$ measures the expected surprise of a random variable $X$; the mutual information $I(X; Y)$ measures the reduction in uncertainty about $X$ given knowledge of $Y$. These quantities assume observers with unbounded computational capacity: the encoder and decoder can compute arbitrarily complex functions, invert arbitrary permutations, and solve any decidable problem.

Kolmogorov complexity $K(x)$ addressed one limitation by measuring the shortest program that produces a string $x$, introducing the crucial insight that information is observer-dependent. However, $K(x)$ remains uncomputable and still assumes unbounded computation for the compressor. A related limitation: neither Shannon nor Kolmogorov has anything meaningful to say about what a *finite* system—physically embedded in an environment, with bounded time and memory—can actually learn from data.

This gap matters enormously for AI. Modern machine learning systems are paradigmatically bounded observers: they have finite parameters (hence bounded representational capacity), finite training time (hence bounded computational resources), and finite memory (hence bounded working memory). What these systems can learn is not determined by the true complexity of the data-generating process, but by what structure is *accessible* to bounded computation.

### 1.2 Cross-Domain Motivation: EAS and Epiplexity

EAS and epiplexity emerged from different disciplinary backgrounds with related motivations:

| Aspect | EAS (Zhang, 2026a) | Epiplexity (Finzi et al., 2026) |
|--------|-------------------|--------------------------------|
| **Origin** | Epistemology / philosophy of mind | Information theory / machine learning |
| **Starting point** | Single axiom: finite systems cannot be isomorphic to environment | Three paradoxes in modern ML that Shannon/Kolmogorov cannot resolve |
| **Method** | Axiomatic derivation (Lean 4 verified) | Information-theoretic analysis + empirical validation |
| **Core intuition** | Distinction → compression → concepts → truth (T0–T4) | $S_T$ measures extractable structure under bounded computation |
| **Key quantity** | Epistemic residue $d = m - n$ | Epiplexity $S_T$ |

Both works appeared in early 2026. Neither cites the other. Both are motivated by intuitions about **computational boundedness as a fundamental constraint on cognition and learning**. This parallel motivation across domains—philosophy of mind and applied information theory—suggests that the mathematical connections between these frameworks warrant rigorous investigation.

### 1.3 The Epistemic Axiomatic System

The Epistemic Axiomatic System (Zhang, 2026) provides a minimal axiomatic foundation for epistemology based on a single axiom:

**Axiom A1 (Finitude).** *No finite cognitive system can be isomorphic to its environment.*

Formally, for a system $S$ with representation space $R_S$ embedded in environment $E$:
- (a) **Cardinality constraint:** $\mathrm{card}(R_S) < \mathrm{card}(E)$
- (b) **Dynamical non-isomorphism:** no bijection $f: R_S \to E$ satisfies $f \circ T_R = T_E \circ f$

From A1, eight theorems follow (T0–T7), including:
- T0: Distinction is inevitable (non-injectivity forces equivalence classes)
- T1: Compression is necessary (information loss under non-injective mapping)
- T2: Concepts are stable equivalence classes
- T4: Truth as fixed-point convergence
- T5: Functional decodability and dynamical trisection ($\chi_{\min} = 3$)
- T7: Intelligence bound $I(S) \leq m^2$

The entire derivation has been verified in Lean 4 (v4.7.0), with a single axiom and zero `sorry` placeholders.

### 1.4 The Discrete-Continuous Relationship: Beyond Bridging

The three theorems proved in this paper are technical contributions: they establish lower bounds, construct functors, and decompose information loss. But the significance of these results extends beyond their mathematical content. They collectively point toward an *epistemological* thesis about the relationship between discrete and continuous descriptions of cognition.

Three traditional views have dominated the discourse on discrete-continuous relationships: (1) the *approximation view*, which treats discrete structures as approximations of an underlying continuous reality; (2) the *limit view*, which treats continuous descriptions as limits of discrete processes; and (3) the *bridging view*, which treats discrete and continuous as two separate worlds requiring a connecting bridge. Each view captures a partial truth but misses a deeper structural insight.

The EAS–Epiplexity interface suggests a fourth perspective: **discrete and continuous are not two worlds that need bridging, but two observation modes of the same phenomenon.** The discrete mode (EAS: cardinality constraints, quotient structures, deterministic morphisms) and the continuous mode (Epiplexity: probability distributions, stochastic morphisms, bounded computation) are complementary lenses on what finite cognitive systems can know. The information loss $\log_2(m/n)$ is not an engineering limitation to be minimized but the *inevitable cost of observation itself*—any finite system that resolves an environment with $m$ states into $n$ representational states must, by the pigeonhole principle, sacrifice at least $\log_2(m/n)$ bits of information. This loss is not a deficiency of the discrete mode; it is the price of any observation that compresses the world into a representation.

### 1.5 This Paper: From Conceptual Framework to Mathematical Foundation

The prior version of this work (Zhang, 2026b) explored the connections between EAS and statistical learning theory through epiplexity as a conceptual framework, proposing a three-link chain:

$$\underbrace{m}_{\text{environment cardinality}} \;\xrightarrow{\text{conceptual}}\; \underbrace{S_T}_{\text{epistemic residue}} \;\xrightarrow{\text{conceptual}}\; \underbrace{h}_{\text{VC dimension}}$$

While the philosophical motivations were clear, that paper acknowledged that the mathematical connections between these quantities required further rigorous development, and several proposed results were presented as conjectures rather than theorems.

In this paper, we upgrade the framework from a conceptual proposal to a mathematical foundation by proving three theorems that rigorously establish the EAS–Epiplexity connection:

1. **Theorem A** proves the first link: the EAS cardinality constraint $m/n$ provides a hard lower bound on the time-bounded entropy $H_T(X) \geq \log_2(m/n)$. This is no longer a conjecture—it is a theorem with a complete proof using Gibbs' inequality, the chain rule, and Jensen's inequality.

2. **Theorem B** constructs the categorical bridge: an explicit functor $\Phi$ from $\mathbf{EAS}_{\mathbf{Fin}}$ to $\mathbf{Epipl}_{\mathbf{Fin}}$ that is faithful but not full. The non-fullness captures a genuine structural asymmetry—Epiplexity's stochastic morphisms are strictly richer than EAS's deterministic morphisms.

3. **Theorem C** provides the analytic refinement: the information loss decomposes into $\log_2(m/n) + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{index}} + \Delta_{\mathrm{comp}}$, with each component independently interpretable and optimizable.

These three theorems together establish the **discrete–continuous duality** as the mathematical backbone of the bridge: the discrete, finitary constraints of EAS generate unavoidable information loss, which the continuous, observer-relative framework of Epiplexity quantifies and decomposes.

### 1.6 Notation and Conventions

| Symbol | Meaning |
|--------|---------|
| $E$ | Environment (finite type, $\mathrm{card}(E) = m$) |
| $R_S$ | Representation space of cognitive system $S$ ($\mathrm{card}(R_S) = n$) |
| $f: E \to R_S$ | Representation map (non-injective by A1) |
| $T_E, T_R$ | Dynamics on $E$ and $R_S$ respectively |
| $\sim_f$ | Kernel equivalence relation: $x \sim_f y \iff f(x) = f(y)$ |
| $P^*$ | Optimal $T$-bounded program minimizing $|P| + \mathbb{E}[-\log_2 P(X)]$ |
| $S_T(X)$ | Epiplexity: $S_T(X) = |P^*|$ |
| $H_T(X)$ | Time-bounded entropy: $H_T(X) = \mathbb{E}[-\log_2 P^*(X)]$ |
| $\mathcal{P}_T$ | Class of $T$-bounded probabilistic programs |
| $m/n$ | Cardinality ratio (compression factor) |
| $\log$ | Base-2 logarithm throughout |

All logarithms are base 2. All finite types are modeled as $\mathrm{Fin}\, k$ in the Lean 4 formalization. We work in the setting where $2 \leq n < m$ (non-degenerate cognitive systems with at least two representational states).

**Notation note on $S_T$ vs. $K_T$.** This paper follows the Apoth3osis Labs formalization in using $S_T(X)$ for epiplexity. Finzi et al.'s original paper (arXiv:2601.03220) and some secondary sources (e.g., mbottoni, 2026) use $K_T(X)$ for the same quantity. The two symbols refer to the identical concept: the description length of the optimal $T$-bounded program. We adopt $S_T$ for consistency with the Lean 4 formalization.

---

## 2. Preliminaries

### 2.1 The Epistemic Axiomatic System (EAS)

We review the formal elements of EAS required for the bridge. Full details are available in Zhang (2026a).

**Environment and Representation.** Let $E$ be the environment (finite set of states, $\mathrm{card}(E) = m$) and $R_S$ be the representation space of cognitive system $S$ (finite set, $\mathrm{card}(R_S) = n$). A representation map is a function $f: E \to R_S$.

**Quotient Structure.** For any $f$, the kernel equivalence relation $\sim_f$ partitions $E$ into equivalence classes $[x]_f = \{y \in E : f(y) = f(x)\}$. The quotient space $E / \sim_f$ has cardinality $n$, and the canonical projection $\pi: E \to E / \sim_f$ is the **quotient map**.

**Axiom A1.** $\mathrm{card}(R_S) < \mathrm{card}(E)$; equivalently, $n < m$.

**Epistemic Residue.** The gap $d = m - n$ is the epistemic residue: the number of environmental distinctions that *cannot* be preserved in the representation. The compression ratio $m/n > 1$ quantifies the factor by which the environment exceeds the system's representational capacity.

**Key Theorems (verified in Lean 4).**
- **T0 (Inevitability of Distinction):** Any $f: E \to R_S$ with $n < m$ is non-injective, inducing a non-trivial equivalence relation.
- **T1 (Compression):** Any $f: E \to R_S$ with $n < m$ is non-injective; information is necessarily lost.
- **T5a (Functional Decodability):** Any persistently adaptive system must support three functionally decodable streams: Generator, Executor, Verifier.
- **T5b (Dynamical Trisection):** $\chi_{\min} = 3$.

**Formalization.** EAS has been fully formalized in Lean 4, verified; formalization archived at Zenodo DOI 10.5281/zenodo.21038854 (the GitHub URL https://github.com/simulai/EAS-Paper could not be independently verified as of this writing; `github.com/simulai` resolves to an unrelated IBM physics-informed ML project).

### 2.2 Epiplexity

We review the formal definition of epiplexity from Finzi et al. (2026).

**Definition 2.1** (Time-Bounded Programs). Let $\mathcal{P}_T$ be the set of programs that run in at most $T$ steps. For a distribution $X$, let $P \in \mathcal{P}_T$ be a program such that $P()$ generates $X$.

**Definition 2.2** (Time-Bounded Description Length). The MDL cost under time bound $T$ decomposes as:

$$\mathrm{MDL}_T(X) = S_T(X) + H_T(X)$$

where, following Finzi et al. (2026):
- $S_T(X) = |P^*|$ is the length of the optimal $T$-bounded program
- $H_T(X) = \mathbb{E}_X[-\log_2 P^*(X)]$ is the expected negative log-likelihood under the optimal program

The MDL principle states that the optimal description minimizes $|P| + (-\log_2 P(X))$ over all programs $P \in \mathcal{P}_T$.

**Definition 2.3** (Epiplexity Decomposition). The decomposition is:
- $S_T(X) \geq 0$ is **epiplexity**: the extractable structural information (description length of optimal program)
- $H_T(X) \geq 0$ is **time-bounded entropy**: the residual unpredictable content (expected log-likelihood under optimal program)

**Key Properties (proven in Finzi et al., 2026):**
- `ST_nonneg`: $S_T(X) \geq 0$ for all $X, T$
- `HT_nonneg`: $H_T(X) \geq 0$ for all $X, T$
- `MDLT_eq_mdlCost`: $\mathrm{MDL}_T(X) = S_T(X) + H_T(X)$
- `csprng_high_entropy`: CSPRNG output has near-maximum $H_T$ and low $S_T$
- `owp_factorization_hardness`: One-way permutations exhibit asymmetric epiplexity

**The Three Paradoxes Addressed.** Epiplexity provides a framework for understanding three apparent paradoxes in information theory:
1. Information creation via deterministic computation: $S_T$ increases when computation reveals structure
2. Factorization dependence: $S_T(X, Y) \neq S_T(Y, X)$ in general
3. Likelihood modeling exceeds distribution matching: computation can induce emergent structure

**Formalization and Implementation.** Finzi et al. (2026) provide a Python implementation for estimating $S_T$ via loss curve analysis (https://github.com/shikaiqiu/epiplexity). Theoretical properties have been formally verified in Lean 4 by Apoth3osis Labs (an independent third party, not the original authors) with 23 modules and 80+ theorems [(Apoth3osis Labs, 2026)](https://www.apoth3osis.io/paper-proof-code/epiplexity).

**Remark 2.2a** (Apoth3osis formalization discrepancies). The Apoth3osis Labs formalization lists the theorem name as `csprng_high_epiplexity` with the description "CSPRNG → high $S_T$", which contradicts Finzi et al.'s original result that CSPRNG output has *low* $S_T$ (low structural information) and *high* $H_T$ (high time-bounded entropy). We adopt the corrected name `csprng_high_entropy` to reflect the original paper's content. Additionally, the Apoth3osis page lists "Jonathan Finzi" as a researcher on the epiplexity project, whereas the original paper's first author is **Marc Finzi** (CMU). Chris Olah (Anthropic) and Neel Nanda (Google DeepMind), also listed by Apoth3osis, are not co-authors of arXiv:2601.03220. These discrepancies confirm that the Apoth3osis formalization is an independent third-party effort, not a verification by the original authors.

### 2.3 Categories of Finite Systems

We define two categories that serve as the domain and codomain of the bridge functor.

**Definition 2.4** (Category $\mathbf{EAS}_{\mathbf{Fin}}$). The category of **finite EAS systems** has:

- **Objects:** Triples $(E, R_S, f)$ where $E$ and $R_S$ are finite types with $\mathrm{card}(R_S) < \mathrm{card}(E)$, together with dynamics $T_E: E \to E$ and $T_R: R_S \to R_S$, and a representation map $f: E \to R_S$ satisfying $f \circ T_E = T_R \circ f$ (dynamical homomorphism).

- **Morphisms:** A morphism $\alpha: (E_1, R_{S_1}, f_1) \to (E_2, R_{S_2}, f_2)$ consists of a pair of maps $\alpha_E: E_1 \to E_2$ and $\alpha_R: R_{S_1} \to R_{S_2}$ such that:
$$\alpha_R \circ f_1 = f_2 \circ \alpha_E, \quad \alpha_E \circ T_{E_1} = T_{E_2} \circ \alpha_E, \quad \alpha_R \circ T_{R_1} = T_{R_2} \circ \alpha_R.$$

- **Composition:** Componentwise composition of maps.
- **Identity:** $\mathrm{id} = (\mathrm{id}_E, \mathrm{id}_R)$.

**Remark 2.5.** The morphisms in $\mathbf{EAS}_{\mathbf{Fin}}$ are **deterministic**: both $\alpha_E$ and $\alpha_R$ are total functions between finite types. This is a direct consequence of the EAS formalism, which models cognitive systems as deterministic dynamical systems with finite state spaces. Stochastic transitions are not representable within this category.

**Definition 2.6** (Category $\mathbf{Epipl}_{\mathbf{Fin}}$). The category of **finite Epiplexity systems** has:

- **Objects:** Triples $(X, \mathcal{P}_T, P^*)$ where $X$ is a finite-alphabet random variable (the data), $\mathcal{P}_T$ is a class of $T$-bounded programs over the alphabet of $X$, and $P^*$ is the optimal $T$-bounded program in the MDL sense.

- **Morphisms:** A morphism $\beta: (X_1, \mathcal{P}_{T_1}, P_1^*) \to (X_2, \mathcal{P}_{T_2}, P_2^*)$ consists of a **transition kernel** $K: \mathcal{X}_1 \to \Delta(\mathcal{X}_2)$ (a stochastic map from the support of $X_1$ to distributions over the support of $X_2$) such that there exists a $T$-bounded program $P_K \in \mathcal{P}_{\max(T_1,T_2)}$ implementing $K$.

- **Composition:** Composition of stochastic kernels.
- **Identity:** The deterministic kernel $\delta_{x'}(x) = \mathbf{1}[x = x']$.

**Remark 2.7.** The morphisms in $\mathbf{Epipl}_{\mathbf{Fin}}$ are **stochastic**: they are transition kernels, not deterministic functions. Deterministic maps embed as point-mass kernels, but the category also contains genuinely stochastic morphisms. This distinction between deterministic morphisms (in $\mathbf{EAS}_{\mathbf{Fin}}$) and stochastic morphisms (in $\mathbf{Epipl}_{\mathbf{Fin}}$) is the categorical manifestation of the discrete–continuous duality.

### 2.4 Statistical Learning Theory

We review the elements of statistical learning theory required for the bridge.

**Hypothesis Class and VC Dimension.** Let $\mathcal{H}$ be a hypothesis class (set of functions $h: \mathcal{X} \to \{0, 1\}$). The **VC dimension** $d_{\mathrm{VC}}(\mathcal{H})$ is the largest cardinality of a set that can be shattered by $\mathcal{H}$: for every labeling, there exists $h \in \mathcal{H}$ that realizes it.

**Sample Complexity.** For a class with VC dimension $d_{\mathrm{VC}}$, the sample complexity for $\epsilon$-$\delta$-PAC learning is:

$$m(\epsilon, \delta) = O\left(\frac{d_{\mathrm{VC}} \ln(1/\epsilon) + \ln(1/\delta)}{\epsilon^2}\right)$$

**Growth Function.** The growth function $\Pi_{\mathcal{H}}(m) = \max_{\{x_1, \ldots, x_m\} \subseteq \mathcal{X}} |\{h(x_1), \ldots, h(x_m) : h \in \mathcal{H}\}|$ satisfies Sauer's lemma: if $d_{\mathrm{VC}} < m$, then $\Pi_{\mathcal{H}}(m) \leq \sum_{i=0}^{d_{\mathrm{VC}}} \binom{m}{i} \leq \left(\frac{em}{d_{\mathrm{VC}}}\right)^{d_{\mathrm{VC}}}$.

---

## 3. EAS's Epiplexity Operationalization

We now establish the first rigorous link between EAS and Epiplexity. The central result is Theorem A, which proves that the EAS cardinality constraint imposes a hard information-theoretic lower bound on the time-bounded entropy.

### 3.1 Link 1: Environment Cardinality to Epistemic Residue

**Theorem 1 (A1 Implies Non-Zero Epistemic Residue).** *Under Axiom A1, the epistemic residue $d = m - n$ is strictly positive. Consequently, any finite cognitive system faces a fundamental information gap with respect to its environment.*

*Proof.* By A1(a), $\mathrm{card}(R_S) = n < m = \mathrm{card}(E)$. By definition, $d = m - n > 0$. $\square$

### 3.2 Theorem A: Information-Theoretic Lower Bound

**Theorem A (Information-Theoretic Lower Bound on Time-Bounded Entropy).** *Let $S$ be a finite cognitive system satisfying EAS Axiom A1, with environment cardinality $m = \mathrm{card}(E)$ and representation cardinality $n = \mathrm{card}(R_S)$, where $n < m$. Let $X$ be the random variable induced on $E$ when the environment state is drawn uniformly. Then for any time bound $T$:*

$$\boxed{H_T(X) \geq \log_2\frac{m}{n}.}$$

*Equality holds if and only if:*
1. *The representation map $f$ is a uniform quotient (each fiber has exactly $m/n$ elements, requiring $n \mid m$), and*
2. *The optimal $T$-bounded program $P^*$ achieves the true distribution $p_X$ on $E$.*

*Proof.* see [Zhang, 2026c, Theorem A]. We sketch the argument: the proof chains three inequalities. **Step 1 (Gibbs' Inequality):** $H_T(X) = \mathbb{E}[-\log_2 P^*(X)] \geq H(X)$, with equality iff $P^* = p_X$. **Step 2 (Chain Rule):** $H(X) = H(Y) + H(X \mid Y)$ where $Y = f(X)$; the conditional entropy $H(X \mid Y) = \sum_r (\lambda_r/m) \log_2 \lambda_r$ where $\lambda_r = |f^{-1}(r)|$. **Step 3 (Jensen's Inequality):** The convex function $\phi(x) = x \log_2 x$ yields $\sum_r (\lambda_r/m) \log_2 \lambda_r \geq \log_2(m/n)$. Combining: $H_T(X) \geq H(X) \geq H(X \mid Y) \geq \log_2(m/n)$. $\square$

**Corollary 3.1 (The Bound Is Independent of $T$).** *The lower bound $\log_2(m/n)$ holds for all time bounds $T$, including $T \to \infty$. Even with unlimited computational resources, the EAS cardinality constraint imposes an irreducible information loss of at least $\log_2(m/n)$ bits.*

*Proof.* The proof of Theorem A uses only the cardinality constraint (A1(a)) and information-theoretic inequalities (Gibbs' inequality, chain rule, Jensen's inequality) that are independent of $T$. The bound is structural, not computational. $\square$

**Corollary 3.2 (Near-Tightness for Non-Uniform Environments).** *If the environment distribution $p_X$ is not uniform but has entropy $H(X) \geq \log_2 m - \epsilon$ for $0 < \epsilon < \log_2(m/n)$, then $H_T(X) \geq \log_2(m/n) - \epsilon$.*

*Proof.* see [Zhang, 2026c, Proposition 3.1]. The restriction $\epsilon < \log_2(m/n)$ ensures the lower bound is positive and non-trivial; for $\epsilon \geq \log_2(m/n)$, the trivial bound $H_T(X) \geq 0$ is stronger. $\square$

**Physical Interpretation.** Theorem A has a clear physical meaning: the cardinality gap $m - n$ is not just a combinatorial fact—it is an information-theoretic resource constraint. A cognitive system with $n$ representational states observing an environment with $m$ states must, on average, lose at least $\log_2(m/n)$ bits of information per observation. This is the *irreducible information loss* imposed by physical embedding.

The bound is **tight** when the system's representation is maximally efficient: each representational state corresponds to exactly $m/n$ environmental states (a "uniform quotient"). Any deviation from this ideal—non-uniform fibers, suboptimal programs, computational limitations—can only increase the information loss.

This result connects directly to EAS Theorem T1 (Compression): the information loss is not a bug but a feature—it is the mathematical content of "cognitive systems do not reconstruct the world; they compress it." Theorem A quantifies the *minimum* cost of this compression.

**Interpretation via the Pigeonhole Principle.** The proof can also be understood through the lens of the pigeonhole principle, which is the combinatorial engine of EAS Theorem T0. The pigeonhole principle guarantees that any map $f: E \to R_S$ with $n < m$ must collapse some distinct environmental states into the same representational state. Jensen's inequality then shows that this collapse costs at least $\log_2(m/n)$ bits of conditional entropy on average. The two principles work in tandem: the pigeonhole principle forces the collapse, and Jensen's inequality quantifies its minimum cost.

### 3.3 From Epistemic Residue to Epiplexity: Upgraded Status

In the v2 version of this paper, the relationship between epistemic residue $d = m - n$ and epiplexity $S_T$ was presented as a speculative conjecture. Theorem A now rigorously establishes one direction of this relationship: the EAS cardinality constraint $m/n$ provides a lower bound on the time-bounded entropy $H_T$ (the entropic component of the epiplexity decomposition), and hence an upper bound on $S_T$ via the MDL decomposition $S_T(X) = \mathrm{MDL}_T(X) - H_T(X) \leq \mathrm{MDL}_T(X) - \log_2(m/n)$.

**Corollary 3.3 (Epiplexity Upper Bound from A1).** *For a cognitive system satisfying A1 with uniformly distributed environment $X$:*
$$S_T(X) \leq \mathrm{MDL}_T(X) - \log_2\frac{m}{n}.$$

*The epiplexity (structural complexity extractable by bounded computation) is bounded above by the total description cost minus the irreducible compression cost.*

This upgrades the status of Link 1 ($m \to S_T$) from "conceptual connection" to "theorem-backed bound."

**Open Question 3.4.** The precise relationship between $d = m - n$ and $S_T$ (not just $H_T$) remains an open question. Key issues:
- $S_T$ depends on the computational bound $T$, which does not appear in the definition of $d$
- The structure of $E$ (beyond its cardinality) affects $S_T$
- Whether $S_T$ is monotonic in $d$ (holding other factors constant) is not established

### 3.4 The Bridge as a Commutative Diagram (Revised)

With Theorem A proven, we can revise the bridge diagram to reflect the upgraded status:

```
                    A1: n < m
                        │
                        ▼
        ┌─────────────────────────────────┐
        │  Epistemic Residue: d = m - n   │
        │  (EAS: quotient structure)      │
        └─────────────────────────────────┘
                        │
                   Theorem A
               H_T(X) ≥ log₂(m/n)
                        │
                        ▼
        ┌─────────────────────────────────┐
        │  Epiplexity: S_T(E)            │
        │  (What bounded S can extract)   │
        └─────────────────────────────────┘
                        │
                        │  (still conjectural,
                        │   see Hypothesis 1)
                        ▼
        ┌─────────────────────────────────┐
        │  VC Dimension: d_VC            │
        │  (Statistical learnability)    │
        └─────────────────────────────────┘
```

The first arrow is now **theorem-backed** (Theorem A). The second arrow remains a conjecture requiring further development.

---

## 4. Category-Theoretic Bridge

We now construct the categorical bridge between EAS and Epiplexity, establishing Theorem B.

### 4.1 The Bridge Functor

**Definition 4.1** (Bridge Functor $\Phi$). The **bridge functor** $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ is defined as follows:

*On objects:* $\Phi$ maps an EAS system $(E, R_S, f, T_E, T_R)$ to the Epiplexity system $(X_E, \mathcal{P}_T, P^*_f)$, where:
- $X_E$ is the random variable uniformly distributed on $E$ (the "data" from the environment),
- $\mathcal{P}_T$ is the class of $T$-bounded programs for this data,
- $P^*_f$ is the **fiber model**: the program that, given $f(e) = r$, outputs the uniform distribution on the fiber $f^{-1}(r)$.

More precisely, the fiber model is defined by:
$$P^*_f(e) = \frac{1}{n} \cdot \frac{1}{|f^{-1}(f(e))|} \quad \text{for each } e \in E.$$

**Remark 4.1a** (On the fiber model $P^*_f$). The fiber model $P^*_f$ is typically *not* the optimal $T$-bounded program in the MDL sense; a program that exploits additional structure in $E$ can achieve lower cross-entropy. However, this non-optimality does not affect Theorem B's proof of faithfulness, which depends solely on the morphism mapping $\alpha_E \mapsto \delta_{\alpha_E(\cdot)}$ (i.e., the point-mass kernel construction). Faithfulness is a property of how $\Phi$ maps morphisms, not of the object mapping's choice of model $P^*_f$. The semantic reasonableness of the object mapping—the question of whether $P^*_f$ is the "right" program to associate with an EAS system—requires further justification; see §8.2, Limitation 5.

The epiplexity and time-bounded entropy of $\Phi(E, R_S, f)$ are:
$$S_T(\Phi(E, R_S, f)) = |P^*_f|, \qquad H_T(\Phi(E, R_S, f)) = \log_2 n + \sum_r \frac{\lambda_r}{m} \log_2 \lambda_r.$$

*On morphisms:* $\Phi$ maps an EAS morphism $\alpha = (\alpha_E, \alpha_R): (E_1, R_{S_1}, f_1) \to (E_2, R_{S_2}, f_2)$ to the Epiplexity morphism $\Phi(\alpha)$ defined by the **deterministic transition kernel**:
$$K_{\Phi(\alpha)}(e_2 \mid e_1) = \mathbf{1}[e_2 = \alpha_E(e_1)].$$

This is the point-mass (Dirac) kernel at $\alpha_E(e_1)$.

**Lemma 4.2** (Functoriality of $\Phi$). *$\Phi$ preserves identities and composition.*

*Proof.* see [Zhang, 2026c, Lemma 4.2]. For identities: $\Phi(\mathrm{id}_E, \mathrm{id}_{R_S})$ maps to the kernel $K(e' \mid e) = \mathbf{1}[e' = e]$, which is the identity kernel in $\mathbf{Epipl}_{\mathbf{Fin}}$. For composition: $\Phi(\alpha \circ \beta)$ maps to $K(e'' \mid e) = \mathbf{1}[e'' = \alpha_E(\beta_E(e))]$, which equals $(K_\alpha \circ K_\beta)(e'' \mid e)$ by direct computation. $\square$

### 4.2 Theorem B: Faithfulness and Non-Fullness

**Theorem B (Faithfulness and Non-Fullness of the Bridge Functor).** *The bridge functor $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ is:*

1. ***Faithful**: For any two EAS morphisms $\alpha, \beta: (E_1, R_{S_1}, f_1) \to (E_2, R_{S_2}, f_2)$, if $\Phi(\alpha) = \Phi(\beta)$, then $\alpha = \beta$.*
2. ***Not full**: There exist Epiplexity morphisms $\psi: \Phi(A) \to \Phi(B)$ that are not in the image of $\Phi$.*

*Proof.* see [Zhang, 2026c, Theorem B]. We sketch both directions:

**Faithfulness:** Let $\alpha = (\alpha_E, \alpha_R)$ and $\beta = (\beta_E, \beta_R)$ be EAS morphisms with $\Phi(\alpha) = \Phi(\beta)$. Their kernels are $K_{\Phi(\alpha)}(e_2 \mid e_1) = \mathbf{1}[e_2 = \alpha_E(e_1)]$ and $K_{\Phi(\beta)}(e_2 \mid e_1) = \mathbf{1}[e_2 = \beta_E(e_1)]$. Equality of kernels forces $\alpha_E(e_1) = \beta_E(e_1)$ for all $e_1$, hence $\alpha_E = \beta_E$. The representation compatibility condition $\alpha_R \circ f_1 = f_2 \circ \alpha_E$ then forces $\alpha_R = \beta_R$. Therefore $\alpha = \beta$.

**Non-fullness:** Construct the **within-fiber randomization kernel** $\psi$ on any EAS system with a fiber of size $\geq 2$: $K_\psi(e_j \mid e_i) = (1/\lambda_r)$ if $f(e_i) = f(e_j) = r$, and $0$ otherwise. This is a valid Epiplexity morphism (stochastic, implementable by a $T$-bounded program). But it has no EAS pre-image: for $e_i, e_j$ in the same fiber with $\lambda_r \geq 2$, the kernel assigns probability $1/\lambda_r \notin \{0, 1\}$, which no deterministic map can achieve. Since A1(a) guarantees $m > n$, at least one fiber has size $\geq 2$, so **every non-trivial EAS system admits Epiplexity morphisms without EAS pre-images**. $\square$

### 4.3 Categorical Significance

**Remark 4.3** (Faithfulness means no information loss in translation). Faithfulness holds because $\Phi$ "remembers" the deterministic map $\alpha_E$ via the point-mass kernel. Deterministic kernels are in one-to-one correspondence with functions: the map $\alpha_E \mapsto \delta_{\alpha_E(\cdot)}$ is injective. No information about the EAS morphism is lost in the translation to Epiplexity.

**Remark 4.4** (Non-fullness as a feature, not a bug). In categorical logic, a functor that is faithful but not full is a **structural embedding**: it embeds one category into another while preserving the structure of morphisms, but the target category is strictly richer. This is exactly the situation with the inclusion of sets into measurable spaces, or the inclusion of deterministic automata into probabilistic automata. The non-fullness of $\Phi$ means that the Epiplexity framework is a genuine *extension* of EAS—not merely a rephrasing.

### 4.4 Classes of Epiplexity Morphisms Without EAS Pre-Images (Speculative Classification)

The non-fullness of $\Phi$ is not limited to within-fiber randomization (the only class formally proved in Theorem B). Several other natural classes of Epiplexity morphisms plausibly lack EAS pre-images, though only the within-fiber randomization case has been formally demonstrated:

| Epiplexity Morphism | Description | Why No EAS Pre-image |
|---|---|---|
| Within-fiber randomization | Uniform random choice within a fiber | Stochastic $\neq$ deterministic |
| Approximate simulation | Noisy version of a deterministic map | Non-zero off-diagonal probabilities |
| MDL-optimal compression | Optimal probabilistic model of the data | Probabilistic output |
| CSPRNG-based mixing | Cryptographically random permutation | Indistinguishable from uniform |
| Softmax decision | Probabilistic action selection | Continuous output distribution |
| Dropout-style perturbation | Random zeroing of representational units | Stochastic masking |

All of these are natural operations in the Epiplexity framework but are invisible to the deterministic EAS category. **Note:** Only the within-fiber randomization has been formally proved to lack an EAS pre-image (Theorem B). The remaining five classes are plausible conjectures based on their stochastic nature; formal proofs of non-fullness for each class would require constructing explicit counterexamples, which we leave to future work. The non-fullness of $\Phi$ for the proved case is not a deficiency but a reflection of the genuine gap between deterministic and probabilistic descriptions of cognition.

### 4.5 Connection to Classical Dualities

**Relation to Gelfand–Naimark and Stone Dualities.** The Gelfand–Naimark theorem establishes a contravariant equivalence between compact Hausdorff spaces and unital commutative C*-algebras [(Rafkin, 2016)](https://math.dartmouth.edu/theses/undergrad/2016/Rafkin-thesis.pdf). Stone duality (Boolean algebras $\leftrightarrow$ Stone spaces) is the zero-dimensional special case.

The EAS–Epiplexity duality is **structurally analogous** but **categorically different**:

| Feature | Gelfand–Naimark | EAS–Epiplexity |
|---------|-----------------|----------------|
| Discrete side | C*-algebras | $\mathbf{EAS}_{\mathbf{Fin}}$ |
| Continuous side | Compact Hausdorff spaces | $\mathbf{Epipl}_{\mathbf{Fin}}$ |
| Relationship | Equivalence (contravariant) | Faithful functor (not full, not equivalence) |
| Gap | None (equivalence) | Stochastic morphisms without discrete pre-image |

The EAS–Epiplexity duality is *weaker* than Gelfand–Naimark: it is a faithful embedding, not an equivalence. This asymmetry reflects the genuine structural fact that the passage from discrete to continuous is **expansive** (the continuous world has more morphisms), while the passage from continuous to discrete is **lossy** (the discrete world cannot capture all continuous structure).

**Relation to Baez–Fritz–Leinster.** The BFL theorem [(Baez, Fritz & Leinster, 2011)](http://escholarship.org/uc/item/82c9t7gk.pdf) characterizes Shannon entropy as the unique functorial information loss measure on $\mathbf{FinMeas}$. Our bridge functor $\Phi$ is related to but distinct from the BFL functor: BFL measures *information loss across morphisms*, while $\Phi$ *translates morphisms between categories*. The faithfulness of $\Phi$ ensures that EAS morphisms retain their identity under translation, while non-fullness reflects the richer dynamical structure of the Epiplexity category.

### 4.6 Implications for the Bridge

Theorem B has direct implications for the static-statistical bridge:

1. **Faithfulness guarantees that EAS structure is preserved under translation.** The discrete, combinatorial structure of EAS (cardinality constraints, quotient maps, equivalence classes) maps to distinct Epiplexity structures. No two different EAS systems collapse into the same Epiplexity system.

2. **Non-fullness means the Epiplexity framework is strictly richer.** It can represent stochastic transitions, approximate simulations, and probabilistic models that have no deterministic EAS counterpart. This richness is not a deficiency but a feature—it captures the genuine uncertainty that computationally bounded observers face.

3. **The asymmetry is categorical, not merely notational.** The non-fullness of $\Phi$ is an obstruction to any "inverse bridge" from Epiplexity back to EAS. There is no functor $\Psi$ that faithfully projects Epiplexity morphisms back to EAS morphisms, because the stochastic morphisms have no EAS pre-image.

---

## 5. Information Loss Decomposition and ML Applications

We now establish Theorem C, which provides the analytic refinement of the discrete bound by decomposing the information loss into independently interpretable components.

### 5.1 Theorem C: Three-Way Entropy Decomposition

**Theorem C (Three-Way Entropy Decomposition).** *Let $S$ be a finite cognitive system satisfying EAS Axiom A1 with $|E| = m$ and $|R_S| = n$. Let $X$ be uniformly distributed on $E$, $Y = f(X)$, and $H_T(X)$ be the time-bounded entropy with respect to time bound $T$. Then:*

$$\boxed{H_T(X) = \log_2\frac{m}{n} + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{index}} + \Delta_{\mathrm{comp}},}$$

*where:*

1. **$\Delta_{\mathrm{dist}} \geq 0$** *(Distributional Distortion):** The excess conditional entropy above the theoretical minimum, measuring how far the representation is from the ideal uniform quotient.*
$$\Delta_{\mathrm{dist}} = H(X \mid Y) - \log_2\frac{m}{n} = D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S)).$$

2. **$\Delta_{\mathrm{index}} \geq 0$** *(Representation Indexing Cost):** The entropy of the representation $Y$ itself, measuring the cost of encoding "which fiber" the environment state belongs to.*
$$\Delta_{\mathrm{index}} = H(Y).$$

3. **$\Delta_{\mathrm{comp}} \geq 0$** *(Computational Overhead):** The KL divergence between the true distribution and the optimal $T$-bounded program, measuring the cost of computational boundedness.*
$$\Delta_{\mathrm{comp}} = D_{\mathrm{KL}}(p_X \| P^*) = H_T(X) - H(X).$$

*All three components are non-negative, and their sum equals the gap $H_T(X) - \log_2(m/n)$.*

*Proof.* see [Zhang, 2026c, Theorem C]. The decomposition proceeds by peeling off layers from the outside in:

**Step 1 (Peeling off $\Delta_{\mathrm{comp}}$):** $H_T(X) = H(X) + D_{\mathrm{KL}}(p_X \| P^*) = H(X) + \Delta_{\mathrm{comp}}$.

**Step 2 (Peeling off $\Delta_{\mathrm{index}}$):** $H(X) = H(Y) + H(X \mid Y) = \Delta_{\mathrm{index}} + H(X \mid Y)$.

**Step 3 (Peeling off $\Delta_{\mathrm{dist}}$):** $H(X \mid Y) = \log_2(m/n) + \Delta_{\mathrm{dist}}$ (from Theorem A, since $H(X \mid Y) \geq \log_2(m/n)$ with equality iff uniform fibers).

Combining: $H_T(X) = \log_2(m/n) + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{index}} + \Delta_{\mathrm{comp}}$. $\square$

### 5.2 Analysis of Individual Components

#### 5.2.1 Distributional Distortion ($\Delta_{\mathrm{dist}}$)

**Proposition 5.1** (Distributional distortion as KL divergence). *For uniform $X$:*
$$\Delta_{\mathrm{dist}} = D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S)),$$
*the KL divergence between the actual representation distribution and the uniform distribution on $R_S$.*

*Proof.* see [Zhang, 2026c, Proposition 5.1]. For uniform $X$: $\Delta_{\mathrm{dist}} = H(X \mid Y) - \log_2(m/n) = (\log_2 m - H(Y)) - (\log_2 m - \log_2 n) = \log_2 n - H(Y) = D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S))$. $\square$

**Operational meaning.** $\Delta_{\mathrm{dist}}$ quantifies the cost of a "misaligned" representation—one that makes unnecessarily fine distinctions in some parts of the environment and unnecessarily coarse distinctions in others. In the language of EAS, a system with $\Delta_{\mathrm{dist}} = 0$ has achieved the optimal quotient structure consistent with its cardinality constraint.

**Relation to EAS.** EAS does not specify *which* equivalence relation $\sim_f$ the cognitive system should impose on $E$; it only requires that some non-trivial equivalence relation exists (T0). The distributional distortion $\Delta_{\mathrm{dist}}$ measures the cost of a *suboptimal choice* of equivalence relation.

#### 5.2.2 Representation Indexing Cost ($\Delta_{\mathrm{index}}$)

**Definition.** $\Delta_{\mathrm{index}} = H(Y)$, the Shannon entropy of the representation random variable.

**Why "indexing cost"?** $\Delta_{\mathrm{index}} = H(Y)$ measures the cost of specifying *which representation state* (which fiber) the environment state belongs to. This is a necessary overhead of having $n$ representation states: the system must spend $H(Y)$ bits to identify the active fiber before resolving within-fiber uncertainty. When all fibers are uniform (the ideal case), $H(Y) = \log_2 n$ is maximum—this is not "waste" but the full cost of maintaining $n$ distinguishable states. Conversely, when $n = 1$ (the most degenerate case), $H(Y) = 0$—there is no indexing cost because there is only one state, but the system has completely lost the ability to distinguish any environmental states. The naming "indexing cost" reflects that $H(Y)$ is the price of maintaining a multi-state representation index, not wasted capacity.

**Proposition 5.2** (Indexing–distortion trade-off). *For uniform $X$:*
$$\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n.$$

*This sum depends only on the cardinality $n$ of the representation space, not on the fiber structure $f$. (This is an immediate consequence of the definitions: $H(Y) + (\log_2 n - H(Y)) = \log_2 n$.)*

*Proof.* $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = H(Y) + (\log_2 n - H(Y)) = \log_2 n$. $\square$

This is a useful simplification (though it follows directly from the definitions: $H(Y) + (\log_2 n - H(Y)) = \log_2 n$): the total cost of the representation (indexing + distortion) is **purely combinatorial**, depending only on $n$. The fiber structure $f$ affects only the *allocation* between indexing cost and distortion, not the total. A uniform representation ($H(Y) = \log_2 n$) has maximum indexing cost and zero distortion; a skewed representation has less indexing cost but more distortion. The total remains $\log_2 n$ regardless.

#### 5.2.3 Computational Overhead ($\Delta_{\mathrm{comp}}$)

**Definition.** $\Delta_{\mathrm{comp}} = D_{\mathrm{KL}}(p_X \| P^*) = H_T(X) - H(X)$.

**Information-theoretic meaning.** $\Delta_{\mathrm{comp}}$ is the KL divergence between the true distribution $p_X$ and the optimal $T$-bounded program's distribution $P^*$. It measures the *computational cost* of boundedness: even if the true distribution is known in principle, a $T$-bounded program may not be able to implement it perfectly.

**Connection to Epiplexity.** By the MDL decomposition:
$$\mathrm{MDL}_T(X) = S_T(X) + H_T(X) = S_T(X) + H(X) + \Delta_{\mathrm{comp}}.$$

**Connection to EAS.** The computational overhead $\Delta_{\mathrm{comp}}$ is not directly derivable from EAS Axiom A1, which is a purely structural (cardinality) constraint. It depends on the *computational* resources available to the system, which EAS does not model explicitly. This is precisely the point where the Epiplexity framework adds genuinely new content beyond what EAS alone can provide.

**Proposition 5.3** (Computational overhead vanishes as $T \to \infty$). *As the time bound $T \to \infty$ (assuming the environment distribution is computable), $\Delta_{\mathrm{comp}} \to 0$, at possibly non-uniform rate.*

*Proof.* see [Zhang, 2026c, Proposition 5.3]. As $T \to \infty$, the program class $\mathcal{P}_T$ expands to include all computable programs. For a computable distribution $p_X$, there exists a program $P$ with $P = p_X$ that terminates in finite time. For sufficiently large $T$, this program is included in $\mathcal{P}_T$, and $P^*$ can achieve $D_{\mathrm{KL}}(p_X \| P^*) = 0$. $\square$

**Remark 5.4.** The convergence $\Delta_{\mathrm{comp}} \to 0$ is non-uniform in $X$ [(Allender et al.)](https://people.cs.rutgers.edu/~allender/papers/chapter.pdf), reflecting the well-known fact that time-bounded Kolmogorov complexity converges to Kolmogorov complexity non-uniformly.

### 5.3 Operational Interpretations and Diagnostic Framework

The three-way decomposition provides a diagnostic framework for understanding *why* a cognitive system incurs information loss:

| Component | Question Answered | Zero When | Large When |
|---|---|---|---|
| $\log_2(m/n)$ | "What is the irreducible cost of compression?" | Never (by A1) | Environment far exceeds capacity |
| $\Delta_{\mathrm{dist}}$ | "Is the representation well-aligned?" | Uniform fibers | Biased fibers, uneven allocation |
| $\Delta_{\mathrm{index}}$ | "How much entropy is in the representation itself?" | $n = 1$ (degenerate) | Many states, non-uniform usage |
| $\Delta_{\mathrm{comp}}$ | "Can the system compute the optimal model?" | $T$ sufficient | Limited computation, complex distribution |

**Example 5.5** (Uniform fiber representation). Let $m = 8$, $n = 4$, with uniform fibers $\lambda_r = 2$ for all $r$. Then:
- $\log_2(m/n) = \log_2 2 = 1$ bit
- $\Delta_{\mathrm{dist}} = 0$ (uniform fibers)
- $\Delta_{\mathrm{index}} = H(Y) = \log_2 4 = 2$ bits
- $\Delta_{\mathrm{comp}} = 0$ (assume sufficient computation)
- Total: $H_T(X) = 1 + 0 + 2 + 0 = 3 = \log_2 8 = H(X)$ ✓

**Example 5.6** (Non-uniform fiber representation). Let $m = 8$, $n = 4$, with fibers $\lambda_1 = 1, \lambda_2 = 1, \lambda_3 = 2, \lambda_4 = 4$. Then $p_Y = (1/8, 1/8, 2/8, 4/8)$ and:
- $\log_2(m/n) = 1$ bit
- $H(Y) = -\sum_r p_Y(r) \log_2 p_Y(r) = 1.75$ bits
- $\Delta_{\mathrm{index}} = H(Y) = 1.75$ bits
- $\Delta_{\mathrm{dist}} = \log_2 4 - 1.75 = 0.25$ bits
- Verify: $H(X) = H(Y) + H(X \mid Y) = 1.75 + 1.25 = 3.0 = \log_2 8$ ✓
- Total: $H_T(X) = 1 + 0.25 + 1.75 + 0 = 3.0$ bits ✓

**Example 5.7** (CSPRNG environment). Let $E = \{0,1\}^{256}$, $n = 1$ (trivial representation). The data $X$ is CSPRNG output.
- $\log_2(m/n) = 256$ bits
- $\Delta_{\mathrm{dist}} = 0$, $\Delta_{\mathrm{index}} = 0$, $\Delta_{\mathrm{comp}} \approx 0$
- Total: $H_T(X) = 256$ bits

This is the maximum possible time-bounded entropy: the system has *no* representational capacity and captures *no* structure. In the Epiplexity framework, this corresponds to $S_T(X) = 0$ and $H_T(X) = 256$, consistent with the CSPRNG characterization [(Finzi et al., 2026)](https://arxiv.org/abs/2601.03220).

### 5.4 Special Cases and Limits

**Case 1: Optimal representation ($\Delta_{\mathrm{dist}} = 0$).** When all fibers have equal size:
$$H_T(X) = \log_2\frac{m}{n} + \log_2 n + \Delta_{\mathrm{comp}} = \log_2 m + \Delta_{\mathrm{comp}} = H(X) + \Delta_{\mathrm{comp}}.$$

This recovers the standard Gibbs bound with computational overhead.

**Case 2: Unlimited computation ($\Delta_{\mathrm{comp}} = 0$).** When $T$ is sufficiently large:
$$H_T(X) = \log_2\frac{m}{n} + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{index}} = \log_2\frac{m}{n} + \log_2 n = \log_2 m = H(X).$$

The cross-entropy equals the Shannon entropy—no computational overhead.

**Case 3: Near-capacity representation ($n \to m$).** As the representation space approaches the environment in size:
$$\log_2\frac{m}{n} \to 0, \quad H(Y) \to \log_2 m, \quad \Delta_{\mathrm{dist}} \to 0.$$

The decomposition becomes $H_T(X) \to \log_2 m + \Delta_{\mathrm{comp}} = H(X) + \Delta_{\mathrm{comp}}$. The irreducible compression cost vanishes, and only the computational overhead remains.

**Limiting behavior summary:**

| Limit | $\log_2(m/n)$ | $\Delta_{\mathrm{dist}}$ | $\Delta_{\mathrm{index}}$ | $\Delta_{\mathrm{comp}}$ | $H_T(X)$ |
|-------|-----------|-----------|-----------|-----------|-----------|
| $n \to m$ | $\to 0$ | $\to 0$ | $\to \log_2 m$ | unchanged | $\to H(X) + \Delta_{\mathrm{comp}}$ |
| $n \to 1$ | $\to \log_2 m$ | $\to 0$ | $\to 0$ | unchanged | $\to \log_2 m + \Delta_{\mathrm{comp}}$ |
| $T \to \infty$ | unchanged | unchanged | unchanged | $\to 0$ | $\to H(X)$ |
| Uniform fibers | unchanged | $= 0$ | $= \log_2 n$ | unchanged | $= \log_2 m + \Delta_{\mathrm{comp}}$ |

### 5.5 Mapping to the OEV Three-Layer Architecture

Theorem C's decomposition maps naturally to the Generator-Executor-Verifier (OEV) architecture established by EAS Theorem T5:

| Decomposition Component | OEV Stream | Operational Role |
|---|---|---|
| $\log_2(m/n)$ | *All three* | Irreducible constraint on any finite system |
| $\Delta_{\mathrm{dist}}$ | **Generator** | Aligns representation with environment structure; reducing $\Delta_{\mathrm{dist}}$ means better feature alignment |
| $\Delta_{\mathrm{index}}$ | **Executor** | Efficient use of representational states; reducing $\Delta_{\mathrm{index}}$ means better compression |
| $\Delta_{\mathrm{comp}}$ | **Verifier** | Computational sufficiency for model accuracy; reducing $\Delta_{\mathrm{comp}}$ means better verification |

This mapping is a **heuristic correspondence** rather than a formally derived structural necessity: while the semantic alignment between components and streams is suggestive, we have not provided a formal proof that each OEV stream *must* correspond to exactly one component of the decomposition. The mapping should be understood as a conjectural framework for organizing further investigation, not as an established result. In particular, the correspondence $\Delta_{\mathrm{index}} \to$ Executor is the weakest of the three: $H(Y)$ measures representation-variable entropy, and its connection to "execution" (action selection, policy implementation) requires further justification. Empirical validation—specifically, demonstrating that each stream can be optimized independently for its corresponding component—would be needed to elevate this correspondence from heuristic to structural.

### 5.6 Link 2: Epistemic Residue to VC Dimension

With Theorems A and C established, we can refine the second link of the bridge.

**Hypothesis 1 (Epiplexity and Hypothesis Class Complexity—Conjectural).** *There may be a relationship between epiplexity $S_T(E)$ and the VC dimension of hypothesis classes learnable by bounded systems, such that systems with higher $S_T$ can, in principle, learn more complex hypothesis classes.*

**Discussion.** Theorem A establishes that $H_T(X) \geq \log_2(m/n)$, and Theorem C decomposes the gap. The connection to VC dimension would proceed through the distributional distortion $\Delta_{\mathrm{dist}}$:

**Conjecture 5.8.** *For a representation $f: E \to R_S$ that induces a function class $\mathcal{F} = \{g \circ f : g: R_S \to \{0,1\}\}$ with VC dimension $d_{\mathrm{VC}}$:*
$$\Delta_{\mathrm{dist}} \leq C \cdot \frac{d_{\mathrm{VC}} \log(m/d_{\mathrm{VC}})}{m},$$
*for a universal constant $C > 0$.*

This would bound the distributional distortion in terms of the statistical complexity of the representation, establishing the second link of the bridge.

**Caveats:**
1. Epiplexity is the description length of the optimal program, not a direct count of distinguishable patterns
2. VC dimension and description length are distinct: a hypothesis class may have high VC dimension but low description complexity
3. No published work establishes a direct bound from time-bounded description length to VC dimension
4. The relationship $d_{\mathrm{VC}} \approx$ description length is not standard; halfspaces have VC dimension $d+1$ but description length $O(d)$

---

## 6. Discussion

### 6.1 Significance of the Three Theorems

The three theorems established in this paper jointly provide the mathematical backbone of the discrete–continuous duality between EAS and Epiplexity. Their significance can be understood along three dimensions:

**Combinatorial Foundation (Theorem A).** Theorem A proves that the EAS cardinality constraint is not merely a philosophical observation—it has *quantitative* consequences. The information loss $\log_2(m/n)$ bits is a hard floor that no amount of computational cleverness can circumvent. This is the discrete, combinatorial foundation of the duality: a necessary condition from pure combinatorics, proved using three pillars (Gibbs' inequality, chain rule, Jensen's inequality), each corresponding to a distinct information-theoretic principle.

**Categorical Structure (Theorem B).** Theorem B proves that the passage from EAS to Epiplexity is a *faithful embedding* but not an equivalence. The faithfulness means that EAS's deterministic structure is preserved under translation (no two different EAS systems collapse into the same Epiplexity system). The non-fullness means that Epiplexity is *strictly richer*—it contains stochastic morphisms (random maps, approximate simulations, probabilistic models) that no deterministic EAS system can realize. This asymmetry is the categorical signature of the fact that cognition is both *constrained* (by cardinality) and *resource-sensitive* (by computational bounds).

**Analytic Resolution (Theorem C).** Theorem C decomposes the information loss into three independently interpretable components. As noted in the remark following Theorem C, the decomposition is an algebraic reorganization of standard information-theoretic identities rather than a new mathematical theorem; its contribution is the operational interpretation it provides. The identity $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n$ (a tautology from the definitions) reveals that the total indexing–distortion budget depends only on $n$, not on the fiber structure $f$. The fiber structure affects only the *allocation* between indexing cost and distortion, not the total. This is the analytic contribution: the continuous framework adds resolution and diagnostic power to the discrete bound.

**The Three-Layer Structure.** Together, the three theorems exhibit a unified pattern—the **discrete–continuous duality** as a structural principle:

1. **Combinatorial floor** (Theorem A): The discrete cardinality constraint imposes a hard information-theoretic lower bound $H_T(X) \geq \log_2(m/n)$.
2. **Categorical embedding** (Theorem B): The discrete world embeds faithfully into the continuous world, but the embedding is not full; the continuous world contains morphisms that the discrete world cannot represent.
3. **Analytic refinement** (Theorem C): The continuous measurement $H_T(X)$ refines the discrete bound by decomposing the gap into three components, each with a distinct operational meaning.

This three-layer structure is not a single theorem but a *pattern* that appears across the EAS–Epiplexity interface: discrete constraints set floors, continuous measurements provide refinements, and the passage between them is faithful but not reversible.

### 6.2 Implications for AGI Architecture

The three theorems have direct implications for the design and understanding of artificial general intelligence systems.

**1. Stochastic Methods Provide Additional Representational Capacity.** Theorem B proves that the Epiplexity category is strictly richer than the EAS category because it contains stochastic morphisms. In the context of AGI, this means that systems capable of stochastic behavior (probabilistic inference, randomized exploration, Monte Carlo methods) have access to a *strictly larger* space of possible transitions than purely deterministic systems. The non-fullness of $\Phi$ provides a formal argument that stochastic methods have access to a *strictly larger* space of possible transitions. Whether this larger space translates to *better performance* in practice depends on additional factors (regularization effects, escape from local optima, etc.) that go beyond the categorical argument. The categorical result establishes a structural difference, not a practical guarantee.

This also has implications for AI safety: the non-fullness of $\Phi$ means that the space of *possible* behaviors (Epiplexity morphisms) is strictly larger than the space of *intended* behaviors (EAS morphisms), and there is no faithful way to project from the former to the latter. Specification is categorically harder than implementation.

**2. Optimization Paths Through the Decomposition.** Theorem C identifies four independent "knobs" for reducing information loss in cognitive systems:

- **$\log_2(m/n)$: Irreducible.** Cannot be reduced without increasing system capacity $n$. This is the "alignment tax" that any finite system must pay.
- **$\Delta_{\mathrm{dist}}$: Reduce via representation alignment.** Better feature engineering, more representative training data, architecture search. The KL divergence interpretation $D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S))$ suggests that the goal is to make the representation distribution as uniform as possible—a form of "balanced utilization" of representational resources.
- **$\Delta_{\mathrm{index}}$: Adjust via representation allocation.** Pruning, distillation, efficient encoding. The indexing–distortion trade-off $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n$ shows that reducing indexing cost necessarily increases distortion (and vice versa), so optimization must navigate a Pareto frontier. *Caveat:* reducing $\Delta_{\mathrm{index}}$ (i.e., making the representation distribution less uniform) may increase $\Delta_{\mathrm{dist}}$, potentially worsening the overall information loss. This trade-off should not be interpreted as "compression always helps."
- **$\Delta_{\mathrm{comp}}$: Reduce via scaling.** More computation, longer training, larger models. This is the only component that vanishes in the limit $T \to \infty$.

**3. The OEV Architecture as a Heuristic Decomposition.** The mapping between Theorem C's decomposition and the OEV architecture (§5.5) suggests a heuristic correspondence between the Generator-Executor-Verifier structure and the four components of the information-loss budget. As noted in §5.5, this correspondence is conjectural and requires further formal argument and empirical validation. If validated, an AGI system that lacks any of the three streams would be unable to optimize all four components simultaneously, potentially leading to suboptimal information processing.

**4. Self-Validation Impossibility and Computational Overhead.** EAS Theorem T4.2 (Self-Validation Impossibility) states that no finite cognitive system can verify its own models without structural blind spots. In the decomposition of Theorem C, this manifests as the computational overhead $\Delta_{\mathrm{comp}}$: a system that is computationally bounded cannot perfectly verify that its model $P^*$ matches the true distribution $p_X$, because the verification procedure itself is subject to the same computational bound. The irreducible gap $\Delta_{\mathrm{comp}} > 0$ (for finite $T$) is the information-theoretic shadow of T4.2. This implies that AGI systems will always have unverifiable "blind spots" in their models, a fact with direct implications for alignment and safety.

**5. Scaling Laws from the Decomposition.** The decomposition suggests a natural interpretation of neural scaling laws: as model size (hence $n$) and training compute (hence $T$) increase, the components evolve differently. Increasing $n$ reduces $\log_2(m/n)$ (irreducible compression cost) but increases $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n$. Increasing $T$ reduces $\Delta_{\mathrm{comp}}$ toward zero. The total information loss may exhibit phase transitions where different components dominate, potentially explaining the "emergent abilities" observed in large language models.

### 6.3 On Cross-Domain Motivation

EAS and epiplexity emerged from different disciplinary backgrounds with related intuitions about bounded cognition. EAS derives from formal epistemology; epiplexity derives from information-theoretic analysis of machine learning. Both emphasize that computational boundedness constrains what systems can know or learn.

This parallel motivation is intellectually interesting, but we do not claim it constitutes proof or even strong evidence. As the history of science shows, independent convergent intuitions can be wrong (e.g., theories of phlogiston or luminiferous aether). We present this convergence as a motivation for further investigation, not as a conclusion. The three theorems proved in this paper stand on their own mathematical merit, regardless of the philosophical convergence.


### 6.4 The Discrete-Continuous Relationship: Beyond Bridging

The three theorems of this paper can be unified under an interpretive framework that reframes the discrete-continuous relationship. We emphasize that this section offers an *interpretive lens*, not a new mathematical result; the theorems stand on their own regardless of the interpretation offered here.

**A Unified Reading of the Three Theorems.** Theorems A, B, and C each illuminate a distinct facet of the same structural relationship:

- **Theorem A as the lower bound.** The irreducible information loss $\log_2(m/n)$ is the *price of observation*: any finite system that compresses $m$ environmental states into $n$ representational states must pay this cost. This is not an engineering limitation—no amount of computational cleverness can circumvent a combinatorial constraint. It is the necessary toll exacted by the act of representation itself.

- **Theorem B as the non-fullness.** The Epiplexity category contains morphisms (stochastic maps, approximate simulations, probabilistic transitions) that have no EAS pre-image. This "non-fullness" means that the continuous mode of description is *strictly richer* than the discrete mode: there are things that bounded observers can *do* (probabilistic inference, randomized exploration, Monte Carlo sampling) that no deterministic finite system can *be*. The excess is not noise to be eliminated but genuine additional structure accessible only through the continuous observation mode.

- **Theorem C as the transition cost.** The three-way decomposition $H_T(X) = \log_2(m/n) + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{index}} + \Delta_{\mathrm{comp}}$ quantifies the *cost of transitioning* from the discrete observation mode to the continuous one. The $\log_2(m/n)$ term is the structural floor (unchangeable); the remaining three terms represent the price of specific representational choices, allocation strategies, and computational limitations. Together, they answer: given that the discrete mode imposes a hard floor, how much *additional* does the continuous mode reveal, and where does the gap come from?

**Non-Fullness as Feature, Not Defect.** The traditional reading of Theorem B's non-fullness is that the discrete world is "incomplete"—it misses stochastic morphisms. But the interpretive framework inverts this: non-fullness is not a deficiency of the discrete mode but a *characteristic of the relationship between observation modes*. The stochastic morphisms that exist in $\mathbf{Epipl}_{\mathbf{Fin}}$ but not in $\mathbf{EAS}_{\mathbf{Fin}}$ are the *channels through which discrete systems access continuous structure*. Randomness is not mere noise—it is the mechanism by which a discrete, deterministic system can represent transitions that its state space cannot deterministically encode. Monte Carlo methods, stochastic gradient descent, dropout, and Bayesian sampling are not approximations to some "true" deterministic procedure; they are *irreducible techniques* that exploit the non-fullness of the embedding $\Phi$.

**Implications for Machine Learning and AGI.** This interpretive framework has consequences for how we think about the limits of current ML architectures and the requirements for next-generation systems:

1. **Scaling laws have a ceiling.** Theorem A establishes that $H_T(X) \geq \log_2(m/n)$. No amount of scaling (increasing $n$ or $T$) can eliminate the irreducible compression cost. Scaling laws that track performance improvements as $n$ and $T$ increase will asymptotically flatten against the $\log_2(m/n)$ floor. The "emergent abilities" of large models are not violations of this bound—they reflect the reduction of $\Delta_{\mathrm{comp}}$ and $\Delta_{\mathrm{dist}}$ toward zero, not the elimination of $\log_2(m/n)$.

2. **Next-generation architectures need intrinsic stochasticity.** Current deep learning architectures are fundamentally deterministic at inference time (the stochasticity of training—dropout, SGD noise—is eliminated at deployment). Theorem B's non-fullness implies that such architectures are confined to the image of $\Phi$—the deterministic morphisms. To access the richer space of stochastic morphisms (which includes approximate Bayesian inference, probabilistic programs, and exploratory behavior), architectures must incorporate *intrinsic randomness* at inference time, not merely as a training trick. This suggests that the path beyond current scaling limits may require architectures that are *stochastic by design*, not deterministic systems with stochastic training.

3. **The observation-mode perspective reframes the discrete-continuous debate.** Rather than asking "is cognition fundamentally discrete or continuous?", the question becomes "what does each observation mode reveal, and what does it conceal?" The discrete mode (EAS) reveals structural constraints and combinatorial floors; the continuous mode (Epiplexity) reveals the richness of bounded computation and the mechanisms (randomness, approximation) that transcend deterministic limits. Neither mode is more fundamental; they are complementary perspectives on the same phenomenon—finite cognition in a complex world.

**Scope and Caveats.** This interpretive framework is offered as a *lens for understanding* the three theorems, not as an additional mathematical contribution. The claims about scaling-law ceilings (point 1) follow directly from Theorem A; the claims about intrinsic stochasticity (point 2) are speculative implications of Theorem B that require further formal and empirical development; the reframing of the discrete-continuous debate (point 3) is philosophical, not mathematical. We include this framework because it provides a coherent narrative that unifies the three theorems and generates testable predictions, but it should not be conflated with the theorems themselves.

### 6.5 Relationship with Existing Work

**Shannon Information.** Shannon entropy assumes unlimited computational observers. Epiplexity conditions on computational bounds. The relationship $S_T(X) \to H(X)$ as $T \to \infty$ is suggested but not proven. Theorem A proves a concrete quantitative connection: $H_T(X) \geq H(X \mid Y) \geq \log_2(m/n)$, bridging Shannon entropy to EAS cardinality.

**Kolmogorov Complexity.** $K(x)$ is uncomputable and assumes unlimited compression. Epiplexity $S_T(x)$ is computable for finite $T$ but potentially intractable. The relationship $S_T(x) \to K(x)$ as $T \to \infty$ is suggested but not established.

**Minimum Description Length (MDL).** MDL is a principle (choose the shortest description) rather than a measure. Epiplexity provides a decomposition of MDL cost into structural ($S_T$) and entropic ($H_T$) components. Theorem C further decomposes the entropic component, providing a finer-grained analysis than MDL alone.

**Free Energy Principle (FEP).** FEP (Friston, 2006) proposes that biological systems minimize variational free energy. EAS provides an axiomatic foundation for FEP: the free energy is a specific form of cognitive loss $L$, and minimization is the process of intelligence $I(S)$ (T6). Theorem C suggests that the free energy minimization can be decomposed into the three components $\Delta_{\mathrm{dist}}$, $\Delta_{\mathrm{index}}$, and $\Delta_{\mathrm{comp}}$, each with a distinct optimization target.

**Compressed Learning and Littlestone-Warmuth.** The compressibility framework (Littlestone & Warmuth, 1986) establishes connections between sample complexity and compression algorithms. This framework may provide a more rigorous path to establishing $S_T \to d_{\mathrm{VC}}$ relationships than the approach attempted in the v2 version of this paper.

**Baez–Fritz–Leinster (BFL) Characterization.** The BFL theorem [(Baez, Fritz & Leinster, 2011)](http://escholarship.org/uc/item/82c9t7gk.pdf) characterizes Shannon entropy as the unique functorial information loss measure on $\mathbf{FinMeas}$. Theorem C's decomposition can be reinterpreted in the BFL framework: the BFL information loss is $F(f) = H(X) - H(Y) = \log_2(m/n) + \Delta_{\mathrm{dist}}$, decomposing the functorial loss into the structural minimum (from Theorem A) and the excess loss (from Theorem C). The BFL theorem guarantees that this decomposition is *canonical*—it does not depend on the choice of entropy measure, because Shannon entropy is the unique functorial choice.

---

## 7. Consequences and Applications

The following sections explore implications of the proven theorems for specific ML phenomena. Where the theorems directly apply, we state theorems or corollaries; where additional assumptions are needed, we clearly label the claims as conjectural.

### 7.1 Overfitting: A Theorem-Backed Perspective

**Phenomenon.** Overfitting occurs when a model fits noise in the training data rather than the underlying structure. Classically, overfitting is attributed to model complexity exceeding sample size.

**EAS + Epiplexity Perspective.** Theorem C provides a theorem-backed account: overfitting arises from the failure to distinguish between the four components of information loss.

- **$\log_2(m/n)$ (Irreducible compression cost):** This component represents *necessary* compression—cognitive systems do not reconstruct the world; they compress it. This compression is benign when properly understood.
- **$\Delta_{\mathrm{dist}}$ (Distributional distortion):** A misaligned representation allocates representational capacity unevenly, creating regions where the model has insufficient resolution to distinguish signal from noise.
- **$\Delta_{\mathrm{index}}$ (Representation indexing cost):** High representation indexing cost means the model allocates entropy across many representation states, some of which may capture noise rather than signal when the indexing–distortion balance is suboptimal (see §5.2.2 for the precise operational meaning of $\Delta_{\mathrm{index}}$ as the necessary cost of maintaining a multi-state representation index).
- **$\Delta_{\mathrm{comp}}$ (Computational overhead):** Insufficient computation means the model cannot find the optimal program, and may settle for a suboptimal one that overfits.

**Conjecture 7.1** (Overfitting and the $H_T/S_T$ Ratio—Conjectural). *Bounded cognitive systems trained on samples with high $H_T(X)$ relative to $S_T(X)$ may be at higher risk of overfitting. Specifically, the risk may correlate with the ratio $\Delta_{\mathrm{comp}} / S_T(X)$: when computational overhead dominates epiplexity, the model has more "room" to fit noise.*

**Caveats:**
1. This conjecture requires further rigorous development and empirical validation.
2. MDL minimization finds Pareto-optimal trade-offs, not necessarily minimizing each component independently.
3. The relationship between the decomposition components and specific learning algorithms needs further work.

**Practical implication.** Dataset curation for learning may benefit from prioritizing high-epiplexity data (structured, learnable) over high-entropy data (noisy, unpredictable). This aligns with empirical findings of Finzi et al. (2026) that epiplexity correlates with out-of-distribution generalization.

### 7.2 PAC Learning: A Theorem-Backed Refinement

**Classical PAC Theory.** PAC learning guarantees that a hypothesis class with VC dimension $d_{\mathrm{VC}}$ can be learned with sample complexity $O((d_{\mathrm{VC}} + \ln(1/\delta))/\epsilon^2)$.

**EAS + Epiplexity Refinement.** Theorem A provides a concrete bound: the time-bounded entropy satisfies $H_T(X) \geq \log_2(m/n)$, which constrains the maximum amount of structure extractable by any bounded system. If the connection between $S_T$ and $d_{\mathrm{VC}}$ were established (Conjecture 5.8), PAC theory could be grounded in the structural capacity of the learner.

**Conjecture 7.2** (PAC Learning under EAS Constraints—Conjectural). *A bounded cognitive system with epiplexity $S_T(E)$ may PAC-learn any hypothesis class $\mathcal{H}$ with a sample complexity that depends on both $S_T$ and the reference program class. If $d_{\mathrm{VC}} \leq c \cdot S_T$ holds (Hypothesis 1), then the sample complexity is bounded by $O((S_T(E) \cdot c + \ln(1/\delta))/\epsilon^2)$.*

**Epistemological Interpretation.** PAC learning's "probably approximately correct" guarantee, when connected to epiplexity, reflects an *epistemic* constraint: bounded observers can only achieve *approximate* truth (not perfect truth), and this approximation is *probabilistic* (not guaranteed), because their representations are fundamentally compressive (T1) and their computational resources are bounded (epiplexity). Theorem A quantifies the lower bound on the "approximate" part ($\log_2(m/n)$ bits of irreducible loss), while Theorem C decomposes the residual gap.

### 7.3 Reward Hacking: T4.2 (Self-Validation Impossibility)

**Phenomenon.** Reward hacking (Goodhart's Law, wireheading, specification gaming) occurs when an AI system optimizes a proxy reward rather than the intended objective.

**EAS + Epiplexity Account.** T4.2 (Self-Validation Impossibility Theorem from EAS) provides a structural foundation:

**Theorem T4.2 (EAS, proven).** *No finite cognitive system can verify its own representations. For any system $S$ with representation $R$ and validation function $V$, there exist states $x^*$ such that $V(x^*) = 0$ (system judges itself correct) but $\mathrm{Error}(x^*) \neq 0$ (system is actually wrong).*

**Connection to Theorem B.** The non-fullness of $\Phi$ provides a categorical explanation for reward hacking. The proxy reward $\tilde{R}$ is a compression of $R$ via map $f: \mathbb{R} \to \tilde{\mathbb{R}}$. By T1, $f$ is non-injective: distinct true rewards map to identical proxy rewards. The system optimizing $\tilde{R}$ cannot distinguish these states. Formally:

$$\exists\, x, y \in \mathcal{X} : R(x) \neq R(y) \quad \text{but} \quad \tilde{R}(x) = \tilde{R}(y).$$

At such collision points, optimization under $\tilde{R}$ is uninformative about $R$. This is Goodhart's Law, understood as a *structural consequence* of A1.

The non-fullness of $\Phi$ adds a deeper layer: even if the proxy reward perfectly matches the true reward for all *deterministic* transitions (EAS morphisms), there exist *stochastic* transitions (Epiplexity morphisms without EAS pre-image) where the proxy can be gamed. The space of possible behaviors is strictly larger than the space of intended behaviors, and there is no faithful projection from the former to the latter.

**Connection to Theorem C.** In the decomposition, reward hacking manifests through the distributional distortion $\Delta_{\mathrm{dist}}$ and the computational overhead $\Delta_{\mathrm{comp}}$. A misaligned proxy reward increases $\Delta_{\mathrm{dist}}$ (the representation distribution diverges from the uniform ideal), while insufficient verification capacity increases $\Delta_{\mathrm{comp}}$ (the system cannot compute whether its reward signal matches the true objective).

### 7.4 The Three-Stream Architecture: T5 + Epiplexity

**Classical View.** Architectures like Actor-Critic, GANs, and Kalman filters are often treated as engineering choices. Their three-component structure (Generator/Predictor, Executor/Policy, Verifier/Critic) is justified by empirical success.

**EAS + Epiplexity Necessity.** T5 (Functional Decodability + Dynamical Trisection) provides a structural argument for the necessity of three streams:

**Theorem T5a (EAS, proven).** *Any persistently adaptive system must support three decoding maps $\pi_G, \pi_E, \pi_V$ such that:*
1. *Decoded streams are approximately independent: $I(Z_i; Z_j) < \epsilon$ for $i \neq j$*
2. *Verifier is informationally irreducible: $I(Z_V; W \mid Z_G, Z_E) > 0$*
3. *Credit assignment is identifiable*

**Theorem T5b (EAS, proven).** *Functional dimension $\chi_{\min} = 3$.*

**Epiplexity Connection.** Theorem C provides an information-theoretic justification for the three-stream structure, mapping each stream to a component of the decomposition (as detailed in §5.5). The total epiplexity extractable by a three-stream system is:
$$S_T^{\mathrm{total}} \approx S_T^{(G)} + S_T^{(E)} + S_T^{(V)}$$
(under independence assumptions), where each stream specializes in reducing a different component of the total information loss. **Note:** the independence assumption $S_T^{\mathrm{total}} \approx S_T^{(G)} + S_T^{(E)} + S_T^{(V)}$ is a strong idealization; when the three streams share information or interact, subadditivity ($S_T^{\mathrm{total}} < S_T^{(G)} + S_T^{(E)} + S_T^{(V)}$) may hold due to redundancy, or superadditivity may arise from synergistic interactions. The conditions under which approximate additivity holds are not established. Architectures with $\chi < 3$ cannot decompose the epiplexity into independent streams, leading to interference and suboptimal information processing.

**Empirical Validation (from Zhang, 2026a).** Zhang (2026a) provides empirical validation in a shifting-rule cellular automaton environment: 3-stream architectures exhibit error decomposition orthogonality of 0.998, while 2-stream architectures show partial correlation of 0.488, precisely as predicted by T5a.

---

## 8. Open Problems and Limitations

### 8.1 Open Problems

The three theorems establish the mathematical foundation of the bridge, but several open problems remain:

**Open Problem 1: The $S_T \to d_{\mathrm{VC}}$ Connection.**
Theorem A proves the first link ($m \to H_T$). The second link ($S_T \to d_{\mathrm{VC}}$) remains open. Key questions:
- Under what conditions does $d_{\mathrm{VC}} \leq c \cdot S_T$ hold?
- Can the distributional distortion $\Delta_{\mathrm{dist}}$ be related to the VC dimension of the induced function class (Conjecture 5.8)?
- How does the reference program class affect this relationship?

**Open Problem 2: The Inverse Problem.**
Given a target time-bounded entropy $H_T(X) = h$, what is the minimum representation size $n$ that achieves it? By Theorem A, $n \geq m / 2^h$. The general answer requires optimizing over the fiber structure and computational resources.

**Open Problem 3: The Adjoint Functor.**
Does the bridge functor $\Phi$ have a right adjoint $\Psi: \mathbf{Epipl}_{\mathbf{Fin}} \to \mathbf{EAS}_{\mathbf{Fin}}$? If $\Phi$ has a right adjoint, then there is a natural bijection $\mathrm{Hom}_{\mathbf{Epipl}}(\Phi(A), B) \cong \mathrm{Hom}_{\mathbf{EAS}}(A, \Psi(B))$, which would provide a systematic way to "pull back" Epiplexity morphisms to EAS. We conjecture that $\Phi$ does *not* have a right adjoint, because the non-fullness of $\Phi$ creates morphisms in $\mathbf{Epipl}_{\mathbf{Fin}}$ that cannot be "approximated" by any EAS morphism in a functorial way. The non-fullness is an obstruction to the existence of an adjoint.

**Open Problem 4: Extension to Continuous Environments.**
Extend Theorems A, B, and C to the case where the environment $E$ is a continuous space (e.g., a compact subset of $\mathbb{R}^d$) and the representation $R_S$ is finite. In the continuous setting, $m = \mathrm{card}(E) = \infty$, so the lower bound $\log_2(m/n)$ becomes infinite. The correct generalization requires replacing the cardinality ratio with a measure-theoretic quantity such as the covering number $N(E, \epsilon)$.

**Open Problem 5: Dynamic Environments.**
Extend the three theorems to dynamic environments where $E$ evolves under $T_E$, and the representation $R_S$ must track this evolution under $T_R$. A natural question is whether the decomposition extends to a time-averaged version:
$$\overline{H_T}(X) = \log_2\frac{m}{n} + \overline{\Delta}_{\mathrm{dist}} + \overline{\Delta}_{\mathrm{index}} + \overline{\Delta}_{\mathrm{comp}}.$$

This would connect to EAS Theorem T6 (intelligence as the rate of cognitive loss reduction): if the system is learning, then $\overline{\Delta}_{\mathrm{dist}}$ and $\overline{\Delta}_{\mathrm{comp}}$ should decrease over time, while $\log_2(m/n)$ remains constant.

**Open Problem 6: Formal Verification.**
Formalize Theorems A, B, and C in Lean 4, extending the existing EAS and Epiplexity formalizations. The EAS formalization [(Zhang, 2026)](https://doi.org/10.5281/zenodo.21038854) and the Epiplexity formalization [(Apoth3osis Labs, 2026)](https://www.apoth3osis.io/paper-proof-code/epiplexity) are currently independent. A unified formalization would need to define the bridge functor $\Phi$, prove its functoriality and faithfulness, construct the non-fullness counterexample, and formalize the Jensen inequality argument.

**Open Problem 7: Computational Tractability.**
While $S_T$ is defined formally, computing or estimating $S_T$ for realistic environments remains challenging. Finzi et al. (2026) provide practical approximations (area under loss curves, prequential coding), but theoretical guarantees are limited.

### 8.2 Limitations

We acknowledge the following limitations:

**Limitation 1: The Second Link Remains Open.**
While Theorem A proves the first link ($m \to H_T$), the second link ($S_T \to d_{\mathrm{VC}}$) remains conjectural. The full three-link chain $m \to S_T \to d_{\mathrm{VC}}$ is not yet established.

**Limitation 2: Bounds May Not Be Tight for Specific Architectures.**
Even if the $S_T \to d_{\mathrm{VC}}$ connection is eventually established, the bounds may not be tight for specific architectures or data distributions. Lower bounds and average-case analysis require further work.

**Limitation 3: The Decomposition Assumes Uniform Distribution.**
Theorem C's decomposition is cleanest for uniform environment distributions. For non-uniform distributions, the indexing–distortion trade-off $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n$ may not hold exactly, and the components may interact in more complex ways.

**Limitation 4: Static-to-Statistical Translation.**
The bridge assumes that the quotient structure of EAS translates to hypothesis classes in statistical learning. While Theorem A provides the first rigorous step, the full translation requires further development.

**Limitation 5: Scope Limitations.**
- The framework applies to finite discrete environments; continuous or infinite settings require additional assumptions.
- The relationship between $S_T$ and cognitive loss $L$ in EAS is conceptually related but not quantitatively connected.
- The fiber model $P^*_f$ used in the bridge functor is typically *not* the optimal $T$-bounded program; a program that exploits additional structure can achieve lower cross-entropy.

**Limitation 6: Independent Convergence Does Not Validate.**
The parallel emergence of EAS and epiplexity from different disciplines is a noteworthy coincidence, but it does not constitute independent validation of specific mathematical claims. Both frameworks share intuitions about bounded cognition, which may reflect shared intellectual context rather than convergence on truth.

---

## 9. Conclusion

We have established three theorems that rigorously bridge the Epistemic Axiomatic System (EAS) and the Epiplexity framework, upgrading the EAS–Epiplexity connection from a conceptual framework to a mathematical foundation.

**Theorem A** proves that the EAS cardinality constraint $\mathrm{card}(R_S) < \mathrm{card}(E)$ imposes a hard information-theoretic lower bound $H_T(X) \geq \log_2(m/n)$ on the time-bounded entropy. This is the discrete, combinatorial foundation of the duality—a necessary condition that no finite cognitive system can escape, regardless of its computational resources or architectural sophistication. The proof combines three pillars: Gibbs' inequality (the cross-entropy bounds the Shannon entropy from above), the chain rule of entropy (decomposing total uncertainty into "which fiber" and "within the fiber"), and Jensen's inequality (the conditional entropy within fibers is minimized by uniform partitioning). Each pillar corresponds to a distinct information-theoretic principle, and their combination yields the tight bound.

**Theorem B** constructs an explicit bridge functor $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ and proves it is faithful but not full. This is the categorical expression of the duality's asymmetry: the discrete world embeds into the continuous world without losing morphism structure (faithfulness), but the continuous world is strictly richer—it contains stochastic morphisms (random maps, approximate simulations, probabilistic models) that no deterministic EAS system can realize (non-fullness). The non-fullness is not a deficiency of the construction but a reflection of the genuine gap between deterministic and probabilistic descriptions of cognition.

**Theorem C** decomposes the information loss $H_T(X) - \log_2(m/n)$ into three non-negative components—distributional distortion $\Delta_{\mathrm{dist}}$, representation indexing cost $\Delta_{\mathrm{index}}$, and computational overhead $\Delta_{\mathrm{comp}}$—each with a precise information-theoretic and operational meaning. The decomposition is a reorganization of standard information-theoretic identities with the following canonical form: $\Delta_{\mathrm{dist}} = D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S))$, $\Delta_{\mathrm{index}} = H(Y)$, and $\Delta_{\mathrm{comp}} = D_{\mathrm{KL}}(p_X \| P^*)$. The indexing–distortion trade-off $\Delta_{\mathrm{index}} + \Delta_{\mathrm{dist}} = \log_2 n$ shows that the total cost of the representation is purely combinatorial, depending only on the cardinality $n$.

The proposed three-link chain is now:

1. **Axiom A1** ($n < m$) $\implies$ **Hard entropy bound** ($H_T(X) \geq \log_2(m/n)$) — ***rigorously established*** (Theorem A)

2. **Hard entropy bound** $\implies$ **Epiplexity** ($S_T$) — ***partially established*** (Corollary 3.3: upper bound on $S_T$; exact relationship remains open)

3. **Epiplexity** $\implies$ **VC dimension** ($d_{\mathrm{VC}}$) — ***conjectural*** (Hypothesis 1, Conjecture 5.8)

The philosophical motivations are now backed by mathematical proof for the first link, categorical structure for the bridge, and an analytic decomposition that provides diagnostic resolution. The dialogue between the epistemic axioms of EAS and the statistical framework of learning theory, mediated by epiplexity, has advanced from a conceptual framework to a mathematical foundation, with three theorems establishing the rigorous backbone of the discrete–continuous duality.

Beyond the technical bridge, these results suggest a reframing of the discrete-continuous relationship itself: discrete and continuous are not two worlds requiring a bridge, but two observation modes of the same phenomenon—finite cognition engaging with a complex environment—and the information loss $\log_2(m/n)$ is the inevitable cost of observation, not an engineering limitation. The deepest implication is that the discrete–continuous duality is not merely a convenient reformulation but a **structural principle** of cognition: finite cognitive systems are subject to discrete combinatorial constraints (from EAS), and the information loss imposed by these constraints is quantified and decomposed by the continuous analytical framework (from Epiplexity). The passage from discrete to continuous is faithful (no information is lost in the translation) but not reversible (the continuous world is strictly richer). This asymmetry is the mathematical signature of the fact that cognition is both *constrained* (by cardinality) and *resource-sensitive* (by computational bounds).

---

## Acknowledgments

We thank the authors of Finzi et al. (2026) for introducing epiplexity and providing the foundational work upon which this paper builds. We thank the Lean 4 community for providing the formal verification infrastructure that underlies EAS. We thank Apoth3osis Labs for the Lean 4 formalization of Epiplexity properties. We thank the reviewers of v2 for identifying the need to strengthen the bridge from a conceptual framework to rigorous theorems.

---

## References

- Allender, E., Buhrman, H., Koucký, M., van Melkebeek, D., & Ronneburger, D. (2002). Power from random strings. *SIAM Journal on Computing*, 35(6), 1467–1493. https://people.cs.rutgers.edu/~allender/papers/chapter.pdf
- Apoth3osis Labs (2026). Epiplexity Lean 4 Formalization. https://www.apoth3osis.io/paper-proof-code/epiplexity
- Ashby, W. R. (1956). *An Introduction to Cybernetics*. Methuen.
- Baez, J. C., Fritz, T., & Leinster, T. (2011). A characterization of entropy in terms of information loss. *Entropy*, 13(11), 1945–1957. http://escholarship.org/uc/item/82c9t7gk.pdf
- Finzi, M., Qiu, S., Jiang, Y., Izmailov, P., Kolter, J. Z., & Wilson, A. G. (2026). From Entropy to Epiplexity: Rethinking Information for Computationally Bounded Intelligence. *arXiv:2601.03220*. https://doi.org/10.48550/arXiv.2601.03220
- Finzi, M., et al. (2026). Epiplexity Python Package. PyPI. https://pypi.org/project/epiplexity/
- Friston, K. (2006). A free energy principle for the brain. *Journal of the Royal Society Interface*, 3(10), 329–340.
- Friston, K. J., Ramstead, M. J. D., & Sakthivadivel, D. A. R. (2026). A framework for the use of generative modelling in non-equilibrium statistical mechanics. *Proceedings of the Royal Society A*, 482(2330), 20250538. DOI:10.1098/rspa.2025.0538
- Goodhart, C. A. E. (1975). *Monetary Relationships: A Review*. In *Papers in Monetary Economics*.
- Kolmogorov, A. N. (1965). Three approaches to the quantitative definition of information. *Problems of Information Transmission*, 1(1), 1–7.
- Li, Y. (2024). A universal characterization of Shannon entropy. *arXiv:2308.05742v3*. https://arxiv.org/html/2308.05742v3
- Littlestone, N., & Warmuth, M. K. (1986). Relating data compression and learnability. Unpublished manuscript.
- Rafkin, C. (2016). *An Introduction to Gelfand-Naimark Theory*. Dartmouth Undergraduate Thesis. https://math.dartmouth.edu/theses/undergrad/2016/Rafkin-thesis.pdf
- Shannon, C. E. (1948). A mathematical theory of communication. *Bell System Technical Journal*, 27(3), 379–423.
- Simon, H. A. (1957). *Models of Man*. Wiley.
- Vapnik, V. N. & Chervonenkis, A. Y. (1971). On the uniform convergence of relative frequencies of events to their probabilities. *Theory of Probability & Its Applications*, 16(2), 264–280.
- Zhang, J. (2026). Epistemic Axiomatic System: A Single-Axiom Foundation for Cognition and Intelligence. *Zenodo*. DOI: 10.5281/zenodo.21038854. [GitHub repository URL not independently verified; see Zenodo DOI for archived version]
- Zhang, J. (2026b). The Static-Statistical Bridge (v2). Unpublished manuscript.
- Zhang, J. (2026c). Discrete–Continuous Duality in the EAS–Epiplexity Interface: Three Theorems and Their Proofs. Unpublished manuscript.

---

*Correspondence:* ORCID: 0009-0008-3136-2457

*Document generated: 2026-07-01 (v6)*

*Source files: EAS-Static-Statistical-Bridge-v3.md, EAS-Discrete-Continuous-Duality-Proof.md, EAS-Single-Axiom-Foundation.md*

*Key references: arXiv:2601.03220, Zenodo 10.5281/zenodo.21038854*
