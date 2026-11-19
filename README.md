# Codon architecture of GJB2 and GJB6 and a complete map of their synonymous alternatives

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24305170.svg)](https://doi.org/10.5281/zenodo.24305170)

Analysis code and output tables for:
Homurlu, S.N.; Altungöz, O. Codon Architecture of the Paralogous Connexin Genes GJB2 and GJB6 and a Complete Map of Their Synonymous Alternatives at the DFNB1 Locus. Submitted to Molecular Genetics and Genomics, 2026.

## Contents
- GJB2_GJB6_manuscript.ipynb: complete analysis workflow that reproduces every number, table and figure in the manuscript, except the splicing predictions.
- SpliceAI_only.ipynb: splicing predictions (SpliceAI v1.3.1) for all 1,130 synonymous alternatives, starting from results/TableS1_all_alternatives.csv; it rebuilds Online Resources 1 and 2 with the SpliceAI columns added.
- input/: input files used in the analysis: RefSeq GenBank records (NM_004004.6, NM_006783.5), human hg38 tRNA genes from GtRNAdb (Release 22) the ClinVar synonymous variant export (accessed 20 October 2026) and, for comparison only, the SpliceAI scores of the 952 SNVs reported by the CADD v1.7 web server (SpliceAI_CADDv1.7_GRCh38_952SNV.csv).
- results/: all output files:
  - Online Resource 1 (ESM_1.xlsx): all 1130 single-codon synonymous alternatives; source tables TableS1_all_alternatives.csv and SpliceAI_GRCh38_1130.csv
  - Online Resource 2 (ESM_2.xlsx): ClinVar synonymous variants with uncertain or conflicting classifications; source tables ClinVar_Synonymous_Atlas_Mapped.csv and SpliceAI_GRCh38_1130.csv
  - SpliceAI delta scores of all 1,130 alternatives (SpliceAI_GRCh38_1130.csv; SpliceAI_only.ipynb)
  - Table 1, summary of all synonymous alternatives, genome-wide gene metrics for MANE Select genes, codon adaptation and tRNA adaptation weights, wobble-penalty sensitivity, topology permutation results, genome-wide summary, primate alignment summary, ancestral codons, evolutionary classification and run metadata
  - Figures 1–4 (Fig1–Fig4; PNG and PDF, 174 mm wide, 600 dpi). The TIFF versions submitted to the journal are produced by the same notebook.

## SpliceAI scores
SpliceAI_only.ipynb computes SpliceAI v1.3.1 delta scores (Jaganathan et al. 2019; maximum distance 50 nt) for all 1,130 synonymous alternatives with the five published SpliceAI models and the GRCh38 gene annotation distributed with the spliceai package. Masked scores, as recommended by the SpliceAI developers for variant interpretation, are used in Online Resources 1 and 2; raw scores are also stored in SpliceAI_GRCh38_1130.csv. The SpliceAI command-line tool skips substitutions in which both alleles are longer than one nucleotide, so its scoring function is reproduced in the notebook with that restriction lifted for the 178 equal-length multinucleotide substitutions; for SNVs the function is identical to the official implementation. For all 952 SNVs, the computed masked scores are identical to the precomputed SpliceAI scores reported by the CADD v1.7 web server (https://cadd.gs.washington.edu/score, model GRCh38-v1.7, annotated output). The GRCh38 reference sequence is retrieved from Ensembl REST, or from the UCSC Genome Browser API if Ensembl is unavailable.

## External data (not included; downloaded automatically by the notebook)
- GENCODE Human Release 50 (GRCh38): annotation and protein-coding transcript sequences, https://www.gencodegenes.org/human/
- SpliceAI v1.3.1 (spliceai package on PyPI): trained models and GRCh38 gene annotation, installed by SpliceAI_only.ipynb
- Ensembl release 116: pairwise primate alignments (LASTZ_NET) via https://rest.ensembl.org and the human ancestral sequence (EPO) from https://ftp.ensembl.org/pub/release-116/

## Software
Python 3.13.18, NumPy 2.4.6, pandas 2.2.3, SciPy 1.16.3, Biopython 1.88, ViennaRNA 2.7.2, matplotlib 3.10.0 (see requirements.txt). Random seed: 2026. SpliceAI_only.ipynb runs SpliceAI 1.3.1 with the TensorFlow and Keras versions provided by Google Colab.

## How to run
1. Open the notebook in Google Colab or Jupyter (an internet connection is required).
2. Run Cells 1 and 2. Cell 2 creates the folder ./gjb_saturation.
3. Copy the four files from input/ into ./gjb_saturation.
4. Run all cells in order. A full run takes about 20–40 minutes; outputs are written to ./gjb_saturation and ./primate_genome.
5. For the splicing predictions, open SpliceAI_only.ipynb and run all cells. When asked, upload results/TableS1_all_alternatives.csv and, optionally, input/SpliceAI_CADDv1.7_GRCh38_952SNV.csv; to reuse the archived scores instead of recomputing them, also upload results/SpliceAI_GRCh38_1130.csv. The SpliceAI step takes about 15–20 minutes on a CPU and less on a GPU.
The NCBI Entrez e-mail address in Cell 2 is used only if the RefSeq records are not found locally; replace it with your own.

## Version history
- v1.2.0: SpliceAI_only.ipynb added; SpliceAI delta scores of all 1,130 synonymous alternatives (results/SpliceAI_GRCh38_1130.csv) and new SpliceAI columns in Online Resources 1 and 2. GJB2_GJB6_manuscript.ipynb and all previous results are unchanged.
- v1.1.0: figures redrawn to Springer artwork requirements and Online Resources 1 and 2 added. Analysis code and all numerical results are unchanged.
- v1.0.0: first archived version.

## License
Code: MIT License. Output tables and figures: CC BY 4.0, except the SpliceAI scores (results/SpliceAI_GRCh38_1130.csv, the SpliceAI columns of Online Resources 1 and 2 and input/SpliceAI_CADDv1.7_GRCh38_952SNV.csv), which derive from the SpliceAI models and the CADD annotation and are provided for academic and non-commercial use under their respective terms.

## Citation
Please cite the article above and this archive: Homurlu, S.N.; Altungöz, O. Analysis code and data for: Codon architecture of the paralogous connexin genes GJB2 and GJB6 and a complete map of their synonymous alternatives (v1.2.0). Zenodo, 2026. https://doi.org/10.5281/zenodo.24305170
