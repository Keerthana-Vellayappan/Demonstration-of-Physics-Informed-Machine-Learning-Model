# Demonstration-of-Physics-Informed-Machine-Learning-Model

# 1. CSTR PIRNN Example

Let us consider a second-order, exothermic, irreversible reaction from A to B

![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/c1337cf1-eb78-47d7-b95b-1ce399d0ad10)


The First Principle equation for this system is as follows:

(𝑑𝐶_𝐴)/𝑑𝑡=𝐹/𝑉 (𝐶_𝐴0−𝐶_𝐴 )−𝑘_0 𝑒^((−𝐸)/𝑅𝑇) 〖𝐶_𝐴〗^2
𝑑𝑇/𝑑𝑡=𝐹/𝑉 (𝑇_0−𝑇)+(−𝛥𝐻)/(𝜌_𝐿 𝐶_𝑃 ) 𝑘_0 𝑒^((−𝐸)/𝑅𝑇) 〖𝐶_𝐴〗^2+𝑄/(𝜌_𝐿 𝐶_𝑃 𝑉)![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/da9e944b-1b0c-4694-8b48-2a21f49d55ed)

Where,
𝐶_𝐴: Concentration of reactant A 
𝑇: Temperature of the reactor 
𝐶_𝐴0: Concentration of reactant A in the feed 
 𝑄 :  Heat input rate 
F: feed volumetric flow rate
𝑇0: Inlet temperature
![image](https://github.com/Keerthana-Vellayappan/Demonstration-of-Physics-Informed-Machine-Learning-Model/assets/160836399/326533d7-df71-4c60-909f-b4b0dc7f58d8)

