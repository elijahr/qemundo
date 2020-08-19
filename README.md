## qemundo

Easy virtual machine manager for QEMU.

## Rationale

QEMU is a powerful tool, but configuring it can be kind of a pain.
Many parameters are needed for a usable machine with networking, etc. qemundo
configures the VM and spits out a simple `run.sh`, ready to boot. If you need to
customize networking, graphics, etc, after your machine is created, just edit
`run.sh`.

Currently supports the following guests:

* netbsd-9-arm64
* ubuntu-bionic-arm64

Pull requests for additional targets are welcome!

## Examples

### Create and run an Ubuntu Bionic arm64 VM

```sh
qemundo install --os ubuntu --arch arm64
./ubuntu-arm64/run.sh
```

### Create and run a NetBSD 9 arm64 VM

```sh
qemundo install --os netbsd-9 --arch arm64
./netbsd-9-arm64/run.sh
```

## Usage

```
Usage: qemundo COMMAND [OPTIONS]

  install [path]          Create a new virtual machine at path (default: <os>-<arch>).
    -o/--os <os>          Install this operating system. (default: netbsd-9)
    -a/--arch <arch>      Emulate this architecture. (default: arm64)
    -s/--size <size>      The size of the disk image. (default: 5G)
    -m/--memory <memory>  The amount of memory to allocate. (default: 512M)
    -p/--cpus <size>      The number of processors. (default: value of nproc)

  list                    Print supported build targets and exit.
  help                    Print this help message and exit.

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