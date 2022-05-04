cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/ena_files/ERR557543
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/fastq_files
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project
pwd
ls
cd Gen_711_Lab
cd fastq_files
cd Final_Project
cd ena_files
cd ERR557547
head tar3_ATTCCT_L001_R1_001.fastq
head tar1_ACTGAT_L001_R1_010.fastq
head Wistar3_ATTCCT_L001_R1_009.fastq.gz
head ERR557550_1.fastq.gz
head SRR098026.fastq
gzip -d GK1_ACTGAT_L001_R1_020.fastq.gz

###### end of troubleshooting

    # converting gz files into fastq using gzip decompression
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Wistarfastq
gzip -d Wistar3_ATTCCT_L001_R1_001.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_002.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_003.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_004.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_005.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_006.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_007.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_008.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_009.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_010.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_011.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_012.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_013.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_014.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_015.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_016.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_017.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_018.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_019.fastq.gz
gzip -d Wistar3_ATTCCT_L001_R1_020.fastq.gz

cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Wistarfastqreverse
gzip -d *.fastq.gz
cat *fastq > Assembled_wistar_reverse.fastq

head Wistar3_ATTCCT_L001_R1_001.fastq
cat *.fastq > Assembled_wistar.fastq

    #isolating sequence (unused)
grep '@' Assembled_wistar.fastq | wc -l
grep '@' Wistar3_ATTCCT_L001_R1_001.fastq | wc -l
grep -A1 '@HWI' Assembled_wistar.fastq | grep -v "@HWI" > Assembled_wistarseq.txt

    # installing tools /reference for assembly
conda install bowtie2
conda install -c bioconda samtools
tar -x -f genome_assemblies_genome_fasta.tar
gzip -d GCF_015227675.2_mRatBN7.2_genomic.fna.gz

bowtie2-build BN72_rat_refseq.fna bowtie
bowtie2 --help
    bowtie2 --very-fast-local -x /bowtie2 -1 /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/fastq_files/SRR097977.fastq -2 /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/fastq_files/SRR098026.fastq -S /mnt/c/Users/Ethan\ O\'Keefe/Desktop/Aligned_wistar.sam
bowtie2 --qc-filter Wistar3_ATTCCT_L001_R2_001.fastq
conda install afterqc


bowtie2 --very-fast-local -x /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Wistar3_ATTCCT_L001_R1_020.fastq -2 /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Wistar3_ATTCCT_L001_R2_020.fastq -S /mnt/c/Users/Ethan\ O\'Keefe/Desktop/Aligned_wistar.sam

python /mnt/c/Users/Ethan\ O\'Keefe/Downloads/AfterQC-master/AfterQC-master/after.py -1 Wistar3_ATTCCT_L001_R2_001.fastq
apt install python2

sudo update-alternatives --install /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/bin/python /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/bin/python2.7 1