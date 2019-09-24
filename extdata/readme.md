## How to apply RIblast to predict lncRNA target 

1. Install RIblast with git clone command
```
git clone https://github.com/Shicheng-Guo/RIblast.git
cd RIblast
make 
```
2. Prepare database or target base
```
cd extdata
wget http://ftp.ensembl.org/pub/release-97/fasta/homo_sapiens/ncrna/Homo_sapiens.GRCh38.ncrna.fa.gz
wget http://ftp.ensembl.org/pub/release-97/fasta/homo_sapiens/cdna/Homo_sapiens.GRCh38.cdna.all.fa.gz 
gunzip Homo_sapiens.GRCh38.ncrna.fa.gz
gunzip Homo_sapiens.GRCh38.cdna.all.fa.gz 
../RIblast db -i Homo_sapiens.GRCh38.cdna.all.fa  -o Homo_sapiens.GRCh38.cdna.all.fa.db
../RIblast db -i Homo_sapiens.GRCh38.ncrna.fa.gz  -o Homo_sapiens.GRCh38.ncrna.fa.db
```

3. Predict target for ncRNA or mRNA
```
grep AC004585.1 Homo_sapiens.GRCh38.ncrna.fa.txt > AC004585.fa
../RIblast ris -i AC004585.fa -o AC004585.txt -d Homo_sapiens.GRCh38.cdna.all.fa.db

grep AC004585.1 Homo_sapiens.GRCh38.ncrna.fa.txt > AC004585.fa
../RIblast ris -i AC004585.fa -o AC004585.txt -d Homo_sapiens.GRCh38.cdna.all.fa.db
```

