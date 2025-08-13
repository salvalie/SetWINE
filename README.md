
---

# SetWine

---

## 📖 Description (English)

SetWine is a Bash script that installs and configures Wine/Proton WoW64 x86\_64 builds with NTsync, DXVK, and Wayland support on Linux.
It uses builds from [Kron4ek's Wine-Builds](https://github.com/Kron4ek/Wine-Builds) and allows running 64-bit, 32-bit, and even 16-bit Windows applications on a pure 64-bit (x86\_64) system.

---

### 🛠 Features

* Downloads and installs the latest **Wine WoW64** or **Proton WoW64** from Kron4ek.
* Always uses **NTsync-enabled** versions.
* Optional **DXVK** setup for DirectX 8/9/10/11.
* Enables **Wayland** support if available.
* Auto-configuration of **Winetricks** for unattended use.
* **Desktop integration**: Associates `.exe`, `.msi`, `.bat` files with Wine.
* Includes **wineshort2desktop**: Creates `.desktop` launchers with icons extracted from `.exe` files.
* Optional **kill shortcut**: `Ctrl+Alt+Q` to terminate all Wine processes.
* **Safe to uninstall**: No risk of breaking system packages.
* Supports 16-bit Windows apps with [winevdm](https://github.com/otya128/winevdm) (on wine-tkg).

---

### 📦 Requirements

* `wget`, `tar`, `unzip`
* `bash`, `grep`, `awk`
* No other Wine installation present
* Vulkan/DXVK-capable x86\_64 hardware

---

### 🚀 Installation

```bash
git clone https://github.com/yourname/SetWine.git
cd SetWine
chmod +x setwine
./setwine
```

### 🚮 Uninstallation

```bash
./setwine uninstall
```

---

### ⚙️ What it does

1. Checks:

   * Internet connection
   * CPU architecture (`x86_64`)
   * Existing Wine installations
   * (Optional) Recommends CachyOS

2. Downloads & installs Wine from Kron4ek:

   * `wine-staging-tkg-ntsync-amd64-wow64`
   * `wine-proton-amd64-wow64`

3. Adds wrapper scripts & symlinks to `~/.local/bin` (ensures it's in `PATH`).

4. Installs **Winetricks**.

5. Initializes the Wine prefix (`~/.wine`).

6. Offers DXVK installation (3 versions).

7. Enables Wayland support if possible.

8. Creates a Wine `.desktop` launcher & MIME associations.

9. Optionally sets up `Ctrl+Alt+Q` shortcut to kill Wine.

10. Installs **wineshort2desktop** for easy `.exe` launcher creation.

11. Installs **winevdm** for 16-bit app support.

---

### 💡 Shortcut creator example

```bash
wineshort2desktop MyGame.exe "My Game"
```

---

## 📖 Descripción (Español)

SetWine es un script en Bash para instalar y configurar compilaciones de Wine/Proton WoW64 x86\_64 con soporte NTsync, DXVK y Wayland en Linux.
Usa compilaciones de [Kron4ek Wine-Builds](https://github.com/Kron4ek/Wine-Builds) y permite correr aplicaciones de Windows de 64, 32 y 16 bits en un sistema puro de 64 bits (x86\_64).

---

### 🛠 Características

* Descarga e instala las últimas **Wine WoW64** o **Proton WoW64** desde Kron4ek.
* Siempre usa versiones con **NTsync** habilitado.
* Configuración opcional de **DXVK** para DirectX 8/9/10/11.
* Habilita soporte **Wayland** si está disponible.
* Configura automáticamente **Winetricks** para uso sin intervención.
* **Integración de escritorio**: asocia `.exe`, `.msi`, `.bat` a Wine.
* Incluye **wineshort2desktop**: crea lanzadores `.desktop` con íconos extraídos de `.exe`.
* Atajo opcional **Ctrl+Alt+Q** para terminar procesos de Wine.
* **Seguro de desinstalar**: no daña paquetes del sistema.
* Soporte para apps de 16 bits con [winevdm](https://github.com/otya128/winevdm) (en wine-tkg).

---

### 📦 Requisitos

* `wget`, `tar`, `unzip`
* `bash`, `grep`, `awk`
* No tener Wine instalado por otro método
* Hardware x86\_64 con soporte Vulkan/DXVK

---

### 🚀 Instalación

```bash
git clone https://github.com/yourname/SetWine.git
cd SetWine
chmod +x setwine_español
./setwine_español
```

### 🚮 Desinstalación

```bash
./setwine_español uninstall
```

---

### ⚙️ Qué hace

1. Verifica:

   * Conexión a internet
   * Arquitectura de CPU (`x86_64`)
   * Instalaciones previas de Wine
   * (Opcional) Recomienda CachyOS

2. Descarga e instala Wine desde Kron4ek:

   * `wine-staging-tkg-ntsync-amd64-wow64`
   * `wine-proton-amd64-wow64`

3. Añade scripts wrapper y enlaces simbólicos en `~/.local/bin` (asegura que esté en `PATH`).

4. Instala **Winetricks**.

5. Inicializa el prefijo Wine (`~/.wine`).

6. Ofrece instalar DXVK (3 versiones).

7. Habilita soporte para Wayland si es posible.

8. Crea un lanzador `.desktop` y asociaciones MIME para Wine.

9. Opcionalmente configura `Ctrl+Alt+Q` para matar procesos de Wine.

10. Instala **wineshort2desktop** para crear lanzadores de `.exe`.

11. Instala **winevdm** para soporte de apps de 16 bits.

---

### 💡 Ejemplo con creador de accesos directos

```bash
wineshort2desktop MiJuego.exe "Mi Juego"
```

---

Si querés, puedo además dejarte **la tabla de inglés ↔ español lado a lado** para que el README sea bilingüe y no tengas que mantener dos bloques separados. Eso haría que quede aún más prolijo y fácil de mantener.
