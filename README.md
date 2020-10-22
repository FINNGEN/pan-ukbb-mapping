# Pan-UK Biobank and FinnGen phenotype mapping

This repository contains a tsv file that maps the Pan-UKBB GWAS results to FinnGen results.
The current mapping can be seen in file `fg-ukbb-file.tsv`

The mapping was done using ICD-10 definitions for FinnGen endpoints. Specifically, the mapping was done using the R6 endpoint definition, using columns COD_ICD_10, HD_ICD_10, and CANC_TOPO for ICD-10 definitions. The INCLUDE column was used for including other endpoint definitions to an endpoint. The match file is included in this repository.

## Files
|filename|description|
|--|--|
| `fg_ukbb_file`| File with matching FinnGen and Pan-ukbb endpoints, as well as google cloud storage links to summary stats of both. |
| `fg_R6_pan_ukbb_map.tsv`| mapping file between Finngen R6 phenotypes and the Pan-ukbb endpoints.|