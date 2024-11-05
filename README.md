# Tutorial-metawrap

Resultados do tutorial:

**READ_QC MODULE**

Neste módulo as reads brutas tiveram os adaptadores do método de sequenciamento pelo TrmGalore, e a contaminação humana foi removida com o bmtagger. O report de qualidade das reads (feito pelo FastQC) segue abaixo:


ERR011347:

    PRE-REPORT:
    
      Foward:
      
      file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011347/pre-QC_report-47/ERR011347_1_fastqc.html
      Reverse:
      file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011347/pre-QC_report-47/ERR011347_2_fastqc.html

    POST-REPORT:

        Foward:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011347/post-QC_report-47/final_pure_reads_1_fastqc.html
        Reverse:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011347/post-QC_report-47/final_pure_reads_2_fastqc.html
        
ERR011348:

     PRE-REPORT:
    
        Foward:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011348/pre-QC_report-48/ERR011348_1_fastqc.html
        Reverse:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011348/pre-QC_report-48/ERR011348_2_fastqc.html

    POST-REPORT:

        Foward:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011348/post-QC_report-48/final_pure_reads_1_fastqc.html
        Reverse:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011348/post-QC_report-48/final_pure_reads_2_fastqc.html

ERR011349:

    PRE-REPORT:

        Foward:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011349/pre-QC_report-49/ERR011349_1_fastqc.html
        Reverse:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011349/pre-QC_report-49/ERR011349_2_fastqc.html

    POST-REPORT:

        Foward:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011349/post-QC_report-49/final_pure_reads_1_fastqc.html
        Reverse:
        file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/READ_QC/ERR011349/post-QC_report-49/final_pure_reads_2_fastqc.html

**ASSEMBLY_MODULE**

O assembly das reads em contigs foi feito com o programa MegaHit. O report do módulo está no link:

    file:///C:/Users/Asus/Tutorial%20metaWRAP/Tentativa%20definitiva/ASSEMBLY/assembly_report.html

**INITIAL_BINNING_MODULE + BIN_REFINEMENT_MODULE**

Durante o binning inicial utilizamos as ferramentas concoct, maxbin2 e metabat2. Estes resultados foram refinados pelo módulo BIN_REFINEMENT, que escolhe a melhor combinação dos bins a ser utilizada. Ao final identificamos 10 bins dentro dos padrões (completude > 50% / contaminação < 10%).

| bin    | completeness | contamination | GC    | lineage        | N50   | size    | binner |
|:------:|:------------:|:-------------:|:-----:|:--------------:|:-----:|:-------:|:------:|
| bin.9  | 98.92        | 0.866         | 0.404 | Clostridiales  | 13250 | 2199852 | binsBC |
| bin.4  | 94.53        | 1.150         | 0.313 | Euryarchaeota  | 4882  | 1490350 | binsC  |
| bin.3  | 85.57        | 0.223         | 0.370 | Clostridiales  | 5890  | 2037832 | binsA  |
| bin.6  | 75.54        | 1.409         | 0.472 | Bacteroidales  | 5116  | 3134665 | binsA  |
| bin.2  | 74.07        | 0.396         | 0.284 | Clostridiales  | 15994 | 1262130 | binsA  |
| bin.5  | 68.49        | 2.684         | 0.444 | Clostridiales  | 2012  | 1162754 | binsBC |
| bin.7  | 59.39        | 2.430         | 0.513 | Clostridiales  | 2029  | 1230066 | binsBC |
| bin.8  | 55.27        | 8.821         | 0.266 | Clostridiales  | 1938  | 1685647 | binsBC |
| bin.10 | 55.12        | 2.588         | 0.422 | Selenomonadales| 1763  | 1055903 | binsC  |
| bin.1  | 53.60        | 6.165         | 0.304 | Bacteria       | 1961  | 934099  | binsBC |

Abaixo temos um gráfico que demonstra comparativamente a qualidade das bins individuais produzidas pelas três ferramentas (concoct, maxbin2 e metabat2) e pelo metawrap:

