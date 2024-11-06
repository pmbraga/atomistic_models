# 1. Force field molecular dynamics simulations 

We start by running the simulation on the cerberus machine: I will use cerberus 1.

## Notes 

### We run the simulation with the commands on the guide;

### Defining the time-step for our simulation is important: we want to find a time step that is smaller than the time required for the fastest dynamics of our system. Since we are dealing with a rigid water molecule, we do not need to concer ourselves with stretching or bending, only vibrations.

![Alt text](/Users/pedrobraga/Documents/Cambridge/atomistic_models/practical_two/force_fields_data_analysis/waterVib1.png)

From this we work out the frequency of the "antisymmetric stretch" which is the lowest energy state from the wavenumber $2756 cm^{-1}$.

$\nu = c\tilde{\nu} = 3\times 10^{10} \times2756 = 8.268\times 10^{13}$

Now we conver this for the time it takes for one vibration

$ t = \frac{\Delta t}{\nu} = \frac{1s}{8.268\times10^{13}'} = 1.21\times10^{-14}s \approx 12 fs $

Since the time required for one vibration is $12 fs$, we want a time step that can distinguish those. We can choose a round, one order of magnitude smaller, number for this, lets use $1$

The code used to replace the XXXXX on the initial parameter files is `sed -i 's/XXXXX/1/g' cp2k.int`

### Now I'll download the results (coordinates and results table) in order to run VMD locally and do the data analysis in this directory. Thus is the commands I used for energy and trajectory:

`scp pm836@cerberus1.lsc.phy.private.cam.ac.uk:/data/cerberus1/pm836/mphil-amm-practical2/01-FF-Water/H2O-64-FF-1.ener /Users/pedrobraga/Documents/Cambridge/atomistic_models/practical_two/force_fields_data_analysis`

`scp pm836@cerberus1.lsc.phy.private.cam.ac.uk:/data/cerberus1/pm836/mphil-amm-practical2/01-FF-Water/H2O-64-FF-pos-1.xyz /Users/pedrobraga/Documents/Cambridge/atomistic_models/practical_two/force_fields_data_analysis`

### Observing the dynamics on VMD using: `vmd -e view-nice.tcl -args 1000 9000 10 H2O-64-FF-pos-1.xyz`: 

It did not quite work. I instead just downlaoded VDM went to: File -> New Molecule -> Load the .xyz file -> Observe the dynamics

### Data analysis 2. Check convergence and stability - jupyter notebook 


