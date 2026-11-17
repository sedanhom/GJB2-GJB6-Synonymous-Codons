# Codon architecture of GJB2 and GJB6 and a complete map of their synonymous alternatives

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24305171.svg)](https://doi.org/10.5281/zenodo.24305171)

Analysis code and output tables for:
Homurlu, S.N.; Altungöz, O. Codon Architecture of the Paralogous Connexin Genes GJB2 and GJB6 and a Complete Map of Their Synonymous Alternatives at the DFNB1 Locus. Submitted to Genes (MDPI), 2026.

## Contents
- GJB2_GJB6_manuscript.ipynb: complete analysis workflow that reproduces every number, table and figure in the manuscript.
- input/: input files used in the analysis: RefSeq GenBank records (NM_004004.6, NM_006783.5), human hg38 tRNA genes from GtRNAdb (Release 22) and the ClinVar synonymous variant export (accessed 20 October 2026).
- results/: all output files: Table 1, summary of all synonymous alternatives, Table S1 (all 1130 alternatives), ClinVar mapping (Table S2 source), genome-wide gene metrics for MANE Select genes, codon adaptation and tRNA adaptation weights, wobble-penalty sensitivity, topology permutation results, genome-wide summary, primate alignment summary, ancestral codons, evolutionary classification, run metadata and Figures 1–4 (PNG and PDF).

## External data (not included; downloaded automatically by the notebook)
- GENCODE Human Release 50 (GRCh38): annotation and protein-coding transcript sequences, https://www.gencodegenes.org/human/
- Ensembl release 116: pairwise primate alignments (LASTZ_NET) via https://rest.ensembl.org and the human ancestral sequence (EPO) from https://ftp.ensembl.org/pub/release-116/

## Software
Python 3.13.18, NumPy 2.4.6, pandas 2.2.3, SciPy 1.16.3, Biopython 1.88, ViennaRNA 2.7.2, matplotlib 3.10.0 (see requirements.txt). Random seed: 2026.

## How to run
1. Open the notebook in Google Colab or Jupyter (an internet connection is required).
2. Run Cells 1 and 2. Cell 2 creates the folder ./gjb_saturation.
3. Copy the four files from input/ into ./gjb_saturation.
4. Run all cells in order. A full run takes about 20–40 minutes; outputs are written to ./gjb_saturation and ./primate_genome.
The NCBI Entrez e-mail address in Cell 2 is used only if the RefSeq records are not found locally; replace it with your own.

## License
Code: MIT License. Output tables and figures: CC BY 4.0.

## Citation
Please cite the article above and this archive: Homurlu, S.N.; Altungöz, O. Analysis code and data for: Codon architecture of the paralogous connexin genes GJB2 and GJB6 and a complete map of their synonymous alternatives (v1.0.0). Zenodo, 2026. https://doi.org/10.5281/zenodo.24305171
