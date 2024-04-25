# MeerkatIO Documentation

## Introduction

Welcome to the [MeerkatIO](https://www.meerkatio.com/)
 documentation. [MeerkatIO](https://www.meerkatio.com/) is a powerful command line interface (CLI) and Python module designed to help developers step away from their computer while their code is running.

## Meerkat Python SDK

### Installation

```bash
# PyPi
$ pip3 install meerkatio
```

### Authenticating

After creating an account at [MeerkatIO](http://meerkatio.com) you will be given a unique token which can be used to authenticate with the SDK. Your Meerkat token can either be set in your environment with the `MEERKAT_TOKEN` environmental variable or in the `~/.meerkat` file in your user’s home directory. No authentication is required to use the free Ping feature of MeerkatIO.

```bash
# Environment
$ export MEERKAT_TOKEN=token

# Cache File
$ echo "token" > ~/.meerkat
```

### Code Example

```python
import meerkat

# Ping when script gets to checkpoint
meerkat.ping()

# Send a confirmation a function has run
output = build_model()
meerkat.email(output)

# Send Slack message to document model performance
perf = get_model_performance(output)
meerkat.slack(perf)

# Send SMS message when the script is finished
meerkat.sms("Script completed!")
```

### Jupyter Notebook Example

```python
import meerkat

# Ping when cell hits a debug checkpoint
%ping

# Send a confirmation that a cell has run
output = build_model()
%email output

# Send Slack message to document model performance
perf = get_model_performance(output)
%slack perf

# Send SMS message when the cell reaches the end
%sms "Cell completed!"
```

## MeerkatIO CLI Tool

### Installation

```bash
# PyPi
$ pip3 install meerkatio
```

### Authenticating

After creating an account at [MeerkatIO](https://www.meerkatio.com/) you can use the same account credentials to authenticate the CLI, giving you access to the full suite of [MeerkatIO](https://www.meerkatio.com/) services. No authentication is required to use the free Ping feature of [MeerkatIO](https://www.meerkatio.com/).

```bash
$ meerkat login
```

### CLI Examples

All users have access to the ping alert feature which will generate a sound when the below command is run.

```bash
$ meerkat ping
$ meerkat email "Bash script output: $1"
$ meerkat sms "Firmware build completed."
$ meerkat slack "Bash script complete"
```

Here is an example of how to use Meerkat with any script running from a terminal in order to ping youself when the script is finished running.

```bash
$ make build && meerkat email "Build succeeded" || meerkat sms "Build failed"
```