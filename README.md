# gwhap singularity image

## instal singularity
git clone https://github.com/singularityware/singularity.git
cd singularity
git fetch --all
git checkout 2.6.0
./autogen.sh
./configure --prefix=/usr/local
make
sudo make install