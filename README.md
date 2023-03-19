# CoreGenome-AF-Phylogeny

`CoreGenome-AF-Phylogeny` is a Snakemake pipeline which uses Alignment-free methods to construct Phylogenetic trees. Given a list of proteomes in fasta format from various species, it performs clustering with all the proteins and selects those from core genomes. Then the pipeline feeds them into the Alignment-free based methods to generate the Phylogenetic tree.

## Installation
```
git clone https://github.com/garrison-chen/CoreGenome-AF-Phylogeny.git
cd CoreGenome-AF-Phylogeny
conda env create --name CoreGenome-AF-Phylogeny --file=environments.yml
conda activate CoreGenome-AF-Phylogeny
```

## Usage
To start with, you need to copy your input data under `data` folder. The data should be fasta format, where each fasta file represents amino acid sequences from a single species. Ideally, the fasta file should cover the proteome. 

Then, edit the `config.yaml` file to set up the parameters you prefer for clustering sequence identity and the number threads you want to use.

After than, run the following command to perform the clustering and output the U-shape plot:
```
snamekame --cores X U-shape-plot.png
```

Then inspect the generated `U-shape-plot.png` to choose a threashold to determine the proteins from core genomes. Now go to `config.yaml` to change the select threshold parameter.

Now you may run the whol pipeline using the following command:
```
snakemake --cores X
```
