# Managing Local virtual machines

Command line syntax to manage your local virtual machines:

wordslab *host* : Manage wordslab virtual machines on your host machine

## Host machine sandbox

wordslab **host init** : Install software prequisites and initialize your host machine sandbox

wordslab **host config show** : Display host machine sandbox configuration

wordslab **host config update** : Update host machine sandbox configuration

## Local virtual machines

wordslab *host vm* : Create and manage virtual machines on your host machine

wordslab **host vm list** : List all wordslab virtual machines created on your local host

wordslab **host vm create** [name] [OPTIONS] : Create a new wordslab virtual machine on your local host
- [name] : Virtual machine name
- --minimum : Use minimum compute and storage config
- --recommended : Use recommended compute and storage config
- --maximum : Use maximum compute and storage config

wordslab **host vm start** [name] [OPTIONS] : Start a local wordslab virtual machine on your local host
- [name] : Virtual machine name
- --minimum        Use minimum compute spec
- --recommended    Use recommended compute spec
- --maximum        Use maximum compute spec
- --proc [number] : Max number of processors
- --mem [number] : Max memory size in GB
- --gpu : Allow acces to GPU ?

wordslab **host vm stop** [name] : Stop a local wordslab virtual machine on your local host
- [name] : Virtual machine name

wordslab **host vm status** [name] : Display the status of a specific wordslab virtual machine on your local host
- [name] : Virtual machine name

wordslab **host vm advise** : Advise a minimum, recommended and maximum config for a local virtual machine

wordslab **host vm resize** [name] : resize an existing wordslab virtual machine on your local host
- [name] : Virtual machine name

wordslab **host vm delete** [name] : DANGER - Delete a local wordslab virtual machine - ALL DATA WILL BE LOST
- [name] : Virtual machine name

## Host machine system info

wordslab **host system info** : Display host machine hardware and operating system information

wordslab **host system status** : Display host machine usage metrics: cpu, memory, storage, network



