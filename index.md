# Introduction
This is a step-by-step instruction how to create running [PenPoint OS](https://en.wikipedia.org/wiki/PenPoint_OS) environment.

It will use a [modified version of QEMU](https://github.com/khnsky/qemu-penpointos), a [libvirt](https://wiki.archlinux.org/title/Libvirt) client ([virt-manager](https://wiki.archlinux.org/title/Virt-Manager) in my case but any should do), and [FreeDOS](https://www.freedos.org/).  
In the guide I will be using [Arch Linux](https://archlinux.org/) and be linking to [ArchWiki](https://wiki.archlinux.org/) but it should work similarily for other distributions.

# Table of Contents
[Creating the VM](#creating-the-vm)

# Creating the VM
Download [FreeDOS 1.3 LiveCD](https://www.freedos.org/download/) and unzip it.
```
$ unzip FD13-LiveCD.zip
Archive:  FD13-LiveCD.zip
  inflating: FD13BOOT.img
  inflating: FD13LIVE.iso
  inflating: readme.txt
```
Install QEMU and libvirt client
```
$ sudo pacman -S qemu-desktop libvirt virt-manager
```
and start the libvirtd service.
```
$ systemctl start libvirtd.service
```

1. Start virt-manager. If 'QEMU/KVM' is grayed out double click to connect.  
2. From the drop-down menu select 'File -> New Virtual Machine'.  
3. Select 'Local install media' and click 'Forward'.
4. Select unzipped FD13LIVE.iso by clicking 'browse' -> 'Browse local'.
5. Unselect 'Automatically detect from installation media/source', type 'FreeDOS', select 'FreeDOS 1.2' and click 'Forward'.  
6. Set CPUs to 1 and click 'Forward'.  
7. Set disk image size to 500MB and click 'Forward'.  
8. Change name and select 'Customize configuration before install' and click 'Finish'.
9. In 'Boot Options' select 'Enable boot menu'.
10. In 'NIC' click remove.  
11. Click 'Begin installation'.  
12. Using arrows select 'Install to harddisk' and press Enter.  
13. Choose language and press Enter.
14. Select 'Yes - Continue with the installation' and press Enter.
15. Select 'Yes - Partition drive C:' and press Enter.
16. Select 'Yes - Please reboot now' and press Enter.
17. Unfortunately now the installation disk is ejected and the virtual machine cannot boot, from the drop-down menu select 'Virtual Machine -> Shutdown -> Force Off' and confirm by clicking 'Yes'.  
18. In the 'Show virtual hardware details' tab the IDE CDROM 1 is empty, click 'Browse', select FD13LIVE.iso, and confirm by clicking 'Choose Volume'.  
19. Click 'Apply' and power on the virtual machine by clikcing the triangle below 'Virtual Machine' menu button.
20. Press Esc to access boot menu and press 3 to select DVD/CD (FD13-LiveCD)
21. Select using arrows 'Install to harddisk', and then language. This looks like repeating steps but it is not.  
22. Select 'Yes - Continue with the installation'.  
23. Select 'Yes - Please erase and format drive C:'
24. Select keyboard layout.  
25. Select 'Full installation including applications and games'.  
26. Select 'Yes - Please install FreeDOS 1.3'.  
27. After installation finishes select 'Yes - Please reboot now' and press Enter.

Installation of FreeDOS is now complete, you can use `shutdown` command to power off.
