---
title: "Sensor de temperatura y humedad conectado"
sub_title: "Usando MQTT y el Node Red "
date: 2019-10-19T08:47:25+02:00
slug: "connected-temperature-humidity-sensor"
images:
    - d1mini_temp_hum/d1mini-temp-hum11-320.jpg
    - d1mini_temp_hum/d1mini-temp-hum11-640.jpg

summary: "Un sensor MQTT conectado con lectura LCD para monitorear las lecturas de temperatura y humedad en mi casa. He construido 3 de estos y los he coloca..."
btn_txt: "Haz uno ahora"
categories:
    - impresion en 3d
    - arduino
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum11" "1280" "960" "640" "320" "sensor de temperatura y humedad terminado" "Sensor de temperatura y humedad terminado en funcionamiento">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Un sensor MQTT conectado con lectura LCD para monitorear las lecturas de temperatura y humedad en mi casa. He construido 3 de estos y los he colocado en diferentes habitaciones, las lecturas de temperatura y humedad son enviadas por el MQTT a mi tablero Node Red en el Raspberry Pi.

Aunque no es realmente necesario tener una lectura digital para un sensor conectado, es práctico poder ver la temperatura sin tener que conectarse al nodo rojo del tablero.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### ***Las piezas utilizadas para construir la unidad del sensor***

- D1 mini
- DHT22 Shield
- Digital readout IC2 KY34-B
- Dupont connectors
- Caja impresa en 3D
- Fuente de alimentación de 5v

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section_header "Primer paso" "Diseño e impresión" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

### Modelado 3D del caso

Utilicé Tinkercad para crear el modelo 3D de mi diseño. Es la primera vez que uso Tinkercad y lo recomiendo encarecidamente. Es muy fácil de usar y produce un buen modelo.

Los archivos stl están disponibles para su descarga en **[Thingiverse](https://www.thingiverse.com/thing:3924670 "Haga clic aquí para visitar Thingiverse")**

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum13" "1280" "960" "640" "320" "Modelo 3D de la base para el sensor de temperatura y humedad" "Modelo 3D de la base">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum14" "1280" "960" "640" "320" "Modelo 3D de la cubierta del sensor de temperatura y humedad" "Modelo 3d de la cubierta">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

#### 3d Imprimiendo el caso

El diseño se imprimió en PLA negro con una resolución de 0,2 y un 20% de relleno. La base se imprimió con el soporte habilitado para el agujero oblongo de la fuente de alimentación.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum01" "1280" "960" "640" "320" "Estuche impreso en 3d para el sensor de temperatura y humedad" "Estuche impreso en 3d para el sensor de temperatura y humedad">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section "-sub" >}}
{{< section_header "Segundo paso" "Programación y conexiones" >}}
{{< /section >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

***

#### Sube el código al mini D1

Usando el código de Arduino de abajo, cambie los detalles de la conexión wifi a su propia red wifi. También establezca la dirección IP del Raspberry Pi ejecutando el servidor mqtt.

También necesitarás las bibliotecas de la junta pertinente

- ESP8266 support libraries
- Mqtt support
- IC2 Display
- DHT22

estos pueden ser fácilmente instalados a través de la opción "administrar bibliotecas" dentro del IDE de Arduino

Cuando termines puedes compilar y subir al mini D1.

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

#### Ensamblar los componentes

Compré tanto el mini D1 como el sombrero DHT22 en AliExpress. Una fuente barata para este tipo de componentes (si no tienes mucha prisa, puede tardar hasta 3 semanas en ser entregado).

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum12" "1280" "960" "640" "320" "soldando bloques de pines a d1 mini" "Soldar el bloque de pines hembra al escudo DHT22 y el bloque macho al mini D1.">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum04" "1280" "960" "640" "320" "conectando la pantalla a d1mini" "Acorta y suelda los cuatro cables DuPont para conectar la pantalla">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% list %}}

***

> ### Conexiones de la pantalla al D1 mini

- Cable rojo VCC a 3.3v
- Cable negro GND a G
- Alambre blanco SCL a D5
- Alambre púrpura SDA a D3

{{% /list %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum02" "1280" "960" "640" "320" "el sensor de temperatura y humedad se encendió" "El sensor de temperatura y humedad se encendió">}}
{{< /section >}}

{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section "-sub" >}}
{{< section_header "Tercer paso" "Ensamblar los componentes en la caja" >}}
{{< /section >}}

{{< section_row "-top" >}}
{{% half_text %}}

He usado mi pistola de pegamento caliente para montar el sensor de temperatura y humedad conectado.

Empieza pegando la pantalla en su lugar. Hay alfileres de localización en la impresión (pero no siempre se alinean muy bien)

{{% /half_text %}}
{{< half_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum06" "1280" "960" "640" "320" "Adjuntar la pantalla de LCD" "Pegamento caliente la pantalla en su lugar">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

#### Es necesario cortar la lengüeta del sensor DHT22 para que quepa en la caja

***

Luego inserte el ensamblaje D1 mini y DHT22, asegúrese de usar una gota de pegamento caliente para asegurar un espacio entre el escudo DHT22 y la pantalla.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum07" "1280" "960" "640" "320" "Ensamblando los componentes de temperatura y humedad en la caja">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum08" "1280" "960" "640" "320" "Ensamblando los componentes de temperatura y humedad con pegamento caliente">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum09" "1280" "960" "640" "320" "los componentes de temperatura y humedad en la caja">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1mini-temp-hum10" "1280" "960" "640" "320" "el sensor de temperatura y humedad terminado se encendió" "El ensamblaje terminado listo para ser cerrado y puesto en su lugar">}}
{{< /section >}}

{{< /section_main >}}

{{< section_main >}}

{{< section_header "Usando el sensor de temperatura y humedad conectado" "Node Red Dashboard" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% quote %}}
En la actualidad sólo los uso para tener una idea de la temperatura y la humedad en toda la casa, el objetivo es utilizarlos eventualmente para abrir y cerrar los circuitos de calefacción por suelo radiante.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "d1mini_temp_hum/d1-mini-nodered" "1024" "768" "512" "256" "salida del nodo rojo para los sensores de temperatura y humedad" "Captura de pantalla del panel Node Red">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
