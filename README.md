# Demonstration of Physics Informed Machine Learning Model

## 1. Continuous Stirred Tank Reactor (CSTR) Example

- Let us consider a second-order, exothermic, irreversible reaction from A to B


<img src="https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/c1337cf1-eb78-47d7-b95b-1ce399d0ad10" alt = " Figure: Schematic diagram of a CSTR" width="250" height="250">



- The First Principle equation for this system are as follows:


     <img src="https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/da9e944b-1b0c-4694-8b48-2a21f49d55ed" width="300" height="90">



- Where,

   - 𝐶_𝐴: Concentration of reactant A (kmol/m3)
   - 𝑇: Temperature of the reactor (K)
   - 𝐶_𝐴0: Concentration of reactant A in the feed
   - 𝑄 :  Heat input rate (kJ/h)
   - F: feed volumetric flow rate (m3/h)
   - 𝑇0: Inlet temperature (K)


- The State and Manipulated variable for this system is:

    - States variables: 𝐱=[𝐶_𝐴−𝐶_𝐴𝑠, 𝑇 −𝑇_𝑠 ]
    - Control / Manipulated variables: 𝐮=[𝐶_𝐴0−𝐶_𝐴0𝑠, 𝑄 −𝑄_𝑠 ]


- The generated dataset with the input and output will look like:

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/f41bd653-cb8d-43de-950e-71946ddc79d8)

- The above data sample is for a dataset with n samples with 6 internal time-steps for each sample.

- The code for demonstrating the PIRNN model for the CSTR is available [here](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/blob/main/CSTR%20PI-RNN%20Example.ipynb)

## 2. Plug Flow Reactor (PFR) Example

- Let us consider a first-order, exothermic, irreversible reaction from A to B


<img src="https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/fdbbc632-3288-45b9-81be-034ecb42bf4a" alt = " Figure: Schematic diagram of a PFR" width="500" height="200">

- The First Principle equation for this system is as follows:


    <img src="https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/e34d27cd-885b-4950-b6e9-37a38b8d0254" width="320" height="100">

- Where,

   - 𝐶_𝐴: Concentration of reactant A (kmol/m3)
   - 𝑇: Temperature of the reactor (K)
   - U :  Overall heat transfer coefficient (kcal /m2 min K)
   - u: superficial velocity (m/min)
   - 𝑇_𝑐: Cooling liquid temperature (K)


- The State and Manipulated variable for this system is:

     - States variables: 𝐱=[𝐶𝐴, 𝑇]
     - Control / Manipulated variables: 𝐮=[𝑇_𝑐−𝑇_𝑐_𝑠]


- The generated dataset with the input and output will look like:

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/2e739dd2-a2e0-4cfb-a841-983dd760df9a)

- The above data is for a dataset with n samples with 6 internal time-steps for each sample with the Plug Flow Reactor length discretized into 10 points.

- The code for demonstrating PIRNN model for a PFR is available [here](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/blob/main/PFR%20PI-RNN%20Example.ipynb)

## 3. Principle for Physics-Informed Loss

<p align="center">

<img src="https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/4f5b19db-09df-4547-9872-a58f16aa458f" alt = " Figure: Schematic diagram of PIRNN model" width="600" height="300">

</p>

- The ODE is explicitly embedded in the loss function and is calculated based on the RNN predicted states, where the derivative (LHS) is approximated using the finite difference method.
- The RHS of the ODE is computed by substituting the PIRNN predicted states and the manipulated inputs into the first principle equation.
- The physics informed loss is the error between the LHS and RHS of the ODE using the PIRNN predicted results and is incorporated during model training. 

## 4. Recurrent Neural Network (RNN) Structure

- RNN are a class of neural networks that is powerful for modeling sequence data such as time series data.
- It can handle sequential data and account for past information in the current prediction.

- The RNN model input and output are as follows:
    - Input: System initial state variable 𝐱_𝟎(𝑡_𝑘), and control variables 𝐮(𝑡_𝑘).
    - Output: Future state dynamics 𝐱(𝑡_𝑘+Δ) are predicted for one sampling period ∆.
<p align="center">
<img src="https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/332a1da6-9b89-4e04-a6b3-1b5c90185319" width="600" height="250">
</p>


## 5. Libraries and Tools used

[PyTorch](https://pytorch.org/): Deep learning framework used for building and training neural networks.

[Matplotlib](https://matplotlib.org/): Python plotting library for creating visualizations.

[SciPy](https://www.scipy.org/): Open-source library used for scientific and technical computing.

[scikit-learn](https://scikit-learn.org/): Machine learning library for Python used for data analysis and modeling.

[similaritymeasures](https://github.com/similaritymeasures/similaritymeasures): Python library for computing similarity measures between curves or time series data.


## 6. Citation

The demonstration of these examples are adapted from the following literature work:

Zheng, Yingzhe, Cheng Hu, Xiaonan Wang, and Zhe Wu. "Physics-informed recurrent neural network modeling for predictive control of nonlinear processes." Journal of Process Control 128 (2023): 103005.

Additionally, you can find our paper [here](https://www.sciencedirect.com/science/article/pii/S0959152423000847)



