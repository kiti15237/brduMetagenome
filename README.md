# brduMetagenome

###Quality Control
- Currently using QC-Chain

###Index the herring genome
`bowtie-build /scratch/users/ctataru5/metagenome/herringGenome/GCA...fna herring`
- move all .ebwt files into installations/bowtie-0.12.7/indexes (or whereever bowtie is installed for you)

###Align to herring genome and write out alignments in sam file
`bowtie -S herring ../../../metagenome/testing/brduTest.fastq test.sam'
- herring refers to the indexed database you built in previous step.

###Separate out the unmapped reads
`samtools view -b -f 4 test.bam > test.unmapped.bam`
- -f is a filter flag. The 4 means unmapped reads. If you want mapped reads, use -F, which does the opposite of 4, or mapped reads.

###Convert the unmapped reads back to fastq format for future analysis
`samtools bam2fq test.unmapped.bam > test.unmapped.fastq`
