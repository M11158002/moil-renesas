---
sidebar_position: 1
---

# Ubuntu APT Mirror Configuration Guide

This guide explains how to change the Ubuntu APT source to use the Taiwan Digital Streaming Co. mirror for faster package downloads.

## Configure APT Source

Ubuntu uses two different source configuration formats depending on your Ubuntu version:

### 1. One-Line-Style Format (Ubuntu < 24.04)

Change the mirror to TWDS (Taiwan Digital Streaming Co.):

```bash
sudo sed -i 's@//.*archive.ubuntu.com@//mirror.twds.com.tw@g' /etc/apt/sources.list
```

Enable HTTPS (recommended):

```bash
sudo sed -i 's/http:/https:/g' /etc/apt/sources.list
```

### 2. DEB822 Format (Ubuntu >= 24.04)

Change the mirror to TWDS (Taiwan Digital Streaming Co.):

```bash
sudo sed -i 's@//.*archive.ubuntu.com@//mirror.twds.com.tw@g' /etc/apt/sources.list.d/ubuntu.sources
```

Enable HTTPS (recommended):

```bash
sudo sed -i 's/http:/https:/g' /etc/apt/sources.list.d/ubuntu.sources
```

### 3. Update Package List

After changing the mirror, update the package list:

```bash
sudo apt update
```

## Important Notes

1. Backup your configuration files before making changes:

   ```bash
   # For Ubuntu < 24.04
   sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
   
   # For Ubuntu >= 24.04
   sudo cp /etc/apt/sources.list.d/ubuntu.sources /etc/apt/sources.list.d/ubuntu.sources.backup
   ```

2. To restore from backup if needed:

   ```bash
   # For Ubuntu < 24.04
   sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
   
   # For Ubuntu >= 24.04
   sudo cp /etc/apt/sources.list.d/ubuntu.sources.backup /etc/apt/sources.list.d/ubuntu.sources
   ```

3. Make sure your system time is correct for HTTPS connections.

## Verify Current Configuration

Check your current settings:

```bash
# For Ubuntu < 24.04
cat /etc/apt/sources.list

# For Ubuntu >= 24.04
cat /etc/apt/sources.list.d/ubuntu.sources
```

## Troubleshooting

If you encounter "Failed to fetch" errors:

1. Verify your internet connection
2. Clear the local package cache:

   ```bash
   sudo apt clean
   ```

3. Update the package list again:

   ```bash
   sudo apt update
   ```
