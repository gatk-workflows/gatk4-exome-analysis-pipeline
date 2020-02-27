# gatk4-exome-analysis-pipeline

### Purpose :
This WDL pipeline implements data pre-processing and initial variant calling according to the GATK Best Practices for germline SNP and Indel discovery in human exome sequencing data.

### Requirements/expectations :
- Human exome sequencing data in unmapped BAM (uBAM) format
- One or more read groups, one per uBAM file, all belonging to a single sample (SM)
- Input uBAM files must additionally comply with the following requirements:
- - filenames all have the same suffix (we use ".unmapped.bam")
- - files must pass validation by ValidateSamFile
- - reads are provided in query-sorted order
- - all reads must have an RG tag
- GVCF output names must end in ".g.vcf.gz"
- Reference genome must be Hg38 with ALT contigs
- Unique exome calling, target, and bait [.interval_list](https://gatk.broadinstitute.org/hc/en-us/articles/360035531852) obtained from sequencing provider. Generally the calling, target, and bait files will not be the same.

### Output :
- Cram, cram index, and cram md5
- GVCF and its gvcf index
- BQSR Report
- Several Summary Metrics

### Software version notes :
- GATK 4 or later 
- Cromwell version support 
  - Successfully tested on v44 
  - Does not work on versions < v23 due to output syntax

### Important Notes :
- Runtime parameters are optimized for Broad's Google Cloud Platform implementation.
- For help running workflows on the Google Cloud Platform or locally please
view the following tutorial [(How to) Execute Workflows from the gatk-workflows Git Organization](https://gatk.broadinstitute.org/hc/en-us/articles/360035530952).
- Please visit the [User Guide](https://gatk.broadinstitute.org/hc/en-us/categories/360002310591) site for further documentation on our workflows and tools.

### Contact Us : 
- The following material is provided by the Data Science Platforum group at the Broad Institute. Please direct any questions or concerns to one of our forum sites : [GATK](https://gatk.broadinstitute.org/hc/en-us/community/topics) or [Terra](https://support.terra.bio/hc/en-us/community/topics/360000500432).

### LICENSING :
Copyright Broad Institute, 2019 | BSD-3

This script is released under the WDL open source code license (BSD-3) (full license text at https://github.com/openwdl/wdl/blob/master/LICENSE). Note however that the programs it calls may be subject to different licenses. Users are responsible for checking that they are authorized to run all programs before running this script.
