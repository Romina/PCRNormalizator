## PCRNormalizator

> **A R script for candidate endogenous miRNAs identification in quantitative RT-PCR experiments**.

It's a data-driven approach to select reference normalizers based on a combination of three different algorithms as described by [1] and used in [2].

geNorm [3] and Normfinder [4], which were implemented into the R/Bioconductor package NormqPCR [5], and a CV-based score generate a stability score such that a smaller score corresponds to higher expression stability. They are combined into the **Summarized Stability Score (SSS)** to select the most stable housekeeping miRNAs according to all the methods. 

In more details, for each miRNA, geNorm calculates the pairwise variation (V) with all other miRNAs across the samples and defines a stability score (M) as the average V of a particular miRNA with all other control miRNAs. Genes with the lowest M values have the most stable expression. Instead, Normfinder is a model-based approach which estimates the intergroup and intragroup variations of a miRNA, and then combines them into a stability value (rho). Then, for each miRNA  the coefficient of variation (CV) is calculated as its standard deviation across samples divided by the mean and scaled it by the sum of all CVs for each sample (CV score). Lastly, the SSS is calculated as the three-dimension Euclidean distance from the origin, i.e.,
SSS = sqr(meanM^2 + rho^2 +CVscore^2) 

In so doing, SSS combined the results from all the methods and allowed to reveal the most
The stability scores generated by each algorithm and SSS are shown for the top 10 candidate miRNAs.


### Usage
Download .zip archive, open .Rmd file using RStudio and execute the notebook chunks.

A tab delimited txt file with Ct values should be provided (see data/Raw_selectedmiRNA.txt as an example). A further tab delimited txt file with sample grouping is needed (see data/samples.txt).


**References**

[1] Marabita F,de Candia P, Torri A, Tegnér J, Abrignani S, Rossi RL "Normalization of circulating microRNA expression data obtained by quantitative real-time RT-PCR." Brief. Bioinform. 2016

[2] Grieco GE, Sebastiani G, Eandi CM, Neri G, Nigi L, Brusco N, D’Aurizio R, Posarelli M, Bacci T, De Benedetto E, Fruschelli M, Orlandini M, Galvagni F, Dotta F, Tosi GM "MicroRNA expression in the aqueous humor of patients with diabetic macular edema."" IntJMolScie 2020

[3] Vandesompele J, De Preter K, Pattyn F, Poppe B, Van Roy N, De Paepe A, Speleman F "Accurate normalization of real-time quantitative RT-PCR data by geometric averaging of multiple internal control genes". Genome Biol. 2002

[4] Andersen CL, Jensen JL, Ørntoft TF "Normalization of real-time quantitative reverse transcription-PCR data: A model-based variance estimation approach to identify genes suited for normalization, applied to bladder and colon cancer data sets". Cancer Res. 2004

[5] Perkins JR, Dawes JM, Orengo C, McMahon SB, Bennett DL, Kohl M "ReadqPCR and NormqPCR: R packages for the reading, quality checking and normalisation of RT-qPCR quantification cycle (Cq) data". BMC Genomics 2012 


