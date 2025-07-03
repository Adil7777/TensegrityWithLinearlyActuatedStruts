# Design and Control Prismatic Triangular Tensegrity Robot with Linearly Actuated Struts

## About the tensegrity prototype

![Tensegrity Structure Scheme (1)](https://github.com/user-attachments/assets/ff08c95b-8db4-4aae-a9d7-2c5a33af3825)

Above you can see the design of prototype for research paper. Tensegrity-based manipulators present challenges for conventional kinematic analysis, which is essential for path planning and control. Traditional manipulator control relies on inverse kinematics using linear algebraic operations on joint and link parameters, given a desired end-effector position. The high-dimensional, nonlinear dynamics of tensegrity structures complicate this process, as models often involve partial differential equations. **This repository presents a data-driven approach to control the prototype.**  

## Control Strategy

![CombinedFigure](https://github.com/user-attachments/assets/0495bb33-1925-4b3c-a6df-951bd304514a)

This prototype contains 6 linear actuators that can be elongated to 73.8 mm. To collect the training data, we have programmed this prototype to undergo different trajectories with reflective marker on it. OpriTrack system was recording XYZ coordinate while the states of linear actuators were recorded as well. This data was then used to train machine learning and neural network models. The picture above presents a visual representation of data collection. The proposed models would take 3 inputs, XYZ coordinate and output 6 values, linear actuator states.  

## Organization of Repository

- Folder **Current Data** contains the data from the OptiTrack motion capture system and states of linear actuators. This data was used for model's training and validation.
- Folder **Old Data** contains the data from the OptiTrack motion capture system and states of linear actuators that was used for training and validation in 2024.
- Folder **models** contains the trained neural network models with different architectures and hyperparameters. 
- Folder **Natural Frequency** contains the data from the experiment with settling time (more details in the paper)



- **data_preprocessing.ipynb** file was used to preproccess and synchronize the data from OptiTrack and states of linear actuators
- **regression_models.ipynb** file contains the source code all the tested regression models for this project.
- **tree_models.ipynb** file contains the code for all tree-based models, which are:
  - Decision Tree Regressor
  - Random Forest Regressor
  - XGBRegressor
- **model.ipynb** file contains the code for neural network models that eventually were chosen in paper to validate on physical setup.
- **validation.ipynb** file calculates the euclidean ditance between the desired and actual coordinate points by evaluating neural networks performance.
- **fluctations.ipynb** file containt the source code to experiment with settling time.
