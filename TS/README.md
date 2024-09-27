# VMware ESXi Power Failure and System Restart Investigation

This guide explains how to check for **power failures** or **system restarts** on a VMware ESXi host using SSH and log files.

## Prerequisites
- **SSH Access** to the ESXi host
- Enabled **SSH service** on the ESXi host, if not already running

## 1. Connect to the ESXi Host via SSH

1. **Enable SSH on the ESXi host** via the vSphere Client:
   - Go to `Host > Actions > Services > Enable Secure Shell (SSH)`.

2. **Connect to the ESXi host** using SSH:
   ```bash
   ssh root@<esxi-host-ip>

# ESXi Host Troubleshooting Guide

## 2. Review System Event Logs
ESXi logs can provide information about potential power failures or other restart causes.

### 2.1 Check `vmkernel.log` for Power Failures
The `vmkernel.log` contains details on hardware events, including power failures and restarts.

```bash
cat /var/log/vmkernel.log | grep -i 'power'
```
### 2.2 Check hostd.log for Shutdown and Restart Events
The hostd.log logs tasks and operations like shutdowns or reboots.
```bash
cat /var/log/hostd.log | grep -i 'shutdown\|reboot'
```
### 2.3 Check vobd.log for Hardware Events
The vobd.log captures hardware-related issues, such as power supply failures or hardware malfunction.
```bash
cat /var/log/vobd.log | grep -i 'power'
```

