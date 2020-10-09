---
title: "Asustar a los pájaros con láser verde automatizado"
sub_title: "La solución para el problema del estornino en el cobertizo de la vaca"
date: 2017-10-10T17:38:26+02:00
slug: "laser-verde-automatizado"
images:
    - laser_bird_scare/bird-scare04-320.jpg
    - laser_bird_scare/bird-scare04-640.jpg
summary: "Construyendo un repelente de pájaros con láser verde usando un Arduino Uno y algo de electrónica básica de pasatiempo. Usado para disuadir la invas..."
btn_txt: "Ver Construir"
categories:
    - arduino

---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "laser_bird_scare/bird-scare04" "1280" "960" "640" "320" "arduino automatizó el susto de los pájaros con láser verde" "Terminado y encendido">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
Construyendo un repelente de pájaros con láser verde usando un Arduino Uno y algo de electrónica básica de pasatiempo. Usado para disuadir la invasión de estorninos de invierno en los establos.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

#### Mi solución para el problema del estornino en la granja

Cada año alrededor de septiembre/octubre, junto con la cosecha de ensilado de maíz, viene la invasión de estorninos. Este es un problema importante en el establo de las vacas, no sólo consumen la mejor parte del ensilaje, los granos de maíz, sino que también dejan depósitos desagradables y potencialmente peligrosos de excrementos sobre el alimento y el equipo de las vacas. La solución fue un láser verde de alta potencia.

Al buscar formas de ahuyentarlos, me encontré con un artículo que mencionaba que las aves en general le temen a la luz de alta intensidad, especialmente a la luz verde. El primer paso fue comprar un par de punteros de láser verde, es increíble lo bien que funcionó. Durante un par de temporadas (sólo hasta marzo), regularmente recorría la granja asustando a los pájaros. Aunque no erradicaba completamente el problema, lo reducía en gran medida ya que la gran mayoría de los estorninos se trasladaban a otros lugares.

Sin embargo, exigía bastante tiempo. Fue entonces cuando decidí automatizar el proceso, empecé por poner un láser en un temporizador. Pero pronto descubrí que la luz debía moverse para obtener el efecto deseado y también para cubrir todo el establo. Así que esto es lo que se me ocurrió, un automatismo láser para asustar a los pájaros.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< image "laser_bird_scare/bird-scare05" "900" "675" "450" "225" "el estornino comiendo con la vaca">}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "What's Needed" "Los componentes utilizados para construir el láser para asustar a los pájaros" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% list %}}

***

> #### ***Las partes principales para la construcción***

- Arduino Uno, usé un Sunfounder Uno genérico ya que tenía que mantener los costos al mínimo.
- Módulo de reloj en tiempo real I2C - RTC DS3231
- Relé 5v disparador de bajo nivel
- La unidad de láser verde de alta potencia fue ordenada a AliExpress
- Motor paso a paso 5V 28BYJ-48 y Tablero de control ULN2003
- Caja impermeable 240 x 190 x 90mm con tapa abatible
- Fuente de alimentación de 9v para Arduino Uno
- Mini breadboard SYB-170

***

{{% /list %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "laser_bird_scare/bird-scare03" "701" "526" "351" "175" "láser verde de alta potencia" "Láser verde de alta potencia">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "laser_bird_scare/bird-scare09" "701" "526" "351" "175" "genérico sunfounder arduino uno" "Sunfounder Uno">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "laser_bird_scare/bird-scare06" "701" "526" "351" "175" "módulo de reloj en tiempo real" "Módulo de reloj en tiempo real">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox_list "-clear" %}}

***

#### Partes misceláneas

- Los cables de conexión de Dupont

- Palitos de pegamento caliente

- El suelo laminado cortado para la tabla de la base

- También usé un pequeño trozo de plexiglás y algunos pequeños tornillos y tuercas para montar la unidad de láser en el motor de paso, Si tuviera que reconstruir las unidades reemplazaría el plexiglás por una placa de montaje impresa en 3D.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}

Construí dos de estas cajas láser automatizadas para asustar a los pájaros, una para cada cobertizo de la granja. El costo de todos los componentes fue de poco menos de 100 euros por unidad y pasé cerca de un día para el montaje y la puesta en marcha de ambas cajas.

