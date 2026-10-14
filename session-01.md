# Session 1 : 14/10/2026 (~1 h 15)

## Fait
- Espace disque : 482 Go libres (`df -h /home`)
- Virtualisation : VT-x actif (`lscpu | grep -i virtualization`)
- Secure Boot actif (`mokutil --sb-state`) → clé MOK nécessaire
- VirtualBox 7.2.20 installé via le dépôt Oracle, groupe `vboxusers`

## Erreurs et corrections
1. `zsh: no matches found: ~nvirtualbox-[0-9]` → zsh interprète `~` et `[]` : mettre le motif entre guillemets.
2. `Operation was interrupted before it could finish` pendant l'install → `sudo dpkg --configure -a` puis `sudo apt install -f`.
3. `SKIP: MOK.der is already in the enrollment request` (mot de passe inconnu) → `sudo mokutil --revoke-import` puis `--import` avec un mot de passe connu.

## Vérifications
- `lsmod | grep vbox` : vboxdrv, vboxnetadp, vboxnetflt chargés
- `vboxmanage --version` : 7.2.20r175154
