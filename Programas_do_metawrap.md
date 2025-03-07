Lista de programas utilizados pelo Metawrap:

**FastQC:** É uma ferramenta que avalia a qualidade de reads. O FastQC funciona pela análise da qualidade individual de cada base da sequência, atribuindo um valor de qualidade Phred para os nucleotídeos. Este programa suporta vários tipos de formatos como fastq, bam, sam, dentre outros. O fastQC é interessante porque faz as seguintes análises: qualidade de cada base em todas as sequências, qualidade das sequências, conteúdo dos nucleotídeos nas sequências, conteúdo de GC, distribuição de GC, distribuição pelo tamanho das reads, quantidade de sequências duplicadas, avaliação de sequências contaminantes ou Kmers (dentre as sequências super-expressas). 

O **FastQC** devolve vários tipos de informações que podem ser vistas no menu:
![image](https://github.com/user-attachments/assets/563d7177-c240-4f98-80ec-7d928a1416e8)



O Basic Statistics retorna algumas infos básicas sobre as suas reads. É interessante observar o Total das Sequencias, %GC, Tamanho Médio e Sequencias de baixa qualidade. Visualmente, isto está apresentado assim:
![image](https://github.com/user-attachments/assets/dbbb19cb-0995-4f58-b03f-441e55e592e1)

![image](https://github.com/user-attachments/assets/ce7f1303-238f-45ca-9c81-bcb1717112d3)

No **Per Base Sequence Quality** temos a representação da qualidade na forma de um boxplot mostrando o erro de todas as bases. 

![g2boxplot](https://github.com/user-attachments/assets/fbac8a59-f828-4b15-9243-fcd1e247d80e)

![image](https://github.com/user-attachments/assets/c41896c9-3077-43ea-b7b8-a586a972b950)

No **Per Sequence Quality** temos a representação da qualidade média das sequencias avaliadas. A variável determinante é o Phred Score que é uma medida de erro. Quanto MAIOR o Phred Score, MENORES são as taxas de erro. A presença de unidades de base com picos ALTOS de % é um indicativo de que a base tem VIÉS. Abaixo temos o exemplo de um grupo de sequencias bons e ruins, respectivamente:

![persequence_good](https://github.com/user-attachments/assets/31a413d9-d4d1-4ef5-b9a9-7c3f91b3aea6)

![image](https://github.com/user-attachments/assets/a65f8ff5-6509-4a19-b7be-9ced5a543574)

No **Per Base Sequence Content** nós observamos a porcentagem de cada nucleotídeo para cada base das reads. Idealmente uma boa imagem seria aquela que apresenta uma linha reta para todos os quatro nucleotídeos, uma vez que a concentração delas deve se manter constante ao longo da read. Exemplos de como essa info é apresentada segue abaixo:

![image](https://github.com/user-attachments/assets/bbafefc6-dd87-4b60-ba29-ab6922816465)

![image](https://github.com/user-attachments/assets/d0dc8df5-424e-496b-a49a-3f33fc0ef760)

No **Per Sequence GC Content** há este tipo de informação:

![image](https://github.com/user-attachments/assets/c63b7211-0109-46c8-9383-92bf3a14d2d4)

No **Sequence Length Distribution** o FastQC mostra o tamanho médio das reads. O ideal é que estejam próximas. Abaixo, há uma imagem de um bom tamanho de read e um ruim, respectivamente:

![image](https://github.com/user-attachments/assets/8ae7b398-7aba-4821-acf3-e7207e7fb2ff)

![image](https://github.com/user-attachments/assets/319e9a17-7daa-4be2-875f-c9c3aff07031)

No **Sequence Duplication Levels** vemos qual a porcentagem da nossa amostra que está repetida e quantas vezes, em média, está repetida. O ideal é vermos algo desta forma:

![image](https://github.com/user-attachments/assets/49ce21c7-c789-4a3c-ad51-1631a26e57d1)

Por fim, no **Overrepresented Sequences** e no **Adapter Content** obtemos mais informações sobre sequencias repetidas presentes na amostra.
Existem outros avaliadores da qualidade de reads, como o DRISEE, que avaliam a qualidade do sequenciamento pela análise de reads duplicadas. Esta abordagem é interessante quando procuramos identificar erros no método de sequênciamento como um todo.

**Trmgalore:** É um wrapper script usado para fazer o trimming de reads, ou seja, para retirar os adaptadores do método de sequenciamento utilizado. Este programa também é utilizado para limpar amostras de Reduced-representation bisulfite sequencing (RRBS-Seq ).

**Bmtagger:** O bmtagger é uma ferramenta usada para a eliminação de contaminantes das reads. Na metagenômica ele é utilizado para limpar a contaminação de genoma humano nas amostras. Este programa indexa os dados no formato blastn ou megablast, alinha as leituras com um genoma de referência (genoma humano) e faz a limpeza das reads contaminadas.

**KRAKEN2:** É um classificador taxonômico que funciona pela análise dos k-mers gerados pelas leituras. Os k-mers são sequências com tamanho fixo geradas a partir de uma sequência inicial. Por isso, dependendo do tamanho da sequência mãe e dos k-mers, uma amostra pode ter vários k-mers diferentes. O kraken2 utiliza a sua base de dados para relacionar os k-mers das amostras com alguma classificação taxonônica.

![image](https://github.com/user-attachments/assets/0a99a17f-c8b0-4621-b7b5-d74729a6a5f0)

**KROna tools:** O Krona é uma ferramenta de visualização interativa que gera imagens, gráficos ou mapas taxônomicos. O Kronatools é o conjunto de scrips que é usado para manipular o Krona. 

**SPAdes:** Montador de genomas que utiliza gráficos de buijin e k-mers para fazer a montagem. Ler o artigo: Bankevich A, et al. SPAdes: a new genome assembly algorithm and its applications to single-cell sequencing. J Comput Biol. 2012 May;19(5):455-77. doi: 10.1089/cmb.2012.0021. Epub 2012 Apr 16. PMID: 22506599; PMCID: PMC3342519.

**MegaHit:** Funciona de forma semelhante ao spades. Ler o artigo do Megahit: https://doi.org/10.1016/j.ymeth.2016.02.020

**QUAST:** É uma ferramenta de avaliação da qualidade de montagens genômicas que pode funcionar ou não com um genoma de referência. Para avaliar a qualidade o QUAST gera resultados como: N50, L50, número de contigs, porcentagem de erro, GC%. O QUAST permite a visualização destes resultados em reports gráficos. Há também o metaQUAST, que é um programa específico para avaliar a qualidade de dados metagenômicos. O artigo do QUAST: https://doi.org/10.1093/bioinformatics/btt086. O artigo do metaQUAST: http://dx.doi.org/10.1093/bioinformatics/btv697.

**bowtie2:** Programa usado para o alinhamento das sequências utilizando um genoma de referência.

**samtools:** É um conjunto de ferramentas amplamente utilizado em bioinformática para manipulação e análise de arquivos de sequenciamento genético no formato SAM (Sequence Alignment/Map) e BAM (Binary Alignment/Map). Com o samtools podemos converter, ordenar, indexar, filtrar, extrair, analisar e concatenar arquivos dos tipos SAM e BAM.

**bwa-index:** O bwa é um alinhador de sequência que utiliza a transformada de Burrows-Wheeler para comprimir e indexar as sequências. Ler artigo: https://doi.org/10.1093/bioinformatics/btp324.

**bwa-mem:** É um mapeador de leituras. Utiliza o output do bwa-index para alinhar as sequências em um genoma de referência.

**metaBAT2:** É uma ferramenta de binning dos contigs. O binning é feito sem uso de um genoma de referência, levando em consideração aabundância de contigs e o perfil de cobertura. O artigo do metaBAT2 é este: https://doi.org/10.7717/peerj.7359.

**maxbin2:** Ferramenta de binning que utiliza um modelo de máxima verossemelhança dos contigs. O artigo é: https://doi.org/10.1093/bioinformatics/btv638.

**CONCOCT:** Ferramenta de binning. https://doi.org/10.1038/nmeth.3103

**CheckM:** Ferramenta que avalia a qualidade dos binning produzidos por amostras de metagenômica. A ferramenta avalia a completude e a contaminação das amostras. https://doi.org/10.1101/gr.186072.114

**Salmon:** Usado para a quantificação dos bins nas amostras. Ferramenta capaz de fazer um heatmap dos bins, permitindo uma análise quantitativa de cada amostra. https://doi.org/10.1038/nmeth.4197

**taxator-tk:** Ferramenta de classificação taxonômica dos bins gerados pela metagenômica. https://doi.org/10.1093/bioinformatics/btu745

**PROKKA:** É usado para a anotação dos contigs, associando-os com proteínas funcionais ou hipotéticas. https://doi.org/10.1093/bioinformatics/btu153
