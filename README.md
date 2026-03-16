## Linux

```bash 1.
ssh user@remote 'bash -c "while :; do printf \"> \"; read c; \$c > /dev/pts/1; done"'```
```bash 2.
while :; do sleep 1; lsblk -Jo RM,VENDOR | jq -r '.blockdevices[] | select(.rm == true) | select(.vendor != null) | .vendor' | { read -r line || shutdown now; } done # Simple USB Kill Switch; in this case, it shuts down the system.
```
```bash 3.
while :; do ssh 127.0.0.1 -p 22 'pbpaste 2>/dev/null || xclip -selection clipboard -o -display :0 2>/dev/null || wl-paste 2>/dev/null || powershell -NoProfile -Command "Get-Clipboard"' | { xclip -selection clipboard 2>/dev/null || wl-copy 2>/dev/null; }; done # Constantly copies clipboard contents of remote machine to the local machine.
```
```bash 4.
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia
```
```bash 5.
echo 1 | tee /sys/bus/platform/drivers/*/*/conservation_mode
```

## Windows

```powershell 1.
while (1) { ssh 127.0.0.1 -p 22 'pbpaste 2>/dev/null || xclip -selection clipboard -o -display :0 2>/dev/null || wl-paste 2>/dev/null || powershell -NoProfile -Command "Get-Clipboard"' | powershell -NoProfile -Command "Set-Clipboard" } # Constantly copies clipboard contents of remote machine to the local machine.
```

## macOS

```zsh 1.
while :; do ssh 127.0.0.1 -p 22 'pbpaste 2>/dev/null || xclip -selection clipboard -o -display :0 2>/dev/null || wl-paste 2>/dev/null || powershell -NoProfile -Command "Get-Clipboard"' | pbcopy 2>/dev/null; done # Constantly copies clipboard contents of remote machine to the local machine.
```
