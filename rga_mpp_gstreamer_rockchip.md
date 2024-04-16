# MPP ROCKCHIP build from sources:
```bash
$ git clone https://github.com/rockchip-linux/mpp.git --depth 1
$ cd mpp/build/linux/aarch64/
$ ./make-Makefiles.bash
$ make -j$(nproc)
$ make install
```
# librga
```bash
$ git clone -b linux-rga https://github.com/JeffyCN/mirrors.git --depth 1
$ mv ./mirrors ./linux-rga && cd linux-rga
$ mkdir build && cd build
$ meson
$ sudo ninja -j4
$ sudo ninja install
```
# gstreamer-rockchip
```bash
$ git clone -b gstreamer-rockchip https://github.com/JeffyCN/mirrors.git --depth 1
$ mv ./mirrors ./gstreamer-rockchip && cd gstreamer-rockchip
$ mkdir build && cd build
$ meson
$ sudo ninja -j4
# Read logs if you receive an error.
# I had a build error with GST_MPP_FORMAT (NV16_10LE4 was unsupported), so commenting out line 77 in gst/rockchipmpp/gstmpp.c fixed my problem.
$ sudo ninja install
```
