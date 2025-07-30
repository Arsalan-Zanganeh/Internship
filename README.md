## System Specifications

The project was executed on the following system:

```bash
Architecture: x86_64
CPU op-mode(s): 32-bit, 64-bit
Byte Order: Little Endian
Address sizes: 39 bits physical, 48 bits virtual
CPU(s): 8
On-line CPU(s) list: 0-7
Thread(s) per core: 2
Core(s) per socket: 4
Socket(s): 1
NUMA node(s): 1
Vendor ID: GenuineIntel
Model name: Intel(R) Core(TM) i7-1065G7 CPU @ 1.30GHz
CPU min MHz: 400.000
CPU max MHz: 3900.0000
...
```


## Challenges and Solutions

### 1. Missing Meson Module

* **Issue**: Encountering No module named 'mesonbuild.machinefile' in running `meson install` after `ninja` command.
* **Solution**: uninstall all meson versions that are installed with pip or apt and their relative libraries in usr/ folder, then install it with root priviledges (not as a superuser) by pip.

  ```bash
  sudo pip install meson
  ```
* **Outcome**: meson successfully installs the compiled artifacts.

### 2. Empty Trace Folder

* **Issue**: After running lttng script, the ust folder of trace is empty.
* **Solution**: Clean install lttng stable ppa version with [LTTng Stable 2.13 PPA installation Guide](https://lttng.org/docs/v2.13/#doc-ubuntu-ppa) 
* **Outcome**: Trace has captured preloaded fuctions.

### 3. Null Trace Compass Views

* **Issue**: Call stack views ( Flame Graph & Flame Graph Selection) are empty.
* **Solution**: install java-21 and set as deafult version of java.

  ```bash
  sudo apt install openjdk-21-jdk -y
  ```
* **Outcome**: Call stack gets visible (still needs sometime based on your Ram and CPU).

### 4. Missing Function Names

* **Issue**: some functions are available only by their address not their names.
* **Solution**: shut down tcpreplay and testpmd before stopping and destroying lttng.
* **Outcome**: Function entries and exits get equal, then you may see the all the function names.
