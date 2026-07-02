# EAS-ML Foundation

**Epistemological Axiomatic Systems for Machine Learning**

A formal foundation connecting epistemological axioms with machine learning theory — establishing rigorous bridges between abstract knowledge theory and concrete ML phenomena.

> **Core Thesis**: A single axiom about epistemic observers generates the entire structure of learning theory — not by analogy, but by mathematical derivation.

---

## 📦 Contents

| File | Description |
|------|-------------|
| [EAS-Single-Axiom-Foundation.md](./EAS-Single-Axiom-Foundation.md) | **Main Paper** — Single axiom system generating T0–T7 theorems |
| [The-Static-Statistical-Bridge.md](./The-Static-Statistical-Bridge.md) | **Bridge Paper** — Formal connection between EAS and Epiplexity with three proved theorems |
| [EAS-Discrete-Continuous-Duality-Proof.md](./EAS-Discrete-Continuous-Duality-Proof.md) | **Duality Proofs** — Three theorems on discrete-continuous relationship |
| [EAS-OEV-Dynamical-Incompleteness.md](./EAS-OEV-Dynamical-Incompleteness.md) | **OEV Dynamics (v2)** — Dynamical incompleteness theorems for the OEV architecture framework |
| [EAS-OEV-v3-Proofs.md](./EAS-OEV-v3-Proofs.md) | **OEV Core Proofs (v3)** — Structural unreachability, acquisition-verification asymmetry, coupling theorem, game-theoretic extension |
| [T5_TwoStream_Impossibility.lean](./T5_TwoStream_Impossibility.lean) | **Lean 4 Proof** — Formal verification of Two-Stream Impossibility Theorem |
| [comparisons/](./comparisons/) | **Framework Comparisons** — EAS vs Friston FEP and other comparative analyses |

---

## 🧭 Framework Positioning

> *What does this framework say that others haven't?*

### Honest Assessment

EAS-OEV is **not a new physical theory**. It is a **unified diagnostic language and prescriptive toolkit** for cognitive system limitations.

After systematically comparing each core claim against existing theory:

| Our Claim | Who Already Said It | Our Increment |
|-----------|-------------------|---------------|
| Systems are imperfect (δ* > 0) | Ashby's Law of Requisite Variety (1956) | Weaker assumption (no "finite resources" needed) |
| Acquisition ≠ Verification | Kalman observability ≠ controllability (1960s) | Quantified via causal inference |
| OEV three layers | Predictive processing / cybernetics loop | Prescriptive: each limitation → intervention direction |
| Instrumentation is optimal | Hacking, embodied cognition, FEP epistemic foraging | Precise definition via Markov blanket |
| Coupling theorem | Observer effect, niche construction | Formalized framework |
| Game-theoretic extension | Information economics (Akerlof, Stiglitz) | **No increment** — reformulation only |

### Three Genuine Contributions

**1. Unified Perspective.** Three seemingly independent phenomena — epistemic incompleteness (Ashby), causal asymmetry (Kalman/Pearl), information bottleneck (Shannon) — analyzed under **a single Markov blanket framework**. Each component is known; the combination is new.

**2. Prescriptive Structure.** The OEV three layers are not descriptive ("what the world is like") but prescriptive ("what interventions to pursue"). A **diagnostic toolkit** for locating bottlenecks:

| Diagnosis | Prescription |
|-----------|-------------|
| Structural unreachability ($\mathcal{H}$ large) | Instrumentation: shrink $\mathcal{H}$ |
| Acquisition-verification gap ($\mathcal{G} \gg \mathcal{V}$) | Expand verification channel |
| Counterfactual unverifiability | Design counterfactually testable experiments |

**3. Quantitative Metric Combination.** $\delta^*$, $\mathcal{G} - \mathcal{V}$, $H(\mathcal{H}|\mathcal{B}_S)$ are each standard tools, but their combination enables **simultaneous quantitative bottleneck localization** in concrete systems.

### Analogy

EAS-OEV is like a **medical diagnostic framework**. Medicine is not new physics — it uses existing biology and chemistry to diagnose and treat. Its contribution is **diagnostic classification** (symptoms → disease → treatment) and **intervention prescription**.

Similarly, EAS-OEV is not new cognitive science. It uses existing information theory, causal inference, and control theory to **diagnose cognitive limitations** and provide **engineering prescriptions**.

