# deseq2_analysis_example
setting up deseq2 on an hpc without sudo

I am taking notes here on how I set up a deseq2 run on an hpc.
Most of what I am seeing out there requires some sudo command.
My admins seem reluctant to let me sudo on the cluster.
So here are my notes on what I am doing to get the analysis done.

First note, that intial attempts to run R and Bioconductor, were met with frustration, since Rcpp could not find the requisite libraries. I settled on using conda so that I could manage my env and mantain a basic level of portability, to other machines. 

--------------------------------------
# setting up a local conda install 

* I opted for miniconda to save some space. 

```
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
* put together a basic R environment and activated it.

```
$ /miniconda3/condabin/conda create -n deseq  r-essentials r-base
$ ./miniconda3/condabin/conda init
$ source ~/.bashrc
$ which conda
~/miniconda3/bin/conda
$ conda activate deseq
(deseq) 
```

* Now let's look at putting deseq2 into this env. 

```
conda install -c bioconda bioconductor-deseq2
# Lots of messages ...
# looks like it is time for an update
$ conda update -n base -c defaults conda
$which R
~/miniconda3/envs/deseq/bin/R
(deseq) 
```
* Looks like we are all set to start deseq2 and looking into differential expression.




