
# Maximizing single-qubit gate fidelity by optimizing pulse parameters

This project focuses on optimizing the pulse width for maximum single-qubit X-gate using Qiskit Dynamics. The notebook optimizing-gate-fidelity.ipynb contains the script for the task.

## Installation
First clone the repository:
```
git clone https://github.com/vilmanieminen/single-qubit-gate-optimization.git
cd single-qubit-gate-optimization
```

Optionally, create a virtual environment:
```
python -m venv venv_name
source venv_name/bin/activate 
# or on Windows:
source venv_name\Scripts\activate
```

Then, install the necessary dependencies using the requirements file:
```
pip install -r requirements.txt
```


## Reflection

The task was very different compared to ones I've done before, so I really liked the challenge.

Doing the project thaugth me the basics of simulating a pulse acting on a very simple qubit model. I tried to familiarize myself with the theory before doing the simulation, but it took me a while to understand each step of the simulation process. I enjoyed realizing while I was improving the code what each part of it was doing exactly, and I think I have good understanding now of the basics of each step and why they are done. I also learned a lot about the theory of quantum circuits and qubit control from the given references, that I could connect with information I had learned in my classes.

I am most interested in the problem about the theory behind it and how to further advance into simulating realistic qubit models. For example, 
    - How would a more complicated Hamiltonian be solved and what kind of minimization methods / approximations would it require?
    - How would adding noise change the process
    - How would this be implemented on a real quantum computer

### Challenges:

The task was sligthly challenging because I had troubles with using JAX together with qiskit.pulse, as qiskit.pulse is not JAX compatible. I was able to get the script to work by only using JAX in the Hamiltonian solver and using NumPy and SciPy when optimizing. 

Another big challenge is the 'BFGS' method in the minimization:
    - When I use large sigma as an input, the optimized width is almost exactly the same as the intial width and the function is evaluated only few times, but the fidelity is high
    - When I use a small sigma, the evaluation is done tens of times, but the fidelity stays very low. 
I wasn't able to fix the problem in a reasonable time, but from the quick read it seem to be a common challenge with gradient based optimizers. The optimization works better for the Nelder-Mead method.

I started by following the tutorials one to one and then tried to modify the code as step 5 was asking, but was not able to figure out a good way to implement different waveforms in the recommended time limit. I would be curios to learn how that can be implemented as I can only think of if - else statements.


As next steps towards more realistic optimization of the qubit performance with respect to the pulse, I would investigate adding noise and decoherence, which were not included in this model as a realistic qubit would be coupled to its environment. I would also research better initialization parameters by running larger test and researching realistic initial values.