### Core Statement

> *We do not tell you "what the world is like." We tell you "what intervention options you have when facing incompleteness."*

### Scope

**Applicable:** Partially observable + intervenable + instrumentable systems (AI design, scientific methodology, organizational management)

**Not applicable:** Completely unobservable / non-intervenable / non-instrumentable systems (pure black boxes, observational astronomy, historical science)

---

## 🔬 Key Results

### Single Axiom System (EAS)

From one axiom — *no dynamical isomorphism exists for finite observers* — we derive:

- **T0**: Epistemic collapse conditions
- **T1–T4**: Structural properties of finite observers
- **T5**: Two-Stream Impossibility Theorem (formally verified in Lean 4)
- **T6**: Intelligence as rate of epistemic loss reduction
- **T7**: Upper bound I ≤ m²

### Static-Statistical Bridge

Three rigorously proved theorems connecting EAS to Epiplexity (Finzi et al., 2026):

| Theorem | Statement | Significance |
|---------|-----------|--------------|
| **A** | H_T(X) ≥ log₂(m/n) | Information-theoretic cost of discrete observation |
| **B** | Bridge functor Φ is faithful but not full | Continuous world richer than discrete can capture |
| **C** | H_T = log₂(m/n) + Δ_dist + Δ_index + Δ_comp | Three-way entropy decomposition |

### Discrete-Continuous Duality

**Central insight**: Discrete and continuous are not two worlds requiring a bridge — they are two observation modes of the same phenomenon.

Key consequences:
- The bridge functor's *non-fullness* is a feature, not a defect
- Randomness is the channel through which discrete systems access continuous worlds
- Optimization priority: architecture first, compute second

### Dynamical Incompleteness (OEV)

From the structural relation S ⊊ E, we derive:

| Theorem | Statement | Source |
|---------|-----------|--------|
| **2.1** | Structural unreachability: δ* > 0 | S ⊊ E + autonomous dynamics |
| **2.2** | Acquisition-verification asymmetry: $\mathcal{G} - \mathcal{V} \geq \mathcal{G} - C_V$ | DPI + channel capacity |
| **2.3** | Counterfactual unverifiability | Pearl causal hierarchy |
| **2.4** | Coupling amplification: action changes $\mathcal{H}$ → both incompleteness types change together | Dynamic Markov blanket |

**Core prescription**: The optimal strategy is not to think harder, but to **build better instruments** — coupling hidden dynamics ($\mathcal{H}$) into the observable boundary ($\mathcal{B}_S$).

---

## 📐 Architecture Correspondence

The EAS framework maps naturally to the OEV (Orchestrator-Executor-Verifier) three-layer architecture:

```
┌─────────────────────────────────┐
│         Orchestrator            │  ← T6: Intelligence = loss reduction rate
│    (Epistemic loss monitor)     │
├─────────────────────────────────┤
│          Executor               │  ← T5: Two-stream processing
│   (Parallel representation)     │
├─────────────────────────────────┤
│          Verifier               │  ← Theorem A: Information bound check
│    (Cross-validation)           │
└─────────────────────────────────┘
```

---

## 🔗 Resources

- **Zenodo DOI**: [10.5281/zenodo.21106945](https://doi.org/10.5281/zenodo.21106945) (EAS main paper, LaTeX)
- **Bridge Paper DOI**: [10.5281/zenodo.21106935](https://doi.org/10.5281/zenodo.21106935)
- **Epiplexity**: [arXiv:2601.03220](https://arxiv.org/abs/2601.03220) (Finzi et al., CMU + NYU)
- **Epiplexity Lean Formalization**: [apoth3osis.io](https://www.apoth3osis.io/research/projects/epiplexity)

---

## 📋 Citation

```bibtex
@misc{zhang2026eas,
  title={EAS-ML Foundation: Epistemological Axiomatic Systems for Machine Learning},
  author={Zhang, Jing},
  year={2026},
  url={https://github.com/simulai/EAS-ML-Foundation}
}
```

---

## 👤 Author

**Jing Zhang** · Independent Researcher  
ORCID: [0009-0008-3136-2457](https://orcid.org/0009-0008-3136-2457)

---

## 📄 License

This work is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
