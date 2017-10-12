# Setting up a Python environement

## 1. Install Miniconda

### On Linux from CLI

You can install [Minconda](https://conda.io/miniconda.html) from the command line with the following commands,

1. Install `git`, `wget` and `make` if they are not installed. For instance, on Ubuntu,

   ```
   sudo apt-get install git wget make
   ```

2. Donwload and install Miniconda. It's preferable to run this as non root user,
   
   ```
   wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh
   chmod +x miniconda.sh
   ./miniconda.sh -b
   echo 'export PATH=~/miniconda3/bin:$PATH' > ~/.bashrc
   source ~/.bashrc
   ```

### Any OS from GUI

1. Download and run [the latest Miniconda installer](https://conda.io/miniconda.html) for Python 3
