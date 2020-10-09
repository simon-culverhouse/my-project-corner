---
title: "Répulsif pour oiseaux au laser vert automatisé"
sub_title: "Solution au problème de l'étourneau dans l'étable"
date: 2017-10-10T17:38:26+02:00
slug: "laser-vert-automatise"
images:
    - laser_bird_scare/bird-scare04-320.jpg
    - laser_bird_scare/bird-scare04-640.jpg
summary: "Construire un répulsif à oiseaux au laser vert en utilisant un Arduino Uno et quelques appareils électroniques de base. Utilisé pour décourager l'i..."
btn_txt: "Voir la construction"
categories:
    - arduino
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "laser_bird_scare/bird-scare04" "1280" "960" "640" "320" "laser vert automatisé arduino pour effrayer les oiseaux" "Terminé et mis sous tension">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Construire un répulsif à oiseaux au laser vert en utilisant un Arduino Uno et quelques appareils électroniques de base. Utilisé pour décourager l'invasion hivernale des étourneaux dans les étables.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

#### Ma solution pour le problème de l'étourneau à la ferme

Chaque année, vers septembre/octobre, avec la récolte d'ensilage de maïs, arrive l'invasion des étourneaux. C'est un problème majeur dans l'étable, non seulement ils consomment la meilleure partie de l'ensilage, les grains de maïs, mais ils laissent aussi des dépôts d'excréments désagréables et potentiellement dangereux sur la nourriture et l'équipement des vaches. La solution était un laser vert de haute puissance.

