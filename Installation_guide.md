```
mkdir dev; cd dev
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
bash Miniforge3-Linux-x86_64.sh -p ./miniforge
mamba create -n lab jupyterlab -c conda-forge
mamba activate lab
mkdir tools; cd tools
git clone https://github.com/isce-framework/dolphin.git
git clone https://github.com/isce-framework/tophu.git
git clone https://github.com/opera-adt/disp-s1.git
git clone https://github.com/opera-adt/sweets.git
git clone https://github.com/opera-adt/burst_db.git
git clone https://github.com/insarlab/MintPy.git
git clone https://github.com/insarlab/MiaplPy.git
mamba env update --name lab --file disp-s1/conda-env.yml
mamba env update --name lab --file sweets/conda-env.yml
# comment isce2
mamba env update --name lab --file MiaplPy/conda_env.yml 
python -m pip install --no-deps -e dolphin/ tophu/ disp-s1/ sweets/ MintPy/ MiaplPy/ burst_db/
pip install pre-commit
python -m pip install flake8
pip install black
mamba install pytest
mamba install -c conda-forge "cudatoolkit=11.6" cupy "pynvml>=11.0"

mamba create -n isce2 isce2
mamba activate isce2
python -m pip install --no-deps -e
python -m pip install --no-deps -e MintPy/ MiaplPy/
mamba install isce3
```
