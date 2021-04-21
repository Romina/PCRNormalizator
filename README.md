# PCRNormalizator




## Imputation of Ct values
Sometimes the Ct values are undetermined (not detected after certain Cycles) or absent (when no reaction takes place in the corresponding well), which raises a mathematical issue for the analysis of the project. 
To address this issue, undetermined values are set to a maximum Ct (e.g. 40). While, if the Ct value is totally absent, an imputation is performed by using the median value of the other biological replicates t.i samples with the same experimental condition. 


###### geNorm: It works by taking the standard deviation of the genes between experimental 
#conditions and comparing it to the other genes within the dataset. The least stable gene 
#is then excluded and the process is repeated, until two genes remain at the end.
#A lower value (<1)depicts higher stability

References
Perkins JR, Dawes JM, Orengo C, McMahon SB, Bennett DL, Kohl M (2012). “ReadqPCR and NormqPCR: R packages for the reading, quality checking and normalisation of RT-qPCR quantification cycle (Cq) data.” BMC Genomics, 13, 296+. doi: 10.1186/1471-2164-13-296, http://www.biomedcentral.com/1471-2164/13/296.


