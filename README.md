This repository contains the source codes for the paper, '**[Conditional TMDTO as a MILP Instance](https://doi.org/10.1109/TIT.2022.3230910)**'. 


## Description of the Attack
In this paper, we have converted the conditional Time-Memory-Data Tradeoffs (TMDTO) problem to a set of linear constrainst and objective functions for the case of stream cipher. Briefly, the problem can be stated as follows:

*What is the minimum number of state bits should be fixed in order to recover a maximum number of state variables directly from the keystream bits while guessing rest of the state bits ?* 

We have addressed this problem for the case where we are allowed to fix the state bits to 0 only. This repository contains the code to convert the above problem to an instance of Mixed Integer Linear Programming (MILP). In the paper, we have implemented it on three stream ciphers: ```Lizard```, ```Grain-128a``` and ```Espresso```. However, this repository contains the code for ```Lizard``` cipher. Code for other ciphers can be obtained by changing the update functions, keystream functions, state length ```state_len```, registers length ```R1_len, R2_len``` and other cipher information in the code.

## How to Reproduce the Results in Table I
Open the file ```TMDTO-Lizard_fwd+bkd.ipynb```.
Change the value of ```n_key``` with the number of keystream bits or equations. Update the value of ```keys_b``` with the number of backward keystream equations. The code outputs the number of fixed bits, which should be the same as the entries under the column ```Method-I``` [```keys_b = 0``` and ```pattern = [0,1,2,...,n_keys-1]``` for ```Method-I```]. Entries under ```Method-II``` column are for the cases when we consider different patterns of keystream bits and take backward keystream bits into consideration. 



## File Structure

1. ```TMDTO-Lizard_fwd+bkd.ipynb```: This file contains the MILP scripts to search for the optimal number of fixed bits, recovery bits and guessed bits for ```Lizard``` cipher. This script can be used to reproduce the data in Table I in the research paper.
## Dependencies

* [Gurobi](https://www.gurobi.com/)
* [Python3](https://www.python.org/download/releases/3.0/)
## Install and Setup Gurobi

1. Create a virtual environment with conda: ```conda create -n TMDTO_MILP```
2. Activate the new environment: ```conda activate TMDTO_MILP```
3. Add Gurobi channels as follows: ```conda config --add channels https://conda.anaconda.org/gurobi```
4. Install Gurobi using conda: ```conda install gurobi``` (academic users can obtain this license)
5. Activate license using the command: ```grbgetkey <license-number>```
6. Install the python package for Gurobi: ```pip install gurobipy```

