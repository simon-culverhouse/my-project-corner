---
title: "Système d'alerte pour les souris"
sub_title: "Détecter l'invasion de souris avec un Raspberry Pi"
date: 2020-09-22T16:42:23+02:00
slug: "systeme-detecteur-souris"
images:
    - mouse_detector/mouse-detector06-320.jpg
    - mouse_detector/mouse-detector06-640.jpg
summary: "Dans ce projet, j'ai mis en place un capteur de mouvement infrarouge connecté à un Raspberry Pi. Lorsqu'un mouvement est détecté, une alerte par SM..."
btn_txt: "Faites-en un"
categories:
    - raspberry pi

description: "Fabriquez un détecteur de souris en utilisant un détecteur de mouvement infrarouge et un Raspberry Pi. Sachez instantanément quand les souris entrent dans votre maison"

---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "mouse_detector/mouse-detector06" "1280" "960" "640" "320" "Le détecteur de souris fini à utiliser un Raspberry Pi" "Le système de détection des souris">}}
{{< /section >}}

<!-- QUOTE -->
{{< section "-multi" >}}
{{% quote %}}
Dans ce projet, j'ai mis en place un capteur de mouvement infrarouge connecté à un Raspberry Pi.

Lorsqu'un mouvement est détecté, une alerte par SMS est envoyée à mon téléphone portable, me disant de sortir les pièges à souris !

{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### Le problème des souris

Vivre à la campagne, dans une maison en pierre, peut être un problème d'infestation de souris. Le plus gros problème est que lorsque nous savons qu'elles sont dans la maison, par exemple, nous en voyons une ou que la nourriture dans le garde-manger commence à être grignotée, nous sommes infestés.

Nous constatons que l'invasion de souris se produit à différents moments de l'année. Pour avoir des pièges en permanence, il faut vérifier régulièrement s'ils ont attrapé quelque chose. Comme ceux-ci se trouvent dans les toits (où les souris ont tendance à arriver en premier), ce n'est pas facile et donc ne se fait pas.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### ***Pièces requises***

- Raspberry Pi
- HC-SR501 PIR Capteur de mouvement
- Boîte de dérivation des câbles électriques en plastique
- Longueur du câble téléphonique à 4 conducteurs
- Dupont connectors

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Le capteur de mouvement" "Construction de la boîte" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

À l'aide d'une mèche à bois de 22 mm, faites un trou dans le couvercle de la boîte à câbles en plastique.

Bien que le diamètre du dôme du capteur de mouvement soit de 24 mm, j'ai constaté que la mèche de 22 mm fait un trou plus grand lorsqu'on perce le plastique. Une fois nettoyé, il s'adapte parfaitement.

{{% /half_text %}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector03" "1280" "960" "640" "320" "Percer le trou pour le capteur de mouvement du détecteur de souris">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

### Assembler le boîtier du capteur de mouvement

Composez le câble pour relier le boîtier du capteur au Raspberry Pi. Je me connecte à un Pi existant qui se trouve à environ 3 mètres.

Coupez 3 fils Dupont femelle/femelle en deux, et soudez à chaque extrémité de la longueur du câble (en vous assurant que les couleurs correspondent à chaque extrémité). Protégez des courts-circuits avec du ruban adhésif thermorétractable ou électrique.

À l'aide d'un pistolet à colle chaude (ou simplement de la colle), fixez le capteur infrarouge au couvercle. Faites passer une extrémité du câble par le trou latéral, et connectez-vous au capteur.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector04" "1280" "960" "640" "320" "la fabrication du câble pour le détecteur de souris" "Réaliser le câble">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector05" "1280" "960" "640" "320" "Utilisation de colle chaude pour fixer le capteur de mouvement du détecteur de souris" "Collage à chaud du capteur">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector01" "1280" "960" "640" "320" "Câblage du détecteur de mouvement de la souris" "Connexion">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector02" "1280" "960" "640" "320" "Le boîtier du détecteur de mouvement de la souris terminé" "Unité finie">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector07" "1280" "960" "640" "320" "Le boîtier du détecteur de mouvement de souris fini dans le grenier" "Le capteur de mouvement vissé à un chevron dans le grenier">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Mise en place du Raspberry Pi" "Connexion et codage" >}}

{{< section "-sub" >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

### Connecter le capteur au Raspberry Pi

- VCC à 5v (pin 2 or 4)

- GRD à GRD (pin 6 or 9)

- OUT à GPIO4 (pin 7)

Après la connexion, ouvrez votre éditeur Python préféré et copiez le bloc de code suivant. Saisissez vos données de connexion pour l'utilisateur et le passe, puis enregistrez le fichier.

J'utilise Free Mobile et je me connecte donc à l'API Free SMS pour envoyer des messages texte. Je pense que la plupart des autres réseaux de téléphonie mobile ont un service similaire.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-code" %}}

``` python
#!/usr/bin/python3
import urllib.request
from gpiozero import MotionSensor

pir_mice = MotionSensor(4)
url = "https://smsapi.free-mobile.fr/sendmsg?user=********&pass=********&msg=Souris+Détecté"

while True:
    pir_mice.wait_for_motion()
    print("Souris!")
    urllib.request.urlopen(url)
    pir_mice.wait_for_no_motion()

```

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}
Et c'est tout, il suffit d'exécuter le script python dans Python Shell et d'attendre une alerte souris sur votre téléphone.

J'utilise ce système d'alerte précoce depuis quelques années maintenant, et grâce à lui, nous avons pu nous occuper des souris dès qu'elles ont commencé à se déplacer.

Je travaille actuellement sur une version portable utilisant une carte esp8266, à utiliser dans des bâtiments annexes.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
