---
layout: default
---
# NextFlow-VC-pipeline

NextFlow-VC-pipeline is a pipeline to detect structural variants. The pipeline is based on the [hartwig medical foundation pipeline](https://github.com/hartwigmedical/pipeline5).
It's built in NextFlow in combination with Singularity. 

## Installation

The installation requires Singularity (3.7.1 tested) and NextFlow (20.10 tested).

Singularity can be installed using the [Singularity documentation](https://sylabs.io/guides/3.7/user-guide/quick_start.html#quick-installation-steps).

NextFlow can be installed using conda or using the [NextFlow documentation](https://www.nextflow.io/docs/latest/getstarted.html#installation).

```bash
conda install -c bioconda nextflow
```

Building the Singularity container. Documentation recommends using sudo, however it's not required.
```bash
sudo singularity build NextFlow-VC.sif NextFlow-VC.def
```

## Usage

First change the nextflow.config file to match the input file paths.
Following example is for Paired-End samples named WGS_Norm_Lane#_R#.fastq.gz
```NextFlow
params {
    // Input parameters
    sampleBaseName = "WGS_Norm"

    refgen = "$HOME/data/refgen/rg6-17.fa.gz"
    reads = "$HOME/data/sample/WGS_Norm/${params.sampleBaseName}*{1,2}.fastq.gz"
    outdir = "$HOME/data/output/"
    
    threads = 8 // max cpus available
}
```

To run the pipeline:
```bash
nextflow -log logs/nf.log run pipeline.nf
```


[Link to default template info](./info.html).
[Link to another page](./another-page.html).