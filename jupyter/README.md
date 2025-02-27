# Jupyter Notebooks

## Usage

There are 3 ways to run Jupyter Notebooks:
  1. __[JupyterHub](https://jupyter.hpcc.ucr.edu) server__

     This method is the easist, however resources are limited thus only used for light testing.

  2. __Interactively as a Job__

     This method is the most difficult, however it provides a way to request more resources than JupyterHub.

  3. __Non-Interactively as a Job__

     This method is not difficult, in fact it is the same method we use for submitting most jobs on the cluster.

## Workflow

The suggested workflow would be to do light development from the __[JupyterHub](https://jupyter.hpcc.ucr.edu) server__ and when you have a polished Jupyter Notebook you can submit it __non-nteractively as a job__ via `sbatch`.

The __Interactively as a Job__ method should only be used in extream situations, when exploring or testing is not possible from the __[JupyterHub](https://jupyter.hpcc.ucr.edu) server__.

## Interactively as a Job

This meothed provides a web-based interactive development environment (IDE) similiar to the [JupyterHub](https://jupyter.hpcc.ucr.edu) server, however you are able to request more compute resources.

First review the following method, [HPCC Web Browser Access](https://hpcc.ucr.edu/manuals_linux-cluster_jobs.html#web-browser-access). After you have read through that, you can procceed with this example.

Download the Jupyter submission script:
```bash
wget https://raw.githubusercontent.com/ucr-hpcc/hpcc_slurm_examples/master/jupyter/submit_jupyter.sh
```

Edit script with proper Slurm resources:
```bash
vim submit_jupyter.sh
``` 

Submit the Jupyter job:
```bash
sbatch submit_jupyter.sh
```

Check for Jupyter job start time:
```bash
squeue -u $USER -o '%i %j %S %Z'
```

If your job has already started, then check the log, which will contain the remainder of your instructions:
```
cat jupyter-notebook-12345678.log
```
Replace `12345678` with your real `JOBID` from the previous step.

## Non-Interactive as a Job

Download the Jupyter Notebook (or create your own):
```bash
wget https://raw.githubusercontent.com/ucr-hpcc/hpcc_slurm_examples/master/jupyter/notebook.ipynb
```

Download the notebook submission script:
```bash
wget https://raw.githubusercontent.com/ucr-hpcc/hpcc_slurm_examples/master/jupyter/submit_notebook.sh
```

Edit script with proper Slurm resources, and options for your notebook:
```bash
vim submit_notebook.sh
```

Submit the notebook job:
```bash
sbatch submit_notebook.sh
```

Check the state of your job:
```bash
squeue -u $USER
```

If your job has started, then you can check the log to verfiy that your script is running:
```
cat jupyter-notebook-12345678.log
```
Replace `12345678` with your real `JOBID` from the previous step.

Once the job has completed, you can download and view your HTML or Notebook results from the [JupyterHub](https://jupyter.hpcc.ucr.edu) server.
