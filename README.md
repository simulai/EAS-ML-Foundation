# EAS-ML Foundation

**Epistemological Axiomatic Systems for Machine Learning**

A formal foundation connecting epistemological axioms with machine learning theory — establishing rigorous bridges between abstract knowledge theory and concrete ML phenomena.

> **Core Thesis**: A single axiom about epistemic observers generates the entire structure of learning theory — not by analogy, but by mathematical derivation.

---

## 📦 Contents

| File | Description | Size |
|------|-------------|------|
| [EAS-Single-Axiom-Foundation.md](./EAS-Single-Axiom-Foundation.md) | **Main Paper** — Single axiom system generating T0–T7 theorems | 135 KB |
| [The-Static-Statistical-Bridge.md](./The-Static-Statistical-Bridge.md) | **Bridge Paper** — Formal connection between EAS and Epiplexity with three proved theorems | 101 KB |
| [EAS-Discrete-Continuous-Duality-Proof.md](./EAS-Discrete-Continuous-Duality-Proof.md) | **Duality Proofs** — Three theorems on discrete-continuous relationship | 69 KB |
| [T5_TwoStream_Impossibility.lean](./T5_TwoStream_Impossibility.lean) | **Lean 4 Proof** — Formal verification of Two-Stream Impossibility Theorem | 9 KB |

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

- **Zenodo DOI**: [10.5281/zenodo.21038853](https://doi.org/10.5281/zenodo.21038853) (all versions)
- **v6 Paper DOI**: [10.5281/zenodo.21105472](https://doi.org/10.5281/zenodo.21105472)
- **Epiplexity**: [arXiv:2601.03220](https://arxiv.org/abs/2601.03220) (Finzi et al., CMU + NYU)
- **Epiplexity Lean Formalization**: [apoth3osis.io](https://www.apoth3osis.io/research/projects/epiplexity)

---

## 📋 Citation

```bibtex
@misc{zhang2026staticstatistical,
  title={The Static-Statistical Bridge: Connecting Epistemic Axiomatic Systems with Epiplexity},
  author={Zhang, Jing},
  year={2026},
  doi={10.5281/zenodo.21105472},
  url={https://zenodo.org/records/21105472}
}
```

---

## 👤 Author

**Jing Zhang** · Independent Researcher  
ORCID: [0009-0008-3136-2457](https://orcid.org/0009-0008-3136-2457)

---

## 📄 License

This work is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## 📊 Framework Comparisons

| File | Description |
|------|-------------|
| [comparisons/EAS-vs-Friston-FEP.md](./comparisons/EAS-vs-Friston-FEP.md) | EAS vs Friston Free Energy Principle — deep comparative analysis |
| [comparisons/EAS-vs-Friston-FEP.pdf](./comparisons/EAS-vs-Friston-FEP.pdf) | Same paper in PDF format |
| [comparisons/EAS-vs-Friston-FEP.tex](./comparisons/EAS-vs-Friston-FEP.tex) | LaTeX source |

