## Challenges and Solutions

### 1. Outdated Meson Version

* **Issue**: The initial Meson version (0.53.2) was incompatible.
* **Solution**:

  ```bash
  pip3 install --user meson --upgrade
  echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
  source ~/.bashrc
  ```
* **Outcome**: Compatibility issue resolved.

### 2. Missing helloworld Executable

* **Issue**: After running `ninja`, the executable was missing.
* **Solution**:

  ```bash
  cd /home/eagle/vpp/build-root/build-vpp-native/external/src-dpdk
  rm -rf build
  meson setup build
  cd build
  meson configure -Dexamples=helloworld
  ninja
  ```
* **Outcome**: Rebuild successfully generated the executable.

### 3. PATH Configuration for Meson

* **Issue**: Installed Meson was not in system's PATH.
* **Solution**: Added `$HOME/.local/bin` to PATH (see Solution above).
* **Outcome**: Correct version of Meson used.

## Conclusion

This project successfully configured HugePages and ran the DPDK helloworld example on CPU cores 0-3. Challenges were resolved through version upgrades and rebuilds. The DPDK environment is confirmed operational.

## References

* [DPDK Documentation](https://doc.dpdk.org)
* [Memif Guide](https://doc.dpdk.org/guides/nics/memif.html)
* VPP Source Code: `/home/eagle/vpp`
