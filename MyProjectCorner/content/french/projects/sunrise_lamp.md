---
title: "Ma lampe du lever du soleil fait maison"
sub_title: "Projet de fabrication d'une lampe à lever de soleil"
date: 2020-01-13T08:34:19+02:00
slug: "ma-lampe-du-lever-du-soleil"
images:
    - sunrise_lamp/sunrise-lamp07-320.jpg
    - sunrise_lamp/sunrise-lamp07-959.jpg
    - sunrise_lamp/sunrise-lamp07-thin.jpg

summary: "C'est la construction de ma lampe du lever du soleil, je voulais savoir si une lampe du lever du soleil pouvait vraiment faciliter le lever lors de..."
btn_txt: "se réveiller en douceur"
categories:
    - maison & jardin
    - impression 3d
    - arduino
---
{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "sunrise_lamp/sunrise-lamp07" "1278" "959" "639" "320" "lampe à lever de soleil terminé" "lampe à lever de soleil terminé">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
C'est la construction de ma lampe du lever du soleil, je voulais savoir si une lampe du lever du soleil pouvait vraiment faciliter le lever lors des sombres matins d'hiver. Je ne voulais pas dépenser plus de 60 euros pour une lampe toute faite (et parce que j'aime faire des choses), j'ai donc imaginé ce design.

L'idée est que la lumière vous stimule pour que vous vous réveilliez, exactement comme un matin d'été, en vous sentant détendu et frais, sans avoir besoin d'un réveil.
{{% /quote %}}
{{< /section >}}

<!-- TEXT BOX WITH HEADING  -->
{{< section "-multi-end" >}}
{{% section_textbox "-clear" %}}

Il est construit autour d'une lampe de table Ikea Fado et d'une ampoule à led à intensité variable, utilisant un socle imprimé en 3d pour abriter l'électronique. L'unité finale sera contrôlée par mon tableau de bord Raspberry Pi Node Red.

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% list %}}

***

> #### ***Pièces nécessaires pour la lampe du lever du soleil***

- Fado Lampe - Ikea

- Ampoule LED à intensité variable - Ikea
- WeMos D1 mini
- Hi-Link 220v AC - 5v DC
- RobotDyn PWM Variateur
- Dupont Connectors
- et la base imprimée en 3D à l'aide de mon imprimante CR10S.

{{% /list %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp12" "1278" "959" "639" "320" "Lampe Fado d'Ikea" "Lampe Fado d'Ikea">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp02" "1278" "959" "639" "320" "Ampoule LED d'Ikea" "Ampoule LED à intensité variable">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp05" "1278" "959" "639" "320" "WeMos D1 mini" "WeMos D1 mini">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp01" "1278" "959" "639" "320" "Hi-Link 220v AC - 5v DC" "Hi-Link 220v AC - 5v DC">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp10" "1278" "959" "639" "320" "RobotDyn PWM Dimmer" "Variateur PWM">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp03" "1278" "959" "639" "320" "base imprimée en 3D" "base imprimée en 3D">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section "-multi-end" >}}
{{% quote %}}
En excluant l'impression en 3d, le coût total s'est élevé à moins de 25€.
{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Conception et impression" "Base imprimée en 3d pour la lampe du lever du soleil" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

J'ai commencé par utiliser SketchUp pour concevoir une base qui contiendrait l'électronique nécessaire au contrôle de la lampe.

La conception peut être téléchargée depuis **[Thingiverse](https://www.thingiverse.com/thing:4102831)**

J'ai imprimé avec 20% de remplissage et 3 couches pour la base et les murs. Cela en fait une belle pièce solide. Le temps d'impression est de plus de 12 heures en utilisant les paramètres que j'ai utilisés.

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp04" "1278" "959" "639" "320" "Base imprimée en 3d pour la lampe du lever du soleil prête à être assemblée">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi-end" >}}
{{% half_text %}}

La lampe ne repose pas entièrement dans le socle imprimé à cause de la conicité du socle. Si je devais reconstruire, j'incorporerais le cône dans le dessin imprimé, mais dans l'état actuel, il laisse quatre petits espaces qui permettent la dispersion de la chaleur.

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp15" "1278" "959" "639" "320" "Mise en évidence des espaces d'air dans l'assemblage des lampes du lever du soleil">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Préparation et construction" "Ajouter l'électronique au socle de la lampe du lever du soleil  " >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

#### Réduire le dissipateur de chaleur

