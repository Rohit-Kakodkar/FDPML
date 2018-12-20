# Freqeuncy Domain Perfectly Matched Layer

For technical details on the method please refer :

	kakodkar et. al. Journal of Applied Physics 118, 094301 (2015)

================================================================================================

	Pre-requisites:		Primary domain should be generated using 
						gendomain.f90 provided in this repository

	Force constant file should generated using Quantum Espresso in *.fc format

	
 	FDPML calculates scattering properties for a particular phonon mode 
	(wavevector and polarization resolved) inside nanostructured materials.
	For in-depth discription of the method refer 
	kakodkar et. al. Journal of Applied Physics 118, 094301 (2015)
	
	Input cards :
	
	&filenames
		flfrc1 = force constant file of the matrix material (should be generated via
				 Quantum espresso). NOT IN XML FORMAT
		flfrc2 = force constant file of impurity material (should be generated via
				 Quantum espresso). NOT IN XML FORMAT
		mass_input = logical, if true masses are calculated with atomic resolution
							  else masses are calculated based on supercell
		mass_file = mass domain file generated by gendomain.f90
		domain_file = domain specification generated by gendomain.f90
	
	&system
		simulation_type = 'interface' or 'nanoparticle'
		PD = size of the primary domain, should be same as the one generated
			 gendomain.f90
		LPML = length of PML. Ignored if PML calculation is auto
		periodic = logical, if true applied periodic boundaries in x and y direction
		crystal_coordinates = logical, if true work in crystal coordinates
		asr = acoustic sum rule. Refer QE documentation
		wavetype = 'half' or 'full' to specify type of incidnet wave
		q = wavevector, ignored if mp = .true.
		mode = polarization
		sigmamax = maximum value of damping coefficient, Ignored if PML calculation is auto
		mp = generate qpoint list base Monkhorst Pack(MP) grid
		qpoint = n, then choose nth q from list of q generated by MP grid
		nk1, nk2, nk3 = k-spacings in x,y and z directions for MP grid
	
	&postprocessing
		calc_TC = logical, calculate transmission coefficient (for interface problems)
		calc_gam = logical, calculate scattering cross-section (for nanoparticle problems)
	
	&plotting
		plot_K  = logical, plot variation of K vector on TD(3)/2 plane
		plot_uinc = logical, plot incident wave
		plot_uscat = logical, plot scattered wave
		plot_sig = logical, plot variation of damping coefficient
		plottingmode = 1, 2, or 3, plot x, y, or z components of above properties
