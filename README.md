# SetWine/Proton


---

SetWine is a Bash script for installing and configuring Wine/Proton WoW64 x86_64 builds with NTsync, DXVK, and Wayland support on Linux systems.  
The script supports Wine and Proton from Kron4ek Repo.

---

## 🛠 Features

- Downloads and installs the latest Wine WoW64 or Proton WoW64 builds from Kron4ek https://github.com/Kron4ek/Wine-Builds.
- Automatically installs NTsync-enabled versions.
- Optionally sets up DXVK for DirectX 8/9/10/11 support.
- Configures Wine to run through `wayland` if available.
- Simplifies Wine setup for gaming or application use.
- Auto-setup of Winetricks: Downloaded and configured to work unattended.
- Creates useful desktop associations**: Associates `.exe`, `.msi`, `.bat`, etc. with Wine.
- Desktop shortcut creator: A tool called `wineshort2desktop` is installed to generate `.desktop` launchers with auto-extracted icons from `.exe` files.
- Tries to create a custom kill shortcut: Sets up a `Ctrl+Alt+Q` shortcut to kill Wine processes on supported desktops.
- Safe by design: Can be removed easily. No risk of corrupting your system install.

---

## 📦 Requirements

- `wget`, `tar`, `unzip`
- `bash`, `grep`, `awk`
- `wine` not being installed by any other way.
- a vulkan dxvk capable x86_64 HW.

---

## 🚀 Installation

Clone the repository and run the script:

```bash
git clone https://github.com/yourname/SetWine.git
cd SetWine
chmod +x setwine
./setwine
```


---

## ⚙️ What the script does

1. Verifies:
   - Internet connection
   - CPU architecture (`x86_64` required)
   - Existing Wine installations
   - Recommended: CachyOS (but works elsewhere)

2. Downloads and installs Wine from [Kron4ek GitHub releases](https://github.com/Kron4ek/Wine-Builds):
   - `wine-staging-tkg-ntsync-amd64-wow64`
   - `wine-proton-amd64-wow64`

3. Adds wrapper scripts and symbolic links to `~/.local/bin`, and ensures this path is in your shell’s `PATH`.

4. Downloads and installs `winetricks`.

5. Initializes the Wine prefix (`~/.wine`).

6. Offers to install DXVK (three selectable versions).

7. Enables Wayland support if available.

8. Creates a Wine `.desktop` launcher and configures MIME types.

9. Sets up a keyboard shortcut (`Ctrl+Alt+Q`) to kill Wine processes via `wineserver -k`.

10. Installs `wineshort2desktop`:
    - Lets you create launchers for `.exe` games/apps with icons extracted from the binaries.

---

## 🚀 Quick usage example for shortcut creator

```bash
wineshort2desktop MyGame.exe "My Game"
```

---

# SetWine/Proton

SetWine es un script en Bash para instalar y configurar compilaciones de Wine/Proton WoW64 x86_64 con soporte NTsync, DXVK y Wayland en sistemas Linux.  
El script soporta Wine y Proton desde el repositorio de Kron4ek.

---

## 🛠 Características

- Descarga e instala las últimas versiones de Wine WoW64 o Proton WoW64 desde Kron4ek https://github.com/Kron4ek/Wine-Builds.  
- Instala automáticamente versiones con NTsync habilitado.  
- Opcionalmente configura DXVK para soporte de DirectX 8/9/10/11.  
- Configura Wine para correr sobre `wayland` si está disponible.  
- Simplifica la configuración de Wine para juegos o aplicaciones.  
- Configuración automática de Winetricks: descargado y configurado para funcionar sin intervención.  
- Crea asociaciones útiles en el escritorio: asocia `.exe`, `.msi`, `.bat`, etc. con Wine.  
- Creador de accesos directos de escritorio: instala `wineshort2desktop` para generar lanzadores `.desktop` con íconos extraídos automáticamente de los archivos `.exe`.  
- Intenta crear un atajo personalizado para matar procesos: configura un atajo `Ctrl+Alt+Q` para terminar procesos de Wine en escritorios compatibles.  
- Seguro por diseño: se puede eliminar fácilmente. Sin riesgo de dañar tu instalación del sistema.

---

## 📦 Requisitos

- `wget`, `tar`, `unzip`  
- `bash`, `grep`, `awk`  
- Wine no debe estar instalado por otro método.  
- Hardware x86_64 con soporte Vulkan y DXVK.

---

## 🚀 Instalación

Clona el repositorio y ejecuta el script:

```bash
git clone https://github.com/yourname/SetWine.git
cd SetWine
chmod +x setwine
./setwine
```

---

## ⚙️ Qué hace el script

- Verifica:  
  - Conexión a internet  
  - Arquitectura de CPU (`x86_64` requerida)  
  - Instalaciones previas de Wine  
  - Recomendado: CachyOS (pero funciona en otros sistemas)

- Descarga e instala Wine desde lanzamientos GitHub de Kron4ek:  
  - `wine-staging-tkg-ntsync-amd64-wow64`  
  - `wine-proton-amd64-wow64`

- Añade scripts wrapper y enlaces simbólicos en `~/.local/bin`, asegurando que esta ruta esté en el `PATH` del shell.

- Descarga e instala `winetricks`.

- Inicializa el prefijo Wine (`~/.wine`).

- Ofrece instalar DXVK (tres versiones seleccionables).

- Habilita soporte para Wayland si está disponible.

- Crea un lanzador `.desktop` para Wine y configura tipos MIME.

- Configura un atajo de teclado (`Ctrl+Alt+Q`) para terminar procesos de Wine con `wineserver -k`.

- Instala `wineshort2desktop`:  
  - Permite crear lanzadores para juegos/aplicaciones `.exe` con íconos extraídos de los binarios.

---

```bash
wineshort2desktop MiJuego.exe "Mi Juego"
```