# DLSS-Enabler

[![Build Installer](https://github.com/artur-graniszewski/DLSS-Enabler/actions/workflows/build-installer.yml/badge.svg)](https://github.com/artur-graniszewski/DLSS-Enabler/actions/workflows/build-installer.yml)
[![Monitor OptiScaler](https://github.com/artur-graniszewski/DLSS-Enabler/actions/workflows/monitor-optiscaler.yml/badge.svg)](https://github.com/artur-graniszewski/DLSS-Enabler/actions/workflows/monitor-optiscaler.yml)

Simulate DLSS Upscaler and DLSS-G Frame Generation features on any DirectX 12 compatible GPU in any DirectX 12 game that supports DLSS2 and DLSS3 natively.

![s3Leq7Q](https://github.com/user-attachments/assets/c81a2724-dbc4-4ec3-a445-87beed546345)

## 🚀 Automated Builds with Latest OptiScaler

This repository now features **automated builds** that keep DLSS-Enabler up-to-date with the latest [OptiScaler](https://github.com/optiscaler/OptiScaler) releases!

### 📦 Download Latest Release

**Recommended**: Download the latest pre-built installer from the [Releases](../../releases) page. These installers are automatically built with:
- ✅ Latest OptiScaler (nightly or stable versions)
- ✅ Latest XeSS library from Intel
- ✅ All required components pre-configured

### 🔄 How Auto-Updates Work

The automated system:
1. **Monitors** OptiScaler repository for new releases every 6 hours
2. **Downloads** the latest `nvngx.dll` from OptiScaler releases  
3. **Renames** it to `dlss-enabler-upscaler.dll` (as required by DLSS-Enabler)
4. **Fetches** the latest `libxess.dll` from Intel's XeSS repository
5. **Builds** a new installer using Inno Setup 6.2.0
6. **Publishes** the installer as a GitHub release

### 🛠️ Local Updates (Advanced Users)

For developers or advanced users who want to update OptiScaler manually:

```powershell
# Download and update OptiScaler to latest nightly
.\update-optiscaler.ps1 -OptiScalerVersion nightly -Force

# Update to specific version
.\update-optiscaler.ps1 -OptiScalerVersion v0.7.7-pre12 -Force

# Update without XeSS (if you have it already)
.\update-optiscaler.ps1 -SkipXeSS
```

## How to

### How to build a setup application

In order to build the setup application for DLSS Enabler, you need to install InnoSetup software first ( https://jrsoftware.org/isdl.php ). The most optimal version is 6.2.0 (nothing below, nothing above - mainly due to the craziness of some AVs that raise the false positives randomly).

After installing the InnoSetup software, double click "DLSS enabler.iss" file and edit its contents (such as build version, etc) in InnoSetup Editor.

Before building new package, you need to download latest libxess.dll file from INTEL repository and place it into "Dll version" subdirectory, otherwise the setup build process will fail due to the missing file.

After successful build, the resulting setup app will be created inside of "Output" directory.
