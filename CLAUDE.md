# MoBPS Quarto Book - Future Work & Roadmap

## MoBPS Source Code Reference

When writing or improving chapters, **always reference the MoBPS source code** for accurate function signatures, parameters, and behavior.

### Two Separate Repositories — Know Which to Use

| Repo | URL | Who it's for | Local path |
|------|-----|-------------|------------|
| **Developer repo** (private) | `git@git.wur.nl:mobps/software.git` | Austin (developer) only — pull latest releases and tarballs | `~/Claude/MoBPS/software/` |
| **Public repo** | `https://github.com/tpook92/MoBPS` | All users — what the manual references | N/A (online only) |

**Never put the WUR GitLab URL (`git.wur.nl`) in any chapter or user-facing content.** All instructions in the manual must point to `https://github.com/tpook92/MoBPS` (branch: `master`).

### Source Locations (for writing chapters)

- **Full R package source:** `~/Claude/MoBPS/MoBPS/R/` — extracted from `MoBPS_1.13.15.tar.gz`, contains all function definitions (~40k lines)
- **Workshop examples (working R scripts):** `~/Claude/MoBPS/software/MoBPS_Workshop_WIAS/` — real usage examples across Tasks 1–11
- **Man pages:** `~/Claude/MoBPS/MoBPS/man/` — parameter documentation in `.Rd` format

### How to Use

- Before writing/editing any chapter, read the relevant `.R` source files to verify function names, parameter names, defaults, and behavior
- Use workshop scripts in `MoBPS_Workshop_WIAS/` as authoritative working examples
- Do not invent or guess function signatures — always verify from source
- To update the local source: `cd ~/Claude/MoBPS/software && git pull` (uses the developer WUR GitLab repo)
- If a new tarball appears after a pull (e.g., `MoBPS_1.13.16.tar.gz`), extract it: `cd ~/Claude/MoBPS && tar xzf software/MoBPS_1.13.16.tar.gz`

### Staleness Check

At the start of every conversation, run:

```bash
find ~/Claude/MoBPS/software/ -name "MoBPS_*.tar.gz" -newer ~/Claude/MoBPS/software/MoBPS_1.13.15.tar.gz 2>/dev/null
# and check age:
stat -f "%Sm" -t "%Y-%m-%d" ~/Claude/MoBPS/software/MoBPS_1.13.15.tar.gz
```

If the most recent `MoBPS_*.tar.gz` in `~/Claude/MoBPS/software/` is **older than 28 days**, warn the user:

> "The MoBPS source tarball (`MoBPS_X.X.X.tar.gz`) is more than 28 days old. Consider pulling the latest release: `cd ~/Claude/MoBPS/software && git pull`"

If a newer tarball is found than what is currently extracted in `~/Claude/MoBPS/MoBPS/`, remind the user to re-extract it.

---

## Overview

This document tracks what still needs to be done to make this Quarto book a comprehensive MoBPS cookbook.

**Current Status:** v0.1 - Initial structure complete with 17 chapters covering core functionality.

---

## Immediate Priorities

### 1. Expand Examples with Working Code

**Status:** Most chapters have code snippets but need:
- [ ] Complete runnable examples for each chapter
- [ ] Add expected output after each code block
- [ ] Include visualizations (plots, tables)
- [ ] Test all code examples for correctness

**Chapters needing most work:**
- Chapter 8-11 (Selection/Mating/Breeding) - add complete workflows
- Chapter 12-14 (Genotyping/Genomic Analysis) - show actual GBLUP outputs
- All chapters - add plots and visual results

### 2. Add Case Studies Section

**Status:** Not yet created

Create new chapters with complete, end-to-end case studies:
- [ ] **Case Study 1: Dairy Cattle Genomic Selection**
  - 20 years of selection
  - Multi-trait selection (milk, fat, protein)
  - Compare genomic vs pedigree selection

