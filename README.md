# SetWINE

## 📖 Description

SetWINE is a Bash script that installs and configures Wine/Proton WoW64 x86_64 builds with NTsync, DXVK, and Wayland support on Linux. The idea is to keep the setup simple in your home folder, making it easier to swap to different Wine versions. At the end, you'll have full control over your Wine or Proton setup, while keeping the setup clean and easy to uninstall completely.

It uses builds from [Kron4ek's Wine-Builds](https://github.com/Kron4ek/Wine-Builds) and allows running 64-bit, 32-bit, and even 16-bit Windows applications on a pure 64-bit (x86_64) system.

---

### 🛠 Features

*   Downloads and installs the latest **Wine WoW64** or **Proton WoW64** from Kron4ek.
*   Always uses **NTsync-enabled** versions if available.
*   Optional **DXVK** setup for DirectX 8/9/10/11.
*   Enables **Wayland** support if available.
*   Auto-configuration of **Winetricks** for unattended use.
*   **Desktop integration**: Associates `.exe`, `.msi`, `.bat` files with Wine.
*   Includes **wineshort2desktop**: Creates `.desktop` launchers with icons extracted from `.exe` files.
*   Optional **kill shortcut**: `Ctrl+Alt+Q` to terminate all Wine processes.
*   **Safe to uninstall**: No risk of breaking system packages.
*   Supports 16-bit Windows apps with [winevdm](https://github.com/otya128/winevdm) (on wine-tkg).

---

### 📦 Requirements

*   `wget`, `tar`, `unzip`, `dialog`
*   `bash`, `grep`, `awk`
*   No other Wine installation present
*   Vulkan/DXVK-capable x86_64 hardware

---

### 🚀 Installation

To quickly download and run SetWINE, use the following command:

```bash
curl -sL https://raw.githubusercontent.com/salvalie/SetWINE/main/setwine -o setwine && chmod +x setwine && ./setwine
```

Alternatively, you can clone the repository:

```bash
git clone https://github.com/salvalie/SetWINE.git
cd SetWINE
chmod +x setwine
./setwine
```

### 🚮 Uninstallation

```bash
./setwine uninstall
```

---

### ⚙️ What it does

1.  **Checks**:
    *   Internet connection
    *   CPU architecture (`x86_64`)
    *   Existing Wine installations
    *   Kernel version for NTsync compatibility

2.  **Downloads & installs Wine from Kron4ek**:
    *   `wine-staging-tkg-ntsync-amd64-wow64`
    *   `wine-proton-amd64-wow64`

3.  **Adds wrapper scripts & symlinks** to `~/.local/bin` (ensures it's in `PATH`).

4.  **Installs Winetricks**.

5.  **Initializes the Wine prefix** (`~/.wine`).

6.  **Offers DXVK installation** (multiple versions).

7.  **Enables Wayland support** if possible.

8.  **Creates a Wine `.desktop` launcher** & MIME associations.

9.  **Optionally sets up `Ctrl+Alt+Q` shortcut** to kill Wine.

10. **Installs `wineshort2desktop`** for easy `.exe` launcher creation.

11. **Installs `winevdm`** for 16-bit app support.

---

### 💡 Shortcut creator example

```bash
wineshort2desktop MyGame.exe "My Game"
```
