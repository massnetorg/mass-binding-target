# mass-binding-target

`mass-binding-target` is a command line tool for generating binding target list by search plot files from disk.

## Build

[Go](http://golang.org) 1.13 or newer.

```shell
go build -o bin/massBindingTarget main.go
```

An executable named `massBindingTarget` will be generated in `./bin` directory.

## Usage

```
NAME:
   massBindingTarget - Get MASS Binding Target List by searching for plot files from disk.

USAGE:
   ./massBindingTarget <export_filename> [flags]

COMMANDS:
   help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --overwrite, -o         overwrite existed binding list file (default: false)
   --all, -a               list all files instead of only plotted files (default: false)
   --keystore value        specify the keystore to eliminate files without private key
   --type value, -t value  specify the searching plot type: m1 (for native MassDB) or m2 (for Chia Plot)
   --dirs value, -d value  specify the searching directories
   --help, -h              show help (default: false)
```

## Running Examples

### For native MassDB

Imagine that you have some native MassDB files distributed among three directories: `/root/plot1`, `/root/plot2`, `/root/plot3`.

The best practice for collect all plotted files is:

```shell
./massBindingTarget -t m1 -d /root/plot1 -d /root/plot2 -d /root/plot3 binding_list.json
```

A file named `binding_list.json` will be generated after the execution.

If you want to collect all files (whether it is plotted or not), use `-a` flag:

```shell
./massBindingTarget -t m1 -a -d /root/plot1 -d /root/plot2 -d /root/plot3 binding_list.json
```

### For Chia Plot


Imagine that you have some Chia Plot files distributed among three directories: `/root/plot1`, `/root/plot2`, `/root/plot3`.

The best practice for collect all files is:

```shell
./massBindingTarget -t m2 -d /root/plot1 -d /root/plot2 -d /root/plot3 binding_list.json
```

A file named `binding_list.json` will be generated after the execution.
