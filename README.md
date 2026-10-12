# Sharpa Avatar App

Sharpa Avatar App is the official desktop application for device configuration, monitoring, firmware updates, and routine operations for Sharpa Avatar.

---

## 📥 Download

Download the latest production installer bundle from [Releases](https://github.com/sharpa-robotics/sharpa-avatar-app/releases).

Choose the archive that matches your system architecture:

```
avatar-app_linux_<arch>_prod_<version>.zip
```

---

## 🚀 Installation (Ubuntu / Debian)

Install the required system tools:

```bash
sudo apt update
sudo apt install -y unzip curl gnupg
```

Extract the downloaded release bundle and run its installer:

```bash
mkdir sharpa-avatar-installer
unzip avatar-app_linux_<arch>_prod_<version>.zip -d sharpa-avatar-installer
cd sharpa-avatar-installer
sudo bash ./install.sh
```

The supported installer:

1. installs the Sharpa Avatar USB device rule;
2. configures the Sharpa software repository;
3. installs the `sharpa-avatar` application package; and
4. installs a compatible `avatar-sdk` package through APT.

### Do not install the App `.deb` directly

The App `.deb` declares a dependency on a compatible Avatar SDK, but the `.deb` itself does not contain or download the SDK. Running `dpkg -i` directly can leave dependencies unresolved when the Sharpa software repository has not been configured.

Use the release bundle and `install.sh` as the supported installation path.

After installation, reconnect the USB device before launching the App.

---

## ▶️ Run

Launch **Sharpa Avatar** from the application menu.

You can also run:

```bash
/opt/sharpa-avatar/sharpa-avatar
```

---

## 📦 Avatar SDK

Sharpa Avatar App and Sharpa Avatar SDK are versioned and released separately.

The supported App installer installs a compatible SDK automatically. Each App package declares its minimum supported SDK version; APT selects an available SDK version that satisfies that requirement.

This is different from bundling one exact SDK inside the App package. Check the compatibility matrix for the supported combinations.

---

## 🔗 Compatibility

| Avatar App | Avatar SDK | Bundled firmware | Installation |
|---|---|---|---|
| 1.1.39 | 1.7.4 | 2.0.7 | Release ZIP installer |

This table will be updated with every public App release.

---

## 🔄 Update

Download the new production installer bundle from [Releases](https://github.com/sharpa-robotics/sharpa-avatar-app/releases), extract it, and run:

```bash
sudo bash ./install.sh
```

The installer refreshes the App and installs a compatible SDK.

---

## ❌ Uninstall

Remove the App:

```bash
sudo apt remove sharpa-avatar
```

To remove both the App and SDK:

```bash
sudo apt remove sharpa-avatar avatar-sdk
```

---

## ⚠️ Requirements

- Ubuntu or Debian-based Linux
- x86_64 (amd64) or ARM64, when an asset for that architecture is provided
- Network access during installation
- Administrator privileges for installation and device-rule setup

---

## Related downloads

- [Sharpa Avatar SDK](https://github.com/sharpa-robotics/sharpa-avatar-sdk)
- [Sharpa Avatar Firmware](https://github.com/sharpa-robotics/sharpa-avatar-ae01-firmware)

---

## 📞 Support

For product support, contact [support@sharpa.com](mailto:support@sharpa.com).
