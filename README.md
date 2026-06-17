# OKD SNO — Installation Guide

## VM Minimum Specs

| Resource | Minimum |
|---|---|
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 120 GB |
| Firmware | UEFI |

## Before You Start

1. Get the MAC address of your VM's NIC: `VM Settings → Network Adapter → Advanced...`
2. Enter it in `agent-config.yaml` at the `macAddress` field

## Generate the ISO

Download the OKD installer from https://github.com/okd-project/okd/releases, then run:

```bash
./openshift-install agent create image --dir . --log-level debug
```

This produces `agent.x86_64.iso`. Mount it as CD/DVD in your VM and boot from it.

## Monitor Installation

```bash
./openshift-install agent wait-for bootstrap-complete --log-level info
./openshift-install agent wait-for install-complete --log-level info
```

Takes roughly **45–90 minutes**. Credentials are in `auth/kubeconfig` and `auth/kubeadmin-password` after completion.
