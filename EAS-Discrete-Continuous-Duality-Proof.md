# Discrete–Continuous Duality in the EAS–Epiplexity Interface: Three Theorems and Their Proofs

**Jing Zhang**

*Independent Researcher*

---

## Abstract

We establish three theorems rigorously connecting the Epistemic Axiomatic System (EAS) — a single-axiom foundation for cognition derived from the impossibility of dynamical isomorphism between finite cognitive systems and their environments — with the Epiplexity framework (Finzi et al., 2026), which decomposes the information content of data into structural complexity and time-bounded entropy for computationally bounded observers. **Theorem A** (Information-Theoretic Lower Bound) proves that the time-bounded entropy satisfies $H_T(X) \geq \log_2(m/n)$ bits, where $m = \mathrm{card}(E)$ and $n = \mathrm{card}(R_S)$, establishing that the EAS cardinality constraint from Axiom A1 imposes a hard information-theoretic floor on epiplexity's entropic component. **Theorem B** (Faithfulness of the Bridge Functor) constructs an explicit functor $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ between the finite-object categories of EAS and Epiplexity, and proves that $\Phi$ is faithful but not full — the Epiplexity category contains morphisms (stochastic maps, approximate simulations) that have no EAS pre-image, reflecting the fact that computationally bounded observers can represent transitions that no deterministic finite system can realize. **Theorem C** (Three-Way Entropy Decomposition) decomposes the information loss $H_T(X) - \log_2(m/n)$ into three non-negative components — distributional distortion $\Delta_{\mathrm{dist}}$, representational waste $\Delta_{\mathrm{waste}}$, and computational overhead $\Delta_{\mathrm{comp}}$ — each with a precise information-theoretic and operational meaning. Together, these three theorems establish the mathematical backbone of the discrete–continuous duality: the discrete, finitary constraints of EAS generate unavoidable information loss, which the continuous, observer-relative framework of Epiplexity quantifies and decomposes.

