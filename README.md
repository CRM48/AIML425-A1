# AIML425-A1

## The Assignment

### Purpose
- To design and train a neural network that maps 3D input coordinates onto the surface of a unit sphere centered at the origin

### The Data
- The input data is any amount of randomly generated 3D coordinates, drawn from normal (Gaussian) distribution (mean = 0, standard deviation = 1)
- Expected outputs (or targets) could be calculated by dividing each coordinate in the vector by the euclidean norm (current length from origin) of the vector
- This data was split at a ratio of 0.7 : 0.15 : 0.15 for training : validation : testing

### The First Plot
- An interactive plot was generated using plotly. It showed these expected output points in 3D space. This visualisation shows how these points lie on the unit sphere

### The Datasets and DataLoaders
- A dataset was created using each set of datas (training, validation, and testing) input and expected output pairs of coordiantes
- From this, a data loader was created for each, which split the datasets in batches of a fixed size (64 was used)

### The Model
- The model was created based on the specifications of the task
- 4 layers, the first was the input layer which took three parameters (the three coordinates
- The second and third layers were hidden and took 20 parameters each
- The final layer was the output layer which took 3 parameters. These represented the produced coordinates for the models prediction
- Inbetween the first and second, and second and third layers, a non-linear activation function is used so the model can learn any complex patterns in the dataset
- These activation functions can and were changed, this was helpful when trying to create an optimal model to solve the problem

### Loss and Optimizer
- The base case used Mean Squared Error as the criterion for loss and Adam as the optimizer
- However, other cases used different optimizers to assess performance

### Training
- Training was done using the model, each epoch first trained the model, then validated that it wasn't overfitting
- Expected outputs were calculated given the inputs, and compared to target outputs (the calculated values) to get a measure of training loss per epoch
- Backpropogation was then used to update weights
- To validate the data the program simply calculated the loss from the model on the validation set
- In the validation stage, backpropogation was not done and weights were left unaffected
- A per epoch analysis was provided to give an idea of how the loss changes given the training process, this analysis was then shown in a visualisation

### Test Data
- The final stage outputs the loss on the test data. This indicates how well the model performs on unseen data and is the best measure of generalisation

## Additional Features

### Changing Activation Functions
- Parameters were added to the method in the model class to allow the user to change the activation function used.

### Testing multiple Activation Functions
- A final section of code was added to compare the per epoch training loss of the model when using different activation functions and display this on a graph.
- This was ultimately added for the purpose of experimentating in the report, however, it can be adjusted to include more activation functions, and also print out test losses if required.

## Using the Program

### Adjusting parameters

#### Activation functions
- Can be changed in the NNModel class
- There are two times activation functions are used, inbetween the input and first hidden layer, and inbetween the two hidden layers
- Any activiation function can be used inbetween either. Adjusting these is a great way to find which combination works best at computing the most accurate model

#### Learning rate, Number of epochs and Batch Size
- All can be easily changed by chnaging their respective global variables

#### Loss function and Optimizer
- Both can be changed by adjusting the function called in the criterion and optimizer variable initialisation
- Changing the loss function will not change the model's performance, but instead how it's performance is measured

### Execution

#### How to Execute
- The program should be run using a GPU
- This can be done using Colab, which the code is designed to work with
- Simply change the runtime type to GPU before running

#### Output of execution
- The first output will be the visualisation of the expected data
- Next the per-epoch training and validation loss
- Then the visualisation of these losses
- Finally, the testing loss
- Any of these outputs can be code commented to remove them from the output flow


  
