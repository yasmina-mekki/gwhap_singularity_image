# gwhap singularity image

## install singularity
<code>
git clone https://github.com/singularityware/singularity.git
cd singularity
git fetch --all
git checkout 2.6.0
./autogen.sh
./configure --prefix=/usr/local
make
sudo make install
</code>


## create an image using singularity
- Create an anconda environnment with all libraries that are needed. Here an example used for the gwhap image.

<code>
conda create -n r_gwhap_r_3.6.1 r-essentials r-base
</code>


- Activate your environnement.
<code>
conda activate r_gwhap_r_3.6.1
</code>

- Export your environnement into an yml file.
<code>
conda env export > environment.yml
</code>


- Create a recipe gwhap_recipe.def. Please refere to the file available here.
- Put your recipe file as well as your yml file into the same folder.
- Create an image using the recipe created above. (you need root privileges)
<code>
sudo singularity build conda.simg gwhap_recipe.def
</code>

## execute the singularity image that you created above
- Create an R file with a simple instruction. For instance : 
<code>
print('Hello world')
</code>

- Execute this script using your singularity image as follow :
<code>
singularity exec conda.simg R script.R
</code>

## create an environnement using the yml file
- You can create an environnement using the yml file as well.
<code>
conda env create -f environment.yml
</code>	

## List of package that included in the yml file

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