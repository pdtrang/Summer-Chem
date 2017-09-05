# Model generator
## Interaction filter strip.py

Input: sif file, format-specific list of amino acid residues (comma separated, no
space)

Output: csv file or txt file which contains models generated from all possible
combinations of interactions

sif_file: list of all possible interactions

list_of_aa_residues: the format-specific list of aa residues that is used as the basis for the interactions and filtered list of interactions. Comma separated.

Example:
```
./strip.py pdb1pwc_h.sif A:400: :PNM
or
./strip.py pdb1pwc_h.sif A:400: :PNM,A:62: :SER,A:298: :HIS
```
Output can be csv file or txt file. The only difference between these two output file formats is that CSV is easier to read by human, but it will be more difficult for the computer program to read as an input.

## Models analysis analyze models.py

This script takes output txt file from strip.py as input. It cannot take csv file. This script analyzes all output models from strip.py

Input: output txt file from strip.py

Output: Output includes figures and files:

• Figures:

– all sets.png: Count for number of models by number of interactions.

– neighbor.png: Residue frequency in all models.

– residue in unique sets.png: Residue frequency in unique models.

– residue in unique sets sorted.png: Residue frequency in unique models, sorted in descending order of frequency.

– unique sets freq.png: Frequency of unique models.

• Files:

– id list.csv: list of all residue IDs and names.

– edges by unique sets.txt: groups of interactions by each unique models.

– unique sets freq.txt: frequency of unique models, ordered by frequency.

Example:
```
./analyze models.py pdb1pwc_h-400 py.txt
```

## PDB generator from unique models PDBgenerator.py

This script takes unique sets freq.txt file from analyze models.py as an input and generates PDB files using unique models.

Input: output unique sets freq.txt file file from strip.py, PDB file to trim

Output: PDB files
Example:
```
./PDBgenerator.py unique_sets_freq.txt 1pwc.pdb
```

## PDB generator from SIF and residue list makePDBfromUniqueModel.py

This script automatically run all steps from previous sections.

Input: sif file, format-specific list of amino acid residues, PDB file

Output: csv file or txt file which contains models generated from all possible
combinations of interactions
Example:
```
./makePDBfromUniqueModel.py pdb1pwc_h.sif A:400:_:PNM 1pwc.pdb
or
./makePDBfromUniqueModel.py pdb1pwc_h.sif A:400:_:PNM,A:62:_:SER,A:298:_:HIS 1pwc.pdb
```
