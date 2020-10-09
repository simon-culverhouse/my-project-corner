---
title: "Capteur de température et d’humidité connecté"
sub_title: "Utilisation du MQTT et du Node Red"
date: 2019-10-19T08:47:25+02:00
slug: "capteur-de-temperature-et-humidite-connecte"
images:
    - d1mini_temp_hum/d1mini-temp-hum11-320.jpg
    - d1mini_temp_hum/d1mini-temp-hum11-640.jpg

summary: "Un capteur connecté au MQTT avec un affichage LCD pour surveiller les relevés de température et d'humidité dans ma maison. J'en ai construit trois ..."
btn_txt: "Faites-en un"
categories:
    - impression 3d
    - arduino
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum11" "1280" "960" "640" "320" "capteur de température et d'humidité fini" "Capteur de température et d'humidité fini en fonctionnement">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Un capteur connecté au MQTT avec un affichage LCD pour surveiller les relevés de température et d'humidité dans ma maison. J'en ai construit trois et les ai placés dans des pièces différentes. Les relevés de température et d'humidité sont envoyés par MQTT à mon tableau de bord Node Red sur le Raspberry Pi.

Bien qu'il ne soit pas vraiment nécessaire d'avoir un affichage numérique pour un capteur connecté, il est pratique de pouvoir voir la température sans avoir à se connecter au tableau de bord du Node Red.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### ***Pièces utilisées pour construire l'unité***

- D1 mini
- DHT22 Shield
- Digital readout IC2 KY34-B
- Dupont connectors
- Boîtier imprimé en 3D
- Alimentation électrique 5v

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section_header "Première étape" "Conception et impression" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

### Modélisation 3D de boiter

J'ai utilisé Tinkercad pour créer le modèle 3D de mon dessin. C'est la première fois que j'utilise Tinkercad et je le recommande vivement. Il est très facile à utiliser et produit un bon modèle.

