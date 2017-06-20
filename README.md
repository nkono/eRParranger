# eRParranger
A bacterial contig rearrangement system in genomic structure based on replication profiling

## Introduction 
This is a software to rearrange

## Preparation
This program does not require other modules. On the other hand, users should prepare two files (assembled contig file and read mapping file).
The assembled contig file can be obtained from SPAdes program (http://bioinf.spbau.ru/spades).
The sequence reads mapped SAM file on SPAdes contig can be generated by BWA program (http://bio-bwa.sourceforge.net).

## Usage
This program requires the assembled contig file and sam file.
An example of a procedure for preparing these files will be described below.

### [Example] Assembled congif file (In the case of SPAdes)
```
spades.py -1 [read_R1.fq] -2 [read_R2.fq] -o [spades_outdir]
```
### [Example] Read mapping for coverage counting (In the case of bwa)
```
bwa index [spades_outdir]/contigs.fasta
bwa bwa [spades_outdir]/contigs.fasta [read_R1.fq]  [read_R2.fq] > [mapped.sam]
```
### Run eRParranger
```
perl eRParranger.pl -c [spades_outdir]/contigs.fasta -s [mapped.sam] -l 50000 -o [eRParranger_outdir]
```

### Output files
This program generates some tsv and fasta format files. *_appres means 

appres


### Output files

```
NODE_10_length_55551_cov_315.268        down:down = direct
NODE_1_length_1046888_cov_229.472       up:down = comp
NODE_3_length_896359_cov_150.788        up:down = comp
NODE_8_length_78037_cov_117.434 down:down = direct
NODE_6_length_117672_cov_118.524        up:down = comp
NODE_2_length_1015448_cov_150.016       up:up = direct
NODE_5_length_306550_cov_191.22 down:up = comp
NODE_4_length_352879_cov_242.566        down:up = comp
NODE_9_length_59775_cov_314.091 down:up = comp
```