J'avais besoin de réduire la hauteur du dissipateur de chaleur du gradateur PWM de RobotDyn pour dégager la base de la lampe.

À l'aide d'une scie à métaux, j'ai retiré 10 mm du haut du dissipateur de chaleur

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp11" "1278" "959" "639" "320" "Réduire le dissipateur de chaleur">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% quote %}}
Je ne recommande généralement pas de réduire la taille d'un dissipateur de chaleur, mais comme la lampe ne fonctionne que pendant 45 minutes par jour, l'accumulation de chaleur sera minime.
{{% /quote %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### Soudage des mini-broches WeMos D1

J'ai utilisé 2 blocs de broches, un 2 et un 4 comme indiqué.

- broches : 5v & G
- broches : D6, D7, D8 et 3.3v

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp05" "1278" "959" "639" "320" "broches à souder sur d1-mini">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### Insert and connect components

L'électronique est maintenue en place avec un peu de colle chaude.

J'ai raccourci les fils de connexion Dupont de longueur standard, je dois vraiment investir dans un kit de sertissage car cela me ferait gagner beaucoup de temps et produirait un meilleur aspect fini.

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp14" "1278" "959" "639" "320" "Lever de soleil 3d base imprimée avec instructions de câblage">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% list %}}

***

> #### ***Connexions de câblage***

1. Alimentation Hi-Link AC.

2. Alimentation Hi-Link AC.
3. Connexion négative DC épissée à la broche de terre de WeMos.
4. Positif DC connecté à la broche 5v de WeMos.
5. La broche de terre du variateur est reliée à la broche G de WeMos.
6. Broche VCC du variateur connectée à WeMos 3.3v.
7. Le variateur Z-C est connecté à la broche D6 de WeMos.
8. Le variateur PWM est connecté à la broche D7 de WeMos.

{{% /list %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}
Couper le câble d'alimentation de la lampe pour laisser environ 100 mm du côté de l'ampoule. Étamer les extrémités avec une petite quantité de soudure et souder également les fils d'alimentation CA du Hi-Link aux fils d'alimentation électrique. Fixez les blocs de connexion du gradateur comme indiqué.
{{% /quote %}}
{{< /section >}}

{{< section "-top" >}}
{{< image "sunrise_lamp/sunrise-lamp09" "1278" "959" "639" "320" "Le câblage de la lampe Sunrise est terminé" "Le câblage de la lampe Sunrise est terminé">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Mise en place" "Programmation du mini WeMos D1" >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

J'utilise déjà Node Red & MQTT sur mon Raspberry Pi pour contrôler divers appareils dans la maison, alors j'ai voulu intégrer la lampe diy sunrise dans le même système.

La partie principale du code qui contrôle le tableau des gradateurs est venue de la page GitHub de Nassir Malik **[HERE](https://github.com/nassir-malik/IOT-AC-Light-Dimmer-With-Alexa/tree/master/Part%20%23%201/robodyn_dimmer)**. Je tiens à le remercier pour son travail, il m'a vraiment aidé.

J'ai ajouté le support Wifi et MQTT et inclus une routine qui augmenterait la luminosité de la lampe diy sunrise sur une période de 30 minutes.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-pi" %}}

``` cpp
#include "hw_timer.h"
#include <ESP8266WiFi.h>
#include <PubSubClient.h>
// Change the credentials below, so your ESP8266 connects to your router
const char* ssid = "Your SSID";
const char* password = "Your Password";
// Change the variable to your Raspberry Pi IP address, so it connects to your MQTT broker
const char* mqtt_server = "MQTT Server IP Address";
// Initializes the espClient. You should change the espClient name if you have multiple ESPs running in your home automation system
WiFiClient sunrise;
PubSubClient client(sunrise);

const byte zcPin = 12;
const byte pwmPin = 13;

byte fade = 1;
byte state = 1;
byte tarBrightness = 5;
byte curBrightness = 0;
byte zcState = 0; // 0 = ready; 1 = processing;

void ICACHE_RAM_ATTR zcDetectISR ();
void ICACHE_RAM_ATTR dimTimerISR ();
int val = 1;
int tim = 1;
String lampState = "off";

void setup_wifi() {
  delay(10);
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("WiFi connected - ESP IP address: ");
  Serial.println(WiFi.localIP());
}
void callback(String topic, byte* message, unsigned int length) {
  Serial.print("Message arrived on topic: ");
  Serial.print(topic);
  Serial.print(". Message: ");
  String messageTemp;

  for (int i = 0; i < length; i++) {
    Serial.print((char)message[i]);
    messageTemp += (char)message[i];
  }
  Serial.println();
  if (topic == "sunriseLamp/state") {
    Serial.print("Turning on Outside light ");
    if (messageTemp == "on") {
      lampState = "on";
      Serial.print("On");
    }
    else if (messageTemp == "off") {
      lampState = "off";
      Serial.print("Off");
    }
  }
  Serial.println();
}
// This functions reconnects your ESP8266 to your MQTT broker
// Change the function below if you want to subscribe to more topics with your ESP8266
void reconnect() {
  // Loop until we're reconnected
  while (!client.connected()) {
    Serial.print("Attempting MQTT connection...");
    // Attempt to connect
    if (client.connect("D1Mini_sunriseLamp")) {
      Serial.println("connected");
      // Subscribe or resubscribe to a topic
      // You can subscribe to more topics (to control more LEDs in this example)
      client.subscribe("sunriseLamp/state");
    } else {
      Serial.print("failed, rc=");
      Serial.print(client.state());
      Serial.println(" try again in 5 seconds");
      // Wait 5 seconds before retrying
      delay(5000);
    }
  }
}
void setup() {
  Serial.begin(115200);
  setup_wifi();
  client.setServer(mqtt_server, 1883);
  client.setCallback(callback);
  pinMode(zcPin, INPUT_PULLUP);
  pinMode(pwmPin, OUTPUT);
  attachInterrupt(zcPin, zcDetectISR, RISING);    // Attach an Interupt to Pin 2 (interupt 0) for Zero Cross Detection
  hw_timer_init(NMI_SOURCE, 0);
  hw_timer_set_func(dimTimerISR);
}
void mqttCheck() {
  if (!client.connected()) {
    reconnect();
  }
  if (!client.loop())
    client.connect("D1Mini_sunriseLamp");
}
void loop() {
  if (WiFi.status() != WL_CONNECTED) {
    delay(1);
    setup_wifi();
    return;
  }
  mqttCheck();
  if (lampState == "off") state = 0;
  if (lampState == "on") {
    val = 1;
    state = 1;
    for (val <= 250; val++;) {
      tarBrightness = val;
      mqttCheck();
      if (lampState == "off") {
        state = 0;
        Serial.println(lampState);
        break;
      }
      delay(7200);
    }
  }
}
void dimTimerISR() {
  if (fade == 1) {
    if (curBrightness > tarBrightness || (state == 0 && curBrightness > 0)) {
      --curBrightness;
    }
    else if (curBrightness < tarBrightness && state == 1 && curBrightness < 255) {
      ++curBrightness;
    }
  }
  else {
    if (state == 1) {
      curBrightness = tarBrightness;
    }
    else {
      curBrightness = 0;
    }
  }
  if (curBrightness == 0) {
    state = 0;
    digitalWrite(pwmPin, 0);
  }
  else if (curBrightness == 255) {
    state = 1;
    digitalWrite(pwmPin, 1);
  }
  else {
    digitalWrite(pwmPin, 1);
  }
  zcState = 0;
}
void zcDetectISR() {
  if (zcState == 0) {
    zcState = 1;

    if (curBrightness < 255 && curBrightness > 0) {
      digitalWrite(pwmPin, 0);

      int dimDelay = 30 * (255 - curBrightness) + 400;//400
      hw_timer_arm(dimDelay);
    }
  }
}
```

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

### **S'installer dans le Node Red**

J'utilise 3 nodes dans le flux.

- Big Timer Node - pour plus d'informations, voir  **[Scargill's Big-Timer](https://tech.scargill.net/big-timer/)**
- Switch Node – utilisé pour une commande manuelle.
- Node de sortie Mqtt

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{< image "sunrise_lamp/SunriseLamp-flow" "1053" "790" "527" "263" "Capture d'écran de Node Red flow" "Capture d'écran de Node Red flow">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
J'utilise la  lampe à lever de soleil depuis quelques jours et bien que la lumière ne me réveille pas à chaque fois, il est agréable de ne pas être dans l'obscurité totale lorsque mon mini google home se met à jouer de la musique.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "sunrise_lamp/sunrise-lamp07" "1278" "959" "639" "320" "La lampe du lever du soleil terminée et prête à l'emploi" "La lampe du lever du soleil terminée et prête à l'emploi">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
