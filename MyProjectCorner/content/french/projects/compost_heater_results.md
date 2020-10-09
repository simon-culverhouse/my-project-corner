---
title: "Résultats du système de chauffage du compost"
sub_title: "Ce que j'ai appris de mon projet de système de chauffage au compost"
date: 2018-12-28T16:26:52+02:00
slug: "systeme-chauffage-compost-resultats"
images:
    - compost_heating/compost-heater02-320.jpg
    - compost_heating/compost-heater02-640.jpg
summary: "Une semaine après la construction du système de chauffage du compost, la température moyenne relevée par les capteurs était passée à 68 °C, ce qui ..."
btn_txt: "Voir les résultats"
categories:
    - mise à jour
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "compost_heating/compost-heater02" "1280" "960" "640" "320" "Système de chauffage au compost fini" "Système de chauffage au compost fini">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### Résultats

Une semaine après la construction du système de chauffage du compost, la température moyenne relevée par les capteurs était passée à 68 °C, ce qui était beaucoup plus rapide que prévu. Cependant, j'ai découvert que si je faisais fonctionner la pompe de circulation à son débit minimum, après trois jours de fonctionnement continu, la température du tas diminuerait au point où l'action de compostage s'arrêterait et je pense que je courais le risque de transformer le tas en un compost "froid".

La réduction de la durée d'extraction de la chaleur par la pompe a amélioré la situation et j'ai pu maintenir la température moyenne du compost à environ 50°C. Le Raspberry Pi était programmé pour arrêter la pompe lorsque la température descendait en dessous de 40°C, et la remettre en marche à 55°C. Cela signifiait que l'approvisionnement en chaleur était insuffisant pour chauffer uniquement avec le système de chauffage du compost.

Après trois mois d'utilisation, j'ai décidé que la chaleur fournie au système de plancher n'était pas assez importante pour être économique (compte tenu du coût de la construction), et j'ai donc décidé d'utiliser le tas de compost comme système de préchauffage de l'eau chaude sanitaire. En tant que famille de six personnes, nous utilisons une quantité considérable d'eau chaude. Souvent, le chauffe-eau de 200 litres ne suffit pas, il fonctionne la nuit avec de l'électricité à bas prix. Une fois le chauffe-eau raccordé, la température de l'eau était en moyenne de 45 °C, même en tenant compte du refroidissement des tuyaux d'alimentation. Cela signifie que pendant la journée, nous n'avions que rarement besoin d'utiliser de l'électricité supplémentaire et que la nuit, il suffisait d'augmenter la température de l'eau de 25°C au lieu de 65°C.

Vers la fin de l'hiver (6 mois après la construction), j'avais remarqué que la température du tas baissait lentement. C'est à ce moment, après quelques recherches, que je me suis rendu compte que le pieu se desséchait. Nous avions eu un hiver vraiment sec (pas normal pour la Bretagne !), et je n'avais pas pensé à arroser le compost. Avec un bon arrosage et l'ajout d'un peu de lisier liquide de la ferme, j'ai relancé l'action de compostage, même si cela a pris quelques semaines pour démarrer.

---

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Au total, le système a continué à fonctionner pendant 14 mois, avec l'ajout occasionnel d'un mélange d'eau et de boue pour lui donner un coup de fouet.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

---

Après cela, j'ai décidé de décomposer le tas de compost, ce qui m'a pris environ une journée pour le faire tout seul. Le compost obtenu (6m3) a été stocké pour un usage futur dans le jardin et la couche inférieure est restée relativement non compostée, donc a été mise de côté pour servir de paillis pour les parterres de fleurs.

---

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### Conclusions

Cela en valait-il la peine ? Oui et non, tout d'abord le non, en tant que source de chaleur pour mon chauffage au sol, il n'était pas suffisant.

D'un autre côté, le projet était très intéressant et j'ai beaucoup appris sur le fonctionnement du compostage. C'était également agréable de faire participer d'autres membres de la famille à l'un de mes projets. En ce qui concerne les coûts, je pense qu'environ la moitié a été couverte par l'économie d'électricité pour l'eau chaude et le reste, eh bien nous n'aurons pas besoin d'acheter des sacs de compost avant quelques années !

Je pense que si je m'étais occupé du tas (c'est-à-dire de l'arrosage et de l'alimentation), peut-être que mon bois aurait maintenu une température plus élevée plus longtemps.

En cassant le tas, j'ai pu constater qu'il y avait encore pas mal de matériaux qui auraient pu être compostés davantage.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

#### Est-ce que je le referais

Oui, j'aimerais expérimenter avec une version plus petite, ou peut-être deux en parallèle.

Mais en se concentrant sur le chauffage de l'eau chaude sanitaire.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
