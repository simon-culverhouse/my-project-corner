---
title: "Capteur de Température ESP8266"
sub_title: "Capteur de température portable MQTT"
date: 2019-10-06T17:20:33+02:00
slug: "capteur-de-temperature-esp8266"
images:
    - esp8266_temp/esp8266-mqtt01-320.jpg
    - esp8266_temp/esp8266-mqtt01-640.jpg
summary: "Un capteur de température « portable » construit à l’aide d’une carte microcontrôleur ESP8266 et d’un capteur étanche DS18B20. Logé dans une boîte ..."
btn_txt: "démarrer l'impression"
categories:
    - impression 3d
    - arduino
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "esp8266_temp/esp8266-mqtt01" "1280" "960" "640" "320" "Portable temperature sensor using ESP8266, MQTT & Node red" "Portable temperature sensor using ESP8266, MQTT & Node red">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}

Un capteur de température « portable » construit à l’aide d’une carte microcontrôleur ESP8266 et d’un capteur étanche DS18B20. Logé dans une boîte imprimée en 3D de ma propre conception.

Lorsqu’il est mis sous tension, le ESP8266 se connecte d’abord au Wifi, puis au serveur MQTT sur mon Raspberry Pi. Une fois connecté, un message est envoyé à intervalles réguliers avec la lecture de la température.

{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% list %}}

***

> #### ***Pièces pour la fabrication du capteur de température ESP8266***

- ESP8266 microcontroller
- DS18B20 capteur de température étanche
- 4.7K resistor
- Boîte imprimée 3D
- Alimentation électrique 5v

{{% /list %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< third_image >}}
{{< image "esp8266_temp/esp8266-mqtt02" "1280" "960" "640" "320" "Carte ESP8266 pour capteur de température" "Carte ESP8266">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "esp8266_temp/esp8266-mqtt06" "1280" "960" "640" "320" "Capteur de température étanche DS18B20" "Capteur de température étanche DS18B20">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "esp8266_temp/esp8266-mqtt05" "1280" "960" "640" "320" "Capteur de température portable assemblé" "Capteur de température portable assemblé">}}
{{< /third_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Design et Impression" "Utiliser SketchUp et mon imprimante 3d" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

Le design du boîtier de la carte esp8266 a été modélisé dans SketchUp. J'ai essayé de la garder aussi compacte que possible tout en laissant de la place pour le câblage.

Imprimé en PLA avec un remplissage de 20% et un soutien pour les découpes.

Les fichiers de conception et d'impression peuvent être trouvés sur **[Thingiverse](https://www.thingiverse.com/thing:4273457)**

{{% /half_text %}}
{{< half_image >}}
{{< image "esp8266_temp/esp8266-box" "1185" "960" "640" "320" "Modèle de croquis du boîtier esp8266">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section_header "Assemblage" "Le soudage des connexions" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "esp8266_temp/esp8266-mqtt04" "1280" "960" "640" "320" "Soudage ESP8266 MQTT Capteur de température">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

J'ai soudé les fils de la DS18B20 directement aux broches de la ESP8266 pour faciliter les choses,

1. Soudez le fil d'alimentation rouge à la broche de 3,3 V en même temps que vous soudez une extrémité de la résistance à la même broche.
2. Soudez le fil de terre noir à la broche GND.
3. Et enfin, connectez le fil de données jaune au D4 (GPIO2), en soudant à nouveau la résistance en même temps.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

Et c'est tout pour l'assemblée !

J'ai ajouté un peu de colle chaude aux connexions des terminaux pour l'isolation et la protection contre la corrosion. Et un tampon autour du trou d'entrée du fil.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Étape finale" "Téléchargez le code" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

***

#### **Ajouter le code à l'unité terminée**

Copiez le code ci-dessous et collez dans l'IDE Arduino. Modifiez les détails de la connexion wifi en fonction de votre propre réseau wifi. Définissez également l'adresse IP du Raspberry Pi qui fait tourner le serveur mqtt.

Vous aurez également besoin des bibliothèques nécessaires :

- ESP8266 board support library
- Dallas Temperature library
- OneWire library
- Mqtt support library

Ils peuvent être facilement installés via l'option "gérer les bibliothèques" dans IDE Arduino

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-pi" %}}

``` cpp
#include <ESP8266WiFi.h>
#include <PubSubClient.h>
#include <OneWire.h>
#include <DallasTemperature.h>

// Data wire to pin D4 on the ESP8266 - GPIO 2
#define ONE_WIRE_BUS 2

// Setup oneWire
OneWire oneWire(ONE_WIRE_BUS);

// Pass our oneWire reference to Dallas Temperature. 
DallasTemperature DS18B20(&oneWire);
char temperatureCString[7];
char temperatureFString[7];

// Change the credentials below, so your ESP8266 connects to your router
const char* ssid = "YOUR WIFI SSID";
const char* password = "YOUR WIFI PASSWORD";

// Change the variable to your Raspberry Pi IP address, so it connects to your MQTT broker
const char* mqtt_server = "YOUR PI IP ADDRESS";

// Initializes the espClient.
WiFiClient esp_temp_portable;
PubSubClient client(esp_temp_portable);

// This connects your ESP8266 to your router
void setup_wifi() {
  delay(10);
  // We start by connecting to a WiFi network
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

// This functions reconnects your ESP8266 to your MQTT broker
void reconnect() {
  // Loop until we're reconnected
  while (!client.connected()) {
    Serial.print("Attempting MQTT connection...");
    if (client.connect("esp_temp_portable")) {
      Serial.println("connected");  
      // Subscribe or resubscribe to a topic
      // You can subscribe to more topics (to control more LEDs in this example)
      client.subscribe("portable/temp1");
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
  //Turn off wifi access point
  WiFi.mode(WIFI_STA);
 }
// ensures that you ESP is connected to wifi and mqtt broker
void loop() {
  //connect wifi if not connected
  if (WiFi.status() != WL_CONNECTED) {
    delay(1);
    setup_wifi();
    return;
}
  if (!client.connected()) {
    reconnect();
  }
  if(!client.loop())
    client.connect("esp_temp_portable");

  getTemperature();
  client.publish("portable/temp1",temperatureCString);
  delay(10000);
 }
```

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

Il ne reste plus qu'à régler le flux d'entrée du MQTT dans Node Red et à brancher l'appareil.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Une utilisation du capteur de température" "Surveiller le bon fonctionnement de mon tas de compost" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

J'en ai un attaché à un poteau de clôture électrique en métal, je l'enfonce dans le tas de compost et je le branche à une batterie. J'enregistre la température sur le tableau de bord Node Red sur mon Raspberry Pi.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "esp8266_temp/compost-temp" "1280" "960" "640" "320" "Mesure de la température du compost avec le capteur ESP8266">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "esp8266_temp/compost-temp02" "1280" "960" "640" "320" "Utilisation du capteur de température ESP8266 pour le compost">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

Ci-dessous, une capture d'écran du tableau de bord Node Red. Elle montre la lecture du capteur de température ESP8266 et un historique sous forme de graphique.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{< image "esp8266_temp/nodered-compost" "960" "720" "480" "240" "Node red tableau de bord pour le capteur de température portable ESP8266">}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

J'ai récemment modifié la conception du capteur de température ESP8266 pour y ajouter un second DS18b20. Celui-ci est utilisé pour surveiller les entrées/sorties de température de l'eau de mon système de chauffage par le sol.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
