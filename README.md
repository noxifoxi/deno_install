# deno_install-arm64

**One-line commands to install Deno on your ARM64 system.**

Because Deno does not have ARM64 binaries [yet](https://github.com/denoland/deno/issues/1846), LukeChannings is building and providing them at [LukeChannings/deno-arm64](https://github.com/LukeChannings/deno-arm64/releases). I have modified the official install script to automate the installation and upgrade process with [LukeChannings](https://github.com/LukeChannings)' builds.

## Install Latest Version

**With Shell:**

```sh
curl -fsSL https://noxifoxi.github.io/deno_install-arm64/install.sh | sh
```

## Install Specific Version

**With Shell:**

```sh
curl -fsSL https://noxifoxi.github.io/deno_install-arm64/install.sh | sh -s v1.6.3
```

## Install Multiple Versions

[`DENO_INSTALL`](#environment-variables) can be used to install a specific version into a different directory.

**With Shell:**

```sh
curl -fsSL https://noxifoxi.github.io/deno_install-arm64/install.sh | DENO_INSTALL=$HOME/deno-1.6.3 sh -s v1.6.3
```

## Environment Variables

- `DENO_INSTALL` - The directory in which to install Deno. This defaults to
  `$HOME/.deno`. The executable is placed in `$DENO_INSTALL/bin`. One
  application of this is a system-wide installation:

  **With Shell (`/usr/local`):**

  ```sh
  curl -fsSL https://noxifoxi.github.io/deno_install-arm64/install.sh | sudo DENO_INSTALL=/usr/local sh
  ```

## Known Issues

### The requested URL returned error: 404

Specified versions that were not build at [LukeChannings/deno-arm64](https://github.com/LukeChannings/deno-arm64/releases) cannot be installed with the script.

```sh
$ curl -fsSL https://noxifoxi.github.io/deno_install-arm64/install.sh | sh -s v1.0.0
curl: (22) The requested URL returned error: 404
```

**How can this issue be fixed?**

Only try to install the versions available on the [releases page](https://github.com/LukeChannings/deno-arm64/releases). The oldest release available is Deno 1.6.3.

### unzip is required

The program [`unzip`](https://linux.die.net/man/1/unzip) is a requirement for the Shell installer.

```sh
$ curl -fsSL https://noxifoxi.github.io/deno_install-arm64/install.sh | sh
Error: unzip is required to install Deno (see: https://github.com/denoland/deno_install#unzip-is-required).
```

**When does this issue occur?**

During the `install.sh` process, `unzip` is used to extract the zip archive.

**How can this issue be fixed?**

You can install unzip via `brew install unzip` on MacOS or `apt-get install unzip -y` on Linux.