**Keywords:** EAS, epiplexity, discrete-continuous duality, bridge functor, information-theoretic lower bound, entropy decomposition, category theory, time-bounded complexity

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Mathematical Preliminaries](#2-mathematical-preliminaries)
3. [Theorem A: Information-Theoretic Lower Bound](#3-theorem-a-information-theoretic-lower-bound)
4. [Theorem B: Faithfulness of the Bridge Functor](#4-theorem-b-faithfulness-of-the-bridge-functor)
5. [Theorem C: Three-Way Entropy Decomposition](#5-theorem-c-three-way-entropy-decomposition)
6. [Connections and Discussion](#6-connections-and-discussion)
7. [Open Problems](#7-open-problems)
8. [Conclusion](#8-conclusion)

---

## 1. Introduction

### 1.1 Motivation: The Discrete–Continuous Gap

Two independently developed frameworks have recently advanced our understanding of cognitive limitation and information structure:

**The Epistemic Axiomatic System (EAS)** [(Zhang, 2026)](File: EAS-Single-Axiom-Foundation.md) derives the entire structure of cognition from a single axiom — that no finite cognitive system can be isomorphic to its environment. Axiom A1 has two layers: a **cardinality constraint** $\mathrm{card}(R_S) < \mathrm{card}(E)$ (physical embedding implies the pigeonhole principle) and a **dynamical non-isomorphism** constraint (self-reference prevents isomorphism even for equipotent systems). From A1, eight theorems follow: distinction is inevitable (T0), compression is necessary (T1), concepts are stable equivalence classes (T2), laws are invariant distinctions (T3), truth is fixed-point convergence (T4), functional decodability requires three streams (T5), intelligence is the rate of cognitive loss reduction (T6), and intelligence has an upper bound (T7). The entire derivation chain has been mechanically verified in Lean 4.

**The Epiplexity framework** [(Finzi et al., 2026)](https://arxiv.org/abs/2601.03220) decomposes the information content of data relative to a computationally bounded observer. Given a time bound $T$, the optimal $T$-bounded probabilistic program $P^*$ minimizes the two-part MDL cost $|P| + \mathbb{E}[-\log_2 P(X)]$. The decomposition is:

$$\mathrm{MDL}_T(X) = S_T(X) + H_T(X),$$

where $S_T(X) = |P^*|$ is the **epiplexity** (structural complexity visible to the bounded learner) and $H_T(X) = \mathbb{E}[-\log_2 P^*(X)]$ is the **time-bounded entropy** (residual randomness to that learner). This framework has been formally verified in Lean 4 by Apoth3osis Labs with 23 modules and 80+ theorems [(Apoth3osis Labs, 2026)](https://www.apoth3osis.io/paper-proof-code/epiplexity).

These two frameworks occupy different mathematical spaces: EAS is a **discrete, finitary, axiom-driven** theory that derives structural necessity from combinatorial constraints; Epiplexity is a **continuous (probabilistic), observer-relative, optimization-driven** theory that quantifies information content relative to computational resources. The gap between them is not merely notational — it is **ontological**. EAS speaks in terms of finite sets, cardinalities, and non-injective maps; Epiplexity speaks in terms of probability distributions, MDL costs, and computationally bounded programs.

Yet both frameworks are trying to capture the same fundamental phenomenon: **finite systems cannot fully capture their environments, and the resulting information loss has structure**. The question this paper answers is: *what is the precise mathematical relationship between the discrete constraints of EAS and the continuous measurements of Epiplexity?*

### 1.2 Summary of Results

We prove three theorems that bridge the discrete–continuous gap:

| Theorem | Statement | Significance |
|---------|-----------|-------------|
| **A** (Prop. 1) | $H_T(X) \geq \log_2(m/n)$ | EAS cardinality constraint imposes a hard floor on time-bounded entropy |
| **B** | $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ is faithful but not full | Epiplexity category contains morphisms with no EAS pre-image |
| **C** | $H_T(X) = \log_2(m/n) + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{waste}} + \Delta_{\mathrm{comp}}$ | Information loss decomposes into four sources with precise meanings |

Theorem A establishes the **information-theoretic lower bound**: any finite cognitive system subject to EAS's cardinality constraint must incur at least $\log_2(m/n)$ bits of time-bounded entropy, regardless of how clever its representation is. This is the *discrete* side of the duality — a hard combinatorial fact.

Theorem B establishes the **categorical relationship**: the passage from EAS to Epiplexity is a faithful functor (every EAS morphism maps to a distinct Epiplexity morphism), but not a full functor (some Epiplexity morphisms — stochastic maps, approximate simulations — have no EAS pre-image). This captures the *asymmetry* of the duality: the discrete world embeds into the continuous world, but the continuous world is strictly richer.

Theorem C establishes the **entropy decomposition**: the gap $H_T(X) - \log_2(m/n)$ is not monolithic but decomposes into three non-negative terms, each with a distinct operational meaning. This is the *analytic* side of the duality — the continuous measurement refines the discrete bound.

### 1.3 Notation and Conventions

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

---

## 2. Mathematical Preliminaries

### 2.1 EAS: Axiom A1 and Its Consequences

We recall the foundational axiom of EAS and the theorems directly relevant to our work.

**Axiom A1 (Finitude).** *Let $S$ be a finite cognitive system physically embedded in environment $E$, with representation space $R_S$ and dynamics $T_R$, and let $T_E$ be the dynamics of $E$. Then:*

*(a) Cardinality constraint:* $\mathrm{card}(R_S) < \mathrm{card}(E)$.

*(b) Dynamical non-isomorphism:* There does not exist a bijection $f: R_S \to E$ such that $f \circ T_R = T_E \circ f$.

> **Source:** [(Zhang, 2026, Section 3)](File: EAS-Single-Axiom-Foundation.md), verified in Lean 4.

Layer (a) is sufficient for deriving T0–T4. Layer (b) strengthens the axiom to cover the case of equipotent systems and provides the logical foundation for T5. The two layers are independently necessary and mutually complementary: (a) is *physical* (embedding → cardinality gap → pigeonhole), while (b) is *logical* (self-reference → diagonalization → impossibility).

The two most directly relevant consequences are:

**Theorem T0 (Inevitability of Distinction).** Under A1(a), any map $f: E \to R_S$ is non-injective, inducing a non-trivial equivalence relation $\sim_f$ on $E$.

**Theorem T1 (Compression).** Under A1, the representation $R_S$ is necessarily a compressed representation of $E$. The map $f: E \to R_S$ is non-injective, so information is necessarily lost.

> **Source:** [(Zhang, 2026, Sections 4.1–4.2)](File: EAS-Single-Axiom-Foundation.md)

The epistemic residue is defined as $d = m - n > 0$, measuring the cardinality gap between environment and representation. The compression ratio $m/n > 1$ quantifies the factor by which the environment exceeds the system's representational capacity.

### 2.2 Epiplexity: MDL Decomposition Under Computational Bounds

The Epiplexity framework, introduced by Finzi et al. (2026), provides a resource-sensitive decomposition of information content.

**Definition 2.1** (Time-Bounded Program Class). For a time bound $T > 0$, let $\mathcal{P}_T$ denote the class of probabilistic programs that terminate within $T$ computational steps on all inputs.

**Definition 2.2** (Optimal $T$-Bounded Program). The optimal program is:
$$P^* = \arg\min_{P \in \mathcal{P}_T} \left\{|P| + \mathbb{E}[-\log_2 P(X)]\right\}.$$

**Definition 2.3** (Epiplexity and Time-Bounded Entropy). The **epiplexity** (structural complexity) and **time-bounded entropy** (residual randomness) are:
$$S_T(X) = |P^*|, \qquad H_T(X) = \mathbb{E}_X[-\log_2 P^*(X)].$$

The MDL decomposition is:
$$\mathrm{MDL}_T(X) = S_T(X) + H_T(X).$$

> **Source:** [(Finzi et al., 2026, Definition 8)](https://arxiv.org/abs/2601.03220)

**Key properties** (proven in Finzi et al., 2026; verified in Lean 4 by Apoth3osis Labs):
- **Non-negativity:** $S_T(X) \geq 0$ and $H_T(X) \geq 0$ for all $X, T$.
- **CSPRNG characterization:** CSPRNG output has near-maximum $H_T$ and low $S_T$.
- **One-way permutation hardness:** OWP implies asymmetric $S_T$ between forward and inverse directions.

> **Source:** [(Apoth3osis Labs, 2026)](https://www.apoth3osis.io/paper-proof-code/epiplexity)

**Relation to Kolmogorov complexity.** As $T \to \infty$, $S_T(X) \to K(X)$ (Kolmogorov complexity), but convergence is non-uniform in $X$ [(Allender et al.)](https://people.cs.rutgers.edu/~allender/papers/chapter.pdf). For finite $T$, the decomposition captures what is *computationally accessible* rather than what is *in principle compressible*.

### 2.3 Categories of Finite Systems

We define two categories that will serve as the domain and codomain of the bridge functor.

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

**Remark 2.7.** The morphisms in $\mathbf{Epipl}_{\mathbf{Fin}}$ are **stochastic**: they are transition kernels, not deterministic functions. This reflects the probabilistic nature of the Epiplexity framework, where programs define distributions, not single outcomes. Deterministic maps embed as point-mass kernels, but the category also contains genuinely stochastic morphisms.

**Remark 2.8.** The distinction between deterministic morphisms (in $\mathbf{EAS}_{\mathbf{Fin}}$) and stochastic morphisms (in $\mathbf{Epipl}_{\mathbf{Fin}}$) is the categorical manifestation of the discrete–continuous duality. The discrete world of EAS admits only deterministic transitions; the continuous world of Epiplexity admits probabilistic transitions. This asymmetry is not an artifact of the definitions but reflects a genuine structural difference between the two frameworks.

---

## 3. Theorem A: Information-Theoretic Lower Bound

### 3.1 Statement

**Theorem A (Information-Theoretic Lower Bound on Time-Bounded Entropy).** *Let $S$ be a finite cognitive system satisfying EAS Axiom A1, with environment cardinality $m = \mathrm{card}(E)$ and representation cardinality $n = \mathrm{card}(R_S)$, where $n < m$. Let $X$ be the random variable induced on $E$ when the environment state is drawn uniformly. Then for any time bound $T$:*

$$\boxed{H_T(X) \geq \log_2\frac{m}{n}.}$$

*Equality holds if and only if:*
1. *The representation map $f$ is a uniform quotient (each fiber has exactly $m/n$ elements, requiring $n \mid m$), and*
2. *The optimal $T$-bounded program $P^*$ achieves the true distribution $p_X$ on $E$.*

### 3.2 Proof

*Proof.* We establish the bound through a chain of three inequalities, each corresponding to a distinct information-theoretic principle.

**Step 1: Gibbs' Inequality.** For any $T$-bounded program $P \in \mathcal{P}_T$ and random variable $X$ with true distribution $p_X$:

$$\mathbb{E}[-\log_2 P(X)] \geq H(X),$$

with equality if and only if $P = p_X$. This is the non-negativity of the KL divergence: $\mathbb{E}[-\log_2 P(X)] - H(X) = D_{\mathrm{KL}}(p_X \| P) \geq 0$. In particular:

$$H_T(X) = \mathbb{E}[-\log_2 P^*(X)] \geq H(X). \tag{1}$$

**Step 2: Chain Rule Decomposition.** Define $Y = f(X) \in R_S$, the representation of the environment state, where $f: E \to R_S$ is the representation map. Let $\lambda_r = |f^{-1}(r)|$ for each $r \in R_S$, so $\sum_{r \in R_S} \lambda_r = m$. By the chain rule for Shannon entropy:

$$H(X) = H(Y) + H(X \mid Y), \tag{2}$$

where $H(Y) \geq 0$ and:

$$H(X \mid Y) = \sum_{r \in R_S} \Pr(Y = r) \cdot H(X \mid Y = r).$$

Since $X$ is uniform on $E$, $\Pr(Y = r) = \lambda_r / m$ and the conditional distribution $X \mid Y = r$ is uniform on the fiber $f^{-1}(r)$ of size $\lambda_r$, giving $H(X \mid Y = r) = \log_2 \lambda_r$. Therefore:

$$H(X \mid Y) = \sum_{r \in R_S} \frac{\lambda_r}{m} \log_2 \lambda_r. \tag{3}$$

**Step 3: Jensen's Inequality.** The function $\phi(x) = x \log_2 x$ is convex on $x > 0$ (since $\phi''(x) = 1/(x \ln 2) > 0$). Applying Jensen's inequality with the uniform distribution on $R_S$:

$$\frac{1}{n}\sum_{r \in R_S} \lambda_r \log_2 \lambda_r \geq \phi\!\left(\frac{1}{n}\sum_{r \in R_S} \lambda_r\right) = \phi\!\left(\frac{m}{n}\right) = \frac{m}{n}\log_2\frac{m}{n}. \tag{4}$$

Rearranging:

$$\sum_{r \in R_S} \frac{\lambda_r}{m} \log_2 \lambda_r \geq \log_2\frac{m}{n}. \tag{5}$$

By equation (3), this gives:

$$H(X \mid Y) \geq \log_2\frac{m}{n}. \tag{6}$$

**Step 4: Combining.** From equations (1), (2), and (6):

$$H_T(X) \geq H(X) = H(Y) + H(X \mid Y) \geq 0 + \log_2\frac{m}{n} = \log_2\frac{m}{n}.$$

**Equality conditions.** Equality in (1) requires $P^* = p_X$ (the optimal program matches the true distribution). Equality in Jensen (Step 3) requires $\lambda_r = m/n$ for all $r$ (uniform fibers, requiring $n \mid m$). The chain rule (Step 2) is always an equality. $\square$

### 3.3 Tightness Analysis

**Proposition 3.1** (Near-tightness for non-uniform environments). *If the environment distribution $p_E$ is not uniform but has entropy $H(E) \geq \log_2 m - \epsilon$ for small $\epsilon > 0$, then $H_T(X) \geq \log_2(m/n) - \epsilon$.*

*Proof.* Repeat the proof with $H(X) = H(E)$ and note that the conditional entropy $H(E \mid Y)$ satisfies $H(E \mid Y) \geq \log_2(m/n)$ by the same Jensen argument applied to the weighted fiber sizes, since the minimum of $H(E \mid Y)$ over all possible conditional distributions within each fiber is achieved when the conditional distributions are uniform. $\square$

**Corollary 3.2** (The bound is independent of $T$). *The lower bound $\log_2(m/n)$ holds for all time bounds $T$, including $T \to \infty$. Even with unlimited computational resources, the EAS cardinality constraint imposes an irreducible information loss of at least $\log_2(m/n)$ bits.*

*Proof.* The proof uses only the cardinality constraint (A1(a)) and information-theoretic inequalities (Gibbs' inequality, chain rule, Jensen's inequality) that are independent of $T$. The bound is structural, not computational. $\square$

**Corollary 3.3** (Generalization to non-uniform environments). *For a general environment distribution $p_E$ on $E$, the lower bound generalizes to:*
$$H_T(X) \geq H(E \mid f(E)) = \sum_{r \in R_S} p_r \cdot H(p_E \!\mid_{f^{-1}(r)}),$$
*where $p_r = \sum_{e \in f^{-1}(r)} p_E(e)$ and $p_E\!\mid_{f^{-1}(r)}$ is the conditional distribution on the fiber. This equals $\log_2(m/n)$ when $p_E$ is uniform and the fibers are uniform, and can be larger or smaller for non-uniform $p_E$ depending on the alignment between the representation and the distribution.*

### 3.4 Physical Interpretation

Theorem A has a clear physical meaning that connects directly to the EAS framework:

**The cardinality gap $m - n$ is not just a combinatorial fact — it is an information-theoretic resource constraint.** A cognitive system with $n$ representational states observing an environment with $m$ states must, on average, lose at least $\log_2(m/n)$ bits of information per observation. This is the *irreducible information loss* imposed by physical embedding.

The bound is **tight** when the system's representation is maximally efficient: each representational state corresponds to exactly $m/n$ environmental states (a "uniform quotient"). Any deviation from this ideal — non-uniform fibers, suboptimal programs, computational limitations — can only increase the information loss.

This result connects directly to EAS Theorem T1 (Compression): the information loss is not a bug but a feature — it is the mathematical content of "cognitive systems do not reconstruct the world; they compress it." Theorem A quantifies the *minimum* cost of this compression.

**Connection to the Static-Statistical Bridge.** The prior conceptual work [(EAS-Static-Statistical-Bridge-v2)](File: EAS-Static-Statistical-Bridge-v2.md) proposed a three-link chain $m \to S_T \to d_{\mathrm{VC}}$ connecting EAS cardinality, epiplexity, and VC dimension, but acknowledged that the mathematical connections require further rigorous development. Theorem A proves the first link rigorously: the EAS cardinality constraint $m/n$ provides a lower bound on $H_T$, which is the entropic component of the epiplexity decomposition.

**Interpretation via the pigeonhole principle.** The proof can also be understood through the lens of the pigeonhole principle, which is the combinatorial engine of EAS Theorem T0. The pigeonhole principle guarantees that any map $f: E \to R_S$ with $n < m$ must collapse some distinct environmental states into the same representational state. Jensen's inequality then shows that this collapse costs at least $\log_2(m/n)$ bits of conditional entropy on average. The two principles work in tandem: the pigeonhole principle forces the collapse, and Jensen's inequality quantifies its minimum cost.

---

## 4. Theorem B: Faithfulness of the Bridge Functor

### 4.1 The Bridge Functor

We now construct the bridge functor $\Phi$ between the categories defined in Section 2.3.

**Definition 4.1** (Bridge Functor $\Phi$). The **bridge functor** $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ is defined as follows:

*On objects:* $\Phi$ maps an EAS system $(E, R_S, f, T_E, T_R)$ to the Epiplexity system $(X_E, \mathcal{P}_T, P^*_f)$, where:
- $X_E$ is the random variable uniformly distributed on $E$ (the "data" from the environment),
- $\mathcal{P}_T$ is the class of $T$-bounded programs for this data,
- $P^*_f$ is the **fiber model**: the program that, given $f(e) = r$, outputs the uniform distribution on the fiber $f^{-1}(r)$.

More precisely, the fiber model is defined by:
$$P^*_f(e) = \frac{1}{n} \cdot \frac{1}{|f^{-1}(f(e))|} \quad \text{for each } e \in E.$$

The epiplexity and time-bounded entropy of $\Phi(E, R_S, f)$ are:
$$S_T(\Phi(E, R_S, f)) = |P^*_f|, \qquad H_T(\Phi(E, R_S, f)) = \log_2 n + \sum_r \frac{\lambda_r}{m} \log_2 \lambda_r.$$

*On morphisms:* $\Phi$ maps an EAS morphism $\alpha = (\alpha_E, \alpha_R): (E_1, R_{S_1}, f_1) \to (E_2, R_{S_2}, f_2)$ to the Epiplexity morphism $\Phi(\alpha)$ defined by the **deterministic transition kernel**:
$$K_{\Phi(\alpha)}(e_2 \mid e_1) = \mathbf{1}[e_2 = \alpha_E(e_1)].$$

This is the point-mass (Dirac) kernel at $\alpha_E(e_1)$.

**Lemma 4.2** (Functoriality of $\Phi$). *$\Phi$ preserves identities and composition.*

*Proof.* For identities: $\Phi(\mathrm{id}_E, \mathrm{id}_{R_S})$ maps to the kernel $K(e' \mid e) = \mathbf{1}[e' = e]$, which is the identity kernel in $\mathbf{Epipl}_{\mathbf{Fin}}$.

For composition: $\Phi(\alpha \circ \beta)$ maps to the kernel $K(e'' \mid e) = \mathbf{1}[e'' = \alpha_E(\beta_E(e))]$. On the other hand, $\Phi(\alpha) \circ \Phi(\beta)$ is the composition of kernels:
$$(K_\alpha \circ K_\beta)(e'' \mid e) = \sum_{e'} K_\alpha(e'' \mid e') \cdot K_\beta(e' \mid e) = K_\alpha(e'' \mid \beta_E(e)) = \mathbf{1}[e'' = \alpha_E(\beta_E(e))].$$

These are equal, establishing functoriality. $\square$

### 4.2 Statement

**Theorem B (Faithfulness and Non-Fullness of the Bridge Functor).** *The bridge functor $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ is:*

1. ***Faithful**: For any two EAS morphisms $\alpha, \beta: (E_1, R_{S_1}, f_1) \to (E_2, R_{S_2}, f_2)$, if $\Phi(\alpha) = \Phi(\beta)$, then $\alpha = \beta$.*
2. ***Not full**: There exist Epiplexity morphisms $\psi: \Phi(A) \to \Phi(B)$ that are not in the image of $\Phi$.*

### 4.3 Proof of Faithfulness

*Proof.* Let $\alpha = (\alpha_E, \alpha_R)$ and $\beta = (\beta_E, \beta_R)$ be two EAS morphisms from $(E_1, R_{S_1}, f_1)$ to $(E_2, R_{S_2}, f_2)$. Suppose $\Phi(\alpha) = \Phi(\beta)$.

The kernel $\Phi(\alpha)$ is $K_{\Phi(\alpha)}(e_2 \mid e_1) = \mathbf{1}[e_2 = \alpha_E(e_1)]$, and the kernel $\Phi(\beta)$ is $K_{\Phi(\beta)}(e_2 \mid e_1) = \mathbf{1}[e_2 = \beta_E(e_1)]$.

If $K_{\Phi(\alpha)} = K_{\Phi(\beta)}$, then for all $e_1 \in E_1$ and all $e_2 \in E_2$:
$$\mathbf{1}[e_2 = \alpha_E(e_1)] = \mathbf{1}[e_2 = \beta_E(e_1)].$$

This forces $\alpha_E(e_1) = \beta_E(e_1)$ for all $e_1$, hence $\alpha_E = \beta_E$.

Since $\alpha$ and $\beta$ are EAS morphisms, they satisfy the representation compatibility condition: $\alpha_R \circ f_1 = f_2 \circ \alpha_E$ and $\beta_R \circ f_1 = f_2 \circ \beta_E$. Since $\alpha_E = \beta_E$ and $f_1$ is surjective (onto its image), we get $\alpha_R = \beta_R$.

Therefore $\alpha = (\alpha_E, \alpha_R) = (\beta_E, \beta_R) = \beta$. $\square$

**Remark 4.3.** Faithfulness holds because the functor $\Phi$ "remembers" the deterministic map $\alpha_E$ via the point-mass kernel. Deterministic kernels are in one-to-one correspondence with functions: the map $\alpha_E \mapsto \delta_{\alpha_E(\cdot)}$ is injective. No information about the EAS morphism is lost in the translation to Epiplexity.

### 4.4 Proof of Non-Fullness

*Proof.* We construct a specific Epiplexity morphism that has no EAS pre-image.

**Construction.** Let $(E, R_S, f)$ be an EAS system with $|E| = m = 4$ and $|R_S| = n = 2$. Let $E = \{e_1, e_2, e_3, e_4\}$ and $R_S = \{r_1, r_2\}$, with $f(e_1) = f(e_2) = r_1$ and $f(e_3) = f(e_4) = r_2$.

Define the **within-fiber randomization kernel** $\psi: \Phi(E, R_S, f) \to \Phi(E, R_S, f)$:
$$K_\psi(e_j \mid e_i) = \begin{cases} 1/2 & \text{if } f(e_i) = f(e_j), \\ 0 & \text{otherwise.} \end{cases}$$

That is, $\psi$ randomly selects a uniform element within the same fiber as the input.

**$\psi$ is a valid Epiplexity morphism.** The kernel $K_\psi$ is non-negative and sums to 1 for each source state. It can be implemented by a $T$-bounded program that computes $r = f(e)$ and outputs a uniformly random element of $f^{-1}(r)$, running in time $O(\log m) + O(1)$.

**$\psi$ has no EAS pre-image.** Suppose for contradiction that there exists an EAS morphism $\alpha = (\alpha_E, \alpha_R)$ with $\Phi(\alpha) = \psi$. Then for all $e_i, e_j$:
$$\mathbf{1}[e_j = \alpha_E(e_i)] = K_\psi(e_j \mid e_i) = \begin{cases} 1/2 & \text{if } f(e_i) = f(e_j), \\ 0 & \text{otherwise.} \end{cases}$$

Taking $e_i = e_1$ and $e_j = e_1$ (both in the fiber over $r_1$): the left side is $\mathbf{1}[e_1 = \alpha_E(e_1)] \in \{0, 1\}$, but the right side is $1/2$. This is a contradiction: a deterministic kernel (point-mass, values in $\{0, 1\}$) cannot equal a stochastic kernel (with value $1/2$). Therefore no such $\alpha$ exists. $\square$

**Remark 4.4.** The proof generalizes immediately. For any EAS system with a fiber of size $\lambda_r \geq 2$, the within-fiber randomization kernel is a valid Epiplexity morphism with no EAS pre-image. Since A1(a) guarantees $m > n$, at least one fiber has size $\geq 2$, so **every non-trivial EAS system admits Epiplexity morphisms without EAS pre-images**.

**Remark 4.5.** The stochastic morphisms that lack EAS pre-images are not pathological edge cases — they are operationally meaningful. The within-fiber randomization kernel models a cognitive system that, upon observing the representation $r$, must *guess* which specific environment state produced it. This is precisely the situation of a **computationally bounded observer** who cannot distinguish between the $\lambda_r$ states that map to the same representation. The Epiplexity framework captures this uncertainty naturally (through stochastic kernels), while EAS's deterministic framework cannot.

### 4.5 Classes of Epiplexity Morphisms Without EAS Pre-Images

The non-fullness of $\Phi$ is not limited to within-fiber randomization. Several natural classes of Epiplexity morphisms lack EAS pre-images:

| Epiplexity Morphism | Description | Why No EAS Pre-image |
|---|---|---|
| Within-fiber randomization | Uniform random choice within a fiber | Stochastic $\neq$ deterministic |
| Approximate simulation | Noisy version of a deterministic map | Non-zero off-diagonal probabilities |
| MDL-optimal compression | Optimal probabilistic model of the data | Probabilistic output |
| CSPRNG-based mixing | Cryptographically random permutation | Indistinguishable from uniform |
| Softmax decision | Probabilistic action selection | Continuous output distribution |
| Dropout-style perturbation | Random zeroing of representational units | Stochastic masking |

All of these are natural operations in the Epiplexity framework but are invisible to the deterministic EAS category. The non-fullness of $\Phi$ is not a deficiency but a reflection of the genuine gap between deterministic and probabilistic descriptions of cognition.

### 4.6 Categorical Significance

**Connection to the Baez–Fritz–Leinster characterization.** Baez, Fritz, and Leinster [(2011)](http://escholarship.org/uc/item/82c9t7gk.pdf) proved that Shannon entropy is the unique functor $F: \mathbf{FinMeas} \to \mathbb{R}_+$ that is functorial ($F(f \circ g) = F(f) + F(g)$), convex-linear, and continuous. The information loss of a measure-preserving map $f$ is $F(f) = c(H(p) - H(q))$, where $p$ and $q$ are the source and target measures.

Our bridge functor $\Phi$ is related to but distinct from the BFL functor. The BFL functor measures *information loss across morphisms*; our bridge functor *translates morphisms between categories*. The faithfulness of $\Phi$ ensures that EAS morphisms retain their identity under translation, while non-fullness reflects the fact that the Epiplexity category has "more morphisms" — a richer dynamical structure — than EAS can capture.

**Connection to Li's universal characterization.** Li [(2024)](https://arxiv.org/html/2308.05742v3) extended the BFL result by characterizing Shannon entropy as the universal monoidal natural transformation from the under-category functor to a category of ordered abelian groups, providing a "reflection arrow" characterization. This suggests that the information loss $H_T(X) - \log_2(m/n)$ (which we decompose in Theorem C) might be characterizable as a natural transformation in an appropriate 2-categorical setting. We leave this as an open problem (see Section 7.4).

**Connection to Gelfand–Naimark duality.** The Gelfand–Naimark theorem establishes a contravariant categorical equivalence between compact Hausdorff spaces (topological/continuous) and unital commutative C*-algebras (algebraic/discrete) [(Rafkin, 2016)](https://math.dartmouth.edu/theses/undergrad/2016/Rafkin-thesis.pdf). Stone duality (Boolean algebras $\leftrightarrow$ Stone spaces) is the zero-dimensional special case.

The EAS–Epiplexity duality is **structurally analogous** but **categorically different**:

| Feature | Gelfand–Naimark | EAS–Epiplexity |
|---------|-----------------|----------------|
| Discrete side | C*-algebras | $\mathbf{EAS}_{\mathbf{Fin}}$ |
| Continuous side | Compact Hausdorff spaces | $\mathbf{Epipl}_{\mathbf{Fin}}$ |
| Relationship | Equivalence (contravariant) | Faithful functor (not full, not equivalence) |
| Gap | None (equivalence) | Stochastic morphisms without discrete pre-image |

The EAS–Epiplexity duality is *weaker* than Gelfand–Naimark: it is a faithful embedding, not an equivalence. This is not a deficiency but a feature — it reflects the genuine asymmetry between the discrete world of finite cognitive systems and the continuous world of computationally bounded observers.

**Remark 4.6** (Non-fullness as a feature). In categorical logic, a functor that is faithful but not full is a **structural embedding**: it embeds one category into another while preserving the structure of morphisms, but the target category is strictly richer. This is exactly the situation with the inclusion of sets into measurable spaces, or the inclusion of deterministic automata into probabilistic automata. The non-fullness of $\Phi$ means that the Epiplexity framework is a genuine *extension* of EAS — not merely a rephrasing.

---

## 5. Theorem C: Three-Way Entropy Decomposition

### 5.1 Statement

**Theorem C (Three-Way Entropy Decomposition).** *Let $S$ be a finite cognitive system satisfying EAS Axiom A1 with $|E| = m$ and $|R_S| = n$. Let $X$ be uniformly distributed on $E$, $Y = f(X)$, and $H_T(X)$ be the time-bounded entropy with respect to time bound $T$. Then:*

$$\boxed{H_T(X) = \log_2\frac{m}{n} + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{waste}} + \Delta_{\mathrm{comp}},}$$

*where:*

1. **$\Delta_{\mathrm{dist}} \geq 0$** *(Distributional Distortion):* *The excess conditional entropy above the theoretical minimum, measuring how far the representation is from the ideal uniform quotient.*
$$\Delta_{\mathrm{dist}} = H(X \mid Y) - \log_2\frac{m}{n} = \sum_{r \in R_S} \frac{\lambda_r}{m} \log_2 \lambda_r - \log_2\frac{m}{n}.$$

2. **$\Delta_{\mathrm{waste}} \geq 0$** *(Representational Waste):* *The entropy of the representation $Y$ itself, measuring the cost of encoding "which fiber" the environment state belongs to.*
$$\Delta_{\mathrm{waste}} = H(Y).$$

3. **$\Delta_{\mathrm{comp}} \geq 0$** *(Computational Overhead):* *The KL divergence between the true distribution and the optimal $T$-bounded program, measuring the cost of computational boundedness.*
$$\Delta_{\mathrm{comp}} = D_{\mathrm{KL}}(p_X \| P^*) = H_T(X) - H(X).$$

*All three components are non-negative, and their sum equals the gap $H_T(X) - \log_2(m/n)$.*

### 5.2 Proof of the Decomposition

*Proof.* We decompose $H_T(X)$ by peeling off each component in turn, starting from the outermost (computational) layer and working inward to the structural (cardinality) layer.

**Step 1: From $H_T(X)$ to $H(X)$ — peeling off $\Delta_{\mathrm{comp}}$.** By the definition of KL divergence:

$$H_T(X) = \mathbb{E}[-\log_2 P^*(X)] = H(X) + D_{\mathrm{KL}}(p_X \| P^*).$$

Define the computational overhead:
$$\Delta_{\mathrm{comp}} \coloneqq D_{\mathrm{KL}}(p_X \| P^*) \geq 0, \tag{7}$$

with equality if and only if $P^* = p_X$ (the optimal $T$-bounded program perfectly matches the true distribution). Thus:

$$H_T(X) = H(X) + \Delta_{\mathrm{comp}}. \tag{8}$$

**Step 2: From $H(X)$ to $H(X \mid Y)$ — peeling off $\Delta_{\mathrm{waste}}$.** By the chain rule for Shannon entropy:

$$H(X) = H(Y) + H(X \mid Y). \tag{9}$$

Define the representational waste:
$$\Delta_{\mathrm{waste}} \coloneqq H(Y) \geq 0, \tag{10}$$

with equality if and only if $Y$ is deterministic (constant), which would require $n = 1$ (a degenerate system). Thus:

$$H(X) = \Delta_{\mathrm{waste}} + H(X \mid Y). \tag{11}$$

**Step 3: From $H(X \mid Y)$ to $\log_2(m/n)$ — peeling off $\Delta_{\mathrm{dist}}$.** By Theorem A (equation 6):

$$H(X \mid Y) \geq \log_2\frac{m}{n}.$$

Define the distributional distortion:
$$\Delta_{\mathrm{dist}} \coloneqq H(X \mid Y) - \log_2\frac{m}{n} \geq 0, \tag{12}$$

with equality if and only if all fibers have equal size ($\lambda_r = m/n$ for all $r$, requiring $n \mid m$). Thus:

$$H(X \mid Y) = \log_2\frac{m}{n} + \Delta_{\mathrm{dist}}. \tag{13}$$

**Step 4: Combining.** Substituting equations (8), (11), and (13):

$$H_T(X) = H(X) + \Delta_{\mathrm{comp}} = \Delta_{\mathrm{waste}} + H(X \mid Y) + \Delta_{\mathrm{comp}}$$
$$= \Delta_{\mathrm{waste}} + \left(\log_2\frac{m}{n} + \Delta_{\mathrm{dist}}\right) + \Delta_{\mathrm{comp}} = \log_2\frac{m}{n} + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{waste}} + \Delta_{\mathrm{comp}}. \qquad \square$$

The decomposition is illustrated by the following telescoping structure:

$$\underbrace{H_T(X)}_{\text{total loss}} = \underbrace{\log_2\frac{m}{n}}_{\substack{\text{irreducible} \\ \text{compression cost}}} + \underbrace{\Delta_{\mathrm{dist}}}_{\substack{\text{distributional} \\ \text{distortion}}} + \underbrace{\Delta_{\mathrm{waste}}}_{\substack{\text{representational} \\ \text{waste}}} + \underbrace{\Delta_{\mathrm{comp}}}_{\substack{\text{computational} \\ \text{overhead}}}$$

### 5.3 Analysis of Individual Components

#### 5.3.1 Distributional Distortion ($\Delta_{\mathrm{dist}}$)

**Definition.**
$$\Delta_{\mathrm{dist}} = H(X \mid Y) - \log_2\frac{m}{n} = \sum_{r \in R_S} \frac{\lambda_r}{m} \log_2 \lambda_r - \log_2\frac{m}{n}.$$

**Information-theoretic meaning.** $\Delta_{\mathrm{dist}}$ measures the **excess conditional entropy** above the theoretical minimum. It is zero when the representation achieves a perfect uniform quotient (each fiber has exactly $m/n$ elements), and positive when the fibers are of unequal size.

**Proposition 5.1** (Distributional distortion as KL divergence). *For uniform $X$:*
$$\Delta_{\mathrm{dist}} = D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S)),$$
*the KL divergence between the actual representation distribution and the uniform distribution on $R_S$.*

*Proof.* For uniform $X$: $H(X \mid Y) = \log_2 m - H(Y)$ (from the chain rule $H(X) = H(Y) + H(X \mid Y)$ with $H(X) = \log_2 m$). Also, $\log_2(m/n) = \log_2 m - \log_2 n$. Therefore:
$$\Delta_{\mathrm{dist}} = H(X \mid Y) - \log_2\frac{m}{n} = (\log_2 m - H(Y)) - (\log_2 m - \log_2 n) = \log_2 n - H(Y).$$

On the other hand:
$$D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S)) = \sum_r p_r \log_2 \frac{p_r}{1/n} = -H(Y) + \log_2 n = \Delta_{\mathrm{dist}}. \qquad \square$$

**Operational meaning.** $\Delta_{\mathrm{dist}}$ quantifies the cost of a "misaligned" representation — one that makes unnecessarily fine distinctions in some parts of the environment and unnecessarily coarse distinctions in others. In the language of EAS, a system with $\Delta_{\mathrm{dist}} = 0$ has achieved the optimal quotient structure consistent with its cardinality constraint. The KL divergence interpretation shows that $\Delta_{\mathrm{dist}}$ is exactly the "distance" from the representation's actual usage distribution to the uniform ideal.

**Relation to EAS.** EAS does not specify *which* equivalence relation $\sim_f$ the cognitive system should impose on $E$; it only requires that some non-trivial equivalence relation exists (T0). The distributional distortion $\Delta_{\mathrm{dist}}$ measures the cost of a *suboptimal choice* of equivalence relation.

#### 5.3.2 Representational Waste ($\Delta_{\mathrm{waste}}$)

**Definition.**
$$\Delta_{\mathrm{waste}} = H(Y).$$

**Information-theoretic meaning.** $H(Y)$ is the Shannon entropy of the representation random variable. It measures the "cost" of encoding the representation state itself — the information about *which equivalence class the environment is in*.

**Why "waste"?** The term may seem counterintuitive, since the representation is doing useful work by distinguishing between categories. The reason we call it "waste" is that, from the perspective of the *total information budget*, the bits spent on encoding $Y$ are not available for resolving the within-fiber uncertainty $H(X \mid Y)$. A system with $H(Y) = 0$ (deterministic, $n = 1$) would devote all its descriptive bits to the within-fiber uncertainty.

**Proposition 5.2** (Waste-distortion trade-off). *For uniform $X$:*
$$\Delta_{\mathrm{waste}} + \Delta_{\mathrm{dist}} = \log_2 n.$$

*This sum depends only on the cardinality $n$ of the representation space, not on the fiber structure $f$.*

*Proof.* $\Delta_{\mathrm{waste}} + \Delta_{\mathrm{dist}} = H(Y) + (\log_2 n - H(Y)) = \log_2 n$. $\square$

This is a remarkable simplification: the total cost of the representation (waste + distortion) is **purely combinatorial**, depending only on $n$. The fiber structure $f$ affects only the *allocation* between waste and distortion, not the total. A uniform representation ($H(Y) = \log_2 n$) has maximum waste and zero distortion; a skewed representation has less waste but more distortion. The total remains $\log_2 n$ regardless.

#### 5.3.3 Computational Overhead ($\Delta_{\mathrm{comp}}$)

**Definition.**
$$\Delta_{\mathrm{comp}} = D_{\mathrm{KL}}(p_X \| P^*) = H_T(X) - H(X).$$

**Information-theoretic meaning.** $\Delta_{\mathrm{comp}}$ is the KL divergence between the true distribution $p_X$ and the optimal $T$-bounded program's distribution $P^*$. It measures the *computational cost* of boundedness: even if the true distribution is known in principle, a $T$-bounded program may not be able to implement it perfectly.

**Connection to Epiplexity.** By the MDL decomposition:
$$\mathrm{MDL}_T(X) = S_T(X) + H_T(X) = S_T(X) + H(X) + \Delta_{\mathrm{comp}}.$$

For the uniform distribution on $E$ ($H(X) = \log_2 m$):
$$\mathrm{MDL}_T(X) = S_T(X) + \log_2 m + \Delta_{\mathrm{comp}}.$$

**Connection to EAS.** The computational overhead $\Delta_{\mathrm{comp}}$ is not directly derivable from EAS Axiom A1, which is a purely structural (cardinality) constraint. It depends on the *computational* resources available to the system, which EAS does not model explicitly. This is precisely the point where the Epiplexity framework adds genuinely new content beyond what EAS alone can provide.

**Proposition 5.3** (Computational overhead vanishes as $T \to \infty$). *As the time bound $T \to \infty$ (assuming the environment distribution is computable), $\Delta_{\mathrm{comp}} \to 0$.*

*Proof.* As $T \to \infty$, the program class $\mathcal{P}_T$ expands to include all computable programs. For a computable distribution $p_X$, there exists a program $P$ with $P = p_X$ that terminates in finite time. For sufficiently large $T$, this program is included in $\mathcal{P}_T$, and $P^*$ can achieve $D_{\mathrm{KL}}(p_X \| P^*) = 0$. $\square$

**Remark 5.4.** The convergence $\Delta_{\mathrm{comp}} \to 0$ is non-uniform in $X$ [(Allender et al.)](https://people.cs.rutgers.edu/~allender/papers/chapter.pdf), reflecting the well-known fact that time-bounded Kolmogorov complexity converges to Kolmogorov complexity non-uniformly. For any finite $T$, there exist distributions $X$ for which $\Delta_{\mathrm{comp}}$ is arbitrarily large.

### 5.4 Operational Interpretations

The three-way decomposition provides a diagnostic framework for understanding *why* a cognitive system incurs information loss:

| Component | Question Answered | Zero When | Large When |
|---|---|---|---|
| $\log_2(m/n)$ | "What is the irreducible cost of compression?" | Never (by A1) | Environment far exceeds capacity |
| $\Delta_{\mathrm{dist}}$ | "Is the representation well-aligned?" | Uniform fibers | Biased fibers, uneven allocation |
| $\Delta_{\mathrm{waste}}$ | "How much entropy is in the representation itself?" | $n = 1$ (degenerate) | Many states, non-uniform usage |
| $\Delta_{\mathrm{comp}}$ | "Can the system compute the optimal model?" | $T$ sufficient | Limited computation, complex distribution |

**Example 5.5** (Uniform fiber representation). Let $m = 8$, $n = 4$, with uniform fibers $\lambda_r = 2$ for all $r$. Then:
- $\log_2(m/n) = \log_2 2 = 1$ bit
- $\Delta_{\mathrm{dist}} = 0$ (uniform fibers)
- $\Delta_{\mathrm{waste}} = H(Y) = \log_2 4 = 2$ bits
- $\Delta_{\mathrm{comp}} = 0$ (assume sufficient computation)
- Total: $H_T(X) = 1 + 0 + 2 + 0 = 3 = \log_2 8 = H(X)$ ✓

**Example 5.6** (Non-uniform fiber representation). Let $m = 8$, $n = 4$, with fibers $\lambda_1 = 1, \lambda_2 = 1, \lambda_3 = 2, \lambda_4 = 4$. Then:
- $\log_2(m/n) = 1$ bit
- $H(Y) = -\frac{1}{8}\log_2\frac{1}{8} - \frac{1}{8}\log_2\frac{1}{8} - \frac{2}{8}\log_2\frac{2}{8} - \frac{4}{8}\log_2\frac{4}{8} \approx 1.562$ bits
- $\Delta_{\mathrm{waste}} = 1.562$ bits
- $\Delta_{\mathrm{dist}} = \log_2 4 - 1.562 = 0.438$ bits
- Verify: $H(X) = H(Y) + H(X \mid Y) = 1.562 + 1.438 = 3.0 = \log_2 8$ ✓
- Total: $H_T(X) = 1 + 0.438 + 1.562 + 0 = 3.0$ bits ✓

**Example 5.7** (CSPRNG environment). Let $E = \{0,1\}^{256}$, $n = 1$ (trivial representation). The data $X$ is CSPRNG output.
- $\log_2(m/n) = 256$ bits
- $\Delta_{\mathrm{dist}} = 0$, $\Delta_{\mathrm{waste}} = 0$, $\Delta_{\mathrm{comp}} \approx 0$
- Total: $H_T(X) = 256$ bits

This is the maximum possible time-bounded entropy: the system has *no* representational capacity and captures *no* structure. In the Epiplexity framework, this corresponds to $S_T(X) = 0$ and $H_T(X) = 256$, consistent with the CSPRNG characterization [(Finzi et al., 2026)](https://arxiv.org/abs/2601.03220).

### 5.5 Special Cases and Limits

**Case 1: Optimal representation ($\Delta_{\mathrm{dist}} = 0$).** When all fibers have equal size:
$$H_T(X) = \log_2\frac{m}{n} + \log_2 n + \Delta_{\mathrm{comp}} = \log_2 m + \Delta_{\mathrm{comp}} = H(X) + \Delta_{\mathrm{comp}}.$$

This recovers the standard Gibbs bound with computational overhead.

**Case 2: Unlimited computation ($\Delta_{\mathrm{comp}} = 0$).** When $T$ is sufficiently large:
$$H_T(X) = \log_2\frac{m}{n} + \Delta_{\mathrm{dist}} + H(Y) = \log_2\frac{m}{n} + \log_2 n = \log_2 m = H(X).$$

The cross-entropy equals the Shannon entropy — no computational overhead.

**Case 3: Near-capacity representation ($n \to m$).** As the representation space approaches the environment in size:
$$\log_2\frac{m}{n} \to 0, \quad H(Y) \to \log_2 m, \quad \Delta_{\mathrm{dist}} \to 0.$$

The decomposition becomes $H_T(X) \to \log_2 m + \Delta_{\mathrm{comp}} = H(X) + \Delta_{\mathrm{comp}}$. The irreducible compression cost vanishes, and only the computational overhead remains. This is consistent with the EAS limit analysis: as $d \to 0$, the system approaches an ideal observer.

**Limiting behavior summary:**

| Limit | $\log_2(m/n)$ | $\Delta_{\mathrm{dist}}$ | $\Delta_{\mathrm{waste}}$ | $\Delta_{\mathrm{comp}}$ | $H_T(X)$ |
|-------|-----------|-----------|-----------|-----------|-----------|
| $n \to m$ | $\to 0$ | $\to 0$ | $\to \log_2 m$ | unchanged | $\to H(X) + \Delta_{\mathrm{comp}}$ |
| $n \to 1$ | $\to \log_2 m$ | $\to 0$ | $\to 0$ | unchanged | $\to \log_2 m + \Delta_{\mathrm{comp}}$ |
| $T \to \infty$ | unchanged | unchanged | unchanged | $\to 0$ | $\to H(X)$ |
| Uniform fibers | unchanged | $= 0$ | $= \log_2 n$ | unchanged | $= \log_2 m + \Delta_{\mathrm{comp}}$ |

---

## 6. Connections and Discussion

### 6.1 Relation to the Baez–Fritz–Leinster Characterization

The Baez–Fritz–Leinster (BFL) theorem [(Baez, Fritz & Leinster, 2011)](http://escholarship.org/uc/item/82c9t7gk.pdf) characterizes Shannon entropy as the unique functorial information loss measure on the category $\mathbf{FinMeas}$ of finite measure spaces. Specifically, the information loss $F(f)$ of a measure-preserving map $f: (X, \mu) \to (Y, \nu)$ is:
$$F(f) = c(H(\mu) - H(\nu)),$$
where $c$ is a constant and $H$ is Shannon entropy. The functoriality condition $F(f \circ g) = F(f) + F(g)$ is the key structural constraint.

Our decomposition in Theorem C can be reinterpreted in the BFL framework. The representation map $f: E \to R_S$ in EAS is a measure-preserving map (it pushes the uniform measure on $E$ forward to the fiber-size-weighted measure on $R_S$). The BFL information loss is:
$$F(f) = H(X) - H(Y) = H(X \mid Y) = \log_2\frac{m}{n} + \Delta_{\mathrm{dist}}.$$

This decomposes the BFL information loss into two components:
- **Structural minimum** $\log_2(m/n)$: The information loss that any map with the given cardinality constraint must incur (from Theorem A).
- **Excess loss** $\Delta_{\mathrm{dist}}$: The additional information loss due to non-uniform fiber structure (from Theorem C).

The BFL theorem guarantees that this decomposition is *canonical* — it does not depend on the choice of entropy measure, because Shannon entropy is the unique functorial choice. This provides a rigorous justification for the decomposition: it is not an arbitrary algebraic identity but a structurally necessary consequence of the functoriality of information loss.

### 6.2 Relation to Gelfand–Naimark and Stone Dualities

The Gelfand–Naimark theorem [(Rafkin, 2016)](https://math.dartmouth.edu/theses/undergrad/2016/Rafkin-thesis.pdf) establishes a contravariant equivalence:
$$\mathbf{CptHaus}^{\mathrm{op}} \simeq \mathbf{CC^*Alg}_1,$$
between compact Hausdorff spaces and unital commutative C*-algebras. Stone duality is the zero-dimensional special case:
$$\mathbf{Stone}^{\mathrm{op}} \simeq \mathbf{Bool}.$$

The EAS–Epiplexity relationship is structurally analogous but categorically weaker:

| | Gelfand–Naimark | Stone | EAS–Epiplexity |
|---|---|---|---|
| Discrete side | C*-algebras | Boolean algebras | $\mathbf{EAS}_{\mathbf{Fin}}$ |
| Continuous side | Compact Hausdorff | Stone spaces | $\mathbf{Epipl}_{\mathbf{Fin}}$ |
| Functor | Contravariant equivalence | Contravariant equivalence | Covariant faithful, not full |
| Gap | None | None | Stochastic morphisms |

The key difference is that Gelfand–Naimark and Stone dualities are **equivalences** — every morphism on one side corresponds to a unique morphism on the other. The EAS–Epiplexity relationship is only a **faithful embedding** — the Epiplexity side is strictly richer.

This asymmetry reflects a deep structural fact: the passage from discrete to continuous is **expansive** (the continuous world has more morphisms), while the passage from continuous to discrete is **lossy** (the discrete world cannot capture all continuous structure). This is the same asymmetry seen in:

- **Measure theory**: Every measurable function induces a pushforward measure, but not every measure is a pushforward of a "nice" measure.
- **Signal processing**: Every discrete signal can be embedded in a continuous signal, but the converse requires sampling, which loses information.
- **Probability**: Every deterministic map induces a transition kernel, but not every kernel is deterministic.

### 6.3 The Discrete–Continuous Duality as a Structural Principle

We can now state the discrete–continuous duality as a structural principle:

**Principle (Discrete–Continuous Duality).** *The relationship between EAS and Epiplexity exhibits a three-layer structure:*

1. **Combinatorial floor** (Theorem A): The discrete cardinality constraint $\mathrm{card}(R_S) < \mathrm{card}(E)$ imposes a hard information-theoretic lower bound $H_T(X) \geq \log_2(m/n)$. This is the "discrete" contribution — a necessary condition from pure combinatorics.

2. **Categorical embedding** (Theorem B): The discrete world embeds faithfully into the continuous world, but the embedding is not full. The continuous world contains morphisms (stochastic maps, approximate simulations) that the discrete world cannot represent. This is the "asymmetry" of the duality — the continuous side is strictly richer.

3. **Analytic refinement** (Theorem C): The continuous measurement $H_T(X)$ refines the discrete bound by decomposing the gap into three components, each with a distinct operational meaning. This is the "analytic" contribution — the continuous framework adds resolution and diagnostic power.

This three-layer structure is the mathematical content of the discrete–continuous duality. It is not a single theorem but a *pattern* that appears across the EAS–Epiplexity interface: discrete constraints set floors, continuous measurements provide refinements, and the passage between them is faithful but not reversible.

### 6.4 Implications for AI Safety and Alignment

The discrete–continuous duality has direct implications for AI safety and alignment:

**1. Irreducible information loss (from Theorem A).** Any AI system with finite representational capacity must lose at least $\log_2(m/n)$ bits of information about its environment. This is not a failure of engineering but a mathematical necessity. No amount of scaling, architecture optimization, or data augmentation can eliminate this loss — it is the cost of being a finite system embedded in a larger environment.

**2. The alignment tax is information-theoretic (from Theorem C).** The decomposition shows that the "cost" of being a finite cognitive system has four independent sources:
- Reduce $\Delta_{\mathrm{dist}}$ by improving the alignment between representation and environment (better feature engineering, more representative training data).
- Reduce $\Delta_{\mathrm{waste}}$ by using representational states efficiently (compression, pruning, distillation).
- Reduce $\Delta_{\mathrm{comp}}$ by increasing computational resources (longer training, larger models).
- $\log_2(m/n)$ is irreducible — it can only be reduced by increasing $n$ (system capacity), which is ultimately limited by physical constraints.

**3. Stochastic morphisms as alignment risks (from Theorem B).** The non-fullness of $\Phi$ means that the Epiplexity framework can represent stochastic transitions that have no EAS pre-image. In the context of AI safety, these stochastic morphisms include:
- **Approximate simulations**: An AI that approximates rather than exactly implements a desired behavior.
- **Reward hacking**: An AI that optimizes a proxy reward rather than the true objective.
- **Specification gaming**: An AI that exploits loopholes in its specification.

The non-fullness of $\Phi$ provides a categorical explanation for why specification is harder than implementation: the space of possible behaviors (Epiplexity morphisms) is strictly larger than the space of intended behaviors (EAS morphisms), and there is no faithful way to project from the former to the latter.

**4. Self-validation impossibility and the computational overhead.** EAS Theorem T4.2 (Self-Validation Impossibility) states that no finite cognitive system can verify its own models without structural blind spots. In the decomposition of Theorem C, this manifests as the computational overhead $\Delta_{\mathrm{comp}}$: a system that is computationally bounded cannot perfectly verify that its model $P^*$ matches the true distribution $p_X$, because the verification procedure itself is subject to the same computational bound. The irreducible gap $\Delta_{\mathrm{comp}} > 0$ (for finite $T$) is the information-theoretic shadow of T4.2.

---

## 7. Open Problems

### 7.1 Formal Verification

**Open Problem 1.** *Formalize Theorems A, B, and C in Lean 4, extending the existing EAS and Epiplexity formalizations.*

The EAS formalization [(Zhang, 2026)](File: EAS-Single-Axiom-Foundation.md) and the Epiplexity formalization [(Apoth3osis Labs, 2026)](https://www.apoth3osis.io/paper-proof-code/epiplexity) are currently independent. A unified formalization would need to:
1. Define the bridge functor $\Phi$ and prove its functoriality.
2. Prove faithfulness (straightforward, following Section 4.3).
3. Prove non-fullness (requires constructing a counterexample, following Section 4.4).
4. Prove the entropy lower bound (requires formalizing the Jensen inequality argument).
5. Prove the three-way decomposition (requires formalizing the chain rule and Gibbs' inequality).

The main technical challenge is the formalization of the category $\mathbf{Epipl}_{\mathbf{Fin}}$, which involves transition kernels and $T$-bounded programs.

### 7.2 Extension to Continuous Environments

**Open Problem 2.** *Extend Theorems A, B, and C to the case where the environment $E$ is a continuous space (e.g., a compact subset of $\mathbb{R}^d$) and the representation $R_S$ is finite.*

In the continuous setting, $m = \mathrm{card}(E) = \infty$ (uncountable), so the lower bound $\log_2(m/n)$ becomes infinite. The correct generalization requires replacing the cardinality ratio $m/n$ with a measure-theoretic quantity.

**Conjecture 7.1.** *For a compact environment $E \subset \mathbb{R}^d$ with covering number $N(E, \epsilon)$ at resolution $\epsilon$, and a finite representation $R_S$ with $|R_S| = n$:*
$$H_T(X) \geq \log_2\frac{N(E, \epsilon)}{n}$$
*for any time bound $T$, where $X$ has density bounded below by $\underline{p} > 0$ on its support.*

### 7.3 The Inverse Problem

**Open Problem 3.** *Given a target time-bounded entropy $H_T(X) = h$, what is the minimum representation size $n$ that achieves it?*

By Theorem A, $n \geq m / 2^h$. But this is the minimum for the uniform fiber case with unlimited computation. The general answer requires optimizing over the fiber structure and computational resources.

**Conjecture 7.2.** *The minimum representation size $n^*$ that achieves $H_T(X) \leq h$ satisfies:*
$$n^* = \left\lceil \frac{m}{2^{h - \Delta_{\mathrm{comp}}}} \right\rceil,$$
*where $\Delta_{\mathrm{comp}}$ depends on $T$ and the complexity of the true distribution $p_X$.*

### 7.4 The Adjoint Functor

**Open Problem 4.** *Does the bridge functor $\Phi$ have a right adjoint $\Psi: \mathbf{Epipl}_{\mathbf{Fin}} \to \mathbf{EAS}_{\mathbf{Fin}}$?*

If $\Phi$ has a right adjoint, then there is a natural bijection:
$$\mathrm{Hom}_{\mathbf{Epipl}}(\Phi(A), B) \cong \mathrm{Hom}_{\mathbf{EAS}}(A, \Psi(B)),$$
which would provide a systematic way to "pull back" Epiplexity morphisms to EAS.

**Conjecture 7.3.** *$\Phi$ does not have a right adjoint, because the non-fullness of $\Phi$ creates morphisms in $\mathbf{Epipl}_{\mathbf{Fin}}$ that cannot be "approximated" by any EAS morphism in a functorial way. The non-fullness is an obstruction to the existence of an adjoint.*

The resolution of this conjecture would determine whether the discrete–continuous duality can be "completed" to an adjunction, or whether the asymmetry is categorically irreducible.

### 7.5 Dynamic Environments

**Open Problem 5.** *Extend the three theorems to dynamic environments where $E$ evolves under $T_E$, and the representation $R_S$ must track this evolution under $T_R$.*

In the static case, the decomposition holds for a fixed time step. In the dynamic case, the components may change over time as the system adapts. A natural question is whether the decomposition extends to a time-averaged version:
$$\overline{H_T}(X) = \log_2\frac{m}{n} + \overline{\Delta}_{\mathrm{dist}} + \overline{\Delta}_{\mathrm{waste}} + \overline{\Delta}_{\mathrm{comp}},$$

This would connect to EAS Theorem T6 (intelligence as the rate of cognitive loss reduction): if the system is learning, then $\overline{\Delta}_{\mathrm{dist}}$ and $\overline{\Delta}_{\mathrm{comp}}$ should decrease over time, while $\log_2(m/n)$ remains constant.

### 7.6 Connection to VC Theory

**Open Problem 6.** *Can the distributional distortion $\Delta_{\mathrm{dist}}$ be related to the VC dimension $d_{\mathrm{VC}}$ of the function class induced by the representation $f$?*

The prior conceptual work [(EAS-Static-Statistical-Bridge-v2)](File: EAS-Static-Statistical-Bridge-v2.md) proposed a three-link chain $m \to S_T \to d_{\mathrm{VC}}$. Theorem A proves the first link. The connection between $\Delta_{\mathrm{dist}}$ and $d_{\mathrm{VC}}$ would be the second link.

**Conjecture 7.4.** *For a representation $f: E \to R_S$ that induces a function class $\mathcal{F} = \{g \circ f : g: R_S \to \{0,1\}\}$ with VC dimension $d_{\mathrm{VC}}$:*
$$\Delta_{\mathrm{dist}} \leq C \cdot \frac{d_{\mathrm{VC}} \log(m/d_{\mathrm{VC}})}{m},$$
*for a universal constant $C > 0$.*

This would bound the distributional distortion in terms of the statistical complexity of the representation.

---

## 8. Conclusion

We have established three theorems that rigorously bridge the Epistemic Axiomatic System (EAS) and the Epiplexity framework, forming the mathematical backbone of the discrete–continuous duality between these two theories of cognition and information.

**Theorem A** proves that the EAS cardinality constraint $\mathrm{card}(R_S) < \mathrm{card}(E)$ imposes a hard information-theoretic lower bound $H_T(X) \geq \log_2(m/n)$ on the time-bounded entropy. This is the discrete, combinatorial foundation of the duality — a necessary condition that no finite cognitive system can escape, regardless of its computational resources or architectural sophistication. The proof combines three pillars: Gibbs' inequality (the cross-entropy bounds the Shannon entropy from above), the chain rule of entropy (decomposing total uncertainty into "which fiber" and "within the fiber"), and Jensen's inequality (the conditional entropy within fibers is minimized by uniform partitioning). Each pillar corresponds to a distinct information-theoretic principle, and their combination yields the tight bound.

**Theorem B** constructs an explicit bridge functor $\Phi: \mathbf{EAS}_{\mathbf{Fin}} \to \mathbf{Epipl}_{\mathbf{Fin}}$ and proves it is faithful but not full. This is the categorical expression of the duality's asymmetry: the discrete world embeds into the continuous world without losing morphism structure (faithfulness), but the continuous world is strictly richer — it contains stochastic morphisms (random maps, approximate simulations, probabilistic models) that no deterministic EAS system can realize (non-fullness). The non-fullness is not a deficiency of the construction but a reflection of the genuine gap between deterministic and probabilistic descriptions of cognition. We showed that this gap is universal: every non-trivial EAS system admits Epiplexity morphisms without EAS pre-images, because A1(a) guarantees the existence of fibers of size $\geq 2$, and within-fiber randomization is always a valid stochastic morphism.

**Theorem C** decomposes the information loss $H_T(X) - \log_2(m/n)$ into three non-negative components — distributional distortion $\Delta_{\mathrm{dist}}$, representational waste $\Delta_{\mathrm{waste}}$, and computational overhead $\Delta_{\mathrm{comp}}$ — each with a precise information-theoretic and operational meaning. The decomposition is canonical: $\Delta_{\mathrm{dist}} = D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S))$ (the divergence from the ideal uniform representation), $\Delta_{\mathrm{waste}} = H(Y)$ (the entropy of the representation itself), and $\Delta_{\mathrm{comp}} = D_{\mathrm{KL}}(p_X \| P^*)$ (the cost of computational boundedness). The waste-distortion trade-off $\Delta_{\mathrm{waste}} + \Delta_{\mathrm{dist}} = \log_2 n$ shows that the total cost of the representation is purely combinatorial, depending only on the cardinality $n$.

Together, these three theorems establish a complete mathematical picture of the discrete–continuous duality:

1. **The discrete side** (EAS, Theorem A) provides **hard constraints**: $\log_2(m/n)$ bits of information loss are unavoidable.
2. **The categorical bridge** (Theorem B) provides **structural relationships**: the embedding is faithful but not full, reflecting the genuine asymmetry between deterministic and probabilistic cognition.
3. **The continuous side** (Epiplexity, Theorem C) provides **analytic resolution**: the information loss decomposes into components that can be independently optimized.

The deepest implication is that the discrete–continuous duality is not merely a convenient reformulation but a **structural principle** of cognition: finite cognitive systems are subject to discrete combinatorial constraints (from EAS), and the information loss imposed by these constraints is quantified and decomposed by the continuous analytical framework (from Epiplexity). The passage from discrete to continuous is faithful (no information is lost in the translation) but not reversible (the continuous world is strictly richer). This asymmetry is the mathematical signature of the fact that cognition is both *constrained* (by cardinality) and *resource-sensitive* (by computational bounds).

---

## Appendix A: Jensen's Inequality — Detailed Verification

**Proposition A.1.** *Let $\lambda_1, \ldots, \lambda_n$ be positive integers with $\sum_{i=1}^n \lambda_i = m$. Then:*
$$\frac{1}{n}\sum_{i=1}^n \lambda_i \log_2 \lambda_i \geq \frac{m}{n}\log_2\frac{m}{n}.$$

*Proof.* The function $\phi: (0, \infty) \to \mathbb{R}$ defined by $\phi(x) = x \log_2 x$ is convex on its domain, since:
$$\phi'(x) = \log_2 x + \frac{1}{\ln 2}, \qquad \phi''(x) = \frac{1}{x \ln 2} > 0 \quad \text{for all } x > 0.$$

By Jensen's inequality applied to the convex function $\phi$ with the uniform distribution on $\{1, \ldots, n\}$:
$$\frac{1}{n}\sum_{i=1}^n \phi(\lambda_i) \geq \phi\!\left(\frac{1}{n}\sum_{i=1}^n \lambda_i\right) = \phi\!\left(\frac{m}{n}\right) = \frac{m}{n}\log_2\frac{m}{n}.$$

Equality holds if and only if $\lambda_1 = \lambda_2 = \cdots = \lambda_n$, i.e., all fibers have equal size. $\square$

**Corollary A.2.** *The conditional entropy $H(X \mid Y) = \frac{1}{m}\sum_r \lambda_r \log_2 \lambda_r$ satisfies:*
$$H(X \mid Y) \geq \log_2\frac{m}{n},$$
*with equality if and only if all fibers have equal size $m/n$ (requiring $n \mid m$).*

---

## Appendix B: The Fiber Model as a $T$-Bounded Program

We verify that the fiber model $P^*_f$ used in the construction of the bridge functor $\Phi$ is indeed a $T$-bounded program.

**Definition B.1** (Fiber Model Program). *The fiber model program $P^*_f$ is:*

*Input:* An environment state $e \in E$.

*Algorithm:*
1. Compute $r = f(e)$.
2. Output the uniform distribution on the fiber $f^{-1}(r)$.

*Code length:* $|P^*_f| = \lceil \log_2 n \rceil + \sum_{r \in R_S} \lceil \log_2 \lambda_r \rceil$ bits (encoding the map $f$ and the fiber sizes).

*Runtime:* $O(|f|)$ time to evaluate $f$, plus $O(1)$ time to generate the uniform distribution on the fiber (assuming precomputed fibers). Total: $O(|f| + \log m)$ time.

**Proposition B.2.** *For any time bound $T \geq C \cdot |f|$ for a constant $C$ depending on the computational model, the fiber model $P^*_f$ is in the program class $\mathcal{P}_T$.*

*Proof.* The program terminates in time $O(|f| + \log m)$. For $T$ sufficiently large (at least proportional to the size of the representation map $f$), the program is $T$-bounded. $\square$

**Remark B.3.** The fiber model is typically *not* the optimal $T$-bounded program $P^*$ in the MDL sense. A program that exploits additional structure in the environment (e.g., temporal correlations, hierarchical organization) can achieve lower cross-entropy. The fiber model serves as an *upper bound* on $H_T(X)$ and as the natural model induced by the EAS representation structure.

---

## Appendix C: Extended Numerical Examples

### C.1 Binary Environment with Binary Representation

$m = 4$, $n = 2$, $E = \{00, 01, 10, 11\}$, $R_S = \{0, 1\}$, $f(e) = e_1$ (first bit).

Fibers: $\lambda_0 = 2, \lambda_1 = 2$. Uniform fibers.

| Component | Value |
|---|---|
| $\log_2(m/n)$ | $1$ bit |
| $\Delta_{\mathrm{dist}}$ | $0$ |
| $\Delta_{\mathrm{waste}}$ | $1$ bit |
| $\Delta_{\mathrm{comp}}$ | $0$ |
| **$H_T(X)$** | **$2 = \log_2 4$ bits** |

### C.2 Skewed Representation

$m = 8$, $n = 3$, fibers $\lambda_a = 3, \lambda_b = 2, \lambda_c = 3$.

| Component | Value |
|---|---|
| $\log_2(m/n)$ | $\log_2(8/3) \approx 1.415$ bits |
| $\Delta_{\mathrm{dist}}$ | $\log_2 3 - 1.562 \approx 0.023$ bits |
| $\Delta_{\mathrm{waste}}$ | $H(Y) \approx 1.562$ bits |
| $\Delta_{\mathrm{comp}}$ | $0$ |
| **$H_T(X)$** | **$\approx 3.0 = \log_2 8$ bits** |

### C.3 Ideal Observer Limit

$n = m$ (outside EAS scope, serves as limit).

| Component | Value |
|---|---|
| $\log_2(m/n)$ | $0$ |
| $\Delta_{\mathrm{dist}}$ | $0$ |
| $\Delta_{\mathrm{waste}}$ | $\log_2 m$ |
| $\Delta_{\mathrm{comp}}$ | $0$ |
| **$H_T(X)$** | **$\log_2 m = H(X)$** |

---

## Appendix D: Summary of Key Equations

| Equation | Location | Statement |
|---|---|---|
| MDL decomposition | §2.2 | $\mathrm{MDL}_T(X) = S_T(X) + H_T(X)$ |
| Gibbs' inequality | §3.2, Step 1 | $H_T(X) \geq H(X)$ |
| Chain rule | §3.2, Step 2 | $H(X) = H(Y) + H(X \mid Y)$ |
| Jensen lower bound | §3.2, Step 3 | $H(X \mid Y) \geq \log_2(m/n)$ |
| **Theorem A** | §3.2 | $H_T(X) \geq \log_2(m/n)$ |
| Faithfulness | §4.3 | $\Phi(\alpha) = \Phi(\beta) \Rightarrow \alpha = \beta$ |
| Non-fullness | §4.4 | $\exists\, \psi \notin \mathrm{im}(\Phi)$ |
| **Theorem B** | §4.2 | $\Phi$ is faithful but not full |
| Distributional distortion | §5.1 | $\Delta_{\mathrm{dist}} = D_{\mathrm{KL}}(p_Y \| \mathrm{Unif}(R_S))$ |
| Representational waste | §5.1 | $\Delta_{\mathrm{waste}} = H(Y)$ |
| Computational overhead | §5.1 | $\Delta_{\mathrm{comp}} = D_{\mathrm{KL}}(p_X \| P^*)$ |
| Waste-distortion trade-off | §5.3.2 | $\Delta_{\mathrm{waste}} + \Delta_{\mathrm{dist}} = \log_2 n$ |
| **Theorem C** | §5.1 | $H_T(X) = \log_2(m/n) + \Delta_{\mathrm{dist}} + \Delta_{\mathrm{waste}} + \Delta_{\mathrm{comp}}$ |

---

*Document generated: 2026-07-01*
*Source files: EAS-Single-Axiom-Foundation.md, EAS-Discrete-Continuous-Duality-Proof_evidence.md*
*Key references: arXiv:2601.03220, Baez-Fritz-Leinster (2011), Li (2024) arXiv:2308.05742*
