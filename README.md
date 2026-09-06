# 📚 Idris2-Naray-Wiki

**Literate Documentation, Formal Specifications, and Verification Suite for [Idris2-Naray](../Idris2-Naray).**

[![Idris2](https://img.shields.io/badge/Idris2-Verified_Wiki-blue.svg)](https://github.com/idris-lang/Idris2)

---

## 📖 Introduction

`Idris2-Naray-Wiki` is the executable verification and literate knowledge base for `Idris2-Naray`. It formalizes the binary ($\mathbb{F}_2$) to ternary ($\mathbb{F}_3$) field transition, Narayana polynomial combinatorics, and elaborator reflection proof audits.

### 🗺️ Quick Reference & Catalogs
* **[Binary-Ternary Narayana Synthesis](Library/Wiki/Foundations/Binary_Ternary_Narayana_Synthesis.md)** — Comprehensive literate synthesis of Narayana polynomials $N(n, k)$, Catalan numbers $C_n$, unit group expansions, and metric state capacities.

---

## 🛠️ Building & Verifying

To build the verification suite and execute all property tests:

```bash
# Build executable
toolbox run -c fedora-toolbox-44 /var/home/justin/.local/bin/idris2 --build Idris2-Naray-Wiki.ipkg

# Run verification suite
toolbox run -c fedora-toolbox-44 ./build/exec/naray-verify
```

---

© Justin Kelly. All rights reserved.
