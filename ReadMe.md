
# 🛡️ WireGuard Auto-Peer Manager

Un script Python pour automatiser l'ajout de clients (Peers) à un serveur WireGuard existant. Il génère les clés, configure les IPs, met à jour le serveur à chaud et affiche un QR Code.

## 📋 Prérequis

1. **WireGuard installé et configuré** :
   Le serveur doit être fonctionnel. Le script s'attend à trouver les fichiers suivants :
   ```text
   /etc/wireguard/
   ├── privatekey    # Clé privée du serveur
   ├── publickey     # Clé publique du serveur
   └── wg0.conf      # Configuration de l'interface

2. **Dépendances système** : Le script a besoin de Python 3 et de qrencode pour l'affichage terminal.
   ```sh
   sudo apt update
   sudo apt install wireguard-tools qrencode -y
   ```
   
   Editer `nano /etc/sysctl.conf`
   ```sh
   net.ipv4.ip_forward=1
   net.ipv6.conf.all.forwarding=1
   ```
   `sudo sysctl -p`

## 💻 Utilisation

```sh
sudo wg-init
sudo wg-add <nom>
sudo wg-remove <nom>
sudo wg-list
```
## Fonctionnalités
- ✅ Génération automatique des clés (Privée/Publique/PSK).
- ✅ Attribution d'IP : Recherche automatique d'une IP libre dans le sous-réseau.
- ✅ Mise à jour à chaud : Utilise wg syncconf pour ne pas couper les connexions existantes.
- ✅ QR Code : Affiché directement dans le terminal pour scanner avec l'app mobile.
- ✅ Sauvegarde : Les fichiers de config générés sont sauvegardés localement.
- 🛑 Support IPv6 : Attribution automatique d’une IP IPv6 et gestion dual-stack non encore activée
