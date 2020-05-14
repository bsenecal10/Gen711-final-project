Brennan Senecal May 13, 2020
Gen711 Final Project
Information regarding data accessed, code, BLAST, MAFFT, and where to visualize results

Downloaded platypus transcriptome from desktop (originally ensemble): 
rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Ornithorhynchus_anatinus.mOrnAna1.p.v1.cdna.abinitio.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Ornithorhynchus_anatinus.mOrnAna1.p.v1.cdna.all.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

Created new file for platypus transcriptome: 
cat Ornithorhynchus_anatinus.mOrnAna1.p.v1.cdna.abinitio.fa Ornithorhynchus_anatinus.mOrnAna1.p.v1.cdna.all.fa > Platypus_transcript

Downloaded platypus venom genes from desktop (originally ensemble): 
rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Ornithorhynchus_anatinus_ENSOANG00000028825_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Ornithorhynchus_anatinus_ENSOANG00000008025_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Ornithorhynchus_anatinus_ENSOANG00000040509_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

Changed file names for platypus venom genes: 
cat Ornithorhynchus_anatinus_ENSOANG00000028825_sequence.fa > Platypus_venom_1
cat Ornithorhynchus_anatinus_ENSOANG00000008025_sequence.fa > Platypus_venom_2
cat Ornithorhynchus_anatinus_ ENSOANG00000040509_sequence.fa > Platypus_venom_3.1

Installed BLAST: 
sudo apt install ncbi-blast+

Created BLAST database with platypus venom genes:
makeblastdb -in Platypus_venom_genes_2 -out Venom_blastdb_2 -dbtype nucl

BLASTed query against database:
blastn -db Venom_blastdb_2 -max_target_seqs 1 -query Platypus_transcript -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out platypus_blast_2.out

Moved sequences and headers to new files according to BLAST sequence matches:

grep -A 31 "GENSCAN00000007782" Platypus_transcript > MSA_1
grep -A 26 "GENSCAN00000028920" Platypus_transcript > MSA_2
grep -A 14 "GENSCAN00000030991" Platypus_transcript > MSA_3
grep -A 15 "GENSCAN00000031000" Platypus_transcript >> MSA_3
grep -A 49 "ENSOANT00000071281.1" Platypus_transcript >> MSA_3
grep -A 91 "ENSOANT00000062509.1" Platypus_transcript >> MSA_3
grep -A 90 "ENSOANT00000053021.1" Platypus_transcript >> MSA_3
grep -A 26 "ENSOANT00000056963.1" Platypus_transcript >> MSA_3
grep -A 22 "ENSOANT00000048653.1" Platypus_transcript >> MSA_3
grep -A 32 "ENSOANT00000066037.1" Platypus_transcript >> MSA_3
grep -A 44 "ENSOANT00000007664.2" Platypus_transcript >> MSA_3
grep -A 89 "ENSOANT00000060584.1" Platypus_transcript >> MSA_3
grep -A 57 "ENSOANT00000001929.3" Platypus_transcript >> MSA_3
grep -A 53 "ENSOANT00000051003.1" Platypus_transcript >> MSA_3
grep -A 100 "ENSOANT00000064417.1" Platypus_transcript >> MSA_3
grep -A 18 "ENSOANT00000066375.1" Platypus_transcript >> MSA_3
grep -A 45 "ENSOANT00000054129.1" Platypus_transcript >> MSA_3
grep -A 39 "ENSOANT00000006282.2" Platypus_transcript >> MSA_3
grep -A 49 "ENSOANT00000075527.1" Platypus_transcript >> MSA_3
grep -A 65 "ENSOANT00000057587.1" Platypus_transcript >> MSA_3
grep -A 51 "ENSOANT00000076532.1" Platypus_transcript >> MSA_3
grep -A 40 "ENSOANT00000040822.2" Platypus_transcript >> MSA_1
grep -A 45 "ENSOANT00000020910.3" Platypus_transcript >> MSA_3
grep -A 26 "ENSOANT00000012764.3" Platypus_transcript >> MSA_2
grep -A 42 "ENSOANT00000009920.3" Platypus_transcript >> MSA_3

Downloaded reptile sequences for MSA from desktop (originally ensemble):
1.
rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Varanus_komodoensis_ENSVKKG00000007127_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Salvator_merianae_ENSSMRG00000021013_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

2.
rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Pseudonaja_textilis_ENSPTXG00000009160_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Notechis_scutatus_ENSNSUG00000008553_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

3.
rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Salvator_merianae_ENSSMRG00000015056_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

rsync -av -e "ssh -i $HOME/jetkey" /Users/brennans/Desktop/Podarcis_muralis_ENSPMRG00000000431_sequence.fa bsenecal@129.114.17.160:/home/bsenecal/Gen711-final-project/Blast_files

Moved reptile venom sequences into the correct MSA files (2 per sequence):
cat Argentine_black_and_white_tegu_1 Komodo_dragon_venom_1 >> MSA_1
cat Mainland_tiger_snake_2 Eastern_brown_snake_venom_2 >> MSA_2
cat Argentine_black_and_white_tegu_venom_3 Common_wall_lizard_venom_3 >> MSA_3

Installed MAFFT:
sudo apt install mafft

Used MAFFT for MSA:
mafft --reorder --localpair --thread 6 MSA_1 > MSA_1.aln
mafft --reorder --localpair --thread 6 MSA_2 > MSA_2.aln
mafft --reorder --localpair --thread 6 MSA_3 > MSA_3.aln

Viewed MSA results with EMBL-EBI tool:
copied entire MSA_#.aln files and pasted into https://www.ebi.ac.uk/Tools/msa/mview/
MSA_1.aln: https://www.ebi.ac.uk/Tools/services/web/toolresult.ebi?jobId=mview-I20200513-214641-0145-12230186-p1m
MSA_2.aln: https://www.ebi.ac.uk/Tools/services/web/toolresult.ebi?jobId=mview-I20200513-215017-0590-50803165-p1m
MSA_3.aln: https://www.ebi.ac.uk/Tools/services/web/toolresult.ebi?jobId=mview-I20200513-215410-0910-66534756-p1m

