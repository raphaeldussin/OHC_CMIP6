template for Mackenzie

# Setting up the conda compute environment

* install anaconda:
```
ssh public3
cd /nbhome/First.Last
wget https://repo.anaconda.com/archive/Anaconda3-2020.11-Linux-x86_64.sh
chmod +x Anaconda3-2020.11-Linux-x86_64.sh
./Anaconda3-2020.11-Linux-x86_64.sh
```

At prompt, install under /nbhome/First.Last/anaconda3
and refuse when the installer wants to add conda init to bashrc/cshrc.
Instead, copy my files and replace Raphael.Dussin by First.Last

```
cp /home/Raphael.Dussin/.condacsh-nb /home/First.Last/.
cp /home/Raphael.Dussin/.condabash-nb /home/First.Last/.
```

* install conda environment:

```
conda env create -f environment/mackenzie.yml
conda activate mackenzie
```

To have the conda env visible in jupyter-lab, this step is required:
```
python -m ipykernel install --user --name mackenzie --display-name "Mackenzie"
```

finally, this builds the git and dask lab extensions:
```
jupyter lab build
jupyter labextension install dask-labextension
```

* configure dask-jobqueue:

```
cp environment/jobqueue.yaml $HOME/.config/dask/jobqueue.yaml
```