Les fichiers stl peuvent être téléchargés sur **[Thingiverse](https://www.thingiverse.com/thing:3924670 "Cliquez ici pour visiter Thingiverse")**, ou en utilisant le lien ci-dessous

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum13" "1280" "960" "640" "320" "Modèle 3d de base pour le capteur de température et d'humidité" "Modèle 3d de la base">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum14" "1280" "960" "640" "320" "Modèle 3d de couverture pour capteur de température et d'humidité" "Modèle de couverture 3d">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

#### 3d Impression de la boiter

Le dessin a été imprimé en PLA noir avec une résolution de 0,2 et un remplissage de 20 %. La base a été imprimée avec un support activé pour le trou oblong d'alimentation électrique.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum01" "1280" "960" "640" "320" "Boîtier imprimé en 3d pour le capteur de température et d'humidité" "Boîtier imprimé en 3d pour le capteur de température et d'humidité">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section "-sub" >}}
{{< section_header "Deuxième étape" "Programmation et connexions" >}}
{{< /section >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

***

#### Téléchargez le code sur le mini D1

En utilisant le code Arduino ci-dessous, changez les détails de la connexion wifi pour votre propre réseau wifi. Définissez également l'adresse IP du Raspberry Pi qui fait tourner le serveur mqtt.

Vous aurez également besoin des bibliothèques en plus

- ESP8266 support libraries
- Mqtt support
- IC2 Display
- DHT22

ils peuvent être facilement installés via l'option "gérer les bibliothèques" dans Arduino IDE

Une fois terminé, vous pouvez compiler et télécharger vers le D1 mini.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-pi" %}}

``` cpp
#include <ESP8266WiFi.h>
#include <PubSubClient.h>
#include <DHT.h>
#include "SSD1306.h" // alias for `#include "SSD1306Wire.h"`
 
#define DHTPIN D4     // what pin the DHT is connected to
 
// Initialize the OLED display using Wire library
SSD1306  display(0x3C, D3, D5); // (I2C Address, SCL Pin, SDA Pin)
 
#define DHTTYPE DHT22   // DHT 22  (AM2302)
const int TEMPERATURE_INTERVAL = 30;
unsigned long last_temperature_sent = 0;
 
// WiFi Connection Details
const char* ssid = "Your SSID";
const char* password = "Your password";
 
// Raspberry Pi IP address, so it connects to your MQTT broker
const char* mqtt_server = "IP address of mqtt server";
 
// Change these to suit
WiFiClient wemos_lounge;
PubSubClient client(wemos_lounge);
 
const int HUMIDITY_INTERVAL = 30;
unsigned long last_humidity_sent = 0;
String display_temp;
String display_humid;
 
DHT dht(DHTPIN, DHTTYPE);
 
// This functions connects your ESP8266 to your router
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
 
// This functions reconnects your ESP8266 to your MQTT broker
void reconnect() {
  // Loop until we're reconnected
  while (!client.connected()) {
    Serial.print("Attempting MQTT connection...");
    if (client.connect("wemos_lounge")) {
      Serial.println("connected");  
      // Subscribe or resubscribe to a topic
      client.subscribe("heating/temperature_lounge");
    } else {
      Serial.print("failed, rc=");
      Serial.print(client.state());
      Serial.println(" try again in 5 seconds");
      // Wait 5 seconds before retrying
      delay(5000);
    }
  }
}
 
void setupHandler() {
  // Do what you want to prepare your sensor
  display.clear();
}
 
void getSendTemperature() {
  if (millis() - last_temperature_sent >= TEMPERATURE_INTERVAL * 1000UL || last_temperature_sent == 0) {
    float temperature = dht.readTemperature(false);
    if (isnan(temperature)) {
      Serial.println("Failed to read from DHT sensor!");
      return;
    }
// May need to offset temperature reading:
// I found the reading to be 3.1° too high
    display_temp = (temperature-3.1);
    int temp = round(temperature-3.1);
    char cstr[16];
    itoa(temp, cstr, 10);
    client.publish("heating/temperature_lounge",cstr);
    Serial.print("Temperature: ");
    Serial.print(temperature);
     
    Serial.println(" °C");
  }
}
 
void getSendHumid() {
  if (millis() - last_humidity_sent >= HUMIDITY_INTERVAL * 1000UL || last_humidity_sent == 0) {
    float humidity = dht.readHumidity();
 
    if (isnan(humidity)) {
      Serial.println("Failed to read from DHT sensor!");
      return;
    }
    display_humid = humidity;
    int humid = round(humidity);
    char cstr[16];
    itoa(humid, cstr, 10);
    client.publish("heating/humidity_lounge", cstr);
    Serial.print("Humidity: ");
    Serial.print(humidity);
    Serial.println(" %");
  } 
 }
 
void displayData() {
    display.clear();
    display.setTextAlignment(TEXT_ALIGN_CENTER);
    display.setFont(ArialMT_Plain_24);
    display.drawString(66, 5, display_temp + "C");
    display.drawString(66, 35, display_humid + "%");
    display.display();
}
 
void setup() {
 
  Serial.begin(115200);
  setup_wifi();
  client.setServer(mqtt_server, 1883);
  // Initialising the display.
  WiFi.mode(WIFI_STA);
  display.init();
  display.clear();
  display.flipScreenVertically();
  display.setTextAlignment(TEXT_ALIGN_CENTER);
  display.display();
}
 
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
    client.connect("wemos_lounge");
  getSendTemperature();
  getSendHumid(); 
  displayData();
  delay(2000);
}
```

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

#### Assemblage des composants

J'ai acheté le D1 mini et le chapeau DHT22 chez AliExpress. C'est une source bon marché pour ce type de composants (si vous n'êtes pas très pressé, la livraison peut prendre jusqu'à 3 semaines).

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum12" "1280" "960" "640" "320" "souder des blocs de broches à d1 mini" "Souder le bloc à broche femelle au shield du DHT22 et le bloc mâle au mini D1">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum04" "1280" "960" "640" "320" "connexion de l'écran à d1 mini" "Raccourcir et souder les quatre fils DuPont pour connecter l'écran">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% list %}}

***

> ### Connexions de l'écran au D1 mini

- Fil rouge VCC à 3,3v
- Fil noir GND à G
- Fil blanc SCL à D5
- Fil violet SDA à D3

{{% /list %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum02" "1280" "960" "640" "320" "mise sous tension du capteur de température et d'humidité" "Mise sous tension du capteur de température et d'humidité">}}
{{< /section >}}

{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section "-sub" >}}
{{< section_header "Troisième étape" "Assemblage des composants dans le boîtier" >}}
{{< /section >}}

{{< section_row "-top" >}}
{{% half_text %}}

J'ai utilisé mon pistolet à colle chaude pour assembler le capteur de température et d'humidité connecté.

Commencez par coller le présentoir. Il y a des épingles de positionnement dans l'impression (mais elles ne s'alignent pas toujours très bien)

{{% /half_text %}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum06" "1280" "960" "640" "320" "Fixation de l'écran lcd" "Coller à chaud le ecran">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

#### Il est nécessaire de couper la languette du capteur DHT22 pour lui permettre de s'insérer dans le boîtier

***

Insérez ensuite l'ensemble D1 mini et DHT22, en veillant à utiliser un peu de colle chaude pour assurer un espace entre le bouclier du DHT22 et l'écran.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum07" "1280" "960" "640" "320" "Assemblage des éléments de température et d'humidité dans le boîtier">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum08" "1280" "960" "640" "320" "Assemblage des éléments de température et d'humidité avec de la colle chaude">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum09" "1280" "960" "640" "320" "les composantes de la température et de l'humidité dans le boîtier">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum10" "1280" "960" "640" "320" "la mise sous tension du capteur de température et d'humidité fini" "L'ensemble fini prêt à être fermé et mis en place">}}
{{< /section >}}

{{< /section_main >}}

{{< section_main >}}

{{< section_header "Utilisation du capteur de température et d'humidité connecté" "Tableau de bord du Node Red" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% quote %}}
Actuellement, je ne les utilise que pour avoir une idée de la température et de l'humidité dans toute la maison, le but étant de les utiliser à terme pour ouvrir et fermer les circuits de chauffage au sol.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1-mini-nodered" "1024" "768" "512" "256" "node red output pour les capteurs de température et d'humidité" "Capture d'écran du tableau de bord du Node Red">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
