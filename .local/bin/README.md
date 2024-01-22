# Table of contents

- [enable_touch](#touch)
- [monitor](#monitor)
- [toradd](#toradd)
- [tordone](#tordone)

## enable_touch

Script enables touchpad on laptop.

```bash
ID=$(xinput | awk -F'id=' '/Touch/ {print $2}' | awk '{print $1}')
ID_TAP=$(xinput list-props "${ID}" | awk -F'[()]' '/Tapping Enabled \(/ {print $2}')

xinput set-prop "${ID}" "${ID_TAP}" 1
```

## monitor

*Monitor* script allows manipulation with connected monitors. Script uses dmenu as a menu for selectiong monitors and positions for their displaying.

To simplify the use of the script the following line might be used in configuration file of window manager(i3 in my case).

```bash
bindsym --release Mod1+c exec monitor
```

## toradd

The script adds a new torrent file to the queue and sends notifications using notify-send.

```bash
transmission-remote -a "#{@}" && notify-send "Transmission status" "Torrent added"
```

## tordone

Script runs every time torrent is downloaded.


```bash
notify-send "Transmission status" "Torrent ${TR_TORRENT_NAME} has been downloaded successfully"
```
