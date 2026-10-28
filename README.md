# Arch Linux: Post-Instalaciòn

Guía rápida para instalar Arch Linux desde el USB booteado usando el instalador guiado `archinstall`.

---

## Cambiar el idioma del teclado

```bash
loadkeys es
```

Ver las distribuciones de teclado disponibles:

```bash
localectl list-keymaps | grep -i es
```

---

## Conectar el wifi

> Solo si lo necesitas (con cable de red normalmente ya hay conexión).

Abrir `iwctl`:

```bash
iwctl
```

Dentro de `iwctl`:

```text
# Ver el nombre del adaptador
device list

# Buscar redes
station wlan0 scan
station wlan0 get-networks

# Conectarse (pedirá la contraseña)
station wlan0 connect "Nombre_de_tu_red"

# Comprobar la conexión
station wlan0 show
exit
```

> Cambia `wlan0` por el nombre que te salga en `device list`.

Probar internet:

```bash
ping -c 3 archlinux.org
```

---

## Iniciar el instalador

```bash
archinstall
```

---

## Opciones del menú

| Opción | Qué elegir |
|---|---|
| **Archinstall language** | Español (si quieres el instalador en español) |
| **Mirrors and repositories** | Región: `Spain` |
| **Locales** | Teclado: `es` · Idioma: `es_ES.UTF-8` |
| **Disk configuration** | `Use a best-effort default partition layout`, elige tu disco y el sistema de archivos (`ext4` es lo más simple) |
| **Bootloader** | `Grub` (o `systemd-boot` si usas UEFI) |
| **Hostname** | El nombre de tu equipo, por ejemplo `miarch` |
| **Root password** | Contraseña de root |
| **User account** | Añade un usuario y márcalo como **sudo** (superuser: yes) |
| **Profile** | `Minimal` (solo terminal) o `Desktop` (XFCE, KDE, GNOME...) |
| **Audio** | `pipewire` |
| **Network configuration** | `Use NetworkManager` (importante para tener wifi al reiniciar) |
| **Timezone** | `Europe/Madrid` |
| **Automatic time sync (NTP)** | Activado |
| **Additional packages** | Opcional, por ejemplo: `nano git htop` |

> ⚠️ **Cuidado:** *Disk configuration* borra el disco que elijas. Verifica que es el correcto.

---

## Finalizar

Al acabar, el instalador preguntará si quieres entrar en el sistema con `chroot`. Puedes responder **no**. Después:

```bash
reboot
```

Quita el USB al reiniciar.

✅ **Listo**
