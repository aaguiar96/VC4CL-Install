# VC4CL setup in Raspbian

## Dependencies
```
$ sudo apt install git cmake clang-3.9 clang-3.9-dev opencl-headers ocl-icd-dev ocl-icd-opencl-dev
$ sudo ln -s /usr/bin/clang{-3.9}
```

## Installing VC4CLStdLib
```
$ git clone https://github.com/doe300/VC4CLStdLib.git
$ mkdir VC4CLStdLib/build && cd VC4CLStdLib/build
$ cmake ..
$ make
$ sudo make install
```

## Installing VC4C
```
$ git clone https://github.com/doe300/VC4C.git
$ mkdir VC4C/build
$ cd VC4C/build
$ cmake -DSPIRV_FRONTEND=OFF ..
$ make
$ sudo make install
```

## Installing VC4CL
```
$ git clone https://github.com/doe300/VC4CL.git
$ mkdir VC4CL/build
$ cd VC4CL/build
$ cmake -DBUILD_TESTING=OFF ..
$ make
$ sudo make install
```

## Finishing ...
```
$ export LD_LIBRARY_PATH=/usr/local/lib
$ sudo ldconfig -v
```

Now run `clinfo` to see if VideoCore IV is detected.
If so, you can test all the setup building `hello_world` example.

## Test
```
$ VC4C --hex -o out hello_world.cl
```
