# SetWINE

An opinionated, **home-located Wine environment** for Linux distros on **x86_64/amd64**: a fast, fully guided setup that needs **no root**, touches nothing outside your `$HOME`, and is trivial to replace or remove.

## Quick run

Paste this in a terminal to download SetWINE into your home folder, make it executable and start it right away:

```bash
curl -fsSL https://raw.githubusercontent.com/salvalie/SetWINE/main/setwine -o ~/setwine && chmod +x ~/setwine && ~/setwine
```

The script is saved as `~/setwine`, so you can review it first or re-run it anytime with `./setwine`.

## Why?

Most Wine setups involve system packages, root privileges, and files scattered across `/usr`. SetWINE does the opposite: it downloads a self-contained Wine build and wires up everything around it inside your home directory, so you get a working gaming-ready Wine stack in minutes — and `setwine uninstall` reverts everything cleanly.

## What it installs

Everything lives under your `$HOME`:

| Location | Purpose |
|---|---|
| `~/.local/wine` | The Wine build itself (Wine-staging-tkg **ntsync** or **Proton WoW64**, from [Kron4ek/Wine-Builds](https://github.com/Kron4ek/Wine-Builds)) |
| `~/.local/bin/wine` | Wrapper: fsync, MangoHud, native d3d DLL overrides, prevents sleep/idle via `systemd-inhibit` |
| `~/.local/bin/winecfg`, `wineserver`, `wineboot` | Symlinks to the build |
| `~/.local/bin/winetricks` | Latest upstream, unattended mode |
| `~/.local/bin/wined` | Run an `.exe` with full log + filtered error log |
| `~/.local/bin/winemode` | Toggle Wine graphics driver between **Wayland ↔ X11** |
| `~/.local/bin/wineshortcut` | Turn any `.exe` into a desktop shortcut with its icon extracted |
| `~/.local/share/applications/wine.desktop` | Double-click handler for `.exe` / `.msi` |
| `~/.wine` | Fresh Wine prefix (your C: drive) |
| DXVK + VKD3D | Installed into the prefix via winetricks |
| `Ctrl+Alt+Q` | "Wine killer": instantly terminates Wine (`wineserver -k`). Supported on GNOME, XFCE, KDE (manual), Cinnamon, Openbox |

Also configures `~/.local/bin` in your `PATH` (`~/.profile`, `~/.xprofile`).

Re-running the installer replaces the Wine build but **never touches your prefix** (`~/.wine`) or installed games. All noisy output goes to logs in `~/.cache/setwine/`.

## Usage

```bash
./setwine                 # interactive installation
./setwine -v              # same, echoing every underlying command live
./setwine uninstall       # revert everything SetWINE did*
./setwine help            # show help
```

\* Except `~/.cache/winetricks` (kept on purpose). Your prefix `~/.wine` is only removed if you explicitly confirm it.

### Requirements

- Linux on **x86_64 / amd64**
- Bash 4+, `wget`, `unzip`, `ping`
- `cabextract` (for most winetricks verbs)
- `icoutils` (provides `wrestool`, for icon extraction)
- `imagemagick` (provides `convert`/`identify`, for icon conversion)
- `zenity` (for `wineshortcut` name dialog)
- A Vulkan driver (Mesa, NVIDIA proprietary, etc.) for DXVK/D7VK
- `systemd` (for sleep inhibitor in the wine wrapper)
- A supported desktop environment for `Ctrl+Alt+Q` hotkeys: GNOME, XFCE, KDE (manual setup), Cinnamon, Hyprland, Openbox, Mango WM, or manually in other environments

## Credits

This project was developed with the assistance of [opencode](https://opencode.ai) and LLMs. All directives, decisions, and supervision were human.

### Acknowledgments

SetWINE exists because of the incredible work done by these projects and their developers. Linux gaming on Wine wouldn't be what it is today without them:

- **[Wine](https://www.winehq.org/)** — The foundation of everything. Decades of work translating Windows APIs to Linux, making it possible to run Windows games natively.
- **[Wine-staging-tkg / Proton](https://github.com/Kron4ek/Wine-Builds)** — Kron4ek's builds provide optimized Wine versions with modern patches (ntsync, WoW64) that make gaming just work.
- **[DXVK](https://github.com/doitsujin/dxvk)** — The DirectX 9/10/11 to Vulkan translation layer that transformed Wine gaming performance. Without it, most modern games would be unplayable.
- **[D7VK](https://github.com/WinterSnowfall/d7vk)** — DirectX 2-7 to Vulkan translation, bringing old-school 3D games into the Vulkan era with impressive performance even on integrated GPUs.
- **[cnc-ddraw](https://github.com/narzoul/cnc-ddraw)** — The DirectDraw wrapper that fixes countless classic games that would otherwise refuse to run or render incorrectly.
- **[VKD3D](https://code.winehq.org/git/vkd3d.git)** — The Direct3D 12 to Vulkan implementation, extending Vulkan coverage to newer APIs.
- **[Winetricks](https://github.com/Winetricks/winetricks)** — The Swiss Army knife for installing Windows DLLs, runtimes, and libraries into Wine prefixes.
- **[otvdm](https://github.com/narzoul/otvdm)** — The 16-bit emulation layer that makes legacy Win16 applications runnable on modern Wine WoW64 setups.
- **[Numix Project](https://numixproject.github.io/)** — Beautiful icon themes that make Linux desktops shine. Icons used under GPL-3.0+.

A personal thank you to all the developers and contributors of these projects. You've made Linux gaming not just possible, but genuinely enjoyable.

---

# SetWINE (Español)

Un entorno Wine **ubicado en tu HOME** y con opiniones para distribuciones Linux en **x86_64/amd64**: una instalación rápida y totalmente guiada que **no necesita root**, no toca nada fuera de tu `$HOME`, y es trivial de reemplazar o eliminar.

## Ejecución rápida

Pega esto en una terminal para descargar SetWINE en tu carpeta personal, darle permisos de ejecución y arrancarlo al momento:

```bash
curl -fsSL https://raw.githubusercontent.com/salvalie/SetWINE/main/setwine -o ~/setwine && chmod +x ~/setwine && ~/setwine
```

El script queda guardado como `~/setwine`, así que puedes revisarlo antes o volver a ejecutarlo cuando quieras con `./setwine`.

## ¿Por qué?

La mayoría de las instalaciones de Wine implican paquetes del sistema, privilegios de root y archivos repartidos por `/usr`. SetWINE hace lo contrario: descarga un build autocontenido de Wine y configura todo lo necesario dentro de tu directorio personal, para tener un entorno Wine listo para juegos en minutos — y `setwine uninstall` revierte todo limpiamente.

## Qué instala

Todo vive bajo tu `$HOME`:

| Ubicación | Propósito |
|---|---|
| `~/.local/wine` | El build de Wine en sí (Wine-staging-tkg **ntsync** o **Proton WoW64**, de [Kron4ek/Wine-Builds](https://github.com/Kron4ek/Wine-Builds)) |
| `~/.local/bin/wine` | Wrapper: fsync, MangoHud, overrides nativos de DLLs d3d, evita suspensión/inactividad vía `systemd-inhibit` |
| `~/.local/bin/winecfg`, `wineserver`, `wineboot` | Enlaces simbólicos al build |
| `~/.local/bin/winetricks` | Última versión upstream, modo desatendido |
| `~/.local/bin/wined` | Ejecuta un `.exe` con log completo + log de errores filtrado |
| `~/.local/bin/winemode` | Alterna el driver gráfico de Wine entre **Wayland ↔ X11** |
| `~/.local/bin/wineshortcut` | Convierte cualquier `.exe` en un acceso directo de escritorio con su icono extraído |
| `~/.local/share/applications/wine.desktop` | Manejador de doble clic para `.exe` / `.msi` |
| `~/.wine` | Prefijo Wine nuevo (tu unidad C:) |
| DXVK + VKD3D | Instalados en el prefijo vía winetricks |
| `Ctrl+Alt+Q` | "Asesino de Wine": termina Wine al instante (`wineserver -k`). Soportado en GNOME, XFCE, KDE (manual), Cinnamon, Openbox |

También configura `~/.local/bin` en tu `PATH` (`~/.profile`, `~/.xprofile`).

Volver a ejecutar el instalador reemplaza el build de Wine pero **nunca toca tu prefijo** (`~/.wine`) ni los juegos instalados. Toda la salida ruidosa va a logs en `~/.cache/setwine/`.

## Uso

```bash
./setwine                 # instalación interactiva
./setwine -v              # lo mismo, mostrando cada comando subyacente en vivo
./setwine uninstall       # revertir todo lo que hizo SetWINE*
./setwine help            # mostrar ayuda
```

\* Excepto `~/.cache/winetricks` (se conserva a propósito). Tu prefijo `~/.wine` solo se elimina si lo confirmas explícitamente.

### Requisitos

- Linux en **x86_64 / amd64**
- Bash 4+, `wget`, `unzip`, `ping`
- `cabextract` (para la mayoría de verbos de winetricks)
- `icoutils` (provee `wrestool`, para extraer iconos)
- `imagemagick` (provee `convert`/`identify`, para convertir iconos)
- `zenity` (para el diálogo de nombre de `wineshortcut`)
- Un driver Vulkan (Mesa, NVIDIA propietario, etc.) para DXVK/D7VK
- `systemd` (para el inhibidor de suspensión en el wrapper de wine)
- Un entorno de escritorio soportado para los atajos `Ctrl+Alt+Q`: GNOME, XFCE, KDE (configuración manual), Cinnamon, Hyprland, Openbox, Mango WM, o configuración manual en otros entornos

## Créditos

Este proyecto fue desarrollado con la asistencia de [opencode](https://opencode.ai) y LLMs. Todas las directivas, decisiones y la supervisión fueron humanas.

### Agradecimientos

SetWINE existe gracias al increíble trabajo de estos proyectos y sus desarrolladores. El gaming en Linux con Wine no sería lo que es hoy sin ellos:

- **[Wine](https://www.winehq.org/)** — La base de todo. Décadas de trabajo traduciendo APIs de Windows a Linux, haciendo posible ejecutar juegos de Windows de forma nativa.
- **[Wine-staging-tkg / Proton](https://github.com/Kron4ek/Wine-Builds)** — Los builds de Kron4ek proporcionan versiones optimizadas de Wine con parches modernos (ntsync, WoW64) que hacen que el gaming funcione.
- **[DXVK](https://github.com/doitsujin/dxvk)** — La capa de traducción de DirectX 9/10/11 a Vulkan que transformó el rendimiento del gaming en Wine. Sin él, la mayoría de juegos modernos serían injugables.
- **[D7VK](https://github.com/WinterSnowfall/d7vk)** — Traducción de DirectX 2-7 a Vulkan, trayendo juegos 3D clásicos a la era de Vulkan con rendimiento impresionante incluso en GPUs integradas.
- **[cnc-ddraw](https://github.com/narzoul/cnc-ddraw)** — El wrapper de DirectDraw que arregla innumerables juegos clásicos que de otro modo se negarían a ejecutarse o renderizarían incorrectamente.
- **[VKD3D](https://code.winehq.org/git/vkd3d.git)** — La implementación de Direct3D 12 a Vulkan, extendiendo la cobertura de Vulkan a APIs más modernas.
- **[Winetricks](https://github.com/Winetricks/winetricks)** — El cuchillo suizo para instalar DLLs de Windows, runtimes y bibliotecas en prefijos de Wine.
- **[otvdm](https://github.com/narzoul/otvdm)** — La capa de emulación de 16-bit que hace posible ejecutar aplicaciones Win16 heredadas en configuraciones modernas de Wine WoW64.
- **[Numix Project](https://numixproject.github.io/)** — Hermosos temas de iconos que hacen brillar el escritorio de Linux. Iconos usados bajo GPL-3.0+.

Un agradecimiento personal a todos los desarrolladores y contribuidores de estos proyectos. Han hecho que el gaming en Linux no solo sea posible, sino genuinamente disfrutable.
