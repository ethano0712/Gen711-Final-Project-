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
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Rat_BN72_reference

head Wistar3_ATTCCT_L001_R1_001.fastq
cat *.fastq > Assembled_wistar.fastq

    ### extracting Tar files
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab
tar -x -f ncurses.tar
cd ncbi-genomes-2022-05-05
gzip -d *.gz

    #isolating sequence (unused)
grep '@' Assembled_wistar.fastq | wc -l
grep '@' Wistar3_ATTCCT_L001_R1_001.fastq | wc -l
grep -A1 '@HWI' Assembled_wistar.fastq | grep -v "@HWI" > Assembled_wistarseq.txt

    # installing tools /reference for assembly
conda install bowtie2
conda install -c bioconda samtools
tar -x -f genome_assemblies_genome_fasta.tar
gzip -d GCF_015227675.2_mRatBN7.2_genomic.fna.gz


   #bowtie2
bowtie2-build BN72_rat_refseq.fna bowtie
bowtie2 --help
    bowtie2 --very-fast-local --qc-filter -x  /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Rat_BN72_reference/bowtie2 -U /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/fastq_files/SRR097977.fastq -U /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/fastq_files/SRR098026.fastq -S /Aligned_wistar.sam
bowtie2 --qc-filter Wistar3_ATTCCT_L001_R2_001.fastq
conda install afterqc


bowtie2 -x /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Bowtie2_index/bt2 --U /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Rat_BN72_reference/Wistar3_ATTCCT_L001_R1_020.fastq -U /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Rat_BN72_reference/Wistar3_ATTCCT_L001_R2_020.fastq --S /Aligned_wistar.sam




python /mnt/c/Users/Ethan\ O\'Keefe/Downloads/AfterQC-master/AfterQC-master/after.py -1 Wistar3_ATTCCT_L001_R2_001.fastq

conda install "C:\Users\Ethan O'Keefe\Downloads\bowtie2-2.4.5-mingw-x86_64 (1)\bowtie2-2.4.5-mingw-x86_64"
which bowtie2
conda update bowtie2
conda install breseq
conda update breseq
conda install bismark
which bowtie2-build
conda install trinity

## working bowtie2 script
bowtie2 -p 4 \
    -x Bowtie2_index/bowtie \
    -U Wistarfastq/Wistar3_ATTCCT_L001_R1_004.fastq \
    -U Wistarfastqreverse/Wistar3_ATTCCT_L001_R2_004.fastq \
    -S Aligned_wistar04.sam

bowtie2 -p 4\
    -x Bowtie2_index/bowtie \
    -U cattest/Assembled_wistar567.fastq \
    -U cattest/Assembled_wistarreverse567.fastq \
    -S Aligned_wistar567.sam

## samtools
        # working sam -> bam script
samtools view -S -b /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Sam_files/Aligned_wistar01.sam > /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Bam_files/Aligned_Wistar01.bam

Conda actviate FinProjEnv
samtools view -S -b /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/cattest/Aligned_wistar567.sam > /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/cattest/Aligned_wistar567.bam
Conda deactivate

samtools -help
samtools index Aligned_Wistar01.bam Aligned_Wistar01.bam.bai
conda create --name FinProjEnv
conda activate FinProjEnv
conda install -c bioconda samtools openssl=1.0
sudo apt-get install libncurses5-dev libncursesw5-dev
conda install -c anaconda ncurses5
conda create --name FinProjEnv2
conda activate FinaProjEnv2
conda update samtools

cd /root
cd /root/miniconda3/envs
ls
cd FinProjEnv
mv ncurses.tar /root/miniconda3/envs
cd lib
ls
mv /root/miniconda3/envs/ncurses.tarncurses-6.3 /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab

# testing multiple fastq assemblies in igv 
cd Final_Project/Wistarfastqreverse
cat Wistar3_ATTCCT_L001_R2_005.fastq  Wistar3_ATTCCT_L001_R2_006.fastq  Wistar3_ATTCCT_L001_R3_007.fastq > Assembled_wistarreverse567.fastq

#====================================== Final Script ================================
######Wistar
# concatenating fastq into assemblises
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Wistarfastq
cat Wistar3_ATTCCT_L001_R1_001.fastq  Wistar3_ATTCCT_L001_R1_002.fastq  Wistar3_ATTCCT_L001_R1_003.fastq Wistar3_ATTCCT_L001_R1_004.fastq  Wistar3_ATTCCT_L001_R1_005.fastq  Wistar3_ATTCCT_L001_R1_006.fastq Wistar3_ATTCCT_L001_R1_007.fastq  Wistar3_ATTCCT_L001_R1_008.fastq > Assembled_wistar1-8.fastq
    #reverse reads
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Wistarfastqreverse
cat Wistar3_ATTCCT_L001_R2_001.fastq  Wistar3_ATTCCT_L001_R2_002.fastq  Wistar3_ATTCCT_L001_R2_003.fastq Wistar3_ATTCCT_L001_R2_004.fastq  Wistar3_ATTCCT_L001_R2_005.fastq  Wistar3_ATTCCT_L001_R2_006.fastq Wistar3_ATTCCT_L001_R2_007.fastq  Wistar3_ATTCCT_L001_R2_008.fastq > Assembled_wistarreverse1-8.fastq

 # Bowtie2 for alignment
bowtie2 -p 4\
    -x Bowtie2_index/bowtie \
    -U Final_data_assembly/Assembled_wistar1-8.fastq \
    -U Final_data_assembly/Assembled_wistarreverse1-8.fastq \
    -S Aligned_wistar1-8.sam

  # Samtools , .sam -> .bam
