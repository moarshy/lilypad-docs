---
description: Lilypad setup
---

# \[CLI] Install Run Requirements

## Install Requirements

{% hint style="info" %}
**Supported platforms**: only supports x86_64 Linux
{% endhint %}

## Install CLI

### 1. With GO toolchain
```bash
go install github.com/bacalhau-project/lilypad@latest
```

You may then need to set:
```bash
export SERVICE_SOLVER="0xd4646ef9f7336b06841db3019b617ceadf435316"
export SERVICE_MEDIATORS="0x2d83ced7562e406151bd49c749654429907543b4"
export WEB3_PRIVATE_KEY=<your private key>
```

### 2. Via officially released binaries
```bash
# Detect your machine's architecture and set it as $OSARCH
OSARCH=$(uname -m | awk '{if ($0 ~ /arm64|aarch64/) print "arm64"; else if ($0 ~ /x86_64|amd64/) print "amd64"; else print "unsupported_arch"}') && export OSARCH;
# Detect your operating system and set it as $OSNAME
OSNAME=$(uname -s | awk '{if ($1 == "Darwin") print "darwin"; else if ($1 == "Linux") print "linux"; else print "unsupported_os"}') && export OSNAME;
# Download the latest production build
curl -sSL -o lilypad https://github.com/bacalhau-project/lilypad/releases/download/v2.0.0-701b8cb/lilypad-$OSNAME-$OSARCH
# Make Lilypad executable and install it
chmod +x lilypad
sudo mv lilypad /usr/local/bin/lilypad
```

You may then need to set:
```bash
export SERVICE_SOLVER="0xd4646ef9f7336b06841db3019b617ceadf435316"
export SERVICE_MEDIATORS="0x2d83ced7562e406151bd49c749654429907543b4"
export WEB3_PRIVATE_KEY=<your private key>
```

Verifying if the install is successful. Execute `lilypad` on your terminal and it should produce the following response. 

```bash
Lilypad

Usage:
  lilypad [command]

Available Commands:
  completion        Generate the autocompletion script for the specified shell
  help              Help about any command
  mediator          Start the lilypad mediator service.
  resource-provider Start the lilypad resource-provider service.
  run               Run a job on the Lilypad network.
  solver            Start the lilypad solver service.

Flags:
  -h, --help   help for lilypad

Use "lilypad [command] --help" for more information about a command.
```