### **This repository has now been archived. The new home for the Broad exome germline pipeline is in the [WARP](https://github.com/broadinstitute/warp) repository. The workflows are also accessible from the [WARP Dockstore Collection](https://dockstore.org/organizations/BroadInstitute/collections/WARPpipelines) **

# gatk4-exome-analysis-pipeline

### Purpose :
This WDL pipeline implements data pre-processing and initial variant calling according to the [GATK Best Practices](https://gatk.broadinstitute.org/hc/en-us/articles/360035535912) for germline SNP and Indel discovery in human exome sequencing data. The workflow takes as input an array of unmapped BAM files (all belonging to the same sample) to perform preprocessing tasks such as mapping, marking duplicates, and base recalibration then uses Haplotypecaller generate a GVCF or VCF. By default the workflow produces a single CRAM file and a GVCF to be used in [joint calling](https://gatk.broadinstitute.org/hc/en-us/articles/360035890431), but can be set to directly output a VCF instead of a GVCF.

- If you are starting with FASTQ files visit the [seq-format-conversion](https://github.com/gatk-workflows/seq-format-conversion) repository for workflows to convert FASTQs to unmapped BAMS.
- The CRAM output from this workflow can be used to perform a variety of other analysis like somatic short variant discovery, germline short variant discovery, or germline copy number variant discovery. Visit the GATK Best Practices documentation to determine what [Best Practices Workflows](https://gatk.broadinstitute.org/hc/en-us/sections/360007226651) are vailable for BAM files.

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
  - Successfully tested on v52

### Important Notes :
- Runtime parameters are optimized for Broad's Google Cloud Platform implementation.
- For help running workflows on the Google Cloud Platform or locally please
view the following tutorial [(How to) Execute Workflows from the gatk-workflows Git Organization](https://gatk.broadinstitute.org/hc/en-us/articles/360035530952).
- Please visit the [User Guide](https://gatk.broadinstitute.org/hc/en-us/categories/360002310591) site for further documentation on our workflows and tools.

### Contact Us : 
- The following material is provided by the Data Science Platforum group at the Broad Institute. Please direct any questions or concerns to one of our forum sites : [GATK](https://gatk.broadinstitute.org/hc/en-us/community/topics) or [Terra](https://support.terra.bio/hc/en-us/community/topics/360000500432).

### LICENSING :
Copyright Broad Institute, 2020 | BSD-3

This script is released under the WDL open source code license (BSD-3) (full license text at https://github.com/openwdl/wdl/blob/master/LICENSE). Note however that the programs it calls may be subject to different licenses. Users are responsible for checking that they are authorized to run all programs before running this script.
