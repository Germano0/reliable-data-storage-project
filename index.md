## Description
Project of a budget[1] custom NAS focused on data integrity[2] (ZFS filesystem + ECC RAM). \
It has been made on Februrary 2020, so considerations on hardware may no longer be valid in future

### Components

```
CASE: Fractal Design Define R5 + 3x Noctua NF-A14 ULN
PSU: Seasonic PRIME GX-650
CPU: AMD Ryzen 5 3600 + Noctua NH-D15
RAM: 2x16 GB Kingston 2666 ECC [KSM26ED8/16ME]
VGA: Radeon R5 230 passiva
MOBO: ASRock X470 Taichi Ultimate
STORAGE: RAID-Z3 + SSD for operating system
OS: CentOS 8 + ZFS On Linux
```

### Notes
- the CPU is the cheapest 3rd gen Ryzen (Zen 2 arch) with certified ECC RAM support. APUs with integrated GPU are not certified. It is also the cheapest to support all PCI Express slots;
- I did not choose a ITX mobo because I needed at least 2 PCIExpress 8x: one for additional LSI HBA and another for further 10Gbit/s NIC. Luckly this mobo has also an integrated 10Gbit/s NIC;
- I did not choose AMD X570 chipset because it isn't fanless;
- the system is not audible during daylight hours and idle power consumption is <50Watt.
- The case IMHO is the best for having 8x 3.5" + 2x 2.5" + 2x 5.25" slots;
- the PSU is the cheapest Seasonic with 150000 hours MTBF
- software stacks for sharing data are SSHFS and syncthing
- mounting a remote folder with following SSHFS flags improves network throughput, even saturating Gigabit/s Ethernet connection during file transfers `$ sshfs -o cache=yes -o kernel_cache -o compression=no user@ip_address:/zpool/dataset /foo/bar`


[1]: budget because it uses a consumer x86 CPU rather than a x96 server CPU for having ECC RAM support  
[2]: https://en.wikipedia.org/wiki/Data_degradation