He tratado de usar piezas fácilmente disponibles para mi espantoso pájaro láser automatizado, el único artículo que puede ser difícil de reemplazar (si es necesario) es la unidad láser. Debería haber comprado un repuesto en el momento de la construcción, pero al ser el artículo más caro el presupuesto no lo permitía. Con suerte, nunca necesitaré un repuesto.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "El edificio" "Ensamblando la caja de pedazos" >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "laser_bird_scare/bird-scare01" "1280" "960" "640" "320" "ensamblado láser verde de miedo a los pájaros">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

Decidí usar un Arduino Uno como controlador porque sólo quería que ejecutara una pequeña cantidad de código y que fuera fácil de usar, sólo hay que conectarlo y listo. De esa manera cualquiera podría mover o instalar la caja en otro lugar si fuera necesario.

La placa de montaje de la electrónica es un corte de suelo laminado que recorté para que encajara perfectamente en la caja impermeable inferior.

Luego dispuse los componentes en la placa y marqué las posiciones con un lápiz, luego quité los componentes y usando un taladro de 3mm taladré agujeros de 4mm de profundidad en las marcas del lápiz.

Luego, cortando una barra de pegamento en 8mm de largo, procedí a pegar estas brocas en caliente sobre los agujeros taladrados, todos excepto la placa de control del láser. Una vez que el pegamento se enfrió, coloqué y pegué en caliente los componentes uno por uno sobre estos "pilares de barras de pegamento". La placa de control del láser se fijó directamente a la placa base de la misma manera.

El motor paso a paso se fijó en el centro de la tapa con pequeños tornillos avellanados.

La mini breadboard fue pegada usando su propio pegamento.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}
Aunque se trata de un montaje muy 'DIY', todas las piezas siguen en su lugar y funcionando después de 2 años de uso y estoy contento con el tiempo ahorrado en comparación con la opción de montaje atornillado.
{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section "-sub" >}}
{{< section_header "La etapa final..." "Codificando y conectando" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

#### El Código de Arduino

He mezclado varios fragmentos de código de ejemplo para producir algo que funcione, el objetivo del código es conseguir que el servo gire el láser a través de un ángulo predefinido a intervalos regulares a lo largo del día. El efecto de barrido del láser permite cubrir un área más grande y también lo hace más efectivo.

El boceto de Arduino.

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
Quería hacer un diagrama de Fritzing para el cableado, pero nunca encontré el tiempo. Así que hice una lista de las conexiones lo mejor posible.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{< image "laser_bird_scare/bird-scare02" "1280" "960" "640" "320" "conectando el miedo a los pájaros con láser verde">}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% section_textbox_list "-clear" %}}

***

#### ***Cableado de los componentes***

Así es como conecté el susto del pájaro láser:

##### *Controlador del motor de pasos*

- IN1 – Arduino Uno Pin 8
- IN2 – Arduino Uno Pin 9
- IN3 – Arduino Uno Pin 10
- IN4 – Arduino Uno Pin 11
- Power + to Breadboard Shared 5v
- Power – to Arduino Uno GND

##### *Módulo de reloj en tiempo real*

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

##### *Junta de Control de Láser*

- Connected to Breadboard Input Ground and Relay

##### *Power Supply*

- Split at Breadboard to supply 9v to Arduino and to Laser

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Prueba de funcionamiento" "Aquí hay un video de ello trabajando en mi cobertizo" >}}

{{< section "-sub" >}}
{{< section "-top" >}}
{{< youtube exR2xbYiY8g >}}
{{< /section >}}
{{< section "-multi-end" >}}
{{% quote %}}
Utilicé el dispositivo láser para ahuyentar a los pájaros durante 3 inviernos y aunque no eliminó completamente los estorninos, definitivamente redujo los números. La principal ventaja era que los pájaros no se quedaban en los establos durante la noche.

Además, continuaría trabajando los fines de semana cuando yo no lo hiciera.
{{% /quote %}}
{{< /section >}}
{{< /section >}}
{{< /section_main >}}
