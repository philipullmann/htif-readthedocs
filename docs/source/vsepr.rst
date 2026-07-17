VSEPR Model
-----------------

The VSEPR model is used to estimate the positions of the electron pairs around an atom.
As the interactions (Hydrogen bonds, Salt bridges and Halogen bonds) depends on the geometry of the acceptor
the calculation of the VSEPR geometry and the determiantion of electron pair position is explained below.

The algorithm used to calculate the VSEPR geometry is based on the following criteria:

1. The acceptor atom is identified and the number of bonded atoms to it
2. The  Number of valence electrons, formal charge and the number of electrons participating in bonds are calculated 
3. If there are more electrons participating in bonds than the explicit number of valence electrons the atom is marked as undervalent
4. The number of lone pairs is calculated (valence electrons - formal charge - electrons in bonds) // 2
5. The steric number is calculated (number number of lone pairs + number of bonded pairs)
6. From the steric number the VSEPR geometry is determined and the positions of the electron pairs are calculated.

After the first section the acceptor therefore is now defined by: Steric number, VSEPR geometry, bond pairs, lone pairs and possible undervalent state.


In the next step the geometry of the plane is calculated. If the electron pairs are in a plane with the acceptor and the neighboring atoms (Phi), if they are out of plane (phi-ortho) or if they
are linear (Linear) to the connection between acceptor - neighboring atom.

1. According to steric number and lone pairs the plane geometry is determined. 
2. If steric number is greated than 5 the atom is in a hypervalent state and skiped as no (biological relevanet) lone pair can exist.
3. A number of corrections are applied mostly to mesomeric systems (e.g. the nitrogen of amides are removed from acceptor list)

Possible plane geometries (Steric number, Lone pairs) are:

- (2, 1): Linear (e.g. AX1E1 - C#N)
- (3, 1): Phi (e.g. AX2E1 - CNC (RING))
- (3, 2): Phi (e.g. AX1E2 - C=O)
- (4, 1): Phi-ortho (e.g. AX3E1 - NH3)
- (4, 2): Phi-ortho (e.g. AX2E2 - COC)
- (4, 3): Linear (e.g. AX1E3) - C[O-])