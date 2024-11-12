Lista de programas utilizados pelo Metawrap:

**FastQC:** É uma ferramenta que avalia a qualidade de reads. o FastQC suporta vários tipos de formatos como fastq, bam, sam, dentre outros.O fastQC é interessante porque faz as seguintes análises: qualidade de cada base em todas as sequências, qualidade das sequências, conteúdo dos nucleotídeos nas sequências, conteúdo de GC, distribuição de GC, distribuição pelo tamanho das reads, quantidade de sequências duplicadas, avaliação de sequências contaminantes ou Kmers (dentre as sequências super-expressas).

**Trmgalore:** É um wrapper script usado para fazer o trimming de reads, ou seja, para retirar os adaptadores do método de sequenciamento utilizado. Este programa também é utilizado para limpar amostras de Reduced-representation bisulfite sequencing (RRBS-Seq ).

**Bmtagger:** O bmtagger é uma ferramenta usada para a eliminação de contaminantes das reads. Na metagenômica ele é utilizado para limpar a contaminação de genoma humano nas amostras. Este programa indexa os dados no formato blastn ou megablast, alinha as leituras com um genoma de referência (genoma humano) e faz a limpeza das reads contaminadas.

**KRAKEN2:** É um classificador taxonômico que funciona pela análise dos k-mers gerados pelas leituras. Os k-mers são sequências com tamanho fixo geradas a partir de uma sequência inicial. Por isso, dependendo do tamanho da sequência mãe e dos k-mers, uma amostra pode ter vários k-mers diferentes. O kraken2 utiliza a sua base de dados para relacionar os k-mers das amostras com alguma classificação taxonônica.

![image](https://github.com/user-attachments/assets/0a99a17f-c8b0-4621-b7b5-d74729a6a5f0)


**KROna tools:** O Krona é uma ferramenta de visualização interativa que gera imagens, gráficos ou mapas taxônomicos. O Kronatools é o conjunto de scrips que é usado para manipular o Krona. 

**SPAdes:** Ler o artigo: Bankevich A, et al. SPAdes: a new genome assembly algorithm and its applications to single-cell sequencing. J Comput Biol. 2012 May;19(5):455-77. doi: 10.1089/cmb.2012.0021. Epub 2012 Apr 16. PMID: 22506599; PMCID: PMC3342519.

MegaHit;

QUAST;

bowtie2;

samtools;

bwa-index;

bwa-mem;

metaBAT2;

maxbin2;

CONCOCT;

CheckM;

Salmon;

taxator-tk;

PROKKA;
