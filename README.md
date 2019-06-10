# Skygrid-Protocol
Input and output files accompanying the Skygrid protocol paper 'Bayesian estimation of past population dynamics in BEAST 1.10 using the Skygrid coalescent model'

The folder **0.alignment** contains the files for preparing the initial alignment of 200 Ebolavirus sequences from Sierra Leone:
* 200\_unaligned.fasta: the 200 sequences as downloaded from GenBank
* 200\_alignment\_unclean.fasta: result of aligning the sequences using MAFFT
* 200\_final.fasta: final alignment after cleaning, with the various cleaning steps discussed in Supplementary Materials
* KR105247.gb: example GenBank entry of the Ebolavirus sequence with accession number KR105247

The folder **1.tempest** contains the following input files for generating a maximum-likelihood tree using IQ-TREE:
* 200\_final.fasta: the multiple sequence alignment generated in the previous step
* partitions.nex: NEXUS file (without any genetic data) delimiting the various partitions within the alignment

All other files within the folder are output files generated by IQ-TREE, with the **.treefile** containing the maximum-likelihood (ML) phylogeny

The folder **2.treetime** contains three subfolders with files corresponding to three different steps when generating a time-stamped ML phylogeny:
* 1.iqtree-196taxa: input files (196\_final.fasta and partitions.nex) to generate the ML phylogeny of 196 Ebolavirus sequences using IQ-TREE, as well as the output files
* 2.treetime-inputfiles: input files to run TreeTime on the 196-taxa data set
* 3.treetime-outputfiles: output files from TreeTime

The folder **3.beauti** contains two FASTA files with genetic data, after removing 4 sequences in the TempEst analysis:
* 196\_CDS.fasta: multiple sequence alignment for the coding region
* 196\_IG.fasta: multiple sequence alignment for the aggregated intergenic regions

These 2 files need to be imported into BEAUti in order to setup the various model components for the BEAST analysis.

The folder **4.beast** contains the BEAST XML file that was generated using BEAUti.

Finally, the folder **5.tracer** contains the output files of 2 independent BEAST analyses of the generated XML file:
* BEAST\_100m\_run.1.log: first replicate of the BEAST analysis, with starting seed 123
* BEAST\_100m\_run.2.log: second replicate of the BEAST analysis, with starting seed 456

These files need to be loaded into Tracer in order to assess convergence and proper mixing of the analyses, as well as determining burn-in.
Note that we here do not provide the **.trees** files generated during the BEAST analysis, as these are not needed to reconstruct the past population dynamics using the Skygrid coalescent model.
