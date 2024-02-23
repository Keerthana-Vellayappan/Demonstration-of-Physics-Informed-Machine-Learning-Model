# Demonstration of Physics Informed Machine Learning Model

# 1. CSTR PIRNN Example

Let us consider a second-order, exothermic, irreversible reaction from A to B

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/c1337cf1-eb78-47d7-b95b-1ce399d0ad10)


The First Principle equation for this system is as follows:

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/da9e944b-1b0c-4694-8b48-2a21f49d55ed)

Where,
𝐶_𝐴: Concentration of reactant A 
𝑇: Temperature of the reactor 
𝐶_𝐴0: Concentration of reactant A in the feed 
 𝑄 :  Heat input rate 
F: feed volumetric flow rate
𝑇0: Inlet temperature

The State and Manipulated variable for this system is:
States variables: 𝐱=[〖𝐶_𝐴−𝐶〗_𝐴𝑠,𝑇 −𝑇_𝑠 ]
Control / Manipulated variables: 𝐮=[〖𝐶_𝐴0−𝐶〗_𝐴0𝑠,𝑄 −𝑄_𝑠 ]

The generated dataset with the input and output will look like:

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/f41bd653-cb8d-43de-950e-71946ddc79d8)

The above data is for a dataset with n samples with 6 internal time-steps for each sample.

# 2. PFR PIRNN Example

Let us consider a first-order, exothermic, irreversible reaction from A to B

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/fdbbc632-3288-45b9-81be-034ecb42bf4a)


The First Principle equation for this system is as follows:

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/e34d27cd-885b-4950-b6e9-37a38b8d0254)

Where,
𝐶_𝐴: Concentration of reactant A (kmol/m3)
𝑇: Temperature of the reactor (K)
U :  Overall heat transfer coefficient (kcal /m2 min K)
u: superficial velocity (m/min)
𝑇_𝑐: Cooling liquid temperature (K)

The State and Manipulated variable for this system is:
States variables: 𝐱=[𝐶𝐴,   𝑇]
Control / Manipulated variables: 𝐮=[𝑇_𝑐−〖𝑇_𝑐〗_𝑠 ]

The generated dataset with the input and output will look like:

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/2e739dd2-a2e0-4cfb-a841-983dd760df9a)

The above data is for a dataset with n samples with 6 internal time-steps for each sample with the Plug Flow Reactor length discretized into 10 points.

# 3. Principle for Physics-Informed Loss

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/4f5b19db-09df-4547-9872-a58f16aa458f)


The ODE is explicitly embedded in the loss function and is calculated based on the RNN predicted states, where the derivative (LHS) is approximated using the finite difference method. 
The RHS of the ODE is computed by substituting the PIRNN predicted states and the manipulated inputs into the first principle equation.
The physics informed loss is the error between the LHS and RHS of the ODE using the PIRNN predicted results and is incorporated during model training. 

# 4. Recurrent Neural Network (RNN) Structure

RNN are a class of neural networks that is powerful for modeling sequence data such as time series data.
It can handle sequential data and account for past information in the current prediction.

The RNN model input and output are as follows:
Input: System initial state variable 𝐱_𝟎 〖(𝑡〗_𝑘), and control variables 𝐮〖(𝑡〗_𝑘).
Output: Future state dynamics 𝐱〖(𝑡〗_𝑘+Δ) are predicted for one sampling period ∆.

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/332a1da6-9b89-4e04-a6b3-1b5c90185319)

# Libraries and Tools used
[PyTorch](https://pytorch.org/): Deep learning framework used for building and training neural networks.

[Matplotlib](https://matplotlib.org/): Python plotting library for creating visualizations.

[SciPy](https://www.scipy.org/): Open-source library used for scientific and technical computing.

[scikit-learn](https://scikit-learn.org/): Machine learning library for Python used for data analysis and modeling.

[similaritymeasures](https://github.com/similaritymeasures/similaritymeasures): Python library for computing similarity measures between curves or time series data.



