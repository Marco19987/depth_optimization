# Depth Optimizer
ROS2 service server that implements a pose refinement alghoritm using depth data.

## Description
A solution to improve the pose estimation results getted from only rgb data for objects with variable dimensions (like an apple), using depth measures.  
* ***input***: estimated object pose, depth frame values from rgb-d camera, cad model of recongized object (models folder)
* ***output***: refined object pose 

## Getting Started

### Dependencies
The ROS2 node (python 3.10) requires the python module NVISII (https://github.com/owl-project/NVISII), which is available only for python <= 3.8. For compatibility reasons, you can use a conda environment as described below, else skip to 4).

1) Install conda [instructions](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html).


2.a) Run the bash script to create the conda environment from the environment.yaml file 
```diff
source setup_environment.sh
```

Alternativly you can directly create the environment

2.b) Setup conda environment 
```diff
conda create --name py_depth_opt python=3.8
conda activate py_depth_opt
```

2.b.1) Install some required packages on python38 env
```diff
conda install -n py_depth_opt pip numpy scipy matplotlib scikit-learn
```

2.b.2) Install NVISII
```diff
pip install nvisii
```

2.b.3) Update python
```diff
conda update python
```


---
***NOTE***

If you use a virtual environment as conda, note that you have to correctly set the ROS2 variable $PYTHONPATH. Following the procedure described in https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#saving-environment-variables, export the variable in the virtual environment by using
```diff
export PYTHONPATH="$CONDA_PREFIX/lib/python3.8/site-packages:$PYTHONPATH"
```

---

Once the conda environemnt is created and the PYTHONPATH correctly set, you can run the node:
```diff
conda activate py_depth_opt
ros2 launch depth_optimization depth_optimizer.launch.py 
```

---
The depth optimizer node depends on several parameters that can be set through the parameters.yaml file in the config folder. Moreover, the two parameters "mesh_path" and "mesh_scale", can be dinamically changed through the cli (ros2 param set) or bu code. 

## How to cite 

If you use this software in a research project, please cite as follows:
```
@INPROCEEDINGS{Costanzo2023,
  author={Marco Costanzo and Marco De Simone and Sara Federico and Ciro Natale and Salvatore Pirozzi},
  booktitle={9th International Conference on Control, Decision and Information Technologies (CoDIT'23)}, 
  title={Enhanced 6D Pose Estimation for Robotic Fruit Picking}, 
  month={July},
  address={Rome, I},
  year={2023},
  url = "https://arxiv.org/abs/2305.15856"
}
```








