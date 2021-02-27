# Code and resources for Lorenz et al. (2021) QNLP paper

This repository holds the code and the datasets for the paper:

- Lorenz, Pearson, Meichanetzidis, Kartsaklis, Coecke (2021). *QNLP in Practice: Running Compositional Models of Meaning on a Quantum Computer*, [arXiv:2102.12846 \[cs.CL\]](https://arxiv.org/abs/2102.12846)

 The paper presents results on the first  NLP experiments conducted on Noisy Intermediate-Scale Quantum (NISQ) computers for datasets of size >= 100 sentences. Exploiting the formal similarity of the compositional model of meaning by Coecke et al. (2010) with quantum theory, we create representations for sentences that have a natural mapping to quantum circuits. We use these representations to implement and successfully train two NLP models that solve simple sentence classification tasks on quantum hardware. We describe in detail the main principles, the process and challenges of these experiments, in a way accessible to NLP researchers, thus paving the way for practical Quantum Natural Language Processing.

## Code requirements

For running the code, you will need Python 3.x. Further, the following packages must also be installed:

* `discopy` (v0.3.4)
* `pytket` (v0.7.2)
* `qiskit`  (v0.23.6)


## Instructions

The two notebooks `mc_task.ipynb` and `rp_task.ipynb` in the folder `code` show, in an exemplary way, the implementation of the pipeline for the two binary classification tasks, MC and RP, respectively. See Sec. 5 of the paper for the general pipeline, Sec. 6 for a description of the tasks and Sec. 7 for an explanation of this implementation in the notebooks. 

The folder `datasets` contains the raw data as `txt` files, as well as, two respective pickle files which are the input read by the notebooks, and which contain the data partitioned into train, dev and test subsets. 

The following applies to both notebooks. Any settings one may want to alter as aprt of the implementation, such as the choice of 'ansatz' or the hardware on which it is computed, are all done in the first cell as explained therein. Note that by default `backend = AerBackend()` envokes a simulator provided through `pytket`, which does not require any IBMQ account. Provided access to an IBMQ account, the user may use the corresponding commented-out lines in the first cell to set the backend to a device-specific one instead. This may be through `IBMQEmulatorBackend(<backend_name>, <credentials>)`, which provides a simulator that has a device-specific noise model, or through `IBMQBackend(<backend_name>, <credentials>)`, in order to compute on actual IBM quantum hardware of one's choice. 

## Remarks

- The notebooks implement the quantum runs (see Sec. 7.4 of the paper). If needed, code that implements the classical calculations (Sec.7.3) may be obtained upon request. 

- It is worth emphasising that the fluctuations in the RP task are considerable and that a user is recommended to do several runs to get an impression for the variances. 

## Links

For further help see: 

* for `discopy`: https://discopy.readthedocs.io/en/main/index.html
* for `pytket`: https://cqcl.github.io/pytket/build/html/index.html
* for `qiskit`: https://qiskit.org/documentation/

