# Installation

This guide demonstrates the installation steps of ORAS CLI on different platforms.

## Homebrew

Install `oras` using [Homebrew](https://brew.sh/):

```bash
brew install oras
```
## Release artifacts

Install ORAS from the latest [release artifacts](https://github.com/oras-project/oras/releases):

### Linux

If you want to install ORAS on an AMD64-based Linux machine, run the following command:

```bash
VERSION="1.0.0"
curl -LO "https://github.com/oras-project/oras/releases/download/v${VERSION}/oras_${VERSION}_linux_amd64.tar.gz"
mkdir -p oras-install/
tar -zxf oras_${VERSION}_*.tar.gz -C oras-install/
sudo mv oras-install/oras /usr/local/bin/
rm -rf oras_${VERSION}_*.tar.gz oras-install/
```

> Note: If you want to install ORAS on an ARM64-based Linux machine, you can download it from `https://github.com/oras-project/oras/releases/download/v1.0.0/oras_1.0.0_linux_arm64.tar.gz`.

### macOS

If you want to install ORAS on a Mac computer with Apple silicon, run the following command:

```bash
VERSION="1.0.0"
curl -LO "https://github.com/oras-project/oras/releases/download/v${VERSION}/oras_${VERSION}_darwin_arm64.tar.gz"
mkdir -p oras-install/
tar -zxf oras_${VERSION}_*.tar.gz -C oras-install/
sudo mv oras-install/oras /usr/local/bin/
rm -rf oras_${VERSION}_*.tar.gz oras-install/
```

> Note: If you want to install ORAS on an Intel-based Mac, you can download it from `https://github.com/oras-project/oras/releases/download/v1.0.0/oras_1.0.0_darwin_amd64.tar.gz`.

### Windows

Add `%USERPROFILE%\bin\` to your `PATH` environment variable so that `oras.exe` can be found.

```cmd
set VERSION="1.0.0"
curl.exe -sLO  "https://github.com/oras-project/oras/releases/download/v%VERSION%/oras_%VERSION%_windows_amd64.zip"
tar.exe -xvzf oras_%VERSION%_windows_amd64.zip
mkdir -p %USERPROFILE%\bin\
copy oras.exe %USERPROFILE%\bin\
set PATH=%USERPROFILE%\bin\;%PATH%
```

## Docker Image

A public Docker image containing the CLI is available on [GitHub Container Registry](https://github.com/orgs/oras-project/packages/container/package/oras):

```
docker run -it --rm -v $(pwd):/workspace ghcr.io/oras-project/oras:v1.0.0 help
```

> Note: the default WORKDIR in the image is `/workspace`.

## Verify

```shell
$ oras version
Version:        1.0.0
Go version:     go1.20.2
Git commit:     b58e7b910ca556973d111e9bd734a71baef03db2
Git tree state: clean
```