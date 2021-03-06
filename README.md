# GenomicSelection

Linear regression based algorithms for genomic selection. For Machine learning algorithms see ML_Pipeline and for Artificial neural network algorithms see ANN_Pipeline.


## rrBLUP
See [rrBLUP](https://cran.r-project.org/web/packages/rrBLUP/rrBLUP.pdf) for more information on the algorithm

Packages needed: rrBLUP, data.table

Arguments needed:

Rscript predict_rrBLUP.R [X_file] [Y_file] [Features2Use] [Y_name] [holdout_set] [save_ID] [save_dir]

Example Script:
```
module load R
export R_LIBS_USER=/mnt/home/azodichr/R/library
Rscript ~azodichr/GitHub/GenomicSelection/predict_rrBLUP.R ~azodichr/03_GenomicSelection/rice_DP_Spindel/01_Data/geno.csv ~azodichr/03_GenomicSelection/rice_DP_Spindel/01_Data/pheno.csv all YLD ~azodichr/03_GenomicSelection/rice_DP_Spindel/11_FeatureSel/holdout_set/holdout5.txt rice ~azodichr/03_GenomicSelection/06_otherTraits/rrblup/
```



## BGLR
See [BGLR](https://cran.r-project.org/web/packages/BGLR/BGLR.pdf) for more information on the algorithms available (BL, BRR, BayesA, BayesB)

Packages needed: BGLR, data.table

Arguments needed:

Rscript predict_rrBLUP.R [X_file] [Y_file] [Features2Use] [Y_name] [BGLR_model] [holdout_set] [save_ID] [save_dir]

Example Script:
```
module load R
export R_LIBS_USER=/mnt/home/azodichr/R/library
Rscript ~azodichr/GitHub/GenomicSelection/predict_BGLR.R ~azodichr/03_GenomicSelection/rice_DP_Spindel/01_Data/geno.csv ~azodichr/03_GenomicSelection/rice_DP_Spindel/01_Data/pheno.csv all YLD BL ~azodichr/03_GenomicSelection/rice_DP_Spindel/11_FeatureSel/holdout_set/holdout5.txt rice ~azodichr/03_GenomicSelection/06_otherTraits/rrblup/
```


## Get AIC/BIC performance metrics
Implementation is not complete. BGLR works on local computer and on HPCC, however, rrBLUP only works on a my local computer and when running on HPCC it errors out. Will work on this later if it becomes a metric others want.

Run with the same arguments as rrBLUP and BGLR above, just use code in /GenomicSelection/working/

Packages needed for rrBLUP: rrBLUP, data.table, psych, AICcmodavg
Packages needed for BGLR: BGLR, data.table, AICcmodavg

Could not install AICcmodavg on HPCC because of conflicts. Contacted help desk and they installed for me. To use run (note, this works for BGLR, but not for rrBLUP, is someone else figures this out let me know!): 
```
module purge
module load GCC/7.3.0-2.30  OpenMPI/3.1.1 R/3.5.1-X11-20180604
export R_LIBS_USER=/mnt/home/azodichr/R/library # or wherever your packages are saved
```

```
Rscript working/predict_rrBLUP.R [X_file] [Y_file] [Features2Use] [Y_name] [holdout_set] [save_ID] [save_dir]
Rscript working/predict_rrBLUP.R [X_file] [Y_file] [Features2Use] [Y_name] [BGLR_model] [holdout_set] [save_ID] [save_dir]
```
