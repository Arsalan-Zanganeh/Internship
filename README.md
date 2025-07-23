## Challenges and Solutions

### 1. Missing Meson Module

* **Issue**: Encountering No module named 'mesonbuild.machinefile' in running `meson install` after ninja command.
* **Solution**: uninstall all meson versions that are installed with pip or apt and their relative libraries in usr/ folder, then install it with root priviledges (not as a superuser) by pip.

  ```bash
  sudo pip install meson
  ```
* **Outcome**: meson successfully installs the compiled artifacts.

### 2. Empty Trace Folder

* **Issue**: After running lttng script, the ust folder of trace is empty.
* **Solution**: Clean install lttng stable ppa version with [LTTng Stable 2.13 PPA installation Guide](https://lttng.org/docs/v2.13/#doc-ubuntu-ppa) 
* **Outcome**: Trace has captured preloaded fuctions.

## Conclusion

This project successfully configured HugePages and ran the DPDK helloworld example on CPU cores 0-3. Challenges were resolved through version upgrades and rebuilds. The DPDK environment is confirmed operational.

## References

* [DPDK Documentation](https://doc.dpdk.org)
* [Memif Guide](https://doc.dpdk.org/guides/nics/memif.html)
* VPP Source Code: `/home/eagle/vpp`
