# MMASTER-workflows

This repository hosts the workflows for the MMASTER procesing methods of ASTER-L1A stereo imagery. The method itself is documented in [Girod et al, 2017, http://dx.doi.org/10.3390/rs9070704 ]

Documentation on readthe docs : https://mmaster-workflows.readthedocs.io/en/latest/index.html

Revised Installation Instructions.
MicMac and PyMMaster can now be installed in the same conda environment as follows. For actual usage consult the readthedocs above.

Create the conda environment, this may take a few minutes to solve.

```
conda env create -f mmaster-environment.yml
```

Activate the new environment and install micmac.

```
conda activate mmaster_environment
git clone https://github.com/micmacIGN/micmac.git
cd micmac
git fetch
git checkout IncludeALGLIB
mkdir build
cd build
LIBRARY_PATH=""
cmake .. -DWITH=QT%=1 -DWITH_CPP11=1 -DOpenGL_GL_PREFERENCE=LEGACY -DWERROR=0 -DWITH_CCACHE=OFF
LIBRARY_PATH=""
make install -j32
```

This should install micmac in the environment. To check it has installed correctly and can access all dependencies you can run `mm3d CheckDependencies`. Which should list the location of all dependencies as in the environment path.

Then we want to add pymmaster to the environment. Return to the cloned pymmaster repository and run:

```
pip install -e MMASTER-workflows
```

To check this has worked run`mmaster_bias_correction.py -h` which should produce the helpfile for mmaster_bias_correction.py.