![binning_results](https://github.com/user-attachments/assets/035d2932-acbe-4069-9888-424b01f01d2e)

**BLOBOLOGY_MODULE**

Neste módulo o metawrap utiliza a ferramenta MEGABLAST para fazer a identificação taxonômica dos contigs de cada amostra. Em paralelo o módulo também usa o bowtie2, que é um programa de alinhamento gênico, que utiliza as reads limpas obtidas no módulo READ_QC. Com ambos os programas e com a base de dados do NCBI, o Metawrap gerou os seguintes resultados:

![final_assembly blobplot taxlevel_superkingdom](https://github.com/user-attachments/assets/ee6a1841-3e3d-473a-98dd-df155a524763)

![final_assembly blobplot taxlevel_phylum](https://github.com/user-attachments/assets/678cda5f-3409-4586-869d-25920e64bdea)

![final_assembly blobplot taxlevel_order](https://github.com/user-attachments/assets/5d2ada48-a722-4793-8d63-eda65f7cd96a)


Utilizando os bins refinados obtidos no módulo BIN_REFINEMENT, os resultados foram:


![final_assembly blobplot binned_yes_no](https://github.com/user-attachments/assets/6d69cf78-7136-4847-934c-b07e042b9547)

![final_assembly blobplot binned_phylum](https://github.com/user-attachments/assets/7b8f424b-36eb-4bf6-9dd4-151d6589e285)

![final_assembly blobplot bin](https://github.com/user-attachments/assets/7c63f483-3395-4701-89fc-51102c9c1550)

**QUANT_BINS_MODULE**

Este módulo utiliza a ferramenta Salmon para criar um heatmap indicando a abundância dos bins em cada amostra. Esta é uma análise importante porque indica quais bins estão mais ou menos frequentes.

![bin_abundance_heatmap](https://github.com/user-attachments/assets/033ac222-716d-4135-a11a-2845db5cd7f8)

Os dados brutos do heatmap são:

| Genomic bins | ERR011349     | ERR011348     | ERR011347     |
|:------------:|:--------------:|:--------------:|:-------------:|
| bin.9       | 0.091679       | 98.577935      | 108.50986      |
| bin.10      | 0.0            | 42.01186       | 40.352775      |
| bin.1       | 6.34819        | 17.996391      | 35.168827      |
| bin.4       | 2.716425       | 23.549049      | 43.3558        |
| bin.2       | 417.129769     | 0.055903       | 0.116925       |
| bin.5       | 124.577122     | 41.4627735     | 22.49089       |
| bin.6       | 54.713377      | 72.460078      | 78.118091      |
| bin.7       | 0.0            | 66.828652      | 76.064576      |
| bin.8       | 0.67023        | 12.080309      | 38.160772      |
| bin.3       | 614.541562     | 0.055526       | 0.284666       |

**REASSEMBLED_BINS_MODULE**

Este módulo procura remontar os bins gerados no módulo BIN_REFINEMENT, remontando bins melhores por meio do SPAdes. Inicialmente este módulo separa os bins em grupos distintos de acordo com o número de incompatibilidades presentes nas leituras. A ferramenta SPAdes cria novos bins que são avaliados quanto a completude e contaminação pelo CheckM. 

Os valores brutos são:

| bin                  | completeness | contamination | GC    | lineage        | N50   | size    |
|:--------------------:|:------------:|:-------------:|:-----:|:--------------:|:-----:|:-------:|
| bin.1.permissive     | 51.90        | 2.823         | 0.304 | Bacteria       | 2349  | 956985  |
| bin.10.permissive    | 56.69        | 0.718         | 0.422 | Selenomonadales| 2355  | 1103724 |
| bin.2.strict         | 74.07        | 0.335         | 0.284 | Clostridiales  | 26474 | 1262290 |
| bin.3.permissive     | 87.41        | 0.0           | 0.370 | Clostridiales  | 8165  | 2048704 |
| bin.4.orig           | 94.53        | 1.150         | 0.313 | Euryarchaeota  | 4882  | 1490350 |
| bin.5.strict         | 67.82        | 1.342         | 0.444 | Clostridiales  | 2651  | 1191457 |
| bin.6.strict         | 80.94        | 1.595         | 0.471 | Bacteroidales  | 9825  | 3235994 |
| bin.7.strict         | 61.17        | 1.403         | 0.513 | Clostridiales  | 2645  | 1268363 |
| bin.8.permissive     | 56.88        | 8.238         | 0.266 | Clostridiales  | 2430  | 1720765 |
| bin.9.orig           | 98.92        | 0.866         | 0.404 | Clostridiales  | 13250 | 2199852 |

A comparação entre os bins do módulo BIN_REFINEMENT e os remontados está representada nos gráficos de qualidade, contaminação e N50:

![reassembly_results](https://github.com/user-attachments/assets/f248e07b-648b-4fe7-8fd7-1ade7769b1a4)

O gráfico final feito pelo CheckM segue abaixo:

![reassembled_bins](https://github.com/user-attachments/assets/b27f53af-42c5-4a91-bfd9-a1b199a1b28d)


