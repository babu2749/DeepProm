============================================================================================================================
## DeepProm: a deep learning approach for the identification of bacterial promoters and their sub-types based on sigma factors
============================================================================================================================

------------------------------------------------------------------------------------------------------
## Authors: Priyadarshini Panemangalore Pai, Jin Hwan Park, Taeyong Kim*, Rajasekhara Reddy Duvvuru Muni*
## Contact: raja.duvvuru@samsung.com; ty76.kim@samsung.com
------------------------------------------------------------------------------------------------------

## DeepProm Version 1.1

 [![Latest Github release](https://github.com/priyadarshinipai/DeepProm)]

## Dependencies
DeepProm was created in a conda environment. To install:

	#### Anaconda3
	For Linux, you can install Anaconda3 from:
	https://docs.anaconda.com/anaconda/install/linux/
	Once the Anaconda3 is installed properly, you can create an environment for DeepProm.
	For Linux, you can do so using the following commands from the terminal:
	```
	conda create -n <name of the environment>
	source activate <name of the environment>
	```
	#### Other packages 
	In the above conda environment, install the following packages.
	1) python 3.6.7
	2) keras 2.2.4
	3) scikit-learn 0.20.2 
	4) pandas 0.23.4 
	5) theano 1.0.3
	6) h5py 2.8.0
	7) numpy 1.15.4
	
	For Linux, from the terminal:
	```
	conda install <package=version>
	```
## Download
```
DeepProm.tar.gz
```
Above file (around 23 MB) should be downloaded from:

github link <https://github.com/priyadarshinipai/DeepProm>

## Installation

Extract the files using:
```
tar -xvcf DeepProm.tar.gz
```

## Usage:

Input (sequence): Place your query sequence in the file named Candidate_promoters.txt
		format(line1: >name of the promoter with no commas; line2: sequence of 81 nucleotides)
----------------------------------------------------------------------------------------------
## Make sure that your query sequence length = 81 nucleotides and it has 'A','T','G','C' only
----------------------------------------------------------------------------------------------
For numerical encoding of input, run from terminal:
```
 $ python Encode.py
```
For promoter identification, run from terminal:
```
$ python DeepProm1.py
```
Relevant output file: Tier1_prediction.txt

For promoter subtype prediction, run from terminal:
```
$ python DeepProm2.py
```
Relevant output file: Tier2_prediction.txt
	
------------------------------------------------------------------------------------
## If you wish to do a large-scale analysis of all putative promoters in the genome:
------------------------------------------------------------------------------------
Place GenBank file in the folder, check for presence of 'FEATURES' with details
of gene positions and presence of a fasta sequence at the end. Also remove any plasmid data in the file.
For extracting gene positions, run from terminal:
```
$ python Sequence_GenePositions.py <input genome filename>
```
Prepare your input genome filename and contents as per example file provided in the Sample_files folder.
Check relevant '_GenePositions.txt' file for gene positions and orientations. For obtaining genome summary
statistics, run from terminal:
```
$ python Genome_Summary.py <relevant '_GenePositions.txt'>
```
Check relevant '_summary.txt' for genome related statistics. For extracting candidate promoter sequences,
run from terminal:
```
$ python 'Extract_Cpromoters.py' <genome sequence file '.fa'> <genome name> <strain name> <relevant '_GenePositions.txt'> 
```
Check relevant '_Candidate_promoters.txt' file for candidate promoters. For numerical encoding of the candidate
promoters, run from terminal:
```
$ python 'Encode_genome.py'
```
For obtaining promoter predictions, run from terminal:
```
$ python DeepProm1_genome.py' <genome name>
```
Relevant output file: Tier1_prediction_<genomename>.txt
For filtering out sequences predicted as non-promoters, run from terminal:
```
$ python filter_Tier1predictions_genome.py
```
For performing promoter subtype predictions, run from terminal:
```
$ python DeepProm2_genome.py <genome name> 
```	
Relevant output file: Tier2_prediction_<genomename>.txt
```
=======================================================================================================================================
## License
This program is available under the terms of the GNU General Public License as published by the Free Software Foundation. 
You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

========================================================================================================================================
