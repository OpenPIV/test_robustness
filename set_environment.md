# How do I set environment for the test

1. Install Anaconda
2. Follow the following 

* on Linux `pip install numpy` pulls 1.19.4 that was somewhere mentioned to create bugs with openpiv
* note that in the example the `master` should be replaced with `remove_capping` or `normalized_correlation` or if the previous version needed, use
`pip install openpiv==0.22.3`
* use `nb_conda` to be sure that the kernel you load in Jupyter is `test_robustness`. @alexlib I find this point sometimes confusing. 
* we also install `watermark` to keep the info about the setup in the Jupyter notebook, read here https://github.com/rasbt/watermark


```
  conda create -n test_robustness python=3.8
  conda activate test_robustness
  conda install numpy
  pip install -e git+https://github.com/openpiv/openpiv-python@master#egg=openpiv-python
  conda install jupyterlab
  conda install nb_conda 
  pip install watermark
  jupyter lab
```

3. In the Jupyter notebook always start with: 
```
    # %load_ext watermark # if it's a first time
    %reload_ext watermark # else
    %watermark -v -m -p numpy,openpiv -g -b
```


