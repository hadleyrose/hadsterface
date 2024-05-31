# hadsterface
## README in PROGRESS
Misc LLM notebooks

## Project Setup

<sup>The below setup assumes working from a **Bash** terminal</sup>

1. Clone project repository
`git clone https://github.com/hadleyrose/hadsterface.git`
1. From project directory, create virtual environment
`python3 -m venv .venv`
1. Activate environment
`source .venv/bin/activate`
1. Pip install packages
`python3 -m pip install pandas huggingface sentence-transformers jupyter ipykernel transformers langchain matplotlib openpyxl datasets`
1. ***--OR--*** Recreate environment from `requirements.txt`
`pip TK`
1. Start up Jupyter Lab
`jupyter lab`

## Troubleshooting
1. `The file '.venv/lib/python3.12/site-packages/psutil/_psutil_osx.abi3.so, 0x0002' seems to be overriding built in modules and interfering with the startup of the kernel. Consider renaming the file and starting the kernel again.`
    > Solution: [Circular import results from having two dependencies: jupyter-ai and jupyterlab - how to debug?](https://github.com/jupyterlab/jupyter-ai/issues/782) - psutil package doesn't behave properly with Apple M processors

    > `pip uninstall psutil && pip install --no-binary :all: psutil`
1. `psutil/arch/osx/cpu.c:30:10: fatal error: 'CoreFoundation/CoreFoundation.h' file not found`

        psutil/arch/osx/cpu.c:30:10: fatal error: 'CoreFoundation/CoreFoundation.h' file not found`
            #include <CoreFoundation/CoreFoundation.h>
                    ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
            1 error generated.
            XCode (https://developer.apple.com/xcode/) is not installed
            error: command '/usr/bin/clang' failed with exit code 1
            [end of output]
        
        note: This error originates from a subprocess, and is likely not a problem with pip.
        ERROR: Failed building wheel for psutil
        Failed to build psutil

    > Solution: In error, note the line `XCode is not installed`

    > Install XCode via https://developer.apple.com/xcode/, **NOT** via App Store, **AND** agree to XCode license agreements
1. `(mach-o file, but is an incompatible architecture (have 'arm64', need 'x86_64'))`
    
        ImportError: dlopen(/Volumes/G-DRIVE ArmorATD/hadsterface/.venv/lib/python3.12/site-packages/numpy/core/_multiarray_umath.cpython-312-darwin.so, 0x0002): tried: '/Volumes/G-DRIVE ArmorATD/hadsterface/.venv/lib/python3.12/site-packages/numpy/core/_multiarray_umath.cpython-312-darwin.so' (mach-o file, but is an incompatible architecture (have 'arm64', need 'x86_64')), '/System/Volumes/Preboot/Cryptexes/OS/Volumes/G-DRIVE ArmorATD/hadsterface/.venv/lib/python3.12/site-packages/numpy/core/_multiarray_umath.cpython-312-darwin.so' (no such file), '/Volumes/G-DRIVE ArmorATD/hadsterface/.venv/lib/python3.12/site-packages/numpy/core/_multiarray_umath.cpython-312-darwin.so' (mach-o file, but is an incompatible architecture (have 'arm64', need 'x86_64'))

        During handling of the above exception, another exception occurred:

        ImportError                               Traceback (most recent call last)
        File /Volumes/G-DRIVE ArmorATD/hadsterface/.venv/lib/python3.12/site-packages/numpy/__init__.py:130
            129 try:
        ...
            141 # mapping of {name: (value, deprecation_msg)}

        ImportError: Error importing numpy: you should not try to import numpy from
                its source directory; please exit the numpy source tree, and relaunch
                your python interpreter from there.

    > Solution: This error is encountered when running ragged.ipynb in VS Code emulation for Mac. Install the latest [VS Code *for* Mac](https://code.visualstudio.com/download) or [follow guidance here](https://stackoverflow.com/a/74918089)