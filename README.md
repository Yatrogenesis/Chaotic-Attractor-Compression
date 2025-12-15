# Chaotic Attractor-Based Compression for High-Dimensional Machine Learning Embeddings

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17932389.svg)](https://doi.org/10.5281/zenodo.17932389)
[![arXiv](https://img.shields.io/badge/arXiv-2025.XXXXX-b31b1b.svg)](https://arxiv.org/abs/2025.XXXXX)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Author**: Francisco Molina Burgos
**ORCID**: [0009-0008-6093-8267](https://orcid.org/0009-0008-6093-8267)
**Date**: November 21, 2025
**Version**: 1.0.0

---

## Abstract

High-dimensional embedding vectors (typically 768D for BERT-base) pose significant storage and transmission challenges in modern machine learning systems. We demonstrate that embeddings exhibiting chaotic attractor dynamics enable extreme compression ratios exceeding 200×. Through rigorous analysis of correlation dimension D₂ and Lyapunov exponents λ₁, we identify datasets where embeddings inhabit low-dimensional manifolds (D₂ < 1) within the nominal high-dimensional space. We present a novel compression algorithm based on Principal Component Analysis (PCA) projection followed by delta encoding in the reduced space, achieving **166-261× compression** on synthetic datasets.

**Key Results**:
- Experimental confirmation of chaotic attractors with D₂ = 0.53 in clustered embeddings
- Root cause analysis showing GZIP achieves only 6.33% efficiency on low-entropy deltas
- Novel attractor-based compression: 224× average ratio
- Theoretical framework connecting dynamical systems and information theory

---

## Publication Status

**Current Status** (November 2025):
- ✅ **Preprint**: Published on Zenodo (DOI: 10.5281/zenodo.17680988)
- 🔄 **arXiv**: Pending endorsement (cs.LG, endorsement code: 8CZ4I7)
- 📋 **Peer Review**: Not yet peer-reviewed

**Target Conference Venues**:
- **ICML 2026** (International Conference on Machine Learning)
  - Deadline: ~January 2026 (estimated)
  - Location: TBD
  - Focus: Machine Learning theory and applications

- **DCC 2026** (Data Compression Conference)
  - Deadline: ~November 2025 / January 2026
  - Location: TBD
  - Focus: Data compression algorithms

**Endorsement Request**: Sent to Dr. Leland McInnes (UMAP author) for arXiv cs.LG category

See [PUBLICATION_STRATEGY.md](PUBLICATION_STRATEGY.md) for detailed publication plan.

---

## Repository Structure

```
PP25-CHAOTIC_ATTRACTOR_COMPRESSION/
├── README.md                          # This file
├── LICENSE                            # MIT (code) + CC-BY 4.0 (paper)
├── CITATION.cff                       # Citation metadata
├── .zenodo.json                       # Zenodo metadata
├── CHANGELOG.md                       # Version history
├── PUBLICATION_STRATEGY.md            # Publication plan
├── paper/
│   └── PAPER_CHAOTIC_ATTRACTOR_COMPRESSION.md # Paper (Markdown, pre-print)
├── code/
│   ├── src/                           # Rust implementation
│   ├── Cargo.toml                     # Rust manifest
│   └── results/                       # Experimental results
└── supplementary/                     # Additional materials
```

---

## Quick Start

### Requirements

- Rust 1.75+
- Cargo
- 4GB RAM minimum

### Installation

```bash
git clone https://github.com/Yatrogenesis/PP25-CHAOTIC_ATTRACTOR_COMPRESSION.git
cd PP25-CHAOTIC_ATTRACTOR_COMPRESSION/code
cargo build --release
```

### Run Experiments

```bash
# Full experiment (9 compression methods)
cargo run --release --bin compression-experiment

# Attractor analysis
cargo run --release --bin analyze_attractor

# Delta diagnostics
cargo run --release --bin analyze_deltas
```

### Expected Output

```
📊 TABLA COMPARATIVA FINAL
Dataset: Clustered Topics
  Int8+GZIP:        9.86x (17.0% loss)
  Delta+ANS:        5.33x (14.7% loss)
  Attractor(PCA-10): 261.29x (68.7% loss) ⭐

🌀 Attractor Analysis:
  D₂ = 0.53 (correlation dimension)
  λ₁ = +0.645 (Lyapunov exponent)
  ✅ CHAOTIC ATTRACTOR CONFIRMED
```

---

## Citation

If you use this work, please cite:

### BibTeX

```bibtex
@misc{molina2025chaotic,
  title={Chaotic Attractor-Based Compression for High-Dimensional Machine Learning Embeddings},
  author={Molina Burgos, Francisco},
  year={2025},
  month={November},
  note={Preprint},
  howpublished={Zenodo},
  doi={10.5281/zenodo.17680988},
  url={https://github.com/Yatrogenesis/PP25-CHAOTIC_ATTRACTOR_COMPRESSION}
}
```

### APA

Molina Burgos, F. (2025). *Chaotic Attractor-Based Compression for High-Dimensional Machine Learning Embeddings* [Preprint]. Zenodo. https://doi.org/10.5281/zenodo.17680988

### IEEE

F. Molina Burgos, "Chaotic Attractor-Based Compression for High-Dimensional Machine Learning Embeddings," Zenodo, Nov. 2025. doi: 10.5281/zenodo.17680988

---

## Key Contributions

1. **Experimental Validation**: First demonstration of chaotic attractors (D₂ < 1) in ML embedding datasets
2. **Root Cause Analysis**: Identified GZIP inefficiency (6.33%) for low-entropy delta encoding
3. **Novel Algorithm**: PCA-based attractor compression achieving 166-261× ratios
4. **Theoretical Framework**: Formal connection between dynamical systems and embedding compression
5. **Open-Source Implementation**: Complete Rust codebase with 9 compression methods

---

## Results Summary

| Method | Ratio | Loss | Status |
|--------|-------|------|--------|
| Attractor(PCA-10) | **224×** | 87% | ✅ Maximum compression |
| Int8+GZIP | 9× | 23% | ✅ Best balance |
| Delta+ANS | 5× | 16% | ⚠️ Improvable |
| Delta+GZIP | 1.1× | 0% | ❌ Inadequate |

**Attractor Properties** (Clustered Topics):
- D₂ = 0.53 (nearly one-dimensional!)
- λ₁ = +0.645 (chaotic)
- Theoretical potential: 1,449× compression

---

## License

This work is dual-licensed under:
- **Code**: MIT License
- **Paper**: CC-BY 4.0

See [LICENSE](LICENSE) for details.

---

## Author

**Francisco Molina Burgos**
- ORCID: [0009-0008-6093-8267](https://orcid.org/0009-0008-6093-8267)
- Email: pako.molina@gmail.com
- GitHub: [@Yatrogenesis](https://github.com/Yatrogenesis)

---

## Acknowledgments

This work was conducted independently. I thank the Rust community for excellent scientific computing libraries.

---

## Related Work

- **Product Quantization**: Jégou et al. (2011) - 48× with ANN search
- **Neural Compression**: Ballé et al. (2018) - VAE for images
- **ANS Coding**: Duda (2013) - Optimal entropy coding

---

**Last Updated**: November 22, 2025
**Repository**: https://github.com/Yatrogenesis/PP25-CHAOTIC_ATTRACTOR_COMPRESSION
**DOI**: [10.5281/zenodo.17680988](https://doi.org/10.5281/zenodo.17680988)
