---
title: "Regarder la télévision britannique en ligne en dehors du Royaume-Uni"
sub_title: "Utilisation d'un Raspberry Pi 4 et du NordVPN"
date: 2020-09-01T23:27:48+02:00
slug: "regarder-television-britannique"
images:
    -  /uk_tv_pi/uk-tv-pi-600.jpg
    -  /uk_tv_pi/uk-tv-pi-800.jpg
summary: "Dans ce tutoriel, je montrerai comment regarder la télévision britannique en ligne depuis l'étranger en utilisant un Raspberry Pi 4 et un VPN du No..."
description: "Dans ce tutoriel, je montrerai comment regarder la télévision britannique en ligne depuis l'étranger en utilisant un Raspberry Pi 4 et un VPN du Nord. En suivant les étapes ci-dessous, il est possible de regarder des services en direct et de rattrapage à partir des quatre principaux réseaux (BBC, ITV, Channel 4 et Channel 5)"
btn_txt: "Mise en place"
categories:
    - raspberry pi
---
{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-pi" %}}

![Regardez la télévision britannique en ligne en dehors du Royaume-Uni sur une Raspberry Pi 4 avec NordVPN](/uk_tv_pi/uk-tv-pi-800.jpg)

***

Dans ce tutoriel, je montrerai comment regarder la télévision britannique en ligne depuis l'étranger en utilisant un Raspberry Pi 4 et un NordVPN.

En suivant les étapes ci-dessous, il est possible de regarder des services en direct et de rattrapage à partir des quatre principaux réseaux (BBC, ITV, Channel 4 et Channel 5)

> Vivant dans le nord de la France, nous avons toujours regardé la télévision britannique avec FreeSat et une antenne parabolique pointée sur le satellite Astra.
>
> Cependant, notre fille est partie à l'université cette année et a voulu continuer à regarder ses chaînes de télévision préférées (BBC, ITV et Channel 4).
>
> En utilisant plusieurs sources en ligne, j'ai trouvé cette solution qui marche.

***
{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-pi" %}}

## Hardware I Used

- Raspberry Pi 4 - 4gb

- USB C Power Supply

- Micro SD Card (8gb class 10 min)

- A case for the Raspberry Pi 4

- Ethernet Cable (or use WiFi)

- Micro HDMI to HDMI cable

- Mouse & Keyboard

## Also Required

- NordVPN Subscription

***

## Installer Raspberry Pi OS

En suivant les instructions sur le site officiel [**Raspberry Pi**](https://www.raspberrypi.org/downloads/ "Go to www.raspberrypi.org"), et en utilisant le **Raspberry Pi Imager**, installez la dernière version du bureau **Raspberry Pi OS**.

Une fois l'installation terminée, insérez la carte SD dans le Pi, connectez l'écran, le câble réseau (si vous l'utilisez), la souris et le clavier. Enfin, branchez le câble d'alimentation pour la mise sous tension.

>Lorsque vous connectez l'écran, utilisez le port micro HDMI 1 (le plus proche du port d'alimentation USB-C), car c'est le port avec le son HDMI intégré.

Suivez le processus d'installation et continuez avec ce tutoriel.

## Mettre à jour le Raspberry Pi

```` shell
sudo apt-get update
````

```` shell
sudo apt-get dist-upgrade
````

***

## Installer un support DRM pour le chrome

L'installation standard de Buster sur Raspberry Pi est fournie avec une version du navigateur Chromium sans [DRM] (https://en.wikipedia.org/wiki/Digital_rights_management "DRM on Wikipedia").

La prise en charge des DRM est nécessaire pour avoir accès à certains services de streaming

**1.** Saisissez la ligne suivante pour télécharger le script d'installation.  

``` shell
wget https://gist.githubusercontent.com/lemariva/0eb4ff4e847700627a5ebb71711c31bf/raw/0cab2916e4de65c0c5f780719221fdc052ac0bda/widevine-flash_armhf.sh
```

**2.** Rendre le fichier téléchargé exécutable avec

```` shell
chmod +x widevine-flash_armhf.sh
````

**3.** Et exécuter le fichier avec

```` shell
sudo ./widevine-flash_armhf.sh
````

***

## Installer OpenVPN

**1.** Ensuite, nous voulons installer OpenVPN en utilisant la commande suivante

```` shell
sudo apt-get install openvpn
````

**2.** Lorsque l'installation est terminée, changez de répertoire pour openvpn

```` shell
cd /etc/openvpn/
````

***

## Mettre en place NordVPN

**1.** Télécharger les fichiers de configuration du NordVpn

```` shell
sudo wget https://nordvpn.com/api/files/zip
````

**2.** Extrayez le fichier téléchargé

```` shell
sudo unzip zip
````

**3.** Supprimer le fichier zip téléchargé

```` shell
sudo rm zip
````

***

## Créer un fichier texte d'authentification

Pour une connexion automatique au NordVpn sans avoir à saisir à chaque fois votre nom d'utilisateur et votre mot de passe.

**1.** Créer le fichier auth.txt

```` shell
sudo nano /etc/openvpn/auth.txt
````

**2.** Tapez votre nom d'utilisateur et votre mot de passe NordVpn sur des lignes séparées

**3.** Appuyez sur "CTRL X" suivi de "Y" pour enregistrer le fichier

***

## Configurer le fichier de connexion

**1.** Entrez la commande suivante pour lister les fichiers dans le dossier en cours

```` shell
ls
````

**2.** Remplacez "uk1234" par votre connexion Vpn britannique préférée ( en état de marche) et copiez dans un nouveau fichier

```` shell
sudo cp uk1234.nordvpn.com.udp1194.ovpn ukvpn.conf
````

**3.** Ensuite, ouvrez le fichier copié dans l'éditeur de texte

```` shell
sudo nano ukvpn.conf
````

**4.** Trouvez la ligne suivante

```` shell
auth-user-pass
````

**5.** Et changer pour

```` shell
auth-user-pass auth.txt
````

**6.** Appuyez sur "CTRL X" suivi de "Y" pour enregistrer le fichier

>Le stockage des noms d'utilisateur et des mots de passe dans un fichier en texte clair pose des problèmes de sécurité. Assurez-vous que votre Raspberry Pi est sécurisé.

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-pi" %}}

## Configurer OpenVPN pour se connecter au démarrage

**1.** Dans l'éditeur de texte, ouvrez le fichier de configuration OpenVPN

```` shell
sudo nano /etc/default/openvpn
````

**2.** Trouver la ligne

```` shell
#AUTOSTART="all"
````

**3.** Décommentez (supprimez le premier #) et remplacez "all" par "ukvpn".

```` shell
AUTOSTART="ukvpn"
````

**4.** Appuyez sur "CTRL X" suivi de "Y" pour enregistrer et fermer le fichier

***

## Redémarrer le Pi et vérifier la connexion

```` shell
sudo reboot
````

Ouvrez Chrome et allez sur [NordVPN](www.nordvpn.com "Aller au site web du NordVPN") ou [What's my IP](https://whatismyipaddress.com/ "Vérifiez avec le site What's My Ip") et vérifiez votre adresse IP publique. Elle devrait maintenant indiquer que vous vous trouvez au Royaume-Uni.

***

## Mettre en place les chaînes de télévision

>Pour utiliser les services de streaming britannique en ligne, vous devez vous inscrire sur chacun des sites web. Pour ce faire, vous devez disposer d'un compte de messagerie électronique valide. Pour ce faire, j'ai créé un nouveau compte Yahoo.

Commencez par créer un raccourci sur votre bureau vers le navigateur DRM Chromium nouvellement installé

[![Ajout d'un raccourci du navigateur Chromium DRM sur le bureau Pi](/uk_tv_pi/uk-tv-pi01-600.jpg)](/uk_tv_pi/uk-tv-pi01.jpg)

Utilisez le raccourci du bureau pour ouvrir le navigateur DRM et visitez les liens suivants pour vous inscrire

- [BBC IPlayer](https://www.bbc.co.uk/iplayer "Lien vers le site IPlayer de la BBC")

![BBC IPlayer webpage](/uk_tv_pi/bbc-iplayer-600.jpg)

- [ITV Hub](https://www.itv.com/hub/itv "Lien vers le Hub d'ITV")

![ITV Hub webpage](/uk_tv_pi/itv-hub-600.jpg)

- [All 4](https://www.channel4.com/now/C4 "Lien vers All 4")

![All 4 webpage](/uk_tv_pi/all-4-600.jpg)

- [My 5](https://www.my5.tv/ "Lien vers My 5")

![My 5 webpage](/uk_tv_pi/my-5-600.jpg)

>Suivez les instructions pour vous inscrire à chacune des chaînes. Vous devrez fournir un code postal britannique et vérifier votre adresse électronique pour créer un compte.
>
> Une fois connecté, mettez le site en signet et ajoutez-le à la barre de signets pour faciliter votre retour.

***

## Vous pouvez désormais regarder en direct et en différé la télévision britannique depuis n'importe où dans le monde

***

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
