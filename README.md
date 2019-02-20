# VC4CL setup on Raspbian using Raspberry Pi 3

## Dependencies
```
$ sudo apt install git                   \
                   cmake                 \
                   clang-3.9             \
                   clang-3.9-dev         \
                   opencl-headers        \
                   ocl-icd-dev           \
                   ocl-icd-opencl-dev    \
                   clinfo             
$ sudo ln -s /usr/bin/clang{-3.9}
```

## Installing VC4CLStdLib
```
$ git clone https://github.com/doe300/VC4CLStdLib.git
$ cd VC4CLStdLib
$ cmake .
$ make
$ sudo make install
```

## Installing VC4C
```
$ git clone https://github.com/doe300/VC4C.git
$ cd VC4C
$ cmake -DSPIRV_FRONTEND=OFF .
$ make
$ sudo make install
```

## Installing VC4CL
```
$ git clone https://github.com/doe300/VC4CL.git
$ cd VC4CL
$ cmake -DBUILD_TESTING=OFF .
$ make
$ sudo make install
```

## Finishing ...
```
$ export LD_LIBRARY_PATH=/usr/local/lib
$ sudo ldconfig -v
```

Now run `sudo clinfo` to see if VideoCore IV is detected.
If so, you can test all the setup building `hello_world` example.

## Test
```
$ cd {VC4C-root-directory}
$ VC4C --hex -o out example/hello_world.cl
```