conda activate FinProjEnv
samtools view -S -b /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Final_data_assembly/Aligned_wistar1-8.sam > /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Final_data_assembly/Aligned_wistar1-8.bam
conda deactivate

#### GK
# decompressing gz files
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/GKfastq
gzip -d *.fastq.gz
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/GKfastqreverse
gzip -d *.fastq.gz
# Concatenating gk fastq into assembly
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/GKfastq
cat GK1_ACTGAT_L001_R1_001.fastq GK1_ACTGAT_L001_R1_002.fastq GK1_ACTGAT_L001_R1_003.fastq  > Assembled_GK1-3.fastq
    #reverse reads
cd /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/GKfastqreverse
cat GK1_ACTGAT_L001_R2_001.fastq GK1_ACTGAT_L001_R2_002.fastq GK1_ACTGAT_L001_R2_003.fastq  > Assembled_GKreverse1-3.fastq

 # Bowtie2 for alignment
bowtie2 -p 4\
    -x Bowtie2_index/bowtie \
    -U Final_data_assembly/Assembled_GK1-3.fastq \
    -U Final_data_assembly/Assembled_GKreverse1-3.fastq \
    -S Aligned_GK1-3.sam

      # Samtools , .sam -> .bam
conda activate FinProjEnv
samtools view -S -b /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Final_data_assembly/Aligned_GK1-3.sam > /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Final_data_assembly/Aligned_GK1-3.bam
conda deactivate

# sorting with igvtools
igvtools sort -m 70000000 Aligned_GK1-3.bam Aligned_GK1-3.sorted.bam
samtools sort Aligned_GK1-3.bam

# Bicseq for CNV calling
conda install -c bioconda bicseq2-norm
conda install -c bioconda bicseq2-seg
BICseq2-norm. --help
BICseq2-norm.pl /mnt/c/Users/Ethan O'Keefe/Documents/Gen_711_Lab/Final_Project/Final_data_assembly/Aligned_GK13.bam  
        # unsucsessful

# SNV with GATK
conda deactivate
conda install -c bioconda gatk
gatk-register /mnt/c/Users/Ethan\ O\'Keefe/downloads/gatk-4.2.6.1/gatk-4.2.6.1/gatk-package-4.2.6.1-local.jar
conda update gatk

# SV with delly
conda install -c bioconda delly
delly call -g /mnt/c/Users/Ethan O'Keefe/Documents/Gen_711_Lab/Final_Project/Rat_BN72_reference/BN72_rat_refseq.fna -o test.bcf -x BN72.excl Aligned_wistar01.sorted.bam

# bcftools
conda install bcftools
bcftools cnv -c /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Rat_BN72_reference/BN72_rat_refseq.fna -s /mnt/c/Users/Ethan O'Keefe/Documents/Gen_711_Lab/Final_Project/Bam_files/Aligned_Wistar01.sorted.bam -o /mnt/c/Users/Ethan O'Keefe/Documents/Gen_711_Lab/Final_Project/ -p 0 test.vcf

bcftools mpileup -O b -o /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/test.bcf \
-f /mnt/c/Users/Ethan O'Keefe/Documents/Gen_711_Lab/Final_Project/Rat_BN72_reference/BN72_rat_refseq.fna /mnt/c/Users/Ethan O'Keefe/Documents/Gen_711_Lab/Final_Project/Bam_files/Aligned_Wistar01.sorted.bam

 bcftools index /mnt/c/Users/Ethan\ O\'Keefe/Documents/Gen_711_Lab/Final_Project/Bam_files/Aligned_wistar01snp.vcf.gz

 bcftools mpileup -f BN72_rat_refseq.fna -O z -o Aligned_wistar03.vcf.gz Aligned_Wistar03.sorted.bam
 bcftools mpileup --no-reference -O b -o Aigned_wistar56.bcf Aligned_Wistar01.sorted.bam

 samtools mpileup -f BN72_rat_refseq.fna Aligned_Wistar02.sorted.bam | bgzip > Aligned_wistar02.vcf.gz

 bcftools view -i '%QUAL>=25' Aligned_wister01.vcf
 bcftools call -O z -mv -o Aligned_wistar02snp.vcf.gz Aligned_wistar02.vcf.gz
 bcftools norm -f BN72_rat_refseq.fna -O z -o Aligned_wistar02norm.vcf.gz Aligned_wistar02.vcf
 bcftools norm -O z -o Aligned_wistar02norm.vcf.gz Aligned_wistar02.vcf
  bcftools norm -f BN72_rat_refseq.fna -O z -o Aligned_wistar56norm2.vcf.gz Aligned_wistar56.vcf

zcat Aligned_wistar02.vcf.gz > Aligned_wistar02.vcf
 zcat Aligned_wistar01snp.vcf.gz | tail | less -S
 gzip Aligned_wistar02.vcf

 bgzip -c Wistar_calls.sorted.vcf > Wistar_calls.sorted.vcf.gz
tabix -p vcf Aligned_wistar02.vcf.gz

bcftools convert -O v -o Wistar_calls.vcf Wistar.calls.bcf
conda install vcftools
vcftools --snp

vcftools --gzvcf Wistar_calls.sorted.vcf.gz --maf 0.99 --max-missing 1.0 --remove-filtered-all --recode --stdout | gzip -c > fixed_in_wistar.vcf.gz

gzip -d fixed_in_wistar.vcf.gz