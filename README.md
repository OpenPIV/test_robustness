# Test robustness of an algorithm
This repository will include Jupyter notebooks that compare robustness of the OpenPIV algorithms

The need is due to the issue https://github.com/OpenPIV/openpiv-python/issues/162 after the update to ver 0.23.0 (see release https://github.com/OpenPIV/openpiv-python/releases/tag/0.23.0) 

The algorithms have not changed substantially, we basically moved the algorithm used in `windef.py` to the `pyprocess.py`. The differences are due to 
the change in the decision of what defines the final grid, the `search_area_size` or `window_size`, i.e. the interrogation window in frame A or in frame B 
if the last one is larger (what is called extended search). So now the window in frame B is always symmetric around window in frame A, thus we do not introduce bias at the edges of the images. 

Additional change is the intensity capping that is easy to remove, but to do so wisely (there is also a pending pull request of `normalized_correlation` see https://github.com/OpenPIV/openpiv-python/tree/normalized_correlation) but this one maybe more robust but fails some tests. Without understanding the reason, we might find ourselves in another bug issue. 

## What to do:
1. Create Jupyter notebook that reads the data, installs the right version of openpiv-python and runs all the tests
2. Create notebook per set of data that @ErichZimmer suggested: 
```

    To Reproduce
    Note: The GUI used and windef script (executed in jupyter) had the same results
    settings used:

    first PIV Challenge (2001) case A:
    link to image set
    preprocessing: None
    correlation: FFT, no padding
    search area: None
    windowing: 64>32>16
    overlap: 32>16>8 (50%)
    validation: "disabled" by large values
    outlier replacement iteration: 5
    outlier replacement kernel: 2

    first PIV Challenge (2001) case B:
    link to image set
    preprocessing: None
    correlation: FFT, no padding
    search area: None
    windowing: 64>32>16
    overlap: 32>16>8 (50%)
    validation: "disabled" by large values
    outlier replacement iteration: 5
    outlier replacement kernel: 2

    OpenPIV python test 4
    preprocessing: None
    correlation: FFT, no padding
    search area: None
    windowing: 64>32>16
    overlap: 32>16>8 (50%)
    validation: "disabled" by large values
    outlier replacement iteration: 5
    outlier replacement kernel: 2
```

