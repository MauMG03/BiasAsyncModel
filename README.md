# Incorporating congnitive biases in an asynchronous opinion model
### a python script for testing and general toying

This repository have an implementation of an asynchrnous opinion model with cognitive biases. The code is based on a previous implementation of an asyncrhonous opinion model.

The new model is implemented in [BiasedInfluenceGraph.py](BiasedInfluenceGraph.py), where the update function is:

$B_{t+1}\[j\] = B_{t}\[j\] + \beta_{ji}(B_{t}\[i\] - B_{t}\[j\])I_{ij}$

Where $\beta_{ji}: \[-1,1\] \to \[-1,1\]$ is the bias function stating how the bias of $j$ towards the opinion of $i$, $\beta_{ji}$, affects $j$'s new opinion. 

## Fairness and Consensus in Opinion Models
#### A python script for generating article plots and general toying

The  clases [InfluenceGraph.py](InfluenceGraph.py) and [WordGenerator.py](WordGenerator.py) are based on the libraries `networkx` for graph handling and `matplotlib` for plotting.