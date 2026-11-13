# Sharpa Avatar App

Sharpa Avatar App is the desktop application for configuring and monitoring the Sharpa AvatarExo Glove, visualizing its data, and using it to teleoperate Sharpa Wave.

## 📥 Download

Download the current [amd64 installer](https://github.com/sharpa-robotics/sharpa-avatar-app/releases/download/v1.2.3/sharpa-avatar_1.2.3_amd64.deb) from [App v1.2.3](https://github.com/sharpa-robotics/sharpa-avatar-app/releases/tag/v1.2.3):

```text
sharpa-avatar_1.2.3_amd64.deb
```

The App installer includes `avatar-sdk 1.8.1-2` for a new installation without an existing SDK. You do not need to download the SDK separately.

## 🚀 Install on Ubuntu or Debian

Install the downloaded App package with APT:

```bash
sudo apt install ./sharpa-avatar_1.2.3_amd64.deb
```

The App installs under `/opt/sharpa-avatar/`. If no SDK is installed, its installer installs the included SDK package under `/opt/avatar-sdk/`. If an SDK is already installed, the installer uses the configured Sharpa APT repository to install the matching version when needed.

The SDK installation runs in the background and may finish after the APT command returns. Check that it completed before using the App:

```bash
cat /var/lib/sharpa-avatar/sdk-install.success
```

If installation is still in progress, `/var/lib/sharpa-avatar/sdk-install.pending` will be present. If it fails, check:

```bash
cat /var/lib/sharpa-avatar/sdk-install.failed
cat /var/log/sharpa-avatar-bundled-sdk.log
```

Reconnect the glove after installation if it is not detected.

## ▶️ Run

Launch **Sharpa Avatar** from the application menu, or run:

```bash
/opt/sharpa-avatar/sharpa-avatar
```

## 📦 Features

- Monitor live glove data in the Dashboard.
- View left and right IMU metrics in curves and data tables, and select them in the chart editor.
- Use skeleton visualization and data collection features in the same App package.
- Visualize glove data and use supported Sharpa Wave teleoperation features.

## 🔗 Compatibility

| Avatar App | Included Avatar SDK | Bundled firmware image | Notes |
|---|---|---|---|
| 1.2.3 | 1.8.1-2 | 2.0.8 | Current public release |

App users do not need a separate SDK download. An installation without an existing SDK uses the included package. When updating an existing installation, the installer can retrieve the matching SDK version from the configured Sharpa APT repository.

The table identifies the firmware image supplied with the SDK, not a stated minimum device firmware version. Installing the App or SDK does not update the firmware on a connected glove. Use the App's firmware upgrade feature if you need to install a firmware image on the device.

## 🔄 Update

Download the newer App `.deb` from [Releases](https://github.com/sharpa-robotics/sharpa-avatar-app/releases), then run `sudo apt install` with the path to that file.

The upgrade configures the Sharpa APT repository and installs the matching SDK version in the background. Network access to that repository is required when the SDK needs updating. Check `/var/lib/sharpa-avatar/sdk-install.success` to confirm that SDK installation finished.

The App remains under `/opt/sharpa-avatar/`. Package upgrades retain the desktop shortcut and user configuration.

## ❌ Uninstall

Remove the App:

```bash
sudo apt remove sharpa-avatar
```

The SDK is a separate Debian package and is not removed automatically with the App. To remove it as well:

```bash
sudo apt remove avatar-sdk
```

## ⚠️ Requirements

- Ubuntu or Debian-based Linux on amd64 for the current App package.
- Administrator privileges to install packages and configure device access.
- Network access to the Sharpa APT repository when upgrading the SDK with the App.
- A supported Sharpa AvatarExo Glove.

## 🔗 Related downloads

- [Sharpa Avatar SDK](https://github.com/sharpa-robotics/sharpa-avatar-sdk)
- [Sharpa Avatar Firmware](https://github.com/sharpa-robotics/sharpa-avatar-ae01-firmware)

## 📞 Support

For product support, contact [support@sharpa.com](mailto:support@sharpa.com).
