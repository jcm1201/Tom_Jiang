# down-stream WES_auto platform

There are currently two modules, Script_QC_auto.R and Script_MAF2CSV.R, which are used to automatically do the WES down-stream analyses.

## Description
?An in-depth paragraph about your project and overview of use.
Script_QC_auto.R: quality control anlyeses for single or multiple samples. it can automate to get the *.csv from the *.maf files. the *.csv includes the easily understand mutation information. 
Script_MAF2CSV.R: mutations analyses for single or multiple samples.it can get the QC summary table.

## Script_QC_auto.R

### Dependencies

?* Describe any prerequisites, libraries, OS version, etc., needed before installing program.
*? ex. Windows 10 
R version >=3.0

### Installing

There are two common R packeges need, as shown below:
dplyr
jsonlite

### Executing program

```
Script_QC_auto.R QC_files_SBG_output  summary_final.csv 
```
* Script_QC_auto.R is the script.
* Input: QC_files_SBG_output, which include the QC information from the SBG output data.
* Output: summary_final.csv, which includes the QC information of all samples we need.


## example

Here is an example for reference
```
Rscript /home/rstudio/chongming/Xilis_project/WES03/Script/Script_QC_auto.R /home/rstudio/chongming/Xilis_project/WES03/results/QC_files_SBG_output  /home/rstudio/chongming/Xilis_project/WES03/results/summary_final.csv
```

### 3 Sample: DLS1_CRC1_L2, DLS2_MCB_L2, and DLS3_CRC1_L2
```
	sam_ID	total_reads	Total_trimmed_reads	Insert_size_peak	Duplication_rate	trim_rate	Q30_before	Q30_after	GC_before	GC_after	Mapped_reads	Mapping_rate	target_coverage_80	Average_coverage	PASS_FAIL
1	DLS1_CRC1_L2	174727136	174727124	149	0.116658	99.99999313	0.951184	0.951184	0.514448	0.514448	174583566	99.91783874	88	194	PASS
2	DLS2_MCB_L2	199897224	199897220	150	0.280486	99.999998	0.954971	0.954971	0.515621	0.515621	199801653	99.95219193	105	224	FAIL
3	DLS3_CRC1_L2	194848646	194848638	150	0.129028	99.99999589	0.951744	0.951744	0.512618	0.512618	194752270	99.95054212	109	225	PASS
```



## Script_MAF2CSV.R;it can get the QC summary table in one script 

### Dependencies

R version >=3.0

### Installing

dplyr
tidyr

### Executing program

```
Rscript ./Script/Script_MAF2CSV.R  ./MAFs_folder ./important_genes.csv
```
* Script_MAF2CSV.R is the script.
* input: ./MAFs_folder is the folder which include the *.MAF; ./select_genes.csv is the select genes list
* output: *Total_mutation.csv, *Filter_mutation.csv, *_select_genes_mutations.csv 


## example

Here is an example for reference
```
Rscript Script_MAF2CSV.R /home/rstudio/chongming/Xilis_project/WES03/results/somatic_gatk_mutect2 /home/rstudio/chongming/Xilis_project/WES03/results/somatic_gatk_mutect2/genes.csv
```

### Sample: DLS1_CRC1_L2, DLS1_CRC1_L2_Filter_mutation.csv
```
Hugo_Symbol	Entrez_Gene_Id	Chromosome	Start_Position	End_Position	Variant_Type	Reference_Allele	Tumor_Seq_Allele2	tumor_f	t_alt_count	t_ref_count	cDNA_Change	Protein_Change	HGNC_Ensembl_ID	sam_ID	mapID	mut	Variant_Classification
MMP23B	8510	1	1567707	1567707	SNP	T	G	0.168	2	14	c.110T>G	p.L37R	ENSG00000189409	DLS1_CRC1_L2_SSHT72	MMP23B_p.L37R	MMP23B(c.110T>G)	Missense_Mutation
CALML6	163688	1	1846738	1846738	SNP	A	T	0.041	4	139	c.19A>T	p.I7F	ENSG00000169885	DLS1_CRC1_L2_SSHT72	CALML6_p.I7F	CALML6(c.19A>T)	Missense_Mutation
PRDM16	63976	1	3331155	3331155	SNP	G	A	0.447	79	98	c.2635G>A	p.V879M	ENSG00000142611	DLS1_CRC1_L2_SSHT72	PRDM16_p.V879M	PRDM16(c.2635G>A)	Missense_Mutation
```



## Authors

Contributors names and contact info

Tom Jiang
chongming.jiang@xilis.net

## Version History

* 0.1
    * Initial Release

## License

This project is licensed under the [Xilis.Inc] License

## Acknowledgments

We would like to thank Elena Helman, Sebastian Pretzer, Garrett Jenkinson, David Stafford, and all members in Data Science of Xilis,Inc for their suggestions and critical feedback.