- [ ] **Case Study 2: Pig Nucleus Breeding**
  - Nucleus + multiplier structure
  - Terminal cross
  - Selection for reproduction and growth

- [ ] **Case Study 3: Maize Hybrid Breeding**
  - Inbred line development
  - Testcross evaluation
  - Heterosis modeling

- [ ] **Case Study 4: Wheat Line Development**
  - Multi-environment trials
  - GxE modeling
  - Line extraction

- [ ] **Case Study 5: Conservation Breeding**
  - Managing diversity
  - Minimizing inbreeding
  - Optimal genetic contribution

### 3. Add Interactive Elements

- [ ] Create downloadable datasets for each chapter
- [ ] Add "Try It Yourself" exercises at chapter ends
- [ ] Create RMarkdown templates for common scenarios
- [ ] Add video tutorial links (if created)

---

## Content Expansion Needed

### Chapter-by-Chapter Improvements

#### Part 1: Getting Started
- [x] Chapter 1: Installation - **Complete**
- [x] Chapter 2: Core Concepts - **Complete**
- [x] Chapter 3: First Simulation - **Complete**
  - [ ] Add troubleshooting section
  - [ ] Add "What can go wrong" callouts

#### Part 2: Building Populations & Traits
- [x] Chapter 4: Creating Populations - **Good foundation**
  - [ ] Add section on importing Ensembl maps
  - [ ] More examples with real VCF files

- [x] Chapter 5: Trait Architecture - **Good foundation**
  - [ ] Add section on validating trait architecture
  - [ ] Examples of estimating effects from GWAS

- [x] Chapter 6: Advanced Population Setup - **Needs expansion**
  - [ ] More detailed `founder.simulation()` examples
  - [ ] Section on validating LD patterns
  - [ ] Comparing simulated vs real LD

- [x] Chapter 7: Population Examples - **Good start**
  - [ ] Add 5-10 more worked examples
  - [ ] Cover more species

#### Part 3: Selection, Mating & Breeding
- [x] Chapter 8: Selection Strategies - **Needs expansion**
  - [ ] Add more custom selection examples
  - [ ] Compare effectiveness of strategies
  - [ ] Economic selection indices

- [x] Chapter 9: Mating Designs - **Needs expansion**
  - [ ] More complex mating strategies
  - [ ] Factorial mating designs
  - [ ] Optimized mate allocation

- [x] Chapter 10: Breeding Simulation - **Needs more examples**
  - [ ] Complete year-by-year breeding program
  - [ ] Multi-stage selection with costs

- [x] Chapter 11: Plant vs Animal - **Too brief**
  - [ ] Dedicated section for plant breeding
  - [ ] Dedicated section for aquaculture
  - [ ] More species-specific examples

#### Part 4: Genotyping & Genomic Analysis
- [x] Chapter 12: SNP Panels - **Too brief**
  - [ ] Imputation examples
  - [ ] Cost-benefit analysis of genotyping
  - [ ] Low-density vs high-density chips

- [x] Chapter 13: Genomic Prediction - **Needs expansion**
  - [ ] Detailed examples for each BVE method
  - [ ] Comparison of methods
  - [ ] Training population optimization
  - [ ] Cross-validation examples

- [x] Chapter 14: Population Structure - **Needs more depth**
  - [ ] Interpretation of results
  - [ ] What values are "good" or "bad"
  - [ ] Managing diversity vs gain trade-offs

#### Part 5: Advanced Topics & Reference
- [x] Chapter 15: Data Export/Import - **Adequate**
  - [ ] Integration with other software examples

- [x] Chapter 16: Performance & Memory - **Good start**
  - [ ] Benchmarks for different scenarios
  - [ ] Memory usage guidelines

- [x] Chapter 17: Function Reference - **Just a skeleton**
  - [ ] Complete parameter descriptions for key functions
  - [ ] Add examples for each function

---

## Missing Major Topics

### Topics That Need Full Chapters

