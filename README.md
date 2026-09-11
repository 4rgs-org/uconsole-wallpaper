# uconsole-wallpaper

>Cycle the current Omarchy theme's wallpapers and apply them to Sway immediately.

Wraps `omarchy-theme-bg-next` to advance the wallpaper and then restarts `swaybg` against the new path, because the long-lived `swaybg` instance spawned at login does not follow the Omarchy symlink. Without this wrapper, the wallpaper state advances but the visible background does not.

## Demo

```
[screenshot placeholder]
```

## Dependencies

- Sway, `omarchy-theme-bg-next` from the Omarchy toolset
- `bash` o `sh` para el `install.sh`
- glibc estándar

## Install

Una línea, vía curl al instalador del repo:

```sh
curl -sSL https://raw.githubusercontent.com/4rgs-org/uconsole-wallpaper/main/install.sh | sh
```


Para una versión específica:

```sh
curl -sSL https://raw.githubusercontent.com/4rgs-org/uconsole-wallpaper/main/install.sh | sh -s -- --tag v0.1.0
```

Para instalar en otro directorio (útil para `~/.local/bin` sin root):

```sh
INSTALL_DIR=$HOME/.local/bin REPO=uconsole-wallpaper bash install.sh
```

El instalador:
- Detecta la arquitectura con `uname -m` (aarch64, x86_64, armv7).
- Baja el tarball de la release seleccionada.
- Verifica `SHA256SUMS` antes de extraer.
- Copia el binario a `/usr/local/bin/uconsole-wallpaper` (o el destino elegido).

## Post-install

Vinculalo al menú:

```diff
- {Icon: " ", Label: "Wallpaper", Action: "omarchy-theme-bg-next"},
+ {Icon: " ", Label: "Wallpaper", Action: "uconsole-wallpaper"},
```

## Build from source

```sh
git clone https://github.com/4rgs-org/uconsole-wallpaper
cd uconsole-wallpaper
go build -o uconsole-wallpaper .
sudo install -m 0755 uconsole-wallpaper /usr/local/bin/uconsole-wallpaper
```

## Usage

| Acción | Resultado |
| --- | --- |
| `(sin argumentos)` | Avanza al siguiente wallpaper del tema activo y reinicia `swaybg`. |

## License

MIT — ver [LICENSE](LICENSE).

## Liability

Software is provided as-is. The maintainers are not responsible for loss of work or data caused by accidental command execution. Always confirm the menu entry before pressing Enter.
