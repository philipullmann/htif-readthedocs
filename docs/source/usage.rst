Usage
#####

Command-line
************************

HTIF expects at least two files as input.
* A file with the 3D structure of the protein in pdb format
* A file with the 3d structures of the Ligands in sdf or mol2 format.  

Introduction Matrix
-----------------

The filtering is defined by the matrix argumment supplied to HTIF. It takes up to 4 internal values.

1. The Logic (Negation or Affirmation) of the filtering. [OPTIONAL]
2. The type of interaction to filter for (Hydrogen bond, Salt brige etc.) [MANDATORY]
3. The amino acid number of the protein. [MANDATORY]
4. The chain of the protein. [OPTIONAL]
5. The substructure or atom to be considered. [OPTIONAL]]


.. code-block:: console

   
   htif -prot rec.pdb -lig ligand.sdf -matrix "H103" -o ligand_filtered.sdf
   htif -prot rec.pdb -lig ligand.sdf -matrix "~H(A)103|BACK|" -o ligand_filtered.sdf

First command represent the minimum requirments for an htif run. In this example Hydrogen bonds to amino acid 103 are filtered.
Second command represents the same filtering but with negation logic, filtering on chain A and using only the backbone atoms.

By default the program will filter as following:

1. Not supplied logic = Affirmation
2. Not supplied chain = All chains
3. Not supplied substructure = All atoms of the amino acid

Chained logic Matrix
-----------------

Multiple amino acids can be used for filtering in two ways.

1. Using the OR logic to indclude the results if one of the amino acid interaction is satisfied. 
2. Using the AND logic to include the results if all of the amino acid interactions are satisfied.


.. code-block:: console

   
   htif -prot rec.pdb -lig ligand.sdf -matrix "H103:H104" -o ligand_filtered.sdf
   htif -prot rec.pdb -lig ligand.sdf -matrix "H103-H104" -o ligand_filtered.sdf

First command represents the OR logic, filtering for Hydrogen bonds if they fullfill one interaction to H103 or H104.
Second command represents the AND logic, filtering for Hydrogen bonds if they fullfill both interactions to H103 and H104.

Substructre definition Matrix
-----------------

Inisde of an amino acid a substructure can be defined to filter for specific atoms. 

.. code-block:: console

   
   htif -prot rec.pdb -lig ligand.sdf -matrix "H103|BACK|" -o ligand_filtered.sdf
   htif -prot rec.pdb -lig ligand.sdf -matrix "H103|SIDE|" -o ligand_filtered.sdf
   htif -prot rec.pdb -lig ligand.sdf -matrix "H103|O1,O2|" -o ligand_filtered.sdf

The first command will filter for Hydrogen bonds to the backbone atoms of amino acid 103.
The second command will filter for Hydrogen bonds to the sidechain atoms of amino acid 103.
The third command will filter for Hydrogen bonds to the atoms O1 and O2 of amino acid 103.


Interaction types and optional arguments:
-----------------

**Hydrogen bonds**

Is invoced with the letter H.

Optional arguments:

* hbond_cutoff_min  = Minimum distance between donor and acceptor atom to be considered a hydrogen bond. Default is 2.5 Angstrom.
* hbond_cutoff_max = Maximum distance between donor and acceptor atom to be considered a hydrogen bond. Default is 3.5 Angstrom.
* angle_tolerance = Tolerance for the angles added on top the standard definitions. Default is 10 degrees.

**Salt briges**

Is invoced with the letter B.

Optional arguments see Hydrogen bonds

**Pi-stacking interactions**

Is invoced with the letter P.

Optional arguments:

* pi_mode = The mode of the pi-stacking detection. Can be either "simple" or "complex". For simple mode the angle between the two rings is checked against a threshold. For complex mode the angle and distance are checked against a pre-calculated QM energy surface for two benzene rings. Default is "complex".
* pi_cutoff = Distance cutoff between the two ring centroids to be considered a pi-stacking interaction. Default is 7.0 Angstrom.
* pi_tolerance = Tolerance of the angle between the two rings. Only used in simple mode. Default is 0.
* pi_energy_cutoff = Energy cutoff for the pre-calculated QM energy surface. If the energy is estimated to be over this value the interaction is rejected. Only used in complex mode. Default is -1.5 kcal/mol.


**Pi-cation interactions**

Is invoced with the letter C.

Optional arguments:

* cat_cutoff_min = Minimum distance between the cation and the ring centroid to be considered a pi-cation interaction. Default is 2.5 Angstrom.
* cat_cutoff_max = Maximum distance between the cation and the ring centroid to be considered a pi-cation interaction. Default is 5.5 Angstrom.
* cat_tolerance = Tolerance for the angles added on top the standard definitions. Default is 10 degrees.


**Halogen bonds**

Is invoced with the letter X.

Optional arguments:

* xbond_cutoff_min = Minimum distance between the halogen and the ring centroid to be considered a halogen bond. Default is 2.0 Angstrom.
* xbond_cutoff_max = Maximum distance between the halogen and the ring centroid to be considered a halogen bond. Default is 3.3 Angstrom.
* xbond_tolerance = Tolerance for the angles added on top the standard definitions. Default is 10 degrees.
* xbond_all = By default Flour will not be considered as a halogen bond donor. If this option is set to True, Flour will be considered as a bond donor. Default is False.


**Ionic Interactions**

Is invoced with the letter I.

Optional arguments:

* ionic_cutoff = Maximum distance between the two ions to be considered an ionic interaction. Default is 6.0 Angstrom.
* ionic_orthogonal_cutoff = Ionic interactions check if a non-hydrogen atom is blocking the direct path. 
This is done by a block cone calculation using this value as the circle radius. 
The higher this value gets the cone is calculated wider. Default is 0.75 Angstrom.
  
**Hydrophobic Interactions**

Is invoced with the letter Y.

Optional arguments:

* hydro_cutoff = Maximum distance between the two hydrophobic atoms to be considered a hydrophobic interaction. Default is 5.9 Angstrom.  
* hydro_orthogonal_cutoof = Hydrophobic interactions check if a non-hydrogen atom is blocking the direct path. See Ionic interaction othogonal cutoff.


Server
************************

To be added ...