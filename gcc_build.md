# GCC build from sources
Качаем исходники с [GitHub](https://github.com/gcc-mirror/gcc/tags) / [RU mirror](http://mirror.linux-ia64.org/gnu/gcc/releases/)
```bash
tar -xvf gcc-13.2.0.tar.gz
cd gcc-13.2.0/

# Скрипт в поставке gcc для скачивания зависимостей.
./contrib/download_prerequisites 
```

```bash
cd ..
mkdir build && cd build
```

Параметры для конфигурации надерганы [отсюда](https://iamsorush.com/posts/build-gcc11/), [отсюда](https://gist.github.com/jeetsukumaran/5224956) и [отсюда](https://gcc.gnu.org/install/configure.html)
```bash
../configure --prefix=/usr/local/gcc-13.2.0 --program-suffix=-13.2.0 --enable-shared --enable-threads=posix --enable-__cxa_atexit --enable-clocale=gnu --disable-multilib --enable-languages=c,c++
```

```bash
make -j 6
sudo make install
```

В `~/.bashrc` добавить:
```b
# Path
export PATH=/usr/local/gcc-13.2.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/gcc-13.2.0/lib64:$LD_LIBRARY_PATH

# To let CMake know
export CC=/usr/local/gcc-13.2.0/bin/gcc-13.2.0
export CXX=/usr/local/gcc-13.2.0/bin/g++-13.2.0 
```
