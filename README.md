# nibabel_nilearn_tutorial_2017
Materials for an intro to neuroimaging in python tutorial from Toronto, july 2017

## building the python environment for this tutorial..

Step 1.. start anaconda or miniconda..

Note in the example below..we are naming our environment "mripython" but you can call it whatever you want

```
conda create -n mripython3.5 python=3.5
source activate mripython3.5
conda install -c conda-forge nilearn
conda install seaborn
conda install docopt
conda install jupyter
source deactivate
```

## Installing the newest version of nilearn

The version available in conda-forge is a year old.. newer released are available to pip install..

**Note: everything we will do in this tutorial has been tested with the above env**

```
conda create -n mripython3.6 python=3.6
source activate mripython3.6
conda install scikit-learn
conda install seaborn
pip install nibabel
pip install -U nilearn
conda install docopt
conda install jupyter
```

## FYI when doing this on the CAMH SCC cluster here are the lines you need

```sh
## loads conda
module load PYTHON/3.6

## create the conda env into ${HOME}/.conda/envs/ with name 3.6_nilearn_01
conda create -n 3.6_nilearn_01 python=3.6

## activates that conda environment
source activate 3.6_nilearn_01

## install the packages - note jupyter is needed for us to be able to use it on jyputer hub
conda install jupyter
conda install scikit-learn
conda install seaborn
pip install nibabel
pip install nilearn
conda install docopt

## adds the 3.6_nilearn_01 environment to the kernels available by jupyter hub
python -m ipykernel install --user --name 3.6_nilearn_01 --display-name "Python (3.6_nilearn_01)"

## deactivate the conda environment
source deactivate
```

## FYI when doing this on SciNet...there are a couple of little changes you can do

+ you need to load the anaconda3 module first
+ here we specified the full path to the conda env we want to build

```
   10  module load python/3.6.4-anaconda5.1.0
   11  conda create --name mripython3
   12  source activate mripython3
   13  pip install nilearn
   14  conda install -c conda-forge nilearn
   15  conda install jupyter

module load python/3.6.4-anaconda5.1.0
conda create -p /scinet/course/ss2017/16_mripython/conda_envs/mripython3.5 python=3.5
source activate /scinet/course/ss2017/16_mripython/conda_envs/mripython3.5/
conda install -c conda-forge nilearn
conda install seaborn
conda install docopt
conda install jupyter
pip install qbatch  # an extra package for running things in parallel on the GPC
conda install pyyaml # only need it for cifitfy on Friday..
source deactivate
```

## the SciNet set-up script contains..

1. creates a sym-link from the tutorial conda env to your SciNet home
2. cp the the scripts into your SciNet
3. link the data into your SciNet $SRATCH
