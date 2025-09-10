# Design-and-Acoustic-Performance-Research-of-Underwater-Acoustic-Absorption-Metamaterials
This repository contains detailed information to reproduce the finite element simulations presented in the manuscript.

COMSOL Multiphysics Version
Version: 6.1

Required Modules: Acoustics Module, Structural Mechanics Module, MEMS Module (for Thermoviscous Acoustics interface)

Model Architecture & Physics Interfaces
Pressure Acoustics, Frequency Domain (acpr):

Used to model the propagation of sound waves in the water domain and the internal air cavities.

Solid Mechanics (solid):

Used to model the structural response of the elastic diaphragm and other solid components.

Thermoviscous Acoustics, Frequency Domain (tva):

Used to model the acoustic fields inside small slits and cavities where viscous and thermal losses are significant. This interface was applied to the air regions inside the metamaterial unit cell.

Acoustic-Structure Boundary (acst):

Multiphysics coupling node used to define the interaction between the acoustic domains (water/air) and the solid diaphragm.

Key Model Settings
Study Type: Frequency Domain.

Frequency Range: 200 Hz to 5000 Hz.

Frequency Step: 10 Hz.

Solver: Direct solver (MUMPS) was used for all frequency domain calculations.

Geometry & Mesh
The 2D axisymmetric or 2D geometry was built according to the dimensions specified in Table 1 and Section 2.1 of the manuscript.

Mesh: Physics-controlled mesh was used with an element size set to "Extremely Fine". Manual mesh sizing was applied to ensure sufficient resolution within the thin diaphragm and narrow slits, guaranteeing at least 6 elements per wavelength at the highest frequency of interest.

Boundary Conditions
Incident Boundary: Plane Wave Radiation condition.

Exit Boundary: Perfectly Matched Layer (PML) to absorb outgoing waves without reflections.

Side Boundaries: Hard Sound Field (acoustically rigid walls).

Diaphragm Boundaries: Fixed Constraints on the edges, with a Boundary Load applied to simulate the pre-tension (T).

Interior Boundaries: Acoustic-Structure Boundary multiphysics coupling was applied on the fluid-solid interfaces.

Material Properties
Material properties for all components are listed in the table below. Properties were primarily defined based on values from the COMSOL Built-in Material Library and standard literature values.

Component	Material	Density (kg/m³)	Speed of Sound (m/s)	Young's Modulus (Pa)	Source
Panel Layer	Polyurethane Film	1200	1800	5.0e6	Built-in Library: Polyurethane (elastic)
Damping Layer	Silicone Composite	1100	1400	1.0e6	Built-in Library: Silicone rubber
Substrate Layer	Fiberglass (FRP)	1900	2500	3.5e9	Built-in Library: G10 FR4
Backing Plate	Aluminum Alloy	2700	5000	7.0e10	Built-in Library: Aluminum alloy
Fluid Domain	Water	1000	1500	-	Built-in Library: Water, liquid
Cavity Fluid	Air	1.2	343	-	Built-in Library: Air
How to Reproduce
Open COMSOL Multiphysics 6.1 with the required modules.

The model can be rebuilt using the geometry dimensions and parameters provided in the manuscript and this document.

Follow the physics settings, boundary conditions, and mesh configuration described above.

Run the frequency domain study.
