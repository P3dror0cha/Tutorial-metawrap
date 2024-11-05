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

![binning_results](https://github.com/user-attachments/assets/035d2932-acbe-4069-9888-424b01f01d2e)

