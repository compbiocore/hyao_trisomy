# CBC analysis template

This is a template for our CBC analyses along with details on how to organize and structure files and descriptions so that they are easy to follow and consistent across the organization.

## Starting and working on a project

 * Naming structure of a repo should be: PIfirstinitialPIlastname_projectname
 * After using this template to create the repo, create a Github project and associated issues that correspond to deliverables for the project
 * Create your Github secrets for the repo and build the necessary Singularity image to run the analyses (see below)
 * For each issue, create a branch and work off of the branch. You can reference issues with their number when making commits, as well as close them by typing `close #{issue_num}`. When an issue is resolved, make a pull request to merge the branch in. Reviewers are not necessary to merge, but can be helpful if you are working collaboratively on a project.
 * Describe the experimental design, required inputs and how to reproduce under the appropriate sections
 * Put any updates for your project into `UPDATES.md`.

## Experimental Design and Goals

Details on the experimental design should go here, including how many groups, how many samples, which samples belong in which groups (or where you can find the sample metadata), the questions we are trying to answer with the design, etc.

## Folder organization and files

For more information see https://compbiocore-brown.slab.com/posts/data-organisation-for-analysis-repos-fdi2cddd. Our folder organization is as follows:

### Folders that should be in the Github repository

 * **metadata:** files such as sample manifests, YAML control files, Dockerfiles
 * **scripts:** bioinformatics scripts for processing data.
   * Following a logical structure for running the scripts, whether it is `00_create_env.sh`, `01_step1.sh`, etc or in chronological order is helpful for the next person to be able to follow
   * It can also be helpful to have a `logs` folder in here to place all of your slurm log outputs.
 * **notebooks:** notebooks (Jupyter, Rmd, Quarto, etc) for working with the processed data
   * Similary, a logical structure to follow for the notebooks is helpful
 * **results:** any end results that will be provided to the collaborator or manuscript

### Folders that should not be in the Github repository

 * **data:** All raw data and large intermediate results that will not eventually be published or providing a starting point for reproducibility should go in here. There is a `.gitignore` that is set up to automatically ignore `.fastq`, `.fastq.gz`, `.sam`, `.bam`, and `data` among other miscellaneous files in there to try to avoid large data commit issues.

### Describing your files

For all folders, there should be a detailed description of what files are in there, whether in the folders README or on the main README. For example, if there is sample metadata, a reference, and a Dockerfile in **metadata**, 3 scripts in **scripts** and 1 figure in **results**, then you would want to set up something like this:

 * **metadata:** Contains `metadata.csv`, `Hg38.gff`, `Dockerfile`. For more details see the `README` in the folder.
 * **scripts:**
   * `00_env.sh`: Creates environment to run bioinformatics scripts including pulling the Singularity image from our container registry.
   * `01_fastqc.sh`: Runs FastQC on samples
   * `02_figures.sh`: Runs analysis pipeline and produces `figure1` in **results**
 * **results:**
   * `figure1.pdf`: Figure showing how great our results are

## How to reproduce

Steps to reproduce the results should go here, including where the data can be found and what the inputs need to be, the order in which things should be run, etc.

## Automated container building
This template also comes with a pre-written github action workflow that will work out-of-the-box as is and automates the process of updating docker images for your analysis project, publishing these updates, and image versioning. To ensure this workflow works for your new repo, you will need to create **two github secrets** for your repo as follows:

* **GH_USERNAME -** this is your guthub username
* **GH_TOKEN -** this is a personal access token (PAT); make sure it has read, write, and delete permissions (if you need to make one and are unsure how, please see:  https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) 

**IMPORTANT:** Before making edits to your repo, please make sure you have visited and read: https://app.gitbook.com/o/-LLCCXzgv2-pRyGi-QB2/s/-LpZv9ZetU-XF7BJyICY/container-automation-pipeline

## Additional notes

We have documented our overall process here: https://www.notion.so/brownccv/CBC-Analyses-Setup-457a3791a4fa432788812c96b1e864b1?pvs=4

# CBC Project Information

In theory this section should get filled out, and then some kind fo script will take this information and automatically combine them into a page that showcases our projects. It has not been implemented yet.

```
title:
tags:
analysts:
git_repo_url:
resources_used:
summary:
project_id:
```
