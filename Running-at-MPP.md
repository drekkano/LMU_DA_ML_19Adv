# Running at RZG

Originally, this tutorial was designed to run in the CIP Pool of the physics
department of the LMU. With some adaptations, it can however be also run at RZG
for MPP users.

Two resources can be in principle used as basis to run the Jupyter notebooks:
one of the login nodes of the slurm cluster and the Jupyter notebook service
(preferred).

The tutorial was originally developped by Guenter Duckeck, Nikolai Hartmann and Alexander Mann from the LMU. Full credits go to them. I only made some small adjustements (e.g. updating the syntax to tensorflow 2.1) but eventually there will be also some changes are required to run it properly for MPP users. For them it's advised to check out my fork on github:  [https://github.com/drekkano/LMU_DA_ML_19Adv](https://github.com/drekkano/LMU_DA_ML_19Adv).

Detailed instruction how to checkout the repsitory can be found below.

After the environment has been setup and the repository checked out, the tutorial can be started by navigating within the Jupyter web interface to the notebook [PythonDA_ML.ipynb](PythonDA_ML.ipynb) and open it.

## Running on the Jupyter Notebook Service
An extensive documentation how to use this service can be found [here](https://www.mpcdf.mpg.de/services/visualization/remote-visualization-service). For the tutorial it is advised to use the DRACO HPC system as COBRA does does not allow outgoing connections (some of the notebooks load external data from the web which result in time-out errors).

In short, setting up an environment will involve the following steps
* Login via the [Web Interface](https://rvs.mpcdf.mpg.de)
* Submit a new session on DRACO with "Jupyter for Machine Learning" as session type
* Connect to the session via your browser

In case you are using the service for the first time you have to perform an initialization step as described in the documentation.

#### Loading the ML Software
To make the typical ML software stack available in your notebooks, the associated modules have to be loaded. This can either be done directly in the notebooks via the following commands

    module('load', 'cuda/10.1')
    module('load', 'cudnn/7.6.2')
    module('load', 'nccl/2.4.8')
    module('load', 'tensorflow/gpu/2.1.0')
    module('load', 'tensorboard/2.1.0')
    module('load', 'tensorboard/2.1.0')
    module('load', 'scikit-learn/0.21.2')

On the long run, it is probably more comfortably to load these module automatically when a Jupyter notebook is started. This can be done during the "Intitialize Remote Visualization" step by adding the following to the default modules for JN sessions (set checkmark to the field)

    cuda/10.1
    cudnn/7.6.2
    nccl/2.4.8
    tensorflow/gpu/2.1.0
    tensorboard/2.1.0
    tensorboard/2.1.0
    scikit-learn/0.21.2

Then the `module(..)` commands above have not to be added anymore to the notebooks.

#### Checking out the Repository
The repo needs to be checked out on the HPC system used (e.g. DRACO). This can be done in two ways. Either open a terminal in the Jupyter interface or log into the corresponding gateaway node (e.g. `ssh USERNAME@draco.mpcdf.mpg.de`). The former is not possible for COBRA as it does not allow for outgoing connections. The latter has to be done when already inside the MPCDF network (e.g. by logging into gatezero.mpcdf.mpg.de first) as the HPC systems are not visible to the outside world. In both cases the repo can then be checked out via
(this probably requires a `module load git` beforehand)

    git clone -b tf-2.1 https://github.com/drekkano/LMU_DA_ML_19Adv.git
    
## Running on the Input Nodes of the Linux Cluster
To be added ...
