# CMake install from kitware ppa
https://apt.kitware.com/
```
$ sudo apt-get update
$ sudo apt-get install ca-certificates gpg wget
$ wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | sudo tee /usr/share/keyrings/kitware-archive-keyring.gpg >/dev/null
```

<summary>UBUNTU 24.04 NOBLE NUMBAT</summary>

```
$ echo 'deb [signed-by=/usr/share/keyrings/kitware-archive-keyring.gpg] https://apt.kitware.com/ubuntu/ noble main' | sudo tee /etc/apt/sources.list.d/kitware.list >/dev/null
```
<summary>UBUNTU 22.04 JAMMY JELLYFISH</summary>

```
$ echo 'deb [signed-by=/usr/share/keyrings/kitware-archive-keyring.gpg] https://apt.kitware.com/ubuntu/ jammy main' | sudo tee /etc/apt/sources.list.d/kitware.list >/dev/null
```
<summary>UBUNTU 20.04 FOCAL FOSSA</summary>

```
$ echo 'deb [signed-by=/usr/share/keyrings/kitware-archive-keyring.gpg] https://apt.kitware.com/ubuntu/ focal main' | sudo tee /etc/apt/sources.list.d/kitware.list >/dev/null
```

```
$ sudo apt-get update
$ sudo rm /usr/share/keyrings/kitware-archive-keyring.gpg
$ sudo apt-get install kitware-archive-keyring
$ sudo apt-get install cmake
```

# CMake build from sources:
```
$ git clone https://gitlab.kitware.com/cmake/cmake.git
$ cd cmakedir
$ mkdir build && cd build
$ ../bootstrap && make -j$(nproc) && make install
```
