# Analyse DLMS/COSEM avec Wireshark

Outils Lua pour analyser les échanges **DLMS/COSEM** dans Wireshark, notamment les trames HDLC et les messages applicatifs associés au comptage intelligent.

> Ce dépôt conserve le travail original du dissector DLMS attribué à Petr Matousek (Brno University of Technology). Il sert ici de base d’étude et d’analyse pour les protocoles de comptage intelligent.

## Cas d’usage

- Lecture et décodage de trames DLMS/COSEM capturées sur réseau
- Analyse des associations **AARQ/AARE**
- Inspection des requêtes et réponses **GET/SET** en LN referencing
- Étude du transport **HDLC** ou du wrapper DLMS sur TCP/IP

## Contenu

| Fichier | Rôle |
|---|---|
| `dlms.lua` | Dissecteur de la couche DLMS et des messages applicatifs |
| `hdlc.lua` | Dissecteur HDLC format 3 et appel du dissector DLMS |
| `wrapper-dlms.lua` | Extraction de messages DLMS encapsulés dans un wrapper TCP/IP |
| `pcap-examples/` | Captures réseau d’exemple |
| `DLSM-description.pdf` | Documentation de référence incluse |

## Installation dans Wireshark

1. Vérifier que votre installation de Wireshark inclut le support **Lua**.
2. Ouvrir **Help → About Wireshark → Folders** et repérer le dossier *Personal Plugins*.
3. Copier les scripts Lua nécessaires dans ce dossier.
4. Redémarrer Wireshark.
5. Si nécessaire, utiliser **Decode As…** pour associer un flux au protocole HDLC ou DLMS Wrapper.

## Périmètre actuel

Le dissector couvre notamment les messages AARQ/AARE et les requêtes/réponses GET/SET en LN referencing. Les APDU chiffrées et le réassemblage complet des segments HDLC ne sont pas pris en charge par cette version.

## Notes

Ce dépôt est destiné à l’analyse et à l’apprentissage du protocole. Avant utilisation sur un environnement de production, validez les règles de sécurité, les clés et les paramètres d’association applicables.