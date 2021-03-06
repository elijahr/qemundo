## qemundo

Easy virtual machine manager for QEMU.

## Rationale

QEMU is a powerful tool, but configuration can be a pain.
Many parameters are needed for a basic machine with networking, etc. qemundo
configures the VM and spits out a simple `run.sh` command, ready to boot. Edit
`run.sh` as needed for additional configuration.

Currently supports the following guests:

* NetBSD 9, arm64
* Ubuntu Bionic, arm64
* Alpine Linux 3, arm64

Pull requests for additional guests are welcome.

## Examples


### Create and run a NetBSD arm64 VM

```sh
qemundo install --os netbsd-9 --arch arm64
./netbsd-9-arm64/run.sh
```

### Create and run an Ubuntu arm64 VM

```sh
qemundo install --os ubuntu-bionic --arch arm64
./ubuntu-bionic-arm64/run.sh
```

### Create and run an Alpine Linux arm64 VM

```sh
qemundo install --os alpine-3 --arch arm64
./alpine-3-arm64/run.sh
```

## Usage

```
Usage: qemundo COMMAND [OPTIONS]

  install [path]          Create a new virtual machine at path (default: <os>-<arch>)..
    -o/--os <os>          Install this operating system (default: alpine-3)
    -a/--arch <arch>      Emulate this architecture (default: arm64)
    -s/--size <size>      The size of the disk image (default: 5G)
    -m/--memory <memory>  The amount of memory to allocate (default: 512M)
    -p/--cpus <count>     The number of processors (default: output of nproc)

  clean                   Remove all cached ISOs and images
  list                    Print supported build targets and exit
  help                    Print this help message and exit
```

## Installation

```sh
curl https://raw.githubusercontent.com/elijahr/qemundo/devel/qemundo -LSsf > qemundo
chmod +x qemundo
mv qemundo ~/bin # Or some other place in PATH
```

Tested on macOS, but should work on other platforms as long as `qemu` is
installed.

## License

Copyright (c) 2020 Elijah Shaw-Rutschman

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.