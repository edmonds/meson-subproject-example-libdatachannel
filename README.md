Example of using meson to build an example program that statically links against libdatachannel as a meson-wrapped subproject.

To build in a Debian container:

```
apt update && apt -y full-upgrade

apt install -y --no-install-recommends -V \
	build-essential \
	ca-certificates \
	cmake \
	git \
	libssl-dev \
	meson \
	ninja-build

git clone https://github.com/edmonds/meson-subproject-example-libdatachannel.git

cd meson-subproject-example-libdatachannel

rm -rf build; meson setup build && ninja -v -C build
```