1. **GWAS and QTL Mapping**
   - Performing GWAS in MoBPS
   - QTL mapping with simulated data
   - Power analysis
   - Comparing GWAS hits to true QTLs

2. **Economic Analysis**
   - Using `compute.costs()` and `compute.costs.cohorts()`
   - Optimizing breeding program budgets
   - ROI calculations
   - Cost-benefit of genomic selection

3. **Comparing Breeding Strategies**
   - Framework for comparison
   - Statistical testing
   - Visualizing comparisons
   - Replication and Monte Carlo

4. **Gene Editing Simulation**
   - Using `gene.editing` parameter
   - Simulating CRISPR/Cas9
   - Introgression scenarios
   - Ethical considerations

5. **Advanced Mating Strategies**
   - Optimal genetic contribution (detailed)
   - Mate allocation algorithms
   - Avoiding inbreeding depression
   - Maximizing genetic gain

6. **Working with Large Populations**
   - Scaling to 100K+ individuals
   - Memory management strategies
   - Parallel processing
   - Using HPC clusters

---

## Technical Improvements

### Documentation Quality

- [ ] Add glossary of terms
- [ ] Create quick reference card (1-page PDF)
- [ ] Add "Common Errors and Solutions" appendix
- [ ] Cross-reference between chapters more thoroughly

### Code Quality

- [ ] Ensure all code is reproducible
- [ ] Add `sessionInfo()` to appendix
- [ ] Test on multiple platforms (Windows/Mac/Linux)
- [ ] Add automated testing for code examples

### Visuals

- [ ] Create diagrams for breeding program workflows
- [ ] Improve plot aesthetics (ggplot2 themes)
- [ ] Add conceptual figures for key ideas
- [ ] Include photos/images where helpful

---

## Long-Term Goals

### Version 1.0 Goals

- [ ] Complete case studies (5 minimum)
- [ ] All code examples tested and working
- [ ] Published HTML version online
- [ ] PDF version generated successfully
- [ ] Companion video tutorials created

### Version 2.0 Goals

- [ ] Interactive web applications (Shiny)
- [ ] Integration with teaching materials
- [ ] Community contributions (case studies from users)
- [ ] Translation to other languages?

---

## Known Issues to Address

1. **Placeholder images:** index.qmd references images that don't exist yet
   - `images/mobps-logo.png`
   - `images/pug.png`

2. **Code not evaluated:** All code chunks have `eval: false`
   - Need to decide which should actually run
   - Consider using cached results for slow code

3. **Cross-references:** Some chapter links may be broken
   - Verify all `#sec-*` references work

4. **Mathematical notation:** Some chapters could benefit from equations
   - Selection intensity
   - Genetic gain prediction
   - Inbreeding formulas

---

## Resources Needed

### Data Files
- [ ] Example VCF files (small, for teaching)
- [ ] Example PLINK files
- [ ] Example phenotype files
- [ ] Pre-built population objects for quick start

### External Content
- [ ] Link to MoBPS workshops on GitHub
- [ ] Link to video tutorials (if they exist)
- [ ] Community forum or discussion board

---

## Contributing

This is a living document. Ideas for improvement:

1. **Test the book!** Run through examples and report issues
2. **Suggest topics:** What's missing? What would help?
3. **Contribute examples:** Send your MoBPS scripts/workflows
4. **Improve clarity:** Flag confusing sections
5. **Add case studies:** Share your breeding program simulations

---

## Maintenance Schedule

**Quarterly updates recommended:**
- Q1: Focus on case studies
- Q2: Improve existing content
- Q3: Add new topics
- Q4: Update for new MoBPS versions

---

## Contact for Improvements

To contribute to this book or suggest improvements:
- Open an issue in the GitHub repository
- Email suggestions to the MoBPS development team
- Fork and submit pull requests

---

**Document Version:** 1.0
**Last Updated:** 2025-11-16
**Next Review:** 2025-12-16

