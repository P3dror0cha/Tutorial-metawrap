# Preparando o metawrap
export MAMBA_ROOT_PREFIX=~/micromamba
eval "$(./bin/micromamba shell hook -s posix)"
micromamba activate metawrap-env
PATH=/temporario2/12689050/metaWRAP/bin:$PATH

wget ftp.sra.ebi.ac.uk/vol1/fastq/ERR011/ERR011347/ERR011347_1.fastq.gz
wget ftp.sra.ebi.ac.uk/vol1/fastq/ERR011/ERR011347/ERR011347_2.fastq.gz

wget ftp.sra.ebi.ac.uk/vol1/fastq/ERR011/ERR011348/ERR011348_1.fastq.gz
wget ftp.sra.ebi.ac.uk/vol1/fastq/ERR011/ERR011348/ERR011348_2.fastq.gz

wget ftp.sra.ebi.ac.uk/vol1/fastq/ERR011/ERR011349/ERR011349_1.fastq.gz
wget ftp.sra.ebi.ac.uk/vol1/fastq/ERR011/ERR011349/ERR011349_2.fastq.gz

gunzip *.gz

mkdir RAW_READS
mv *fastq RAW_READS

# Módulo READ_QC
mkdir READ_QC
metawrap read_qc -1 RAW_READS/ERR011347_1.fastq -2 RAW_READS/ERR011347_2.fastq -t 24 -o READ_QC/ERR011347
metawrap read_qc -1 RAW_READS/ERR011348_1.fastq -2 RAW_READS/ERR011348_2.fastq -t 24 -o READ_QC/ERR011348
metawrap read_qc -1 RAW_READS/ERR011349_1.fastq -2 RAW_READS/ERR011349_2.fastq -t 24 -o READ_QC/ERR011349

find ~/READ_QC/ERR011347 -type f \( -name "*post-report*" -o -name "*pre-report*" \) -exec mv {} ~/resultados_tutorial/resultados_read_qc/ERR011347 \;
find ~/READ_QC/ERR011348 -type f \( -name "*post-report*" -o -name "*pre-report*" \) -exec mv {} ~/resultados_tutorial/resultados_read_qc/ERR011348 \;
find ~/READ_QC/ERR011349 -type f \( -name "*post-report*" -o -name "*pre-report*" \) -exec mv {} ~/resultados_tutorial/resultados_read_qc/ERR011349 \;

# Módulo de ASSEMBLY
# Parte inicial precisa ser revisada
cat CLEAN_READS/ERR*_1.fastq > CLEAN_READS/ALL_READS_1.fastq
cat CLEAN_READS/ERR*_2.fastq > CLEAN_READS/ALL_READS_2.fastq

metawrap assembly -1 CLEAN_READS/ALL_READS_1.fastq -2 CLEAN_READS/ALL_READS_2.fastq -m 200 -t 24 -o ASSEMBLY

find ~/ASSEMBLY -type f \( -name "*assembly_report*" -o -name "*final_assembly*" \) -exec mv {} ~/resultados_tutorial/resultados_assembly \;

# Módulo de BINNING
metawrap binning -o INITIAL_BINNING -t 24 -a ASSEMBLY/final_assembly.fasta --metabat2 --maxbin2 --concoct CLEAN_READS/ERR*fastq

# Módulo de Refinamento dos bins
metawrap bin_refinement -o BIN_REFINEMENT -t 24 -A INITIAL_BINNING/metabat2_bins/ -B INITIAL_BINNING/maxbin2_bins/ -C INITIAL_BINNING/concoct_bins/ -c 50 -x 10
find ~/BIN_REFINEMENT -type f \( -name "*.stats*" -o -name "*.png*" \) -exec mv {} ~/resultados_tutorial/resultados_bin_refinement \;

# Módulo BLOBOLOGY
metawrap blobology -a ASSEMBLY/final_assembly.fasta -t 24 -o BLOBOLOGY --bins BIN_REFINEMENT/metawrap_50_10_bins CLEAN_READS/ERR*fastq
find ~/BLOBOLOGY -type f \( -name "*.png*" \) -exec mv {} ~/resultados_tutorial/resultados_blobology \;

# Módulo QUANT BINS
metawrap quant_bins -b BIN_REFINEMENT/metawrap_50_10_bins -o QUANT_BINS -a ASSEMBLY/final_assembly.fasta CLEAN_READS/ERR*fastq
find ~/QUANT_BINS -type f \( -name "*.png*" -o -name "*.tab*" \) -exec mv {} ~/resultados_tutorial/resultados_heatmap \;

# Módulo REASSEMBLED BINS
metawrap reassemble_bins -o BIN_REASSEMBLY -1 CLEAN_READS/ALL_READS_1.fastq -2 CLEAN_READS/ALL_READS_2.fastq -t 24 -m 800 -c 50 -x 10 -b BIN_REFINEMENT/metawrap_50_10_bins
find ~/BIN_REASSEMBLY -type f \( -name "*.stats*" -o -name "*.png*" \) -exec mv {} ~/resultados_tutorial/resultados_bin_reassembly \;

# Módulo CLASSIFY BINS
metawrap classify_bins -b BIN_REASSEMBLY/reassembled_bins -o BIN_CLASSIFICATION -t 24
find ~/BIN_CLASSIFICATION -type f \( -name "*.stats*" -o -name "*.tab*" \) -exec mv {} ~/resultados_tutorial/resultados_bin_classification \;
