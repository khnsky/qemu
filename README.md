# Overview
This is a fork of [QEMU](https://gitlab.com/qemu-project/qemu) that adds an
absolute pointing mode to the PS/2 mouse device.

This allows to install [PenPoint OS](https://en.wikipedia.org/wiki/PenPoint_OS)
(SDK) in [FreeDOS](https://www.freedos.org/) and use a graphics tablet and
stylus to navigate PenPoint.

See: [step-by-step installation guide](https://khnsky.github.io/qemu-penpointos/)

# Building
To build run:
```
$ git clone 'https://github.com/khnsky/qemu-penpointos'
$ cd qemu-penpointos
$ mkdir build
$ cd build
$ ../configure --target-list=x86_64-softmmu --enable-modules --disable-werror
$ ninja
```

For more information see QEMU documentation.

