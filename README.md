# cirad-meso-bioinfo
a module checker on slurm pbs for the installation of the computing cluster. You can use this on the CIRAD server and also on any slurm or the pbs server and even configured with any instance. a general purpose utility to check the available modules from the circard servers and will provide support as you dont have to load the modules and then go through the list. It directly reads the bin files from the agi_bin files and then iterates over an indexed array stores them as memory and outputs the results by a operator comparison. To make it easier a brace expansion of the {a..z} so that you dont have to call each letter iteratively. 
```
#!/usr/bin/env bash
# -*- coding:  utf-8 -*-
# Universität Potsdam, Germany
# Author: Gaurav 
# date: 2024-2-12
# using a iterative storage indexed array for the faster iterations
echo "i am your module checker"
echo "i am reading the files from the nfs partition"
echo "the partitition is located at /nfs/work/agap_id-bin/modulefiles/ "
echo "executing the available module check list"
module load bioinfo-cirad
module load bioinfo-ifb
echo "for i in {a..z} \ 
        do cat file_modules.bioinfo-cirad.txt \
             | cut -f 12 -d " " | grep ^$i; \
done"
read -r -p "please enter the module name:" module
for i in $(for i in {a..z}; do cat file_modules.bioinfo-cirad.txt | cut -f 12 -d " " | grep ^$i; done);
do 
        if [[ $i == "${module}" ]]
          then 
             echo "the module is present"
fi
done
```
Gaurav,\
Academic Staff Member,\
Bioinformatics,\
Institute for Biochemistry and Biology,\
University of Potsdam,\
Potsdam,Germany
