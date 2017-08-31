# Summer-Chem-2017

Interaction filter

strip.py sif_file list_of_aa_residues


sif_file: list of all possible interactions

list_of_aa_residues: the formati-specific list of aa residues that is used as the basis for the interactions and filtered list of interactions. Comma separated.

Example: 

strip.py 1pwc.sif A:400:_:PNM

strip.py 1pwc.sif A:400:_:PNM,A:62:_:SER
