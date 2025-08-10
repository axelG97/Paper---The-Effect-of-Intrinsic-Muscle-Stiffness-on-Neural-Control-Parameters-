# Paper---The-Effect-of-Intrinsic-Muscle-Stiffness-on-Neural-Control-Parameters-
The Effect of Intrinsic Muscle Stiffness on Neural Control Parameters in Musculoskeletal Models: A Simulation Study


Readme.txt
﻿This is the python code needed to produce all results for the manuscript 'The Effect of Intrinsic Muscle Stiffness on Neural Control Parameters in Musculoskeletal Models: A Simulation Study'.


Axel Gründemann 10-08-2025
TU Delft
Erasmus MC




----------------------------------------------------------------


Code is run for three models: 
'huxley' is the used Huxley model, from Vardy
'thijs' is the hill_expanded model, from Thijs
'stroeve' is the hill_simple model, from Stroeve


----------------------------------------------------------------


General notes: 
-Experiment names in the paper manuscript differ from in the code. Experiment 3 in the code is referred to as Experiment 2 in the paper. Experiment 2 in the code is Experiment 1 in the paper. Experiment 1 in the code is Experiment 0 in the paper.
-All scripts now adjusted to run from a google colab. To run any script as a notebook instead, do the following:
--Remove these lines:
from pydrive.auth import GoogleAuth
from pydrive.drive import GoogleDrive
from google.colab import auth
from oauth2client.client import GoogleCredentials
from google.colab import drive
drive.mount('/content/drive')


--Then, add these lines
import sys, os
root_path = os.getcwd()


--in the file ‘Exp3_feedback_robustplotter_runme.ipynb’, the path names in the functions xr.open_dataset need to be adjusted according to save locations that you are using. The same holds for the path names in mat4py.loadmat functions in most experiment 3 (experiment 2 in the paper) files like Exp3_feedback_findrobustness_runme.ipynb. 


----------------------------------------------------------------


Each experiment file contains some of the following folders:


Results: Folder where the results are printed. The figures are saved here directly, and the folders contain a folder 'data' where all data is sent to


Functions: Contains all used functions
save_functions.py is called to save experiment data
plot_functions.py is called to plot the results 
muscle_functions.py is called to calculate the muscle dynamics
matrices_functions.py is called to generate or update the arm environment matrices, excluded in experiment 1
integrator_functions.py is called to execute all the other functions in the order needed for the simulations. It calls upon the matrices_functions.py file and the muscle_functions.py file to generate new state information of both the system variables and the muscle variables. It furthermore calls upon the plot_functions.py file to generate figures depicting the muscle and system information over the experiment time. It calls upon the save_functions.py file to save the data
general_functions.py contains a list of all the python packages used
constants_functions.py is called to generate or to prepare the constants used in the experiments


Optimal_trajectories: Map containing the optimal trajectory data for experiment 3.


--------------------------------------------------------


Experiment 1


Exp1a_runme.ipynb - produces the data and graphs for experiment 1a
Exp1a_runme_shortmuscle.ipynb - reproduces the FL curve for the short muscle
Exp1b_msdfit_runme.ipynb - runs the stretch simulations at different velocities, produces data for experiment 1b
Exp1b_msdfit_plotter.ipynb - fits the experiment 1b data to a mass-spring-damper system and plots the results
Exp1c_FLV_generatedata_runme.ipynb - generates the data to produce the force-length-velocity curves for the three models in experiment 1c
Exp1c_FLV_plotter.ipynb - plots the FLV curves for experiment 1c


(as Experiment 1 is called Experiment 0 in the paper and is supplementary information in the appendix, the datafiles have been left out, as these are too large. They can be generated again simply by using the code)
--------------------------------------------------------


Experiment 2a


Exp2a_stabtest_1cell_runme.ipynb - allows for running simulations on experiment 2a. Tested excitation levels need to be changed manually.


--------------------------------------------------------


Experiment 3+2b


Exp2b_stabtest_1cell_runme.ipynb - allows for running simulations on experiment 2b. Tested excitation levels need to be changed manually. Stable trajectories were determined qualitatively, based on criteria described in the paper. thi
Exp2ab_plot_runme.ipynb - contains the found the minimal excitation levels of experiment 2 and plots the graph 
Exp3_feedback_testvector_runme.ipynb - This allows for plugging in a feedback vector and testing the effects.
Exp3_feedback_optimiser_global_runme.ipynb - This allows for running the global optimiser to find optimal values. Other optimisers were also tried, for more information you can contact me.
Exp3_feedback_findrobustness_runme.ipynb - This contains a function that loops trough the parameter space of the feedback system, prints the found costs and saves the dataset for plotting 
Exp3_feedback_robustplotter_runme.ipynb - Allows for the plotting of the feedback robustness data and trajectories of optimal feedback vectors.


Contains a folder with ‘Optimal Trajectories’ which are the reaching trajectories that the algorithm trained on. The source of this data is described in the paper.
--------------------------------------------------------


--------------------------------------------------------




For any questions feel free to contact me at axelgrundemann@gmail.com.
