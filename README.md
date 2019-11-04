# sample_script

This is a short sample script.

It is provided with two input files.
The first file is a tab-delimited file of small RNA which had their first 11 sequences mapped to the cleaved ends of a degradome.
The second file is a fasta file generated from mapping the degradome sequences to the genome and taking the sequences 20bp above
and 20bp below the cleaved end of the degradome. From this mapping data fasta sequences were generated using bedtools.

This script confirms the interaction of precursors and targets by mapping the small RNA to the genomic precursor of the degradome sequence. This is done using patman, a short read alignment program.
This script uses File::Temp to create temporary pattern and database files to be mapped using patman.
Output is stored in a third temporary file which is then checked to ensure that the small RNA extends across the cleavage site.

This program was originally written to map very large input files. It avoids the necessity to map all sequences against each other, in addition to this the use of temporary files enables alignments to be analysed before being written into the final output. This reduces later filtering steps. To speed up the processing of this program it can be run in parallel.

To run this script the program patman and the cpan module File::Temp are required. These have been provided along with some sample input files, these are not my work. For further information regarding these programs please refer to their websites https://bioinf.eva.mpg.de/patman/patman-1.2.html and https://perldoc.perl.org/File/Temp.html#COPYRIGHT-AND-LICENSE

To run this script:
perl confirm_sRNA_cleavage.pl sRNA_degradome.txt genome_transcripts_cleaved.fa output.txt
