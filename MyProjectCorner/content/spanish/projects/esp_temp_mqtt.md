---
title: "Sensor de Temperatura ESP8266"
sub_title: "Sensor de temperatura portátil MQTT"
date: 2019-10-06T17:20:33+02:00
slug: "sensor-de-temperatura-esp8266"
images:
    - esp8266_temp/esp8266-mqtt01-320.jpg
    - esp8266_temp/esp8266-mqtt01-640.jpg
summary: "Un sensor de temperatura portátil construido con una placa de microcontrolador ESP8266 y un sensor impermeable DS18B20. Alojado en una caja impresa..."
btn_txt: "empezar a imprimir"
categories:
    - impresion en 3d
    - arduino
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "esp8266_temp/esp8266-mqtt01" "1280" "960" "640" "320" "Sensor de temperatura portátil usando ESP8266, MQTT y Node red" "Sensor de temperatura portátil usando ESP8266, MQTT y Node red">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}

Un sensor de temperatura portátil construido con una placa de microcontrolador ESP8266 y un sensor impermeable DS18B20. Alojado en una caja impresa en 3D de mi propio diseño.

Cuando se enciende, el ESP8266 se conecta primero a Wifi y luego al servidor MQTT en mi Raspberry Pi. Una vez conectado se envía un mensaje a intervalos regulares con la lectura de la temperatura.

{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% list %}}

***

> #### ***Las piezas para hacer que el sensor de temperatura del ESP8266***

- ESP8266 microcontroller
- DS18B20 sensor de temperatura a prueba de agua
- 4.7K resistor
- Caja impresa en 3D
- Fuente de alimentación de 5v

{{% /list %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< third_image >}}
{{< image "esp8266_temp/esp8266-mqtt02" "1280" "960" "640" "320" "La placa ESP8266 para el sensor de temperatura" "Placa ESP8266">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "esp8266_temp/esp8266-mqtt06" "1280" "960" "640" "320" "El sensor de temperatura a prueba de agua DS18B20" "El sensor de temperatura a prueba de agua DS18B20">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "esp8266_temp/esp8266-mqtt05" "1280" "960" "640" "320" "Un sensor de temperatura portátil ensamblado" "Un sensor de temperatura portátil ensamblado">}}
{{< /third_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Diseño e impresión" "Usando SketchUp y mi impresora 3D" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

El diseño de la carcasa de la placa esp8266 fue modelado en SketchUp. He tratado de mantenerlo lo más compacto posible, mientras que aún se deja espacio para el cableado.

Impreso en PLA con un 20% de relleno y soporte para los recortes.

Los archivos de diseño e impresión se pueden encontrar en **[Thingiverse](https://www.thingiverse.com/thing:4273457)**

{{% /half_text %}}
{{< half_image >}}
{{< image "esp8266_temp/esp8266-box" "1185" "960" "640" "320" "Modelo SketchUp de la caja del esp8266">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section_header "Montaje" "Soldando las conexiones" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "esp8266_temp/esp8266-mqtt04" "1280" "960" "640" "320" "Soldadura ESP8266 MQTT Sensor de temperatura">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

He soldado los cables del DS18B20 directamente a las clavijas del ESP8266 para facilitar la tarea,

1. Soldar el cable de alimentación rojo a la clavija de 3,3v al mismo tiempo soldando un extremo de la resistencia a la misma clavija.
2. Suelde el cable negro de tierra a la clavija GND.
3. Y finalmente, conectar el cable de datos amarillo a D4 (GPIO2), soldando de nuevo la resistencia al mismo tiempo.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

¡Y eso es todo para la asamblea!

Añadí un poco de pegamento caliente a las conexiones terminales para el aislamiento y la protección contra la corrosión. Y un toque alrededor del agujero de entrada del cable.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Etapa final" "Sube el código" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

***

#### **Añade el código a la unidad terminada**

Copia el código de abajo y pégalo en el IDE de Arduino. Cambie los detalles de la conexión wifi a su propia red wifi. También establezca la dirección IP del Raspberry pi ejecutando el servidor mqtt.

También necesitará las bibliotecas correspondientes:

- ESP8266 board support library
- Dallas Temperature library
- OneWire library
- Mqtt support library

Estos pueden ser fácilmente instalados a través de la opción "administrar bibliotecas" dentro del IDE de Arduino

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

Sólo queda configurar el flujo de entrada del MQTT en el Nodo Rojo y conectar la unidad.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Un uso para el sensor de temperatura" "Vigilar lo bien que funciona mi pila de abono" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

Tengo uno de estos pegado a un poste de metal de la cerca eléctrica, lo empujo a la pila de abono y lo enchufo a la batería de carga de un teléfono. Registra la temperatura en el nodo rojo del tablero de mi MQTT habilitado para Raspberry Pi.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "esp8266_temp/compost-temp" "1280" "960" "640" "320" "Midiendo la temperatura del abono con el sensor ESP8266">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "esp8266_temp/compost-temp02" "1280" "960" "640" "320" "Usando el sensor de temperatura ESP8266 para el abono">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

A continuación se muestra una captura de pantalla del Node Red Dashboard. Muestra la lectura del sensor de temperatura ESP8266 y un historial en forma de gráfico.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{< image "esp8266_temp/nodered-compost" "960" "720" "480" "240" "El tablero Node red para el sensor de temperatura portátil ESP8266">}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

Recientemente he modificado el diseño del sensor de temperatura ESP8266 para añadir un segundo DS18b20. Este se usa para monitorizar la temperatura del agua de entrada/salida de mi sistema de calefacción por suelo radiante.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
