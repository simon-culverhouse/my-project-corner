---
title: "Unidad de temperatura y cronómetro con Arduino"
sub_title: "Una ayuda para la temperatura y el temporizador de los pollos escaldados"
date: 2019-09-27T07:40:10+02:00
slug: "unidad-de-temperatura-y-cronometro-con-arduino"
images:
    - arduino_temp_timer/arduino-temp-timer06-320.jpg
    - arduino_temp_timer/arduino-temp-timer06-639.jpg
summary: "Hice esta unidad de temperatura y temporizador de arduino para ayudar a escaldar los pollos antes de desplumarlos. Incorpora un sensor a prueba de ..."
btn_txt: "Iniciar el tiempo"
categories:
    - impresion en 3d
    - arduino
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "arduino_temp_timer/arduino-temp-timer06" "1278" "959" "639" "320" "Temperatura de arduino terminada y temporizador" "Unidad de temperatura y temporizador">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Hice esta unidad de temperatura y temporizador de arduino para ayudar a escaldar los pollos antes de desplumarlos. Incorpora un sensor a prueba de agua para monitorear la temperatura del agua y una cuenta regresiva para el tiempo de inmersión. Tanto la temperatura como la cuenta atrás se muestran en la pantalla de 4 dígitos.
{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### **Componentes requeridos**

- Arduino Uno (o genérico)
- DS18D20 sensor de temperatura a prueba de agua con un cable de 1m
- TM1637 4 digit 7 segment display
- Caja impresa en 3D - Ver en **[Thingiverse](https://www.thingiverse.com/thing:3903097)**
- 4.7kΩ resistor

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Primera etapa" "La caja impresa en 3D" >}}

{{< section "-sub" >}}

{{< section_row "-sub" >}}
{{% half_text %}}

#### Remezclando el diseño

Basé mi diseño en una caja de Arduino Uno impresa en 3d disponible **[Aquí](https://www.thingiverse.com/thing:659873)**, que modifiqué en SketchUp.

La adición de un recorte para la pantalla de 4 dígitos, un agujero para el cable del sensor y el aumento de la altura de la cubierta para permitir más espacio. Aquí está el diseño final de **[Thingiverse](https://www.thingiverse.com/thing:3903097)**

{{% /half_text %}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer02" "1278" "959" "639" "320" "3d Impresión Arduino Uno Caja" "3d Imprimiendo la caja">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Segunda etapa" "Cableándolo" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "arduino_temp_timer/arduino-temp-timer03" "1278" "959" "639" "320" "El cableado de la temperatura y el temporizador de Arduino está terminado." "El cableado de la temperatura y el temporizador de Arduino está terminado.">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### Las conexiones

Utilizando cables de conexión dupont acortados, la energía y la tierra para el sensor de temperatura y la pantalla se soldaron a un solo cable de suministro, y la línea de datos para el sensor se soldó a la fuente de alimentación a través de la resistencia. Los cables CLK y DIO fueron acortados. Todas las conexiones fueron envueltas en plástico retráctil para evitar cualquier cortocircuito. Finalmente soldé un pin corto a cada cable para conectarlo a la UNO y uní la pantalla con mi pistola de pegamento caliente.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{% half_text %}}

***

Utilicé un tablero genérico Sunfounder Arduino Uno que tenía de un proyecto anterior.

Los otros artículos, aparte de los que se compraron en Amazon.

***

{{% /half_text %}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer08" "1278" "959" "639" "320" "Sunfounder genérico Arduino Uno" "Sunfounder genérico Arduino Uno">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### **Conexiones con Arduino Uno**

- Power to 5v Pin
- Ground to ground Pin
- Data wire to Pin 2
- Display CLK to Pin 6
- Display DIO to Pin 5

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Tercera Etapa" "Subir el código" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer05" "1278" "959" "639" "320" "La temperatura y el temporizador de Arduino casi han terminado" "Listo para montar">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "arduino_temp_timer/arduino-temp-timer04" "1278" "959" "639" "320" "La temperatura y el temporizador de Arduino están en funcionamiento" "La temperatura y el temporizador de Arduino están en funcionamiento">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### Configurar la UNO

Copia el boceto de Arduino abajo y usando el IDE de Arduino sube al Uno.

***

Se necesitarán tres bibliotecas adicionales

- OneWire
- DallasTemperature
- TM1637

***

Estos pueden ser fácilmente instalados usando las librerías de gestión en el IDE de Arduino

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

Este corto pedazo de código imprime la temperatura a los primeros 2 dígitos de la pantalla y un temporizador de cuenta atrás de 30 segundos a los últimos 2 dígitos.

He descubierto que 30 segundos es más o menos lo adecuado para hacer el trabajo, pero se puede ajustar fácilmente hasta un minuto cambiando la segunda variable.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

Esta cajita es de gran ayuda cuando estamos matando pollos.

Mantener el agua a la temperatura perfecta nunca ha sido tan fácil y un temporizador preciso (en lugar de contar en nuestras cabezas) es genial!
{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}