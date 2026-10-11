# Energy Efficient Comparative Synapses in a Versatile Tiny Model"  (C)DVTINY 
This model expands the 2022 C_CNN model [1], employing comparative synapses first proposed in 1999 [2], long before AdderNet [3] ( comparative synapse: |x+w|-|x-w| = min(x,w) vs. adder net -|x-w| ) 

Several comparative-synapse layers are defined as custom Keras-3 layers and used in (C)DVTINY, a versatile CNN architecture designed for TinyML. Replacing classic (multiplicative) synapses with min(x,w) type ones (comparative) can help to reduce significantly the energy consumption when replacing multipliers with comparisons. Demo code for defining and traing models is available as notebook.   

"A formal paper describing this research will be released soon. In the meantime, if you find this repository useful, please feel free to star it or cite our base approach [insert citation/link]."

References 
[1] https://ieeexplore.ieee.org/document/9817267 published 2022

[2] https://ieeexplore.ieee.org/document/802828 published 1999

[3] https://ieeexplore.ieee.org/document/9156624 published 2020

