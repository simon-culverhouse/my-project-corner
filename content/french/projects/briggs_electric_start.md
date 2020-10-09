---
title: "InStart Batterie Alternative"
sub_title: "Alternative à la batterie de démarrage de Briggs & Stratton"
date: 2020-07-22T22:13:10+02:00
slug: "instart-batterie-alternative"
images:
    - instart_lawnmower/instart-lidl11-320.jpg
    - instart_lawnmower/instart-lidl11-640.jpg


summary: "Économiser de l'argent en adaptant une batterie rechargeable Lidl bon marché pour l'utiliser avec une tondeuse à gazon InStart Briggs & Stratton..."
btn_txt: "Démarrer la tondeuse"
categories:
    - maison & jardin
    - impression 3d
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "instart_lawnmower/instart-lidl11" "1280" "960" "640" "320" "adaptateur de batterie fini pour la tondeuse à gazon briggs & stratton instart" "Terminé et prêt à démarrer">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Lors d'une récente visite au supermarché du coin, j'ai trouvé une tondeuse à gazon en promotion, avec une réduction de 50 %. Sur le marché d'une nouvelle tondeuse à gazon, une réduction de 430€ à 215€ était une trop bonne offre pour la refuser.

Mais la raison pour laquelle elle était en promotion était qu'il s'agissait d'un modèle Briggs & Stratton à démarrage électrique, et qu'ils avaient perdu la batterie et le chargeur ! Je l'ai achetée sur un coup de tête, en pensant que j'achèterais une batterie et un chargeur tout en réalisant une économie considérable.

Je n'avais pas pensé au coût d'une batterie et d'un chargeur de remplacement, qui s'élevait à environ 140 euros !

{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% section_textbox "-clear" %}}

#### Ma solution

J'ai décidé d'essayer d'adapter une de mes batteries d'outils électriques existantes pour faire le travail. Après enquête, j'ai découvert qu'un mini taille-haie de Lidl avait un bloc de batteries rechargeables dont la tension et le courant étaient très similaires à ceux du modèle Briggs & Stratton.

En testant la batterie de Lidl, j'ai découvert un autre problème, la batterie InStart de Briggs & Stratton a 3 bornes. Le positif, le négatif et une troisième borne qui sert d'interrupteur pour le bouton (ou la clé) de démarrage. Lorsque le positif et le négatif de la batterie de remplacement sont connectés sans utiliser la troisième borne, le moteur du démarreur tourne continuellement.

J'allais devoir trouver un moyen de contourner ce problème

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Première étape" "Conception et production du modèle 3d" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

#### Conception TinkerCad

J'ai décidé de modéliser l'adaptateur de batterie en deux parties, l'une s'insérant dans le support de batterie de la tondeuse à gazon et l'autre dans la batterie du Lidl.

La raison principale de la production en deux parties est de faciliter le processus d'impression. En tant qu'unité, il faudrait un support d'impression beaucoup plus important.

***

La première étape a consisté à modéliser une réplique de la batterie InStart. En prenant les mesures de la tondeuse à gazon, j'ai modélisé un bloc qui donnait accès aux broches positives et négatives. Il comporte également un grand trou pour recevoir l'adaptateur de la batterie du Lidl

La deuxième partie du design était un support pour la batterie du Lidl qui s'insérait dans le premier modèle comme indiqué ci-dessous. Ce modèle possède un cylindre central pour le ressort et des trous pour les connexions électriques.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl12" "1280" "960" "640" "320" "modèle tinkercad de la partie principale" "Modèle de batterie InStart">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl13" "1280" "960" "640" "320" "modèle tinkercad de la pièce d'adaptation" "Adaptateur de batterie de Lidl">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl14" "1280" "960" "640" "320" "modèle tinkercad de pièces assemblées" "Pièces assemblées en TinkerCad">}}
{{< /third_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Deuxième étape" "Impression 3d des parties" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

#### Le bloc principal

Imprimé en PLA à l'envers avec une résolution de 0,2 mm et un remplissage de 20 %. Ajout d'un support pour les deux fentes latérales.

{{% /half_text %}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl02" "1280" "960" "640" "320" "Partie principale imprimée en 3d pour l'adaptateur de batterie">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### L'adaptateur

Encore une fois, imprimé en PLA avec une résolution de 0,2 mm et un remplissage de 20 %. Support ajouté pour l'anneau de localisation de la hauteur.

{{% /half_text %}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl03" "1280" "960" "640" "320" "Partie imprimée en 3d pour l'adaptateur de batterie">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{< image "instart_lawnmower/instart-lidl04" "1280" "960" "640" "320" "adaptateur de batterie fini pour la tondeuse à gazon briggs & stratton instart" "Pièces imprimées assemblées">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

Les fichiers de conception et d'impression peuvent être téléchargés sur **[Thingiverse](https://www.thingiverse.com/thing:4565535)**, ou en utilisant le bouton ci-dessous.
***
{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< download_box text="Cliquez sur le bouton pour télécharger les fichiers stl" link="instart_lawnmower/battery_adaptor.zip" buttonText="Télécharger" >}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Étape finale" "Connexions des bornes de la batterie" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% quote %}}
Pour faire les connexions entre la batterie du Lidl et les bornes de Briggs et Stratton, j'ai utilisé des bandes de cuivre récupérées d'un ancien adaptateur de luminaire.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

En plus de l'insertion des bornes en cuivre, j'ai ajouté un ressort de compression de 30 mm de long x 6 mm de diamètre dans le trou central.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl05" "1280" "960" "640" "320" "l'insertion des bornes de la batterie et du ressort">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl07" "1280" "960" "640" "320" "l'insertion des bornes de la batterie">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

Les bornes en cuivre sont ensuite soudées pour terminer l'appareil.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl06" "1280" "960" "640" "320" "la connexion des bornes de la batterie">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl08" "1280" "960" "640" "320" "connecter et souder les bornes de la batterie">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section_header "Démarrage de la tondeuse" "Utilisation de l'adaptateur de batterie de Briggs & Stratton Lidl" >}}

{{< section "-sub" >}}


{{< section_row "-top" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl10" "1280" "960" "640" "320" "L'adaptateur de batterie Briggs & Stratton Lidl sur la tondeuse à gazon" "Faites glisser l'adaptateur en place">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl11" "1280" "960" "640" "320" "L'adaptateur de batterie Briggs & Stratton prêt à l'emploi" "Insérez la batterie du Lidl et c'est prêt à démarrer">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% quote %}}
Le clip YouTube ci-dessous montre comment cela fonctionne. La batterie a tendance à rebondir un peu si on la laisse dans l'adaptateur, alors je la retire pendant que j'utilise la tondeuse.

À part cela, elle fonctionne très bien.

{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< youtube sM8bHVu_H6M >}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}
