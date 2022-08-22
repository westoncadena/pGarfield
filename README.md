# pGarfield_New
This is the new version of pGarfield that includes the use of the Heed. pGarfield_New is the toolkit that is sourced when using. Examples has gem2B.C along with the other files needed.

## Making the Tool-kit
pull this repository off off git hub and enter the pGarfield/pGarfield_New directory
If you are using the RAAD2 system for TAMUQ you can just use 
```
git clone https://github.com/westoncadena/pGarfield.git
module load garfield/parallel
export GARFIELD_HOME=<home driectory>/pGarfield/pGarfield_New
PARALLEL=1 GARFIELD_HEED_INTERFACE=1 make
```
This will load all of the dependencies neeed before you make it. The PARALLEL=1 allows Garfield to use MPI's random number server and GARFIELD_HEED_INTERFACE=1 allows the Heed to use Garfield's random number server (which is now MPI's). If you wish to make the serial/series version of Garfield, ignore these two commands and just use make 

If you are not on the RAAD2 system then you will have to load the dependencies yourself before making pGarfield_New: 
```
source <root_install_dir>/bin/thisroot.sh
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<boost_install_dir>/lib
export GARFIELD_HOME=<pgarfield_sim_source_dir>
cd <pgarfield_sim_source_dir>          (should already be here)
PARALLEL=1 GARFIELD_HEED_INTERFACE=1 make
```

## Using Example
The repository includes an Example folder that contains code for a simulation of a particle track through a detector. In the folder, SRC contains all the source files, while OUTPUT is where you will compile and run your code. The input of simulation parameters is through a card file. The card file is specified through the command line argument. See Example/SRC/card.ini for a sample card file. In the file card, make sure you source the IonMobilityFile and the MeshDirectory. NumEvents is the number of tracks through the detector. For all physics related changes for the simulation, you will only need to change the card.ini. Note that if you do change the Mesh Directory, make sure that the sensor's demensions lines up with it as well.

## faisal.job
Located at Examples/OUTPUT/fasial.job, this is what you will be using to submit jobs to the RAAD2 machine. in here, make sure the directories for the SRC_DIR and the WORK_DIR are correct. In addtion, export the correct GARFIELD_HOME and HEED_DATABASE. For right now, the best speed up occurs at 24 cores.
```
export GARFIELD_HOME=<home driectory>/pGarfield/pGarfield_New
export HEED_DATABASE=<home directory>pGarfield/pGarfield_New/Heed/heed++/database/
```
once you are satisfied with your card.ini and have your faisal job corrected, then you can submit your job
```
sbatch faisal.job
```
