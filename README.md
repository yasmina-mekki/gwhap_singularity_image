# gwhap singularity image

## install singularity
```
git clone https://github.com/singularityware/singularity.git
cd singularity
git fetch --all
git checkout 2.6.0
./autogen.sh
./configure --prefix=/usr/local
make
sudo make install
```


## create an image using singularity
- Create an anconda environnment with all libraries that are needed. Here an example used for the gwhap image.

```
conda create -n r_gwhap_r_3.6.1 r-essentials r-base
```


- Activate your environnement.
```
conda activate r_gwhap_r_3.6.1
```

- Export your environnement into an yml file.
```
conda env export > environment.yml
```


- Create a recipe gwhap_recipe.def. Please refere to the file available here.
- Put your recipe file as well as your yml file into the same folder.
- Create an image using the recipe created above. (you need root privileges)
```
sudo singularity build conda.simg gwhap_recipe.def
```

## execute the singularity image that you created above
- Create an R script file with a simple instruction. For instance : 
```
print('Hello world')
```

- Execute this script using your singularity image as follow :
```
singularity exec conda.simg R script.R
```

## create an environnement using the yml file
- You can create an environnement using the yml file as well.
```
conda env create -f environment.yml
```	

## List of package that included in the yml file

- R 3.6.1 version
- dplyr
- magrittr
- grDevices
- tools
- utils
- stringr
- parallel
- R.utils
- ggplot2
- readr
- data.table
- RSQLite
- dummies
- Rcpp
- devtools
- rbgen
- karyoploteR
- BiocStyle