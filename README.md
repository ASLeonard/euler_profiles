# Running `snakemake` on Euler

## Installing snakemake

Install [mamba](https://github.com/conda-forge/miniforge?tab=readme-ov-file#install)

Version 8
```
mamba create -n snake8 -c conda-forge -c bioconda python=3.12 snakemake=8
```

Version 7
```
mamba create -n snake8 -c conda-forge -c bioconda python=3.12 snakemake=7.32.4
```

## Running snakemake


Internally, there are some changes to the profiles, so these currently are not identical in their operation.

### Version 8

```
snakemake -s <snakefile> --configfile config.yaml **--executor slurm --profile "slurm/v8"** -n
```

### Version 7

```
snakemake -s <snakefile> --configfile config.yaml **--profile "slurm/full"** -n
```

#### Using `screen`

Snakemake often needs to run for a long time while the workflow completes.
It is easier to use `screen` and let a process run in the background (and persist after logging out)!

You can always log back in to the same head node and reconnect to your screen with `screen -r` (or `screen -r <ID>` if you have multiple screens active).

