<h1>ft_linear_regression</h1>

<h3>ft_linear_regression is one of the project of 42-network here the <a href='https://cdn.intra.42.fr/pdf/pdf/102546/en.subject.pdf'>Subject</a></h3>

<h3>The aim of this project is to introduce you to the basic concept behind machine learning.
For this project, you will have to create a program that predicts the price of a car by
using a linear function train with a gradient descent algorithm.</h3>

---

<h1>Project Overview</h1>

<h2>Data</h2>

### Sample from `data.csv`

| km     | price |
|--------|-------|
| 240000 | 3650  |
| 139800 | 3800  |
| 150500 | 4400  |
| 185530 | 4450  |
| 176000 | 5250  |
| 114800 | 5350  |
| 166800 | 5800  |
| 89000  | 5990  |
| 144500 | 5999  |
| 84000  | 6200  |

#### The column `km` represents the kilometers driven by the car.  
#### The column `price` is the selling price of the car.


<h2>Code Steps</h2>

- ### Data Preprocessing

  - #### load data from csv file
    ```python
    import pandas as pd

    dfile_name = "data.csv"
    data_csv = pd.read_csv(file_name)
    ```
  - #### Split the data into input X and output or target Y
    ```python
    import numpy as np

     X = np.array(data_csv["km"]).reshape(-1,1)
     Y = np.array(data_csv["price"]).reshape(-1,1)
    ```
  - #### Split the input X and the target Y to trainin and validation sets
    ```python
    from sklearn.model_selection import train_test_split


    # Train Val Split
    X_train, X_val, Y_train, Y_val = train_test_split(X,Y, test_size=0.2, random_state=88)

    ```
    - <h5>80% of data for training and keep 20% for testing</h5>
    - <h5>We fix the `random_state` to 88 to ensure reproducibility. It controls how the data is shuffled before splitting.</h5>


  - #### Scaling data by using MinMaxScaler method that transform data to a range between 0 and 1
    ```python
    from sklearn.preprocessing import MinMaxScaler
    
    # Scaling
    scaler_X = MinMaxScaler().fit(X_train)
    X_train = scaler_X.transform(X_train)
    X_val = scaler_X.transform(X_val)
    ```
    this steap help learning rate to control the jumps of gradient descent also avoid large numbers

---

- ### Trianing with <a href=''>Gradient Descent</a> algorithm</h4>
  - #### Create Gadient Descent Model
    - ##### to discover theore behinde gradient descent check this [Document](../README.md)
---
- ### Visualizing to see if our model undestand the data or not</h4>

  - #### use matplotlib.pyplot library to show the actual points and our model prediction</h5>


---
- ### Save the wights in a file.csv to predict the price of a car for a new given mileage</h4>

