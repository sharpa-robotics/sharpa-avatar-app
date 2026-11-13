# Sharpa Avatar

Sharpa Avatar is the desktop application for device configuration, monitoring,
firmware updates, and routine operations with Sharpa Avatar devices.

---

## 📥 Download

Download the latest `.deb` package from the Sharpa Software Hub:

👉 [Sharpa Avatar downloads](https://software-release-gateway.sharpa.com.cn/oss/latest/sharpa-avatar/linux)

Linux package names follow this format:

```text
sharpa-avatar_<version>_amd64.deb
```

---

## 🚀 Installation (Ubuntu)

Open a terminal in the directory containing the downloaded package and run:

```bash
sudo apt install ./sharpa-avatar_<version>_amd64.deb
```

Replace `<version>` with the version you downloaded. APT installs any missing
Ubuntu dependencies automatically; access to an Ubuntu package mirror may be
required.

If you prefer to use `dpkg`, run:

```bash
sudo dpkg -i sharpa-avatar_<version>_amd64.deb
sudo apt-get install -f
```

During a fresh installation, the matched SDK is set up automatically in the
background after the application package is installed. You can open the app while this is in
progress; the backend starts automatically when the SDK is ready.

---

## ▶️ Run

After installation, launch the application with:

```bash
sharpa-avatar
```

Or find **Sharpa Avatar** in your application menu.

Connect your device before using the application. If it is not accessible after
the first installation, unplug and reconnect it, then check again.

---

## 📦 SDK (Linux)

Sharpa Avatar ships with a **matched Avatar SDK** and manages its installation
automatically.

### Keep the application and SDK matched

- Upgrade or reinstall `sharpa-avatar` to install the SDK paired with that
  application release.
- Avoid installing, upgrading, or replacing `avatar-sdk` independently when
  using the desktop application.
- Do not replace SDK binaries or libraries under `/opt/avatar-sdk/` or alter
  the application's bundled SDK files under `/opt/sharpa-avatar/`.
- Use the application's settings for supported configuration changes.

For product releases, the installer reads `/opt/avatar-sdk/share/avatar-product.txt`
to preserve prod (`avatar-sdk`) or research (`avatar-sdk-research`). No SDK means
prod by default. Existing installations are updated through the configured APT
repository to the exact SDK version paired with the App.
The installer sets up the SDK version paired with the application. Existing
installations may require access to the configured APT repository.

The installer also checks and restores the complete USB device rules from the
selected SDK, even when that SDK version is already installed.

### Where files live (reference)

| Item                 | Path                                             |
| -------------------- | ------------------------------------------------ |
| Avatar application   | `/opt/sharpa-avatar/`                            |
| Installed Avatar SDK | `/opt/avatar-sdk/`                               |
| Backend binary       | `/opt/avatar-sdk/bin/avatar-backend`             |
| USB device rules     | `/etc/udev/rules.d/70-sharpa-avatar-glove.rules` |
| SDK installer log    | `/var/log/sharpa-avatar-bundled-sdk.log`         |
| Application logs     | `~/.sharpa-avatar/logs/`                         |

### Installation status and recovery

SDK installation status is recorded under `/var/lib/sharpa-avatar/`:

- `sdk-install.pending`: installation or retry is pending.
- `sdk-install.success`: SDK installation and device-rule setup completed.
- `sdk-install.failed`: an installation attempt failed; check the installer log.

On systems using systemd, retry a failed installation with:

```bash
sudo systemctl restart sharpa-avatar-bundled-sdk.service
```

Keep the app open while the installer retries; the backend starts when the
installation completes successfully.

---

## 🔄 Update

Product OTA runs `apt update` and installs the App with the exact matching SDK
from the existing prod/research line. The App restarts only after both packages
and the USB rules have been checked successfully. An APT or SDK failure stops
the update instead of switching SDK lines or using the bundled prod SDK as a
fallback.
The 1.2.3 updater installs the application and its matching SDK. The app
restarts only after both packages and the USB rules have been checked
successfully. An APT or SDK failure stops the update.

To update manually, download the newer `.deb` package and install it with:

```bash
sudo apt install ./sharpa-avatar_<new-version>_amd64.deb
```

To reinstall the same application version, download the intended package again
and run:

```bash
sudo apt install --reinstall ./sharpa-avatar_<version>_amd64.deb
```

---

## ❌ Uninstall

To remove the application:

```bash
sudo apt remove sharpa-avatar
```

Removing the application also removes its bundled-SDK installation service.
The separately installed `avatar-sdk` package and system USB device rules
remain installed.
The separately installed SDK package and system USB device rules remain
installed.

---

## ⚠️ Requirements

- Ubuntu 22.04, validated for this Linux release
- x86_64 / amd64 architecture
- Administrator privileges for installation and updates

---

## 📌 Notes

- This application is distributed through Sharpa Robotics' software hub.
- Keep the application and its matched SDK together when updating.
- Make sure the device is properly connected before use.

---

## 📞 Support

For issues or questions, contact the Sharpa Robotics development team.
Include the application version, SDK version, and relevant logs when reporting
an installation or connection issue.

