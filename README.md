# GPCR-Bench
GPCR-Bench provides a high quality GPCR docking benchmarking set: 25 PDB structures covering all NR structures as of January 2015, and active and decoy compounds in the spirit of DUD.

# How to use
Download files for your GPCR target of choice, or download all to run a comparison of methods for all 25 GPCR targets.

# File descriptions
 - Receptor_chembl19_set.sdf.bz2
 
3D coordinates for all the molecules in the benchmarking set (~200 actives and ~10000 decoys). Ligands were prepared with the software MoKa and CORINA. The tautomeric states with a minimum abundance threshold of 20% were generated with TAUTHOR and the ionic states with a minimum abundance threshold of 10% at pH 7.4 with BLABBER. All low energy 3D conformations were created with CORINA including up-to 10 ring conformations per molecule in an energy window of ~2 kcal/mol. 

 - Receptor_chembl19_set.smi
 
Smiles strings of all the molecules in the benchmarking set (~200 actives and ~10000 decoys).

 - Receptor_diverse_actives.id
 
ID names of all the actives in the set.

 - Receptor_dude_decoys.id
 
ID names of all the decoys in the set.

 - Receptor.pdb
 
Clean PDB file of the high resolution crystal structure containing only the protein coordinates.

 - Receptor.mol2
 
MOL2 structure file of the co-crystal ligand with hydrogens included

 - Receptor.zip
 
MAESTRO grid zip file for GLIDE (Schrodinger) docking

 - Receptor.fxx
 
HYDE (Biosolveit) receptor file



# Ligand Retrieval from ChEMBL19. 
Ligands were extracted for each target from the ChEMBL19 database, using an automated script based on the ChEMBL Web Service API. Only compounds with bioactivity_type corresponding to Ki, Kd, IC50 or EC50 and with a value less than or equal to 10000 were stored. Compounds with assay_description matching PUBCHEM_BIOASSAY or DRUGMATRIX were not included as these data sources led to many false positives in the set. Compounds were then filtered for 'drug-likeness', which included the following terms: Sulfur Count <=2; Chlorine Count <=3 ; Bromine Count <=1 ; Iodine Count <=1; Fluorine Count <=6; 250 <= Molecular Weight <= 500 ; 0 <= H-Donors <= 4 ; 1 <= H-Acceptors <= 8; 0 <= Rotatable Bonds  <=7; Rings <= 5; # of Atoms >= 12. Targets for which there were still over 1000 ligands were further filtered to include only Ki values, and only ligands with Ki <= 100nM; Targets with over 400 ligands included Ki, Kd, IC50 or EC50 with value <= 100nM; all other targets had less than 400 ligands and included Ki, Kd, IC50 or EC50 with value <= 10000nM. Finally, for all targets with more than 200 ligands, 200 maximally diverse ligands were chosen using the 'Diverse Molecules' component in PipelinePilot9.1 based on ECFP4 fingerprints. To each set we also added all the co-crystal ligands available in the PDB, which is important for cross docking experiments.

# Decoy generation. 
http://dude.docking.org/

Mysinger MM, Carchia M, Irwin JJ, Shoichet BK J. Med. Chem., 2012, Directory of Useful Decoys, Enhanced (DUD-E): Better Ligands and Decoys for Better Benchmarking
