**IMPORTANT**

This project is deprecated and will no longer be maintained.
Please clone https://github.com/toradex/aktualizr instead.

# aktualizr-torizon

This is the Toradex implementation of the Aktualizr client that integrates libaktualizr. The application is intented to be built as a part of a yocto build. The corresponding yocto layer can be found at <https://github.com/toradex/meta-toradex-torizon>.
This project uses git submodules. You should either clone it with `--recurse-submodules` flag or run `git submodule update --init --recursive` later.

To build the application locally:
```bash
# First install any needed build dependencies
sudo apt install asn1c build-essential cmake curl libarchive-dev libboost-dev libboost-filesystem-dev libboost-log-dev libboost-program-options-dev libcurl4-openssl-dev libpthread-stubs0-dev libsodium-dev libsqlite3-dev libssl-dev python3
# And then build the project
mkdir build && cd build
cmake ..
make
```
