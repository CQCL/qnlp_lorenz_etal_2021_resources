# Code and resources for Lorenz et al. "QNLP in Practice" paper

This repository holds the code and the datasets for the paper:

- Lorenz, Pearson, Meichanetzidis, Kartsaklis, Coecke (2023). *QNLP in Practice: Running Compositional Models of Meaning on a Quantum Computer*, Journal of Artificial Intelligence Research, Vol. 76 [\[pdf\]](https://dl.acm.org/doi/pdf/10.1613/jair.1.14329)

The paper presents results on the first  NLP experiments conducted on Noisy Intermediate-Scale Quantum (NISQ) computers for datasets of size >= 100 sentences. Exploiting the formal similarity of the compositional model of meaning by Coecke et al. (2010) with quantum theory, we create representations for sentences that have a natural mapping to quantum circuits. We use these representations to implement and successfully train two NLP models that solve simple sentence classification tasks on quantum hardware. We describe in detail the main principles, the process and challenges of these experiments, in a way accessible to NLP researchers, thus paving the way for practical Quantum Natural Language Processing.

> **Note**\
> Although the code in this repository is functional and may still serve as a useful resource, as of May 2023 we would strongly encourage users to install the open source QNLP package [lambeq](https://cqcl.github.io/lambeq/index.html), which offers more up-to-date functionality and features and greatly simplifies experiments similar to the ones described in the paper. In fact, in lambeq's [training tutorials](https://cqcl.github.io/lambeq/training.html) you can find implementations of the same MC and RP experiments performed in the paper that are much more intuitive and accessible compared to the notebooks of this repository. You can install lambeq by typing ``pip install lambeq``.

## Code requirements

For running the code, you will need Python 3.7 or later. Further, the following packages must also be installed:

* `discopy` (v0.3.5)
* `pytket` (v0.10.1)
* `qiskit`  (v0.25.4)
* `pytket-qiskit`

## Instructions

The two notebooks `mc_task.ipynb` and `rp_task.ipynb`, in the folder `code` show, in an exemplary way, the implementation of the pipeline for the two binary classification tasks, MC and RP, respectively. See Sec. 5 of the paper for the general pipeline, Sec. 6 for a description of the tasks and Sec. 7 for an explanation of this implementation in the notebooks, specifically Sec. 7.4 for the implementation of the quantum runs in these two notebooks. The analogous implementations of the classcial simulations for the MC and RP task as described in Sec. 7.3 of the paper can be found in the two notebooks `mc_task_simulation.ipynb` and `rp_task_simulation.ipynb`, respectively. 

The folder `datasets` contains the raw data (train, dev and test subsets, respectively) as `txt` files, which are the input read by the notebooks.

In all 4 mentioned notebooks any settings one may want to alter as part of the implementation, such as the choice of 'ansatz', are all done in the first cell as explained therein. For the two notebooks `mc_task.ipynb` and `rp_task.ipynb` concerning the quantum runs the first cell in addition allows to choose the hardware on which to run the computation. Note that by default `backend = AerBackend()` envokes a simulator provided through `pytket`, which does not require any IBMQ account. Provided access to an IBMQ account, the user may use the corresponding commented-out lines in the first cell to set the backend to a device-specific one instead. This may be through `IBMQEmulatorBackend(<backend_name>, <credentials>)`, which provides a simulator that has a device-specific noise model, or through `IBMQBackend(<backend_name>, <credentials>)`, in order to compute on actual IBM quantum hardware of one's choice. 

Finally, running the notebook `mc_task_simulation.ipynb` or `rp_task_simulation.ipynb` requires making `discopy` compatible with `jax` by setting `IMPORT_JAX = True` in discopy's `config.py`. 

## Remarks

- It is worth emphasising that the fluctuations in the RP task are considerable and that a user is recommended to do several runs to get an impression for the variances. 

## Links

For further help see: 

* for `discopy`: https://discopy.readthedocs.io/en/main/index.html
* for `pytket`: https://cqcl.github.io/pytket/build/html/index.html
* for `qiskit`: https://qiskit.org/documentation/
* for `lambeq`: https://cqcl.github.io/lambeq/index.html

