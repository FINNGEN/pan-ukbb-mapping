# Pan-UK Biobank and FinnGen phenotype mapping

This repository contains tsv files that maps the Pan-UKBB GWAS results to FinnGen results.

The mapping was done using ICD-10 definitions for FinnGen endpoints. Specifically, the mapping was done using the released endpoint definitions, using columns COD_ICD_10, HD_ICD_10, and CANC_TOPO for ICD-10 definitions. The INCLUDE column was used for including other endpoint definitions to an endpoint. The match file is included in this repository.

## Matching procedure and code used

Writeup on phenotype matching for R6: <https://github.com/FINNGEN/meta-analysis-runs/tree/main/PHENOMAP_R6>

Phenotype matching script: <https://github.com/FINNGEN/phenotype-matching>

## Files

|filename|description|
|--|--|
| `fg_ukbb_file`| File with matching FinnGen and Pan-ukbb endpoints, as well as google cloud storage links to summary stats of both. |
| `fg_R6_pan_ukbb_map.tsv`| mapping file between Finngen R6 phenotypes and the Pan-ukbb endpoints. |
| `fg_R8_pan_ukbb_map.tsv`| mapping file between Finngen R8 phenotypes and the Pan-ukbb endpoints. |
| `fg_R12_pan_ukbb_map.tsv`| mapping file between Finngen R12 phenotypes and the Pan-ukbb endpoints. |

## Column descriptions

### fg_ukbb_file

|column|description|
|---|---|
|fg_phenotype|FinnGen phenotype name|
|fg_link|FinnGen phenotype summary statistic link. Not all of the phenotypes have been analysed, for example due to too low case numbers.|
|ukbb_phenotype|Pan-ukbb phenotype name, a Phecode or an ICD10 code.|
|ukbb_link|link to Pan-UKBB phenotype summary statistic. Lifted to build 38.|

### fg_R*_pan_ukbb_map.tsv

|column|description|
|---|---|
|endpoint_1|endpoint/phenotype that all endpoint_2s were matched against, FinnGen R6 endpoints |
|endpoint_2|best match for endpoint_1, Pan-UKBB endpoints |
|score| similarity score between finngen(endpoint_1) and pan-ukbb (endpoint_2) endpoints calculated by dividing the size of the unique FG ICD10 codes' and unique Phecode ICD10 codes' intersection by the size of their union. |
|matches_1|Matching ICD10 codes for FinnGen endpoint|
|matches_2|matching ICD10 codes for Pan-UKBB endpoint|
|regex_1|regex that was used to match FinnGen endpoint to ICD10 codes|
|regex_2|not applicable, Pan-UKBB phenotypes were not matched using regex but a mapping from Phecodes to ICD10|
|other_hits|All of the other pan-ukbb endpoints that matched the FinnGen endpoint. Written as 'endpoint\|score' and multiple values are separated with a semicolon.|

## File resources

FinnGen R12 phenotype file was acquired from [FinnGen homepage](https://www.finngen.fi/sites/default/files/inline-files/FINNGEN_ENDPOINTS_DF12_Final_2023-05-17_public.xlsx) and exported as tab-separated file.  
Pan-ukbb phenotype file was acquired from [pan-ukbb phenotype manifest](https://docs.google.com/spreadsheets/d/1AeeADtT0U1AukliiNyiVzVRdLYPkTbruQSk38DeutU8/edit#gid=30994804)  
ICD10 -> phecode map was acquired from [pan-ukbb github](https://raw.githubusercontent.com/atgu/ukbb_pan_ancestry/master/data/UKB_PHENOME_ICD10_PHECODE_MAP_20200109.txt)  
