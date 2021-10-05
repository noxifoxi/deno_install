# deno_install

**One-line commands to install Deno on your ARM64 system.**

Builds are provided by [LukeChannings](https://github.com/LukeChannings) at [LukeChannings/deno-arm64](https://github.com/LukeChannings/deno-arm64/releases).

## Install Latest Version

**With Shell:**

```sh
curl -fsSL https://github.com/noxifoxi/deno_install-arm64/raw/master/install.sh | sh
```

## Install Specific Version

**With Shell:**

```sh
curl -fsSL https://github.com/noxifoxi/deno_install-arm64/raw/master/install.sh | sh -s v1.6.3
```

## Install and Manage Multiple Versions

**With [asdf](https://asdf-vm.com) and [asdf-deno](https://github.com/asdf-community/asdf-deno):**

```sh
asdf plugin add deno

# Get latest version of deno available
DENO_LATEST=$(asdf latest deno)

asdf install deno $DENO_LATEST

# Activate globally with:
asdf global deno $DENO_LATEST

# Activate locally in the current folder with:
asdf local deno $DENO_LATEST

#======================================================
# If you want to install specific version of deno then use that version instead
# of DENO_LATEST variable example
asdf install deno 1.0.0

# Activate globally with:
asdf global deno 1.0.0

# Activate locally in the current folder with:
asdf local deno 1.0.0
```

## Environment Variables

- `DENO_INSTALL` - The directory in which to install Deno. This defaults to
  `$HOME/.deno`. The executable is placed in `$DENO_INSTALL/bin`. One
  application of this is a system-wide installation:

  **With Shell (`/usr/local`):**

  ```sh
  curl -fsSL https://github.com/noxifoxi/deno_install-arm64/raw/master/install.sh | sudo DENO_INSTALL=/usr/local sh
  ```

## Known Issues

### unzip is required

The program [`unzip`](https://linux.die.net/man/1/unzip) is a requirement for the Shell installer.

```sh
$ curl -fsSL https://github.com/noxifoxi/deno_install-arm64/raw/master/install.sh | sh
Error: unzip is required to install Deno (see: https://github.com/denoland/deno_install#unzip-is-required).
```

**When does this issue occur?**

During the `install.sh` process, `unzip` is used to extract the zip archive.

**How can this issue be fixed?**

You can install unzip via `brew install unzip` on MacOS or `apt-get install unzip -y` on Linux.