En examinant les moyens de les faire fuir, je suis tombé sur un article mentionnant que les oiseaux en général ont peur de la lumière à haute intensité, en particulier de la lumière verte. La première étape a été d'acheter quelques pointeurs laser verts, c'est incroyable comme cela a bien fonctionné. Pendant quelques saisons (jusqu'en mars), je faisais régulièrement le tour de la ferme pour effrayer les oiseaux. Bien que cela n'ait pas complètement éradiqué le problème, cela l'a considérablement réduit, car la grande majorité des étourneaux sont partis ailleurs.

Cependant, cela a demandé pas mal de temps. C'est alors que j'ai décidé d'automatiser le processus, j'ai commencé par mettre un laser sur une minuterie. Mais j'ai vite découvert que la lumière devait être en mouvement pour obtenir l'effet désiré et aussi pour couvrir toute l'étable. C'est ainsi que j'ai imaginé un système automatisé d'effarouchement des oiseaux au laser.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "laser_bird_scare/bird-scare05" "900" "675" "450" "225" "étourneau mangeant avec la vache">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Ce qu'il faut" "Composants utilisés pour la construction du laser d'effarouchement des oiseaux" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% list %}}

***

> #### ***Principales parties de la construction***

- Arduino Uno, j'ai utilisé un Sunfounder Uno générique car je devais réduire les coûts au minimum
- Module d'horloge en temps réel I2C - RTC DS3231
- Relais 5v à déclenchement de bas niveau
- Un laser vert de haute puissance a été commandé à AliExpress
- Moteur pas à pas 5V 28BYJ-48 et tableau de bord ULN2003
- Boîtier étanche 240 x 190 x 90mm avec couvercle à charnière
- Alimentation électrique 9v pour Arduino Uno
- Mini breadboard SYB-170

***

{{% /list %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "laser_bird_scare/bird-scare03" "701" "526" "351" "175" "laser vert à haute puissance" "Laser vert à haute puissance">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "laser_bird_scare/bird-scare09" "701" "526" "351" "175" "générique arduino uno" "Sunfounder Uno">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "laser_bird_scare/bird-scare06" "701" "526" "351" "175" "module d'horloge en temps réel" "Module d'horloge en temps réel">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox_list "-clear" %}}

***

#### Pièces diverses

- Les fils de connexion Dupont

- Bâtons de colle chaude

- Revêtement de sol stratifié découpé pour le panneau de base

- J'ai également utilisé un petit morceau de plexiglas et quelques petites vis et écrous pour monter l'unité laser sur le moteur pas à pas. Si je devais reconstruire les unités, je remplacerais le plexiglas par une plaque de montage imprimée en 3D.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

J'ai construit deux de ces boîtes automatiques d'effarouchement des oiseaux au laser, une pour chaque étable de la ferme. Le coût de tous les composants s'est élevé à un peu moins de 100 euros par unité et j'ai passé environ une journée à assembler et à installer les deux boîtes.

J'ai essayé d'utiliser des pièces facilement disponibles pour mon système d'alerte laser automatisé, le seul élément qui peut être difficile à remplacer (si nécessaire) est l'unité laser. J'aurais peut-être dû acheter une pièce de rechange au moment de la construction, mais le budget ne me le permettait pas, étant donné que c'est l'article le plus cher. J'espère ne jamais avoir besoin d'un remplacement.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "La construction" "Assemblage de la boîte de pièces" >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "laser_bird_scare/bird-scare01" "1280" "960" "640" "320" "laser vert assemblé peur des oiseaux">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

J'ai décidé d'utiliser un Arduino Uno comme contrôleur parce que je voulais seulement qu'il exécute une petite quantité de code et qu'il soit facile à utiliser, il suffit de le brancher et c'est parti. De cette façon, n'importe qui pouvait déplacer ou installer le boîtier à un autre endroit si nécessaire.

J'ai utilisé des méthodes très simples pour construire la plaque de montage de l'électronique, qui est un morceau de sol stratifié que j'ai découpé pour qu'il s'adapte parfaitement à la boîte étanche du bas.

J'ai ensuite disposé les composants sur la plaque et marqué les positions avec un crayon, puis j'ai retiré les composants et, à l'aide d'une perceuse de 3 mm, j'ai percé des trous de 4 mm de profondeur sur les marques de crayon.

Ensuite, j'ai découpé un bâton de colle en longueurs de 8 mm et j'ai collé à chaud ces mèches sur les trous percés, tous sauf la carte contrôleur laser. Une fois la colle refroidie, j'ai placé et collé à chaud les composants un par un sur ces "piliers de bâton de colle". La carte de contrôle du laser a été fixée directement à la plaque de base de la même manière.

Le moteur pas à pas a été fixé au centre du couvercle à l'aide de petites vis à tête fraisée.

La mini-plaque à pain a été collée avec son propre bâton de colle.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}
Bien que ce soit un assemblage très "bricolé", toutes les pièces sont toujours en place et fonctionnent après deux ans d'utilisation et je suis satisfait du temps gagné par rapport à un assemblage vissé.
{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section "-sub" >}}
{{< section_header "Phase finale" "Codage et connexion" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

#### Le code Arduino

J'ai mélangé différents exemples de code pour produire quelque chose qui fonctionne. Le but du code est d'amener le servo à faire tourner le laser selon un angle prédéfini à intervalles réguliers tout au long de la journée. L'effet de balayage du laser permet de couvrir une plus grande surface et le rend également plus efficace.

Le sketch Arduino.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-pi" %}}

``` cpp
// Real time module
#include "Wire.h"
#define DS3231_I2C_ADDRESS 0x68
// Convert normal decimal numbers to binary coded decimal
byte decToBcd(byte val)
{
  return( (val/10*16) + (val%10) );
}
// Convert binary coded decimal to normal decimal numbers
byte bcdToDec(byte val)
{
  return( (val/16*10) + (val%16) );
}
// Stepper motor set up
const int IN1=11;
const int IN2=10;
const int IN3=9;
const int IN4=8;
// Relay set up
const int relayPin =7; //the "s" of relay module attach to
const char tab1[] =
{
  0x01, 0x03, 0x02, 0x06, 0x04, 0x0c, 0x08, 0x09
};
const char tab2[] =
{
  0x01, 0x09, 0x08, 0x0c, 0x04, 0x06, 0x02, 0x03
};
void setup()
// Stepper motor & relay
{
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  pinMode(relayPin, OUTPUT); //initialize relay as an output
  digitalWrite(relayPin, HIGH); //disconnect the relay
// Real time module
  Wire.begin();
  Serial.begin(9600);
  // set the initial time here:
  // DS3231 seconds, minutes, hours, day, date, month, year
  
  // Un-comment following line to set current time (change values), once set comment out again and re-upload
  
 //setDS3231time(00,52,23,3,3,1,18);
void loop()
{
  byte second, minute, hour, dayOfWeek, dayOfMonth, month, year;
  // retrieve data from DS3231
  readDS3231time(&second, &minute, &hour, &dayOfWeek, &dayOfMonth, &month, &year);
    // send it to the serial monitor
  Serial.print(hour, DEC);
  // convert the byte variable to a decimal number when displayed
  Serial.print(":");
  if (minute<10)
  {
    Serial.print("0");
  }
  Serial.print(minute, DEC);
  Serial.print("--");
  delay(1000);
   { 
      if (hour > 8 and hour < 18)
    {
      if (minute == 10 or minute == 20 or minute == 30 or minute == 40 or minute == 50 or minute == 0)
        {
          LaserOn();
        }
    }  
  
  }
}
void ctlStepMotor(int angle, char speeds )
{
  for (int j = 0; j < abs(angle) ; j++)
  {
    if (angle > 0)
    {
      for (int i = 0; i < 8; i++)
      {
        digitalWrite(IN1, ((tab1[i] & 0x01) == 0x01 ? true : false));
        digitalWrite(IN2, ((tab1[i] & 0x02) == 0x02 ? true : false));
        digitalWrite(IN3, ((tab1[i] & 0x04) == 0x04 ? true : false));
        digitalWrite(IN4, ((tab1[i] & 0x08) == 0x08 ? true : false));
        delay(speeds);
      }
    }
    else
    {
      for (int i = 0; i < 8 ; i++)
      {
        digitalWrite(IN1, ((tab2[i] & 0x01) == 0x01 ? true : false));
        digitalWrite(IN2, ((tab2[i] & 0x02) == 0x02 ? true : false));
        digitalWrite(IN3, ((tab2[i] & 0x04) == 0x04 ? true : false));
        digitalWrite(IN4, ((tab2[i] & 0x08) == 0x08 ? true : false));
        delay(speeds);
      }
    }
  }
}
void StepMotorStop()
{
  digitalWrite(IN1, 0);
  digitalWrite(IN2, 0);
  digitalWrite(IN3, 0);
  digitalWrite(IN4, 0);
}

void LaserOn()
{
  digitalWrite(relayPin, LOW); //Close the relay
  {
    for (int i=1; i<=2; i++)
    {
        ctlStepMotor(120, 10);
        StepMotorStop();
        delay(1000);
        ctlStepMotor(-120, 10);
        StepMotorStop();
        delay(1000);
    }
        digitalWrite(relayPin, HIGH); //Open the relay
        delay(30000);
    }
}

void setDS3231time(byte second, byte minute, byte hour, byte dayOfWeek, byte
dayOfMonth, byte month, byte year)
{
  // sets time and date data to DS3231
  Wire.beginTransmission(DS3231_I2C_ADDRESS);
  Wire.write(0); // set next input to start at the seconds register
  Wire.write(decToBcd(second)); // set seconds
  Wire.write(decToBcd(minute)); // set minutes
  Wire.write(decToBcd(hour)); // set hours
  Wire.write(decToBcd(dayOfWeek)); // set day of week (1=Sunday, 7=Saturday)
  Wire.write(decToBcd(dayOfMonth)); // set date (1 to 31)
  Wire.write(decToBcd(month)); // set month
  Wire.write(decToBcd(year)); // set year (0 to 99)
  Wire.endTransmission();
}
void readDS3231time(byte *second,
byte *minute,
byte *hour,
byte *dayOfWeek,
byte *dayOfMonth,
byte *month,
byte *year)
{
  Wire.beginTransmission(DS3231_I2C_ADDRESS);
  Wire.write(0); // set DS3231 register pointer to 00h
  Wire.endTransmission();
  Wire.requestFrom(DS3231_I2C_ADDRESS, 7);
  // request seven bytes of data from DS3231 starting from register 00h
  *second = bcdToDec(Wire.read() & 0x7f);
  *minute = bcdToDec(Wire.read());
  *hour = bcdToDec(Wire.read() & 0x3f);
  *dayOfWeek = bcdToDec(Wire.read());
  *dayOfMonth = bcdToDec(Wire.read());
  *month = bcdToDec(Wire.read());
  *year = bcdToDec(Wire.read());
}
```

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Je voulais faire un Fritzing diagram pour le câblage, mais je n'ai jamais trouvé le temps. J'ai donc répertorié les connexions de la meilleure façon possible.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{< image "laser_bird_scare/bird-scare02" "1280" "960" "640" "320" "Le câblage du laser vert pour l'effarouchement des oiseaux">}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% section_textbox_list "-clear" %}}

