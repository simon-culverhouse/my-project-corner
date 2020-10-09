---
title: "Making A DIY Sunrise Alarm Lamp"
sub_title: "A gentle way to wake up on dark winter mornings"
date: 2020-01-13T08:34:19+02:00
slug: "making-a-diy-sunrise-lamp"
images:
    - sunrise_lamp/sunrise-lamp07-320.jpg
    - sunrise_lamp/sunrise-lamp07-959.jpg
    - sunrise_lamp/sunrise-lamp07-thin.jpg

summary: "This is my sunrise lamp build, I wanted to find out if a sunrise lamp could really make it easier to get up on dark winter mornings. Not wanting to..."
btn_txt: "rise and shine"
categories:
    - house & garden
    - 3d printing
    - arduino

---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "sunrise_lamp/sunrise-lamp07" "1278" "959" "639" "320" "Finished Sunrise Alarm Lamp" "Finished Sunrise Alarm Lamp">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
This is my sunrise lamp build, I wanted to find out if a sunrise lamp could really make it easier to get up on dark winter mornings. Not wanting to spend the 60+ euros on a ready made lamp (and because I like to make stuff), I came up with this design.

The idea is that the light stimulates you into waking up, exactly as you would on a summer’s morning, feeling relaxed and fresh, without the need for an alarm.
{{% /quote %}}
{{< /section >}}

<!-- TEXT BOX WITH HEADING  -->
{{< section "-multi-end" >}}
{{% section_textbox "-clear" %}}

It is built around an Ikea Fado table lamp and dimmable led bulb, using a 3d printed base to house the electronics. The final unit will be controlled through my Raspberry Pi Node Red dashboard.

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

> #### ***Parts Required for the Sunrise Lamp***

- Fado Lamp - Ikea

- Dimmable LED Bulb - Ikea
- WeMos D1 mini
- Hi-Link 220v AC - 5v DC
- RobotDyn PWM Dimmer
- Dupont Connectors
- The 3D Printed Base

{{% /list %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp12" "1278" "959" "639" "320" "Fado Lamp From Ikea" "Fado Lamp From Ikea">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp02" "1278" "959" "639" "320" "LED Bulb From Ikea" "LED Bulb From Ikea">}}
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
{{< image "sunrise_lamp/sunrise-lamp10" "1278" "959" "639" "320" "RobotDyn PWM Dimmer" "RobotDyn PWM Dimmer">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "sunrise_lamp/sunrise-lamp03" "1278" "959" "639" "320" "Sunrise lamp 3D Printed Base" "3D Printed Base">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section "-multi-end" >}}
{{% quote %}}
Excluding the 3d print the total cost came in at under 25€
{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Design and Printing" "3d Printed Base for Sunrise Lamp" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

I started by using SketchUp to design a base that would hold the electronics to control the lamp.

The design can be downloaded from **[Thingiverse](https://www.thingiverse.com/thing:4102831)**

I printed with 20% infill and 3 layers for base and walls. This makes it a nice solid print. The print time is upwards of 12 hrs using the settings that I used.

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp04" "1278" "959" "639" "320" "3d printed base for sunrise lamp ready for assembly">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi-end" >}}
{{% half_text %}}

The lamp doesn't sit fully in the printed base because of the taper on the base of the lamp. This was not intended but it's not extremely visible and the 4 small gaps allow for heat dispersal (not that it gets very hot at all).

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp15" "1278" "959" "639" "320" "showing gaps in sunrise lamp assembly">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Preparation and build" "Adding the Electronics to the Sunrise Lamp Base" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

#### Cut down the dimmer heatsink

It is necessary to reduce the height of the heatsink on the RobotDyn PWM dimmer to clear the base of the lamp.

Using a metal saw I removed 10mm from the top of the heatsink

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp11" "1278" "959" "639" "320" "reduce height of heatsink">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% quote %}}
I wouldn’t usually recommend reducing the size of a heatsink, but as the lamp will only be in operation for 45 minutes per day the heat build up should be minimal.
{{% /quote %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### Soldering the WeMos D1 Mini Pins

I used 2 blocks of pins, a 2 & a 4 as shown.

- Pins: 5v & G
- Pins: D6, D7, D8 & 3.3v

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp05" "1278" "959" "639" "320" "soldering pins on d1-mini">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### Insert and connect components

The electronics are held in place with a dab of hot glue

I’ve shortened standard length Dupont connection wires, I really need to invest in a crimping kit as it would save me a lot of time and produce a better finished look.

{{% /half_text %}}
{{< half_image >}}
{{< image "sunrise_lamp/sunrise-lamp14" "1278" "959" "639" "320" "sunrise lamp wiring">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% list %}}

***

> #### ***Wiring Connections***

1. Hi-Link AC supply.

2. Hi-Link AC supply.
3. DC Negative connection spliced to WeMos Ground pin.
4. DC Positive connected to WeMos 5v pin.
5. Dimmer Ground pin spliced to WeMos G pin.
6. Dimmer VCC pin connected to WeMos 3.3v
7. Dimmer Z-C pin connected to WeMos D6 pin.
8. Dimmer PWM pin connected to WeMos D7 pin.

{{% /list %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}
Cutting the lamp power cable to leave approx. 100mm on the bulb side. Tin the ends with a small amount of solder & also solder the Hi-Link AC supply wires to the power supply wires. Secure in the dimmer connection blocks as shown.
{{% /quote %}}
{{< /section >}}

{{< section "-top" >}}
{{< image "sunrise_lamp/sunrise-lamp09" "1278" "959" "639" "320" "Sunrise Alarm Lamp finished wiring" "Finished Sunrise Alarm Lamp wiring">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Setting Up" "Programming the WeMos D1 Mini" >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

I already use Node Red & MQTT running on my Raspberry Pi to control various devices around the house, so I wanted to integrate the diy sunrise lamp into the same system.

The main part of the code that controls the dimmer board came Nassir Malik’s GitHub page **[HERE](https://github.com/nassir-malik/IOT-AC-Light-Dimmer-With-Alexa/tree/master/Part%20%23%201/robodyn_dimmer)**. I would like to thank him for his work, really helped me out.

I added Wi-Fi and MQTT support and included a routine that would increase the brightness of the diy sunrise lamp over a 30 minute period.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-code" %}}

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

### **Node Red Set Up For Sunrise Lamp**

I’m using 3 nodes in the flow.

- Big Timer Node – for more information refer to **[Scargill's Big-Timer](https://tech.scargill.net/big-timer/)**
- Switch Node – used for a manual override.
- Mqtt Output Node

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{< image "sunrise_lamp/SunriseLamp-flow" "1053" "790" "527" "263" "Screenshot of Node Red flow" "Screenshot of Node Red flow">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
I have been using the DIY Sunrise Lamp for a few days and although the light doesn’t wake me up every time, it is nice to not be in total darkness when my google home mini starts playing music.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "sunrise_lamp/sunrise-lamp07" "1278" "959" "639" "320" "Homemade Sunrise Alarm Lamp" "The Finished Sunrise Alarm Lamp">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
