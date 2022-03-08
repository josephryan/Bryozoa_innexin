# Bryozoa Innexin Phylogeny
 Principal Investigators: Nina Castillo, Scott Santagata, and Joseph Ryan 
 
 Draft or Version Number: v.0.01 
 
 Date: 8 March 2022

## SUMMARY OF CHANGES FROM PREVIOUS VERSION
first version

## 1 INTRODUCTION: BACKGROUND INFORMATION AND SCIENTIFIC RATIONALE  

### 1.1 _Background Information_  

Innexins facilitate cell-cell communication by forming gap junctions or non-junctional hemichannels, which play important roles in metabolic, chemical, ionic, and electrical coupling. Phylogenetic analyses have shown that innexins from distantly related lineages have diversified independently (Yen and Saier, 2007).

### 1.2 _Rationale_  

There has not yet been an extensive analysis of innexins in Spiralia (Lophotrochozoa). This analysis will include sets of innexins from 8 major spriralian lineages and will include 5 major bryozoan lineages (including unpublished data). 

### 1.3 _Hypotheses_  

Based on the phylogenetic analysis included in Yen and Saier (2007), which included 1 Annelida, 1 Mollusca, and 1 Platyhelminthes, and outgroups as well as a study on ctenophore innexins (currently in review) that included Lottia gigantea, Capitella teleta, and Schistosoma mansoni as outgroups, we expect that a few innexin families will have been present in the last common ancestor of Spiralia, but that the majority of innexins will be lineage-specific.  

### 1.4 _Objectives_  

Build a phylogeny of the innexin superfamily that can be used to reconstruct the evolution of innexins within Spiralia.

## 2 STUDY DESIGN AND ENDPOINTS  

#### 2.1 Download amino acid files

We will extract innexins from the following protein models or transcriptomes (source in parens) [Phyla in brackets]:<br>
    1. Branchiostoma lanceolatum (ENSEMBL) [Chordata]<br>
    2. Nematostella vectensis (ENSEMBL) [Cnidaria]<br>
    3. Drosophila melanogaster (ENSEMBL) [Arthropoda]<br>
    4. Caenorhabditis elegans (ENSEMBL) [Nematoda]<br>
    5. Capitella teleta (ENSEMBL) [Annelida]<br>
    6. Lottia gigantea (ENSEMBL) [Mollusca]<br>
    7. Schistosoma mansoni (ENSEMBL) [Platyhelminthes]<br>
    8. Adineta vaga (ENSEMBL) [Rotifera]<br>
    9. Crassostrea gigas (ENSEMBL) [Mollusca]<br>
    10. Lingula anatina (ENSEMBL) [Brachiopoda]<br>
    11. Phoronis australis (OIST) [Phoronida]<br>
    12. Notospermus geniculatus (OIST) [Nemertea]<br>
    13. Praesagittifera naikaiensis (OIST) [Platyhelminthes]<br>
    14. Bugula neritina (NCBI PRJNA498596) [Ectoprocta]<br>
    15. Homera antarctica (NEW) [Ectoprocta]<br>
    16. Cellarinelloides crassus (NEW) [Ectoprocta]<br>
    17. Alcyonidium flabelliforme (NEW) [Ectoprocta]<br>
    18. Electra sp. (NEW) [Ectoprocta]<br>
    19. Streblospio benedicti (http://zakas.statgen.ncsu.edu/data/Sbenedicti_v2.proteins.fasta.gz) [Annelida]

#### 2.2 Build alignment using hmmsearch  

```
hmm2aln.pl --fasta_dir=dir --hmm=PF00876.hmm --name=hmm2aln.output --threads=48 --nofillcnf=nofill.conf
```

#### 2.3 Generate a maximum likelihood tree  

```
iqtree-omp -s [alignment] -nt AUTO -bb 1000 -m TEST -pre [output prefix] 
```

#### 2.4 Generate a Bayesian tree

```
prset aamodelpr = fixed(BEST_MODEL_FROM_IQ-TREE); lset rates=gamma;
```

#### 2.5 Choose best tree to be the main figure based on the tree with best likelihood score

```
raxmlHPC -p 12345 -m PROTGAMMA[best-fit_model] -s [aln file] -n [name]
```

## 3 WORK COMPLETED SO FAR WITH DATES  

No analyses have been conducted

## 4 LITERATURE REFERENCED

Yen MR, Saier Jr MH. Gap junctional proteins of animals: the innexin/pannexin superfamily. Progress in biophysics and molecular biology. 2007 May 1;94(1-2):5-14.

## APPENDIX

Version&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;Date&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Significant Revisions  
1.1  
1.2  
1.3  
1.4  
