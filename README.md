# pGarfield_New
This is the new version of pGarfield that includes the use of the Heed. pGarfield is the toolkit that is sourced when using. Examples has gem2B.C along with the other files needed.

## Making the Tool-kit
pull this repository off off git hub and enter the pGarfield_New directory. then use: 

```
source <root_install_dir>/bin/thisroot.sh
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<boost_install_dir>/lib
export GARFIELD_HOME=<pgarfield_sim_source_dir>
cd <pgarfield_sim_source_dir>
PARALLEL=1 GARFIELD_HEED_INTERFACE=1 make
```
the PARALLEL=1 allows Garfield to use MPI's random number server and GARFIELD_HEED_INTERFACE=1 allows the Heed to use Garfield's random number server (which is now MPI's). If you wish to make the serial/series version of Garfield, ignore these two commands and just use make

If you are using the RAAD2 system for TAMUQ you can use module load garfield/parallel. This will load all of the dependencies, but remeber to export Garfield home as the new tool kit after.

The repository includes a sample simulation client that supports the input of simulation parameters through a file (card file). The card file is specified through the command line argument. See Example/SRC/card.ini for a sample card file. in the file card, make sure you source the IonMobilityFile and the MeshDirectory

## fasial.job
Located at Examples/OUTPUT/fasial.job, this is what you will be using to submit jobs to the RAAD2 machine. in here, make sure the directories for the SRC_DIR and the WORK_DIR are correct. In addtion, export the correct GARFIELD_HOME and HEED_DATABASE

