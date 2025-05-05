---
title: "Resources"
layout: page
---

*This is an archive of essays, protocols, scripts, lecture notes, practicals and other resources*


1. [Molecular biology calculators](/Calculators/)
2. [Code](#Code)
	1. [Matlab scripts](#matlab-scripts)
	2. [Python scripts](#python-scripts)
3. [Text](#text)
	1. [Old texts and manuscripts](#old-texts-and-manuscripts)
	2. [Essays and lecture notes](#essays-and-lecture-notes)

---

# Calculators

## Lab protocols and calculators

- [GoldenGate Calculator](https://cakelabdna.github.io/2768cd316e26196a473a415dc9bdb2c707f1dbd4/index.html)
Online calculator for DNA Assembly.

- [Assembly Report](https://docs.google.com/spreadsheets/d/12G5TwARG7o5OzgPICj9YPiSczuWmx1yngZYTKdHQzaY/edit#gid=683324272&range=A1:J15)    
<iframe width="1000" height="480" src="https://docs.google.com/spreadsheets/d/12G5TwARG7o5OzgPICj9YPiSczuWmx1yngZYTKdHQzaY/htmlembed/sheet?gid=683324272&range=A1:J15"></iframe>

# Code

## MATLAB scripts

- [Plankton Simulator](https://github.com/scaralbi/plankton-simulator)
	The plankton-simulator is a collection of matlab scripts simulating the dynamics of structured microbial communities.
	The simulator is based on a multiscale biophysical model that incorporates species traits, consumer-resource dynamics and stochastic ecosystem assembly.
	The model hierarchically simulates features of ecosystem at different scales by defining three classes in the ecosystem using object-oriented programming in MATLAB: Species, Demes (spatially-isolated subcompartments) and Plankton (collection of Demes).


<img src="https://github.com/scaralbi/plankton-simulator/blob/master/flowchart.png?raw=true" alt="flowchart" style="max-width: 50%; height: auto;">


- [Biofilmer](https://github.com/scaralbi/biofilmer)
	The biofilmer is a repository of MATLAB scripts to quantify properties of fluorescence time-lapse microscopy biofilm images.
	![alt text](https://github.com/scaralbi/biofilmer/blob/master/imageanalysis.png?raw=true)

## Python scripts

- [Plot circular genomes with pyCirclize](https://github.com/scaralbi/MV_Resistance)
A repo to store scripts to analyse and visualise results from WGS and Sanger sequencing experiments
 The scripts are based on python and can be executed via the terminal after having cloned the repo.
 Many of the circular plot diagrams are made using the package pyCirclize.
 
  1. [Plot Whole Genome Sequencing Results against a Reference Genome](#plot-whole-genome-sequencing-results-against-a-reference-genome)
  2. [Compare mutations between wild-type and mutants](#filter-mutations-in-mutants-compared-to-respective-backgrounds)


### [Plot Whole Genome Sequencing Results against a Reference Genome](GenSeqRefViewer.py)
[This Python script](GenSeqRefViewer.py) allows to generate a circular plot of a genomic structure. It draws a diagram of a genome along with various genomic annotations like Forward CDS, Reverse CDS, rRNA, tRNA, and also includes mutation and coverage data for a particular DNA sequencing strain.

#### Instructions

##### Prerequisites
Before you run this script, you need to have the following Python packages installed:

- pycirclize
- pandas
- numpy
- matplotlib
- argparse

You can install these using pip:

```shell
pip install pycirclize pandas numpy matplotlib argparse
```

##### Data Requirements

Your data files should be located in the following paths:
 
- Coverage data and Identity data: `"Data/reads_alignments/{Strain}_{Reference}.csv"`  
- Mutation data: `"Data/variant_analysis/{Reference}_allmutations.csv"`  
- Genbank file for genome annotations: `"Data/genome_annotations/{Reference}.gff"`  

Where:

- `{Strain}` is the strain from which the DNA sequencing reads are obtained.
- `{Reference}` is the accession number of the reference genome sequencing the reads have been aligned to.

The generated figure will be saved to `"Figures/WGS/{Strain}_vs_{Reference}_mutations.png"`.

##### Execution

You can run the script using Python3. From the terminal, navigate to the directory containing the script, and run the following command:

```shell
python3 GenSeqRefViewer.py -strain= "wt_Nixon" -ref= "NC000911"
```

Replace `<strain_name>` with the strain name (as labelled in the csv files) and `<reference_name>` with the reference genome NCBI accession number (e.g., 'NC000911').

#### Outputs
The script generates a circular diagram of a genome with the given strain and reference genome, highlighting areas of low coverage and unconserved genomic regions. The final diagram is saved as a PNG image with a high resolution (DPI=900). The filename will be of the form `"{Strain}_vs_{Reference}_mutations.png"` and it will be saved in the `"Figures/WGS/"` directory.

![alt text](https://github.com/scaralbi/MV_Resistance/blob/main/Figures/WGS/wt_Howe_vs_NC000911_genomeview.png?raw=true)

--- 


# Text

## Old texts and manuscripts

* [Aristotle, *Historia Animalium* 9.36.20, translated by D'Arcy Wentworth Thompson, 1910](/OldTexts/Aristotle_ HistoryofAnimals_IX.html)

* [Historical references on bioelectrochemistry](/OldTexts/Historical_Pills_Bioelectrochemistry.md)

* [ISAAC NEWTON’S GENERAL SCHOLIUM TO THE PRINCIPIA (1713, 1726)](/OldTexts/brief-guide-to-the-general-scholium-a4.pdf)


## Essays and lecture notes


### Genetics, molecular, synthetic biology and biotechnology

* [Molecular Biology](/pdfs/molecularbiology.pdf)
* [GMO Papayas](/pdfs/papayaogm.pdf)
* [Plant Biotechnology](/pdfs/plantbiotech.pdf)
* [Bacterial Genetics](/pdfs/bacterialgenetics.pdf)
* [Genes and Genomes](/pdfs/genesandgenomes.pdf)
* [Genomic Manipulation](/pdfs/GenomicManipulation.pdf)
* [Molecular Biology of The Chloroplast, Peter Nixon](/pdfs/Nixon1.pdf)
* [Systems Biology](/pdfs/isb.pdf)
* [Biophysics, Robert Endres](/pdfs/Lecture_biophysics.pdf)
* [Biophysics, Robert Endres](/pdfs/Lecture_biophysics.pdf)
* [Dynamics in Gene Regulation, Robert Endres](/pdfs/Lecture_dynamics.pdf)
* [Mathematical Modelling in Biology](/pdfs/Lecture_modelling.pdf)
* [Quantitative imaging of cell topology](/pdfs/quantitativeimaginf.pdf)
* [Synthetic Biology](/pdfs/SynBio.pdf)
* [Synthetic Genomics, Tom Ellis](/pdfs/Parts.pdf)
* [Bacterial Logic Gates, Tom Ellis](/pdfs/SynBio.pdf)
* [Part Libraries in SynBio, Tom Ellis](/pdfs/Parts.pdf)
* [Optogenetics, Mark Isalan](/pdfs/Parts.pdf)
* [Advanced Synthetic Biology Applications: Pattern Formation, Mark Isalan](/pdfs/Parts.pdf)
* [Synthetic Biology IC Exam 15-16](/pdfs/SynbioExam2015-16.pdf)

### Biochemistry

* [Structure of the Nicotine Receptor](/pdfs/nAChR.pdf)
* [Neurobiology](/pdfs/Neuro.pdf)
* [Proteins and Enzymes](/pdfs/PROTEINS AND ENZYMES 1-7)
* [Enzymology 1](/pdfs/ENZYMOLOGY)
* [Enzymology 2](/pdfs/ENZYMOLOGY2)
* [DNA Repair](/pdfs/DNArepair.pdf)
* [Bacterial Genetics](/pdfs/bacterialgenetics.pdf)
* [Tryptophan Operon in *B.subtilis*](/pdfs/genesandgenomes.pdf)
* [Bioinformatics](/pdfs/Bioinformatics.pdf)
* [Proteomics](/pdfs/Proteomics.pdf)
* [Protein Folding](/pdfs/proteinfolding.pdf)
* [Biological NMR Spectroscopy](/pdfs/NMR.pdf)
* [Cryo-EM](/pdfs/CRYO-EM.pdf)

### Albi’s essays

* [Prospects for the Development of Cyanobacterial Biofilm Bioreactors](/pdfs/prospects-development-cyanobacterial.pdf)
* [Human Practices in Synthetic Biology](/pdfs/humanpractices.pdf)
* [Economics Thought in Italy Before WWII](/pdfs/economics-italy.pdf)
* [Ricordi d'Africa: La Seconda Battaglia di El Alamein](/pdfs/ricordiafrica.pdf)

# Posters

## The Paradox of The Plankton
<object data="/pdfs/paradox_poster.pdf" type="application/pdf" width="1000px" height="700px">
    <embed src="/pdfs/paradox_poster.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="http://yoursite.com/the.pdf">Download PDF</a>.</p>
    </embed>
</object>

## mini iGEM IC SB 2019- SynBio Field Programmable Gate Array (FPGA)
<object data="pdfs/mini-iGEM-poster.pdf" type="application/pdf" width="1000px" height="700px">
    <embed src="/pdfs/mini-iGEM-poster.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="http://yoursite.com/the.pdf">Download PDF</a>.</p>
    </embed>
</object>

## iGEM PixCell 2018: Electronic Control of Gene Expression
<object data="/pdfs/iGEMposter.pdf" type="application/pdf" width="1000px" height="700px">
    <embed src="/pdfs/iGEMposter.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="http://yoursite.com/the.pdf">Download PDF</a>.</p>
    </embed>
</object>


# Texts


## "Collective Dynamics of Microbial Biofilms Undergoing Signalling Waves"
