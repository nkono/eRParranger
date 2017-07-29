# eRParranger
A bacterial contig rearrangement system in genomic structure based on replication profiling

## Introduction 
Our strategy achieved contig rearrangement with intracellular DNA replication behaviour mechanisms and can be applied to almost all bacteria because the DNA replication system is commonly observed. Therefore, the results made it possible to understand the genomic structural information and long-range syntenic relationships from a draft genome based on short reads.

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
Usage:   perl eRParranger.pl <command> [options]

Command: -c FILE       SPAdes contig file (format: FASTA)
         -s FILE       read mapped file on SPAdes contig (format: SAM)
         -l INT        minimum contig length [50000]
	 -o STR        output dir name [eRPoutput]
```

perl eRParranger.pl -c [spades_outdir]/contigs.fasta -s [mapped.sam] -l 50000 -o [eRParranger_outdir]


Example data is available from https://github.com/nkono/eRParranger/examples

```
perl eRParranger.pl -c examples/WT_spades_contigs.fasta -s Example/1A1L1_ext1M_spades_1A1L1_ext1M.sam -o output
```


### Output files
This program generates some tsv and fasta format files.

[_appres.tsv] files have contig name, genomic position (start and end), coverage.

[_coverage.tsv] files have genomic position, coverage.

[_tmp.fasta] files have concatenated contig sequence.

[eRParranger.list] file has rearranged contig list.

Here, [contig_] files are generated based on inputted contig data, and [eRParranger_] files are based on rearranged contig data.




