#steps to run the simulation

#To clean the directory

foamCleanTutorials

#To generate mesh and check mesh quality

blockMesh

checkMesh

#To run the simulation

myicoScalarTransportFoam > myicoScalarTransportFoam &

pyFoamPlotWatcher.py myicoScalarTransportFoam

# other way to run

icoFoam > log.icoFoam &

tailf log.myicoScalarTransportFoam

# while the simulation running we can analyze the probes 

cd postProcessing/probes1/0/

#ceating the backup file without disturbing the simulation

cp U U-bkp1 

#opening the U-bkp1

geany U-bkp1 &

#For post-process there shouldn't be any brackets, so we have to remove the brackets

#If you are using the bkp file tha use U as U-bkp1

sed 's/(/ /g' U-bkp1 >U_mod
sed 's/)/ /g' U_mod >U_final

#At directory level plot the data using gnuplot

gnuplot plot_probes




