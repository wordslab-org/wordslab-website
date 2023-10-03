# Overview

## Discover wordslab manager

1. Launch a terminal.

2. Navigate to your wordslab installation directory.

3. Execute **wordslab --help** or **wordslab [command] --help** to discover the commands syntax.

4. Execute **wordslab host system info** to analyze the hardware and software of your host machine.

## Create a sandbox on your host machine

1. Execute **wordslab host init** to initialize a sandbox on your host machine.

This command will:
- check the minimum hardware prerequisites
- install all the software prerequisites on your machine
- let you select the directories in which you want to store your virtual disks
- let you configure resource consumption limits to protect your host machine
- store all this information in a config database for future reference

## Create a new local virtual machine

1. Execute **wordslab host vm create [name]** to create a local virtual machine named [name].

This command will prompt you with all the information necessary to configure the new virtual machine.

## List the local virtual machines

1. Execute **wordslab host vm list**.

This command will give you the local virtual machines stored on on your host machine, and several properties regarding their current state.

## Start and stop a local virtual machine

1. Execute **wordslab host vm start [name]**.

2. Execute **wordslab host vm stop [name]**.

These commands will start / stop a local virtual machine, but will also set the host machine network so that you can access them (which may require admin privileges if you requested firewall openings for example).

## Download and deploy a Kubernetes app on a running virtual machine

1. Execute **wordslab app download [vm] [url]** where [vm] is the virtual machine name and [url] is a Kubernetes app URL.

Example of Kubernetes app provided by wordslab : https://raw.githubusercontent.com/wordslab-org/wordslab/main/wordslab.manager/apps/notebooks/wordslab-notebooks-gpu-app.yaml

2. Execute **wordslab app list [vm]** to get the ID of the specific version of a Kubernetes application you want to deploy.

Example of Kubernetes app ID : EIwKfHXcw/0VPijBmAXb/kmVvVBQNf/kIvWlClakako=

3. Execute **wordslab app deployment create [vm] [ID]** to deploy the Kubernetes app in a namespace of your choice.

4. Execute **wordslab app deployment list [vm]** to get the local URLs at which you can access the application.

Example of URLs:
- Jupyterlab: http://127.0.0.1/notebooks/lab
- Web interface (port 7860): http://127.0.0.1/notebooks/gradio
- API endpoint (port 8000): http://127.0.0.1/notebooks/fastapi



