# Energy Efficient Comparative Synapses in a Versatile Tiny Model:  (C)DVTINY 
This model expands the 2022 C_CNN model [1], employing comparative synapses first proposed in 1999 [2], long before AdderNet [3] ( Comparative synapse: syn(x,w)=|x+w|-|x-w| = 2*min(x,w) vs. Adder Net syn(x,w)= -|x-w|) 

Several comparative-synapse layers are defined as custom Keras-3 layers and used in (C)DVTINY, a versatile CNN architecture designed for TinyML. Replacing classic (multiplicative) synapses with min(x,w) type ones (comparative) can help to reduce significantly the energy consumption when replacing multipliers with comparisons. Demo code for defining and traing models is available as a Jupyter notebook (tested under Google COLAB [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/comp-dvtiny-v1-1.ipynb) or Kaggle; GPU, (or TPU) is required - training comparative synapses is generally slow. Several [pretrained models are available](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/tree/main/trained_models); one may evaluate and use them: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/eval-comparative-models.ipynb.ipynb)

Some papers describing this research in more details will be released soon. In the meantime, if you find this repository useful, please feel free to star it or cite [our base approach](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/CITATION.cff)  

References 
[1] https://ieeexplore.ieee.org/document/9817267 published 2022
[2] https://ieeexplore.ieee.org/document/802828 published 1999
[3] https://ieeexplore.ieee.org/document/9156624 published 2020

SOME RESULTS 
Model DVTINY_N_1_d_0.3_(1, 4, 6)_k_16_nl(0, 0, 0)_hid_0
Using various synapse types in both convolutional and dense layers

CIFAR10 results (81k parameters /  6453k MAC or MiAC or SAC) 
Note: MAC - Multiply and Accumulate; MiAC = Min and Accumulate; SAC - Subtract and Accumulate 

|Synapse type | Val. Accuracy (%)| .keras model | 
| :---: | :---: | :---: |
| comp (L1) | 79.42 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_CL_cifar10%20Sz_32%20Bt_128%20Lrate_%200.00128%20Ep_600%20Tep_14%20Kpar_81.0kMAC-1.0%20Vacc_79.42%20TrAcc_79ValData_Val_acc_79.42%20Lat_0.28.keras) |
| multiplier | 79.7 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_Mm_cifar10%20Sz_32%20Bt_128%20Lrate_%200.00128%20Ep_400%20Tep_1.2%20Kpar_80.48kMAC-1.0%20Vacc_79.74%20TrAcc_79.35ValData_Val_acc_79.7.keras) |
| AdderNet | 76.91 | |


Fashion-MNIST results (80.2k parameters / 4721k MAC or MiAC or SAC) 

|Synapse type | Val. Accuracy (%)| .keras model | 
| :---: | :---: | :---: |
| comp (L1) | 92.44 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_CL_f-mnist%20Sz_28%20Bt_128%20Lrate_%200.00128%20Ep_200%20Tep_12.4%20Kpar_80.72kMAC-1.0%20Vacc_92.44%20TrAcc_91.89ValData_Val_acc_92.44%20Lat_0.21.keras) |
| multiplier | 92.09 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_Mm_f-mnist%20Sz_28%20Bt_128%20Lrate_%200.00128%20Ep_200%20Tep_1.6%20Kpar_80.2kMAC-1.0%20Vacc_92.09%20TrAcc_91.92ValData_Val_acc_92.09%20Lat_0.12.keras) |
| AdderNet | t.b.c. | |


SVHN results ( k parameters / k MAC or MiAC or SAC) 

|Synapse type | Val. Accuracy (%)| .keras model | 
| :---: | :---: | :---: |
| comp (L1) | 93.09 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_CL_svhn_n%20Sz_32%20Bt_128%20Lrate_%200.00192%20Ep_200%20Tep_19.8%20Kpar_81.0kMAC-1.0%20Vacc_93.09%20TrAcc_90.41ValData_Val_acc_93.09%20Lat_0.keras) |
| multiplier | 93.35 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_Mm_svhn_n%20Sz_32%20Bt_128%20Lrate_%200.00128%20Ep_200%20Tep_2.5%20Kpar_80.48kMAC-1.0%20Vacc_93.35%20TrAcc_90.08ValData_Val_acc_93.35%20Lat_0.07.keras) | 
| AdderNet | t.b.c. | |

MNIST results ( 80.2 k parameters / 4721k MAC or MiAC or SAC) 

|Synapse type | Val. Accuracy (%)| .keras model | 
| :---: | :---: | :---: |
| comp (L1) | 99.5 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_CL_mnist%20Sz_28%20Bt_128%20Lrate_%200.00192%20Ep_200%20Tep_12.5%20Kpar_80.72kMAC-1.0%20Vacc_99.5%20TrAcc_99.52ValData_Val_acc_99.5%20Lat_0.24.keras) |
| multiplier | 99.56 | [***](https://github.com/radu-dogaru/comparative-synapse-in-dvtiny-model/blob/main/trained_models/GPU_DVTINY_N_1_d_0.3_(1%2C%204%2C%206)_k_16_nl(0%2C%200%2C%200)_hid_0Sy_Mm_mnist%20Sz_28%20Bt_128%20Lrate_%200.00064%20Ep_200%20Tep_1.4%20Kpar_80.2kMAC-1.0%20Vacc_99.56%20TrAcc_99.7ValData_Val_.keras) | 
| AdderNet | t.b.c. | |






