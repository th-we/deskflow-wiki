### Linux compile guide
1. Open terminal of your choice
1. Navigate to the synergy-core dir you cloned
    1. `cd synergy-core`
1. Create a build dir
    1. `mkdir build && cd build`
1. You may need to tell cmake where Qt is located (Normally not required if you used a package to install Qt)
    1. `export CMAKE_PREFIX_PATH={you Qt install location}`
    1. The Qt path should end something like this
        1. `../Qt/5.12.6/gcc_64`
1. Run cmake 
    1. `cmake ..`
1. Run make
    1. `make`

The binaries will be located in `synergy-core/build/bin`