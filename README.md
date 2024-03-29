# RNAseq pipeline analysis



## Clone git hub directory
```
git clone https://github.com/thibaultdestanque/RNA_seq_Nextflow.git
```

## Import univec
Import univec.fasta and put it in `Other_files` directory.
```
wget Other_files/univec.fasta ftp://ftp.ncbi.nlm.nih.gov/pub/UniVec/UniVec
```

## Import Genome and annotation
Import your genome and its annotation (gff3) and copy it in `Ref_Genome` directory
```
cp Path/to/your/genome/genome.fa Directory/where/you/clone/github/directory/Ref_Genome/genome.fa
cp Path/to/your/annotation/annotation.gff3 Directory/where/you/clone/github/directory/Ref_Genome/annotation.gff3
```

## Import Fastq
Import your fastq files to analyse and put them in `Fastq` Directory
```
cp Path/to/your/fastq/files/*fastq Directory/where/you/clone/github/directory/Fastq/*fastq
```

## Launch pipeline
To launch the pipeline, simply go to the directory `My_folder` (see below) and type: 
```
nextflow run main.nf
```

# Documentation

## Scripts

`main.nf` is the nextflow pipeline with all tools and commands launched. Parameters are stored and can be changed in `nextflow.config`.


## Working directory

Tree folders must look like this: 

`My_folder`                
- `main.nf`                        
- `nextflow.config`                
- `Ref_Genome`                     
   - `genome.fa`                 
   - `genomeIndex`                
        - 'genome index files'      
   - `genome_annotation.gff3`    
- `Fastq`
   - `fastq files to analyse`
- `Other_files`
   - `univec.fa`

-`Folders/files` that must be present before launching the script
            
            
            
## Steps:

### Trimmomatic
Trimming reads tool.

http://www.usadellab.org/cms/index.php?page=trimmomatic
Bolger, Anthony M., Marc Lohse, and Bjoern Usadel. 2014. “Trimmomatic: A Flexible Trimmer for Illumina Sequence Data.” Bioinformatics 30 (15): 2114–20. https://doi.org/10.1093/bioinformatics/btu170.

### Gsnap
Indexing and alignment tool.

Wu, Thomas D., Jens Reeder, Michael Lawrence, Gabe Becker, and Matthew J. Brauer. 2016. “GMAP and GSNAP for Genomic Sequence Alignment: Enhancements to Speed, Accuracy, and Functionality.” In Statistical Genomics: Methods and Protocols, edited by Ewy Mathé and Sean Davis, 283–334. Methods in Molecular Biology. New York, NY: Springer New York. https://doi.org/10.1007/978-1-4939-3578-9_15.
  
### Htseq count
Count of reads per genes.

Falini, Giuseppe, and Simona Fermani. 2004. “Chitin Mineralization.” Tissue Engineering 10 (1–2): 1–6. https://doi.org/10.1089/107632704322791646.



## Conda

### Trimmomatic
Version 0.36

Used in Trim process of main.nf: `conda 'bioconda::trimmomatic=0.36'`. 


### Gsnap
Version 2018.07.04

Used in Index_Genome and Alignment process of main.nf: `conda 'bioconda::gmap=2018.07.04'`


### Htseq-count
Version 0.6.1

Used in Htseq_count process of main.nf: `conda 'bioconda::htseq=0.6.1'`


### RNA seq analysis with R
Using RNAseqAnalysis_last_annotation.R script