***

#### ***Câblage des composants***

Voici comment j'ai câblé le laser anti-oiseaux :

##### *Contrôleur de moteur pas à pas*

- IN1 – Arduino Uno Pin 8
- IN2 – Arduino Uno Pin 9
- IN3 – Arduino Uno Pin 10
- IN4 – Arduino Uno Pin 11
- Power + to Breadboard Shared 5v
- Power – to Arduino Uno GND

##### *Real Time Clock Module*

- SCL – Arduino Uno Pin A5
- SDA – Arduino Uno Pin A6
- VCC – Arduino Uno 3.3v
- GND to Breadboard Shared Ground

##### *Relay*

- IN – Arduino Uno Pin 7
- VCC to Breadboard Shared 5v
- GND to Breadboard Shared Ground
- Output:
  - Laser Controller Board
  - Breadboard 9v Input

##### *Laser Controller Board*

- Connected to Breadboard Input Ground and Relay

##### *Power Supply*

- Split at Breadboard to supply 9v to Arduino and to Laser

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Essai" "Voici une vidéo de son travail dans mon hangar" >}}

{{< section "-sub" >}}
{{< section "-top" >}}
{{< youtube exR2xbYiY8g >}}
{{< /section >}}
{{< section "-multi-end" >}}
{{% quote %}}
J'ai utilisé le dispositif laser anti-oiseaux pendant trois hivers et bien qu'il n'ait pas permis de se débarrasser complètement des étourneaux, il a définitivement réduit leur nombre. Le principal avantage était que les oiseaux ne passaient pas la nuit dans les étables.

De plus, il permettait de continuer à travailler le week-end lorsque je ne le faisais pas.
{{% /quote %}}
{{< /section >}}
{{< /section >}}
{{< /section_main >}}
