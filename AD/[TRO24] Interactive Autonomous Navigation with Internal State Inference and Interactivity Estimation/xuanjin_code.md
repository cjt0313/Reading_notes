1. copy behaviorsim_c
2. make the file by make.sh
3. copy the dataset and nuplan-dev package to your working director:
   1. NOTE: a more efficient way is to use the soft links.
4. enter xuanjing's bashrc, and copy the enviromental variables at the bottom to your own bashrc file, then re-source it
5. install nuplan-devkit and behavior_main
6. make changes in the scripts
7. run the python scripts
NOTE: to successfully run the [0722] version, one needs to build a new soft link to in .../split/trainval to .../trainval