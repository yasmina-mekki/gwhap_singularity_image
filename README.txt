##### Singularity #####

- installation de singularity.
	git clone https://github.com/singularityware/singularity.git
	cd singularity
	git fetch --all
	git checkout 2.6.0
	./autogen.sh
	./configure --prefix=/usr/local
	make
	sudo make install
- Une dépendance manque lors de cette instalation. Il faut l installer par sois même
	apt-get install package

##### Image using singularity #####

- Créer un environnement anaconda avec toutes les bibliothèques nécessaire à tes analyses.
- Activer ton environnement.
- Exporter cet environnement dans un fichier yml:
	conda env export > environment.yml
- Faire une recipe miniconda_image_2.def
- Placer la recipe et le fichier de l'export de l'environnement au sein du même dossier.
- créer une image via cette recipe. (Il faut avoir les droits sudo).
	sudo singularity build conda.simg Nom_de_la_recipe.def


##### execution #####
- Executer un scipt python utilisant l'image
	singularity exec image.simg python script.py

Lien : 
Pour la création de l'image :  https://stackoverflow.com/questions/54678805/containerize-a-conda-environment-in-a-singularity-container
Pour l'installation de singularity : http://www.apc.univ-paris7.fr/~souchal/2018/03/06/tp--cr%C3%A9er-un-conteneur-avec-singularity/
Pour l'execution : https://sylabs.io/guides/2.6/user-guide/quick_start.html
