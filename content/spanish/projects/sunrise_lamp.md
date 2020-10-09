---
title: "Lámpara de alarma del amanecer DIY"
sub_title: "Mi proyecto de lámpara de amanecer DIY"
date: 2020-01-13T08:34:19+02:00
slug: "lampara-de-alarma-del-amanecer-diy"
images:
    - sunrise_lamp/sunrise-lamp07-320.jpg
    - sunrise_lamp/sunrise-lamp07-959.jpg
    - sunrise_lamp/sunrise-lamp07-thin.jpg

summary: "Esta es la construcción de mi lámpara del amanecer, quería saber si una lámpara del amanecer podría facilitar el levantarse en las oscuras mañanas ..."
btn_txt: "Despierta suavemente"
categories:
    - casa y jardin
    - impresion en 3d
    - arduino

---
{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "sunrise_lamp/sunrise-lamp07" "1278" "959" "639" "320" "Lámpara de alarma del amanecer DIY" "Lámpara de alarma del amanecer">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Esta es la construcción de mi lámpara del amanecer, quería saber si una lámpara del amanecer podría facilitar el levantarse en las oscuras mañanas de invierno. No queriendo gastar los más de 60 euros en una lámpara ya hecha (y porque me gusta hacer cosas), se me ocurrió este diseño.

La idea es que la luz te estimula para que te despiertes, exactamente como lo harías en una mañana de verano, sintiéndote relajado y fresco, sin necesidad de una alarma.
{{% /quote %}}
{{< /section >}}

<!-- TEXT BOX WITH HEADING  -->
{{< section "-multi-end" >}}
{{% section_textbox "-clear" %}}

Está construido alrededor de una lámpara de mesa Ikea Fado y una bombilla de leds regulables, usando una base impresa en 3d para alojar la electrónica. La unidad final se controlará a través de mi tablero de mandos Raspberry Pi Node Red.

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

> #### ***Partes requeridas para la lámpara de amanecer DIY***

- Fado Lamp - Ikea

- Bombilla LED regulable - Ikea
- WeMos D1 mini
- Hi-Link 220v AC - 5v DC
- RobotDyn PWM Dimmer
- Dupont Connectors
- y la Base de Impresión 3D usando mi impresora CR10S.

{{% /list %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp12" "1278" "959" "639" "320" "Lámpara de mesa Ikea Fado" "Lámpara de mesa Ikea Fado">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp02" "1278" "959" "639" "320" "Bombilla LED regulable" "Bombilla LED regulable">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp05" "1278" "959" "639" "320" "WeMos D1 mini" "WeMos D1 mini">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp01" "1278" "959" "639" "320" "Hi-Link 220v AC - 5v DC" "Módulo Hi-Link">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp10" "1278" "959" "639" "320" "RobotDyn PWM Dimmer" "RobotDyn PWM Dimmer">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp03" "1278" "959" "639" "320" "Base impresa en 3d para la lámpara del amanecer" "Base impresa en 3d">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section "-multi-end" >}}
{{% quote %}}
Excluyendo la impresión en 3D, el coste total fue inferior a 25 euros.
{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Diseño e impresión" "Base impresa en 3d para la lámpara del amanecer" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

Empecé usando SketchUp para diseñar una base que sostuviera la electrónica para controlar la lámpara.

El diseño se puede descargar AQUÍ de **[Thingiverse](https://www.thingiverse.com/thing:4102831)**

 Esto hace que sea una bonita pieza sólida. El tiempo de impresión es de más de 12 horas usando los ajustes que usé. Imprimí con un 20% de relleno y 3 capas para la base y las paredes.

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp04" "1278" "959" "639" "320" "Base impresa en 3d para la lámpara del amanecer lista para su montaje.">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi-end" >}}
{{% half_text %}}

La lámpara no se asienta completamente en la base impresa debido al estrechamiento de la base de la lámpara. Si tuviera que construir de nuevo, incorporaría el cono en el diseño impreso, pero entonces, tal y como está ahora, deja 4 pequeños huecos que permiten la dispersión del calor. 

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp15" "1278" "959" "639" "320" "Mostrando los huecos de aire en el ensamblaje de la lámpara del amanecer">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Preparación y construcción" "Añadiendo la electrónica a la base de la lámpara del amanecer" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

#### Cortar el disipador de calor

Necesitaba reducir la altura del disipador térmico del regulador PWM del RobotDyn para despejar la base de la lámpara.

Usando una sierra de metal quité 10mm de la parte superior del disipador térmico

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp11" "1278" "959" "639" "320" "Cortar el disipador de calor">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% quote %}}
Normalmente no recomendaría reducir el tamaño de un disipador, pero como la lámpara sólo funcionará durante 45 minutos al día, la acumulación de calor será mínima.
{{% /quote %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### Soldadura de los Pines WeMos D1 Mini

Utilicé dos bloques de pins, un 2 y un 4 como se muestra.

- Pins: 5v & G
- Pins: D6, D7, D8 & 3.3v

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp05" "1278" "959" "639" "320" "pines de soldadura en d1-mini">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### Insertar y conectar los componentes

La electrónica se mantiene en su lugar con un poco de pegamento caliente

He acortado los cables de conexión de Dupont de longitud estándar, realmente necesito invertir en un kit de engarce ya que me ahorraría mucho tiempo y produciría un mejor acabado.

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp14" "1278" "959" "639" "320" "cableado de la lámpara del amanecer">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% list %}}

***

> #### ***Conexiones de cableado***

1. Hi-Link AC supply.

2. Hi-Link AC supply.
3. DC Negative connection empalmado a WeMos Ground pin.
4. DC Positive conectado al WeMos 5v pin.
5. Dimmer Ground pin empalmado a WeMos G pin.
6. Dimmer VCC pin conectado al WeMos 3.3v
7. Dimmer Z-C pin conectado al WeMos D6 pin.
8. Dimmer PWM pin conectado al pin WeMos D7.

{{% /list %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}
Cortar el cable de alimentación de la lámpara para dejar unos 100mm en el lado de la bombilla. Estañar los extremos con una pequeña cantidad de soldadura y también soldar los cables de suministro de CA de alta velocidad a los cables de suministro de energía. Asegure los bloques de conexión del regulador de intensidad luminosa como se muestra.
{{% /quote %}}
{{< /section >}}

{{< section "-top" >}}
{{< image "sunrise_lamp/sunrise-lamp09" "1278" "959" "639" "320" "La lámpara del amanecer terminó el cableado" "La lámpara del amanecer terminó el cableado">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Estableciendo..." "Preparando el WeMos D1 Mini" >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

Ya uso el Node Red y MQTT que se ejecuta en mi Raspberry Pi para controlar varios dispositivos en la casa, así que quería integrar la lámpara diy sunrise en el mismo sistema.

La parte principal del código que controla el tablero del regulador de voltaje vino de la página de GitHub de Nassir Malik **[HERE](https://github.com/nassir-malik/IOT-AC-Light-Dimmer-With-Alexa/tree/master/Part%20%23%201/robodyn_dimmer)**. Me gustaría agradecerle su trabajo, me ayudó mucho.

Añadí soporte Wifi y MQTT e incluí una rutina que aumentaba el brillo de la lámpara del amanecer diy en un período de 30 minutos.

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

### **Instalar la lámpara de amanecer DIY en el node red**

Estoy usando 3 nodes en el flujo.

- Big Timer Node - para obtener más información, consulte **[Scargill's Big-Timer](https://tech.scargill.net/big-timer/)**
- Switch Node – usado para una anulación manual.
- Mqtt Output Node

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{< image "sunrise_lamp/SunriseLamp-flow" "1053" "790" "527" "263" "lámpara del amanecer Node Red instalado" "Captura de pantalla del flujo del Node Red">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
He estado usando la lámpara del amanecer DIY durante unos días y aunque la luz no me despierta siempre, es agradable no estar en la oscuridad total cuando mi mini casa de Google empieza a tocar música.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "sunrise_lamp/sunrise-lamp07" "1278" "959" "639" "320" "La lámpara del amanecer terminada y lista para ser usada" "La lámpara del amanecer terminada">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
