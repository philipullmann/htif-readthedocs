FAQ
========



| Q: Are other formats supported for the ligand except of mol2 and sdf?
| A: Currently not. It is important for HTIF to have the correct connectivity of the ligand. Therefore pdb/pdbqt is not supported. You can use OpenBabel to convert your ligand into sdf or mol2 format.

| Q: Are other formats supported for the receptor except of pdb (like mmCIF)?
| A: Currently not.

| Q: Can I filter interactions for pdbs at once (e.g. different receptor mutations or trajectories)?
| A: No, currently HTIF can only filter interactions for one pdb input at a time.

| Q: Can I use Nucleic acids or peptides as ligands?
| A: Yes, HTIF can be used to filter interactions of nucleic acids and peptides as long as they are in the formats accepted by HTIF.

| Q: How does HTIF deal with non-standard amino acids?
| A: Non-standard amino acids are detected by HTIF but can cause problems as their connectivity is unkown. For example the backbone carbonyl can be interpreted as a hydroxy group. We recommend to transfer it into a standard amino acid.

| Q: Can HTIF filter for interactions with water molecules?
| A: Yes, Water molecules can be used for filtering.

| Q: Why can I not use AND and OR logic in the same matrix?
| A: The current implementation of HTIF make it complex to use both logics at one point. We recommend to run HTIF multiple times with different matrices and combine the results afterwards.

| Q: I suspect an interaction was present but not detected by HTIF. What can I do?
| A: Before reporting a bug, please relax your filtering criteria. For example increase the tolerance angle and distance and look if the interaction is detected.
