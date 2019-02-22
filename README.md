# Singularity container recipe and run script for the MaSuRCA assembler

### Clone this repository

```
mkdir isugif
cd isugif
git clone git@github.com:ISUGIFsingularity/spades.git
```

### Place singularity container into SIMG folder inside this repo

You can pull the singularity image using these commands

```
cd spades
mkdir SIMG
cd SIMG
singularity pull shub://ISUGIFsingularity/spades:1.8.0
ln -s ISUGIFsingularity-spades-master-1.8.0.simg  ISUGIFsingularity-spades-master.simg
```

### Add Alias and PATH

Place the following into your .bashrc folder for container use

```
#make sure you are in the spades folder that corresponds to the Path2thisRepo
export spadesgit=`pwd`
export PATH=$PATH:$spadesgit/wrappers
```

Place the following into your .bashrc folder to use scripts without container (preferred method unless testing container functions)

```
export spadesgit=path2thisrepo
export PATH=$PATH:$spadesgit/spades
```


### Notes

For this to function properly had to add ```--bind $spadesgit:/mnt``` to the wrappers

Example

```
 singularity exec --bind $spadesgit:/mnt --bind $PWD $spadesgit/SIMG/ISUGIFsingularity-spades-master.simg /mnt/spades/summary.sh
```
