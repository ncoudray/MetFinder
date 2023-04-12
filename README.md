*MetFinder* is a tool for quantification of melanoma metastasis tumor burden in mouse whole slide images of livers and brains.

MetFinder relies on a deep-learning network trained by manual annotations from pathologists to recognize tumor and non-tumor regions in a whole slide, H&E stained image, removing artifacts and other types of tissues from the analysis. Thus far this tool is trained for the quantification of tumor burden resulting from human xenograft models of melanoma metastasis in mouse livers and mouse brains.


# Web access
MetFinder can be access at http://spawebwcdcdvm01.nyumc.org/. Slides can be downloaded via the webinterface and will run on our local computers.

# Local installation
If you want to run MetFinder on your own cluster machines, it will have to be run via command line.

First, install the DeepPATH pipeline via the [DeepPATH github page]](https://github.com/ncoudray/DeepPATH/).

Then, you need to download the checkpoints associated with the brain met from [01_brain_B022_35k](https://genome.med.nyu.edu/public/tsirigoslab/DeepLearning/MetFinder/checkpoints/01_brain_B022_35k), and those associated with the liver met from [01_liver_L032_200k](https://genome.med.nyu.edu/public/tsirigoslab/DeepLearning/MetFinder/checkpoints/01_liver_L032_200k). 

The `sb_MetFinder.sh` script above is a template script written for slurm/bash clusters. See the  [DeepPATH github page]](https://github.com/ncoudray/DeepPATH/) for more details about the different instructions. In the script above, you will need to change the variables declared in the first few lines:
- The `#SBATCH#` instructions are specific to our SLURM cluster. You need to adjust to whatever cluster you are using.
- you will need to instal the `conda3_520_env_deepPath.yml` environment, as described in [DeepPATH github page]](https://github.com/ncoudray/DeepPATH/), and eventually adjust the `conda activate` line according to the path where your environement is created
- `PATH_TO_CODE` corresponds to the path where the DeepPATH is saved on your machine
- `PATH_TO_BRAIN_CHEKPOINTS` and `PATH_TO_LIVER_CHEKPOINTS` are the paths where the checkpoints downloaded previously have been saved
- `nbox` and  `noverlap` can be modified to `299` and `0` respectively if you want to run MetFinder without tile overlap (save time and space)


# Template slides
Template slides can be downloaded from (https://genome.med.nyu.edu/public/tsirigoslab/DeepLearning/MetFinder/slides)



