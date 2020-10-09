---
title: "Unité de température et de minuterie Arduino"
sub_title: "Une aide à la température et à la minuterie pour l'échaudage des poulets"
date: 2019-09-27T07:40:10+02:00
slug: "arduino-temperature-et-minuterie"
images:
    - arduino_temp_timer/arduino-temp-timer06-320.jpg
    - arduino_temp_timer/arduino-temp-timer06-639.jpg
summary: "J'ai fabriqué cette unité de température et de minuterie arduino pour faciliter l'échaudage des poulets avant la plumaison dans ma plumeuse. Il int..."
btn_txt: "Démarrer"
categories:
    - impression 3d
    - arduino
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "arduino_temp_timer/arduino-temp-timer06" "1278" "959" "639" "320" "Température et minuterie de Arduino fini" "Température et minuterie de Arduino fini">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
J'ai fabriqué cette unité de température et de minuterie arduino pour faciliter l'échaudage des poulets avant la plumaison dans ma plumeuse. Il intègre un capteur étanche pour surveiller la température de l'eau et un compte à rebours pour le temps d'immersion. La température et le compte à rebours sont affichés sur l'écran à 4 chiffres.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### **Composantes requises**

- Arduino Uno (ou générique)
- DS18D20 capteur de température étanche avec 1m de câble
- TM1637 Affichage à 4 chiffres et 7 segments
- Boîte imprimée en 3D - Voir sur **[Thingiverse](https://www.thingiverse.com/thing:3903097)**
- 4.7kΩ resistor

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Première étape" "Le boîtier imprimé 3d" >}}

{{< section "-sub" >}}

{{< section_row "-sub" >}}
{{% half_text %}}

#### Remixer le design

J'ai basé ma conception sur un boîtier Arduino Uno existant, disponible **[ICI](https://www.thingiverse.com/thing:659873)**, que j'ai modifié dans SketchUp.

L'ajout d'une découpe pour l'affichage à 4 chiffres, d'un trou pour le fil du capteur et l'augmentation de la hauteur du couvercle pour permettre plus de dégagement. Voici la conception finale sur **[Thingiverse](https://www.thingiverse.com/thing:3903097)**

{{% /half_text %}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer02" "1278" "959" "639" "320" "3d Impression arduino uno case" "Impression de la boîte">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Deuxième étape" "Le câblage" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "arduino_temp_timer/arduino-temp-timer03" "1278" "959" "639" "320" "Le câblage de la température et de la minuterie de l'Arduino est terminé" "Le câblage est terminé">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### Les connexions

En utilisant des fils de connexion dupont raccourcis, l'alimentation et la masse du capteur de température et de l'écran ont été soudées à un seul fil d'alimentation, et la ligne de données du capteur a été soudée à l'alimentation électrique via la résistance. Les fils CLK et DIO ont juste été raccourcis. Toutes les connexions ont été emballées sous film rétractable pour éviter tout court-circuit. Finalement, j'ai soudé une broche courte à chaque fil pour le branchement à l'ONU et j'ai fixé l'écran à l'aide de mon pistolet à colle chaude.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{% half_text %}}

***

J'ai utilisé une carte Arduino Uno générique de Sunfounder que j'avais eue lors d'un projet précédent.

Les autres articles, mis à part ceux-là, ont été achetés chez Amazon.

***

{{% /half_text %}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer08" "1278" "959" "639" "320" "Carte générique Arduino Uno de Sunfounder" "Carte générique Arduino Uno de Sunfounder">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### **Connexions à Arduino Uno**

- Alimentation à la broche 5v
- Broche de terre à terre
- Fil de données vers le pin 2
- Affichage CLK à la broche 6
- Affichage DIO à la broche 5

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Troisième étape" "Téléchargement du code" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer05" "1278" "959" "639" "320" "La température et la minuterie d'Arduino sont presque terminées" "Prêt à monter">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer04" "1278" "959" "639" "320" "Température et minuteur Arduino" "Mise en service de l'unité de température et de minuterie">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### Mise en place de Arduino UNO

Copiez le sketch Arduino ci-dessous et utilisez le téléchargement de l'IDE Arduino vers la Uno.

***

Trois bibliothèques supplémentaires seront nécessaires

- OneWire
- DallasTemperature
- TM1637

***

Ceux-ci peuvent être facilement installés en utilisant les bibliothèques de gestion dans le IDE Arduino

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-pi" %}}

``` cpp

#include <OneWire.h>
#include <DallasTemperature.h>
#include "TM1637.h"
#define CLK 6 //Pins for TM1637       
#define DIO 5 //Pins for TM1637
TM1637 tm1637(CLK,DIO);

// Data wire is plugged into Digital Pin 2
#define ONE_WIRE_BUS 2

// Setup a oneWire instance to communicate with any OneWire devices
OneWire oneWire(ONE_WIRE_BUS);

// Pass our oneWire reference to Dallas Temperature. 
DallasTemperature DS18B20(&oneWire);
char temperatureCString[7];
char temperatureFString[7];

// Set timer duration
int second = 30;

void setup() {

  Serial.begin(115200);
  DS18B20.begin();
  tm1637.init();
  tm1637.set(BRIGHTEST); 
  // BRIGHT_TYPICAL = 2,BRIGHT_DARKEST = 0,BRIGHTEST = 7;
  delay(500);
}

void getTemperature() {
  float tempC;
  float tempF;
  do {
    DS18B20.requestTemperatures(); 
    tempC = DS18B20.getTempCByIndex(0);
    dtostrf(tempC, 2, 0, temperatureCString);
    tempF = DS18B20.getTempFByIndex(0);
    dtostrf(tempF, 3, 2, temperatureFString);
    Serial.println(temperatureCString);
    delay(100);
  } while (tempC == 85.0 || tempC == (-127.0));
}

void loop() {
  getTemperature();
  int result = atoi(temperatureCString);
  int num1 = (result / 10) % 10;
  int num2 = result % 10;
  int num3 = second % 10;
  int num4 = (second / 10) % 10;
  tm1637.display(0,num1);
  tm1637.display(1,num2);
  tm1637.display(2,num4);
  tm1637.display(3,num3);
  tm1637.point(POINT_ON);
  if (second > 0) {
    second--;
  }else
  second = 30;
  Serial.println("Temperature has been sent");
  delay(200);
  } 
```

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

Ce court code imprime la température sur les deux premiers chiffres de l'écran et un compte à rebours de 30 secondes sur les deux derniers chiffres.

J'ai constaté qu'une durée de 30 secondes est à peu près suffisante pour faire le travail, mais qu'elle peut être facilement ajustée jusqu'à une minute en changeant la deuxième variable.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

Cette petite boîte est d'une grande aide quand on abat des poulets.

Maintenir l'eau à la température idéale n'a jamais été aussi facile et une minuterie précise (au lieu de compter dans nos têtes) est géniale !
{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}
