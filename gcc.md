# GCC build from sources
Download `gcc-<version>.tar.gz` from [GitHub](https://github.com/gcc-mirror/gcc/tags) / [RU mirror](http://mirror.linux-ia64.org/gnu/gcc/releases/).

Version 13.2.0 is taken as an example.
```bash
tar -xvf gcc-13.2.0.tar.gz
cd gcc-13.2.0/

# script for downloading dependencies
./contrib/download_prerequisites 
```

```bash
cd ..
mkdir build && cd build
```

Configuration parameters taken from  [here](https://iamsorush.com/posts/build-gcc11/), [here](https://gist.github.com/jeetsukumaran/5224956) and [here](https://gcc.gnu.org/install/configure.html).
```bash
../configure --prefix=/usr/local/gcc-13.2.0 --program-suffix=-13.2.0 --enable-shared --enable-threads=posix --enable-__cxa_atexit --enable-clocale=gnu --disable-multilib --enable-languages=c,c++
```

```bash
make -j 6
sudo make install
```

Add to `~/.bashrc`:
```b
# Path
export PATH=/usr/local/gcc-13.2.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/gcc-13.2.0/lib64:$LD_LIBRARY_PATH

# To let CMake know
export CC=/usr/local/gcc-13.2.0/bin/gcc-13.2.0
export CXX=/usr/local/gcc-13.2.0/bin/g++-13.2.0 
```
