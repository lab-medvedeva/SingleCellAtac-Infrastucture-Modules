## SingleCell Docker files


### How to run Docker files

#### SnapATAC
```
docker run --gpus all -it --shm-size=10G -d --rm --name snapatac -v $PWD:/workspace/BioInfo akhtyamovpavel/snapatac bash
```

#### SnapTools
```
docker run --gpus all -it --shm-size=10G -d --rm --name snapatac -v $PWD:/workspace/BioInfo akhtyamovpavel/snaptools bash
```
