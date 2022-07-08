---
title: How to use HPC Clusters - Basics
categories: HPC
tags: [HPC,linux,cluster,nova]
maths: 1
toc: 1
---

{% include toc.html %}

# What is a Cluster ?

1. Several computers put together where, each computer is a node is called a [cluster](https://en.wikipedia.org/wiki/Computer_cluster).

# Tidbits

1. For all the information about clusters at the ISU, visit [here](https://www.hpc.iastate.edu/).
2. You can look up the specifications of all the clusters available for us [here](https://www.hpc.iastate.edu/systems).
3. There are a few non-ISU clusters that could be made available to us (Anvil, Bridge, Expanse, etc). Aditya Balu has access to a lot of the clusters available through [XSEDE](https://www.xsede.org/). Contact him if you need more resources.

# Steps to Connect to Cluster

1. Connect to the VPN if not on the same network as the cluster.
2. Use the command enclosed by “<>”. < ssh netid@clusteradress >
    1. Example for Nova users (Due to bias) - < ssh isu_net_id@nova.its.iastate.edu >
3. If 2-factor authentication is enabled for the accessing any cluster, you will need to input the authentication code followed by your password to gain access.

# Basics of handling cluster

1. **NEVER** run any **code/command** that take more than **30 secs** to execute on the **login node**. Use compute nodes in such cases. ISU [HPC](https://www.hpc.iastate.edu/guides/condo-2017/managing-jobs-using-slurm-workload-manager) website has the necessary commands.
2. Use ****“**tmux**” to ensure safety of your work progress on cluster. Read more about tmux [here](https://leimao.github.io/blog/Tmux-Tutorial/).
3. Use virtual environments for different projects. 
4. Use “**version control”** like git to better manage code development.
5. Check for [modules](https://hpc-wiki.info/hpc/Modules) that are loaded on the cluster. Basic commands to handle modules are given below.
    1. < module list > → shows currently loaded modules
    2. < module spider “library” > → search for all available versions of the “library” that can be loaded. Example : < module spider python >.
    3. < module load “library” > → self-explanatory. Use the exact name of the version you want. (Copy the version name from the list you get after using < module spider >).
    4. < module purge >
6. Use “alias” for the most used commands. **Example** → you can assign path shortcuts to speed up navigation across various folders on the cluster. Create “alias” inside “.bashrc”. Read more about “alias” [here](https://alvinalexander.com/blog/post/linux-unix/create-aliases/).
    1. From your home directory → Use command < vi .bashrc > or < vim ~/.bashrc >
    2. Use < i > to start editing inside the vim / vi editor. Read more about editors [here](https://www.geeksforgeeks.org/getting-started-with-vim-editor-in-linux/).
    3. Add < alias = “cd /work/baskarg/aapowadi” > and save the file using < Esc key, :wq, enter key>
    4. 
7. Use < which “library/software” > to check the **location** of the library/software you are currently using.

# Virtual Environments

> Why Virtual Environment ? → Different projects may need different versions of libraries and to avoid conflict in such cases, we use virtual environment. Read more about virtual environments [here](https://www.geeksforgeeks.org/python-virtual-environment/).
> 

**Creating Virtual Environments**

1. Go to a folder of your choice. 
2. Use < virtualenv -p python “name” >. “name” is adequately to avoid confusion.

**Activating and Deactivating Virtual Environments**

1. Go to the folder where you installed the virtual environment (alias could be used).
2. Use < source bin/activate > to activate the virtual environment. If successfully activated, the environment name will pop up on your next command line as shown below. (”multimae” is the name of the virtual env).
    
    ![Screen Shot 2022-07-01 at 11.10.47.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/85ee4a39-40f6-4da6-8632-37f94a8011d2/Screen_Shot_2022-07-01_at_11.10.47.png)
    
3. You could also activate virtual environment from any location.                                             Use < source path/to/bin/activate >.
4. Use < deactivate > to deactivate the virtual environment.

**Installing Libraries Inside the Virtual Environment** 

1. Use < pip list > to check out all the installed libraries inside the virtual environment.
2. Use < pip install “library_name” > to install libraries. Google “pip install library” to find the right name to use.
