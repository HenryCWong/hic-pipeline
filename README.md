[![CircleCI](https://circleci.com/gh/ENCODE-DCC/hic-pipeline/tree/dev.svg?style=svg)](https://circleci.com/gh/ENCODE-DCC/hic-pipeline/tree/dev)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![MIT License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

# ENCODE Hi-C uniform processing pipeline

## Overview

The [ENCODE](https://www.encodeproject.org/) pipeline for processing Hi-C data based on [Juicer](https://github.com/aidenlab/juicer)

This is a fork of the encodedcc/hic-pipeline to work on Washington University at St. Louis's Compute 1 Cluster.
Maintained by Henry C. Wong (wongh@wustl.edu,cywongx@gmail.com,henrycwong@mst.edu). 

## Installation

1. Git clone this pipeline.
    ```bash
    $ git clone https://github.com/ENCODE-DCC/hic-pipeline
    ```

2. Run an interactive session on the compute cluster using a docker container that contains caper, java, and python. Feel free to use mine (henrycwong/pipeline). 
   ```bash
      LSF_DOCKER_VOLUMES="${YOUR_PATHS_HERE}:${YOUR_PATHS_ERE}" bsub -G compute-group -q queue-group -a "docker(henrycwong/pipeline)" /bin/sh
   ```
   

3. Follow [Caper's README](https://github.com/ENCODE-DCC/caper) carefully to configure it for your platform (local, cloud, cluster, etc.)
> **IMPORTANT**: Configure your Caper configuration file `~/.caper/default.conf` correctly for your platform.

   ```bash
      caper init pbs
   ```
   We're not using pbs, but we're using the way the caper calls pbs to run on an LSF server. If you don't know what any of that means, don't worry about it. 
   After the init command you will want to add a path for caper to store the pipeline's output. 

## Usage

To verify your installation, you can run the following pipeline with a test data set by invoking the following command from the root of the cloned repository.

> Note: this will incur some cost when running in cloud environments.

```bash
$ caper run hic.wdl -i tests/functional/json/test_hic.json --backend-file lsf.backend.conf
```

For detailed usage, see [usage](docs/usage.md)

## Inputs

See [inputs](docs/reference.md#inputs)


## Outputs

See [outputs](docs/reference.md#outputs)

## Contributing

We welcome comments, questions, suggestions, bug reports, feature requests, and pull requests (PRs). Please use one of the existing Github issue templates if applicable. When contributing code, please follow the [Developer Guidelines](docs/CONTRIBUTING.md#developer-guidelines).
