---
title: "Sistema de alerta del ratón"
sub_title: "Detectar la invasión de ratones con un Raspberry Pi"
date: 2020-09-22T16:42:23+02:00
slug: "raspberry-pi-alerta-raton"
images:
    - mouse_detector/mouse-detector06-320.jpg
    - mouse_detector/mouse-detector06-640.jpg
summary: "En este proyecto, he instalado un sensor de movimiento infrarrojo conectado a un Raspberry Pi. Cuando se detecta movimiento, se envía una alerta po..."
btn_txt: "Haga uno"
categories:
    - raspberry pi

description: "Haz un detector de ratones usando un sensor de movimiento infrarrojo y un Pi de frambuesa. Sepa instantáneamente cuando los ratones se mueven en su casa"

---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "mouse_detector/mouse-detector06" "1280" "960" "640" "320" "El detector de ratones terminado usando un Pi de frambuesa" "El sistema de detección de ratones">}}
{{< /section >}}

<!-- QUOTE -->
{{< section "-multi" >}}
{{% quote %}}
En este proyecto, he instalado un sensor de movimiento infrarrojo conectado a un Raspberry Pi.

Cuando se detecta movimiento, se envía una alerta por mensaje de texto a mi teléfono móvil, diciéndome que saque las trampas para ratones.

{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### El problema de los ratones

Vivir en el campo, en una casa de piedra, la infestación de ratones puede ser un problema. El mayor problema es que para cuando sabemos que están en la casa, por ejemplo, vemos uno o la comida en la despensa comienza a ser mordida, estamos infestados.

Encontramos que la invasión de los ratones se produce en varios momentos del año. Tener trampas permanentemente en su lugar significa comprobar regularmente para ver si han atrapado algo. Como están en el techo (donde los ratones tienden a llegar primero), no es fácil y por lo tanto no se hace.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### ***Partes requeridas***

- Raspberry Pi
- HC-SR501 PIR Sensor de movimiento
- Caja de conectores del cable eléctrico de plástico
- Longitud del cable telefónico de 4 núcleos
- Dupont conectores

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "El sensor de movimiento" "Construir la caja" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

Usando una broca para madera de 22 mm, haz un agujero en la tapa de la caja de cables de plástico.

Aunque el diámetro de la cúpula del sensor de movimiento es de 24mm, he encontrado que la broca de 22mm hace un agujero más grande al perforar el plástico. Una vez limpiado, es un ajuste perfecto.

{{% /half_text %}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector03" "1280" "960" "640" "320" "Perforar el agujero para el sensor de movimiento del detector de ratones">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

### Montar la caja del sensor de movimiento

Prepara el cable para conectar la caja del sensor al Pi de Frambuesa. Me estoy conectando a un Pi existente que está a unos 3 metros de distancia.

Corta 3 cables Dupont hembra/hembra por la mitad, y suelda a cada extremo de la longitud del cable (asegurándote de que los colores se correspondan en cada extremo). Proteja de los cortocircuitos con cinta termocontraíble o eléctrica.

Usando una pistola de pegamento caliente (o sólo pegamento), fije el sensor de infrarrojos a la tapa. Pase un extremo del cable a través del agujero lateral y conéctelo al sensor.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector04" "1280" "960" "640" "320" "haciendo el cable para el detector de ratones" "Haz que el cable">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector05" "1280" "960" "640" "320" "Usando pegamento caliente para fijar el sensor de movimiento del detector de ratones" "Pegamento caliente en el sensor">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector01" "1280" "960" "640" "320" "Cablear el sensor de movimiento del detector de ratones" "Conectando">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector02" "1280" "960" "640" "320" "La caja del sensor de movimiento del detector de ratones terminada" "Unidad terminada">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector07" "1280" "960" "640" "320" "La caja del sensor de movimiento del detector de ratones terminada en el ático" "El sensor de movimiento atornillado a una viga en el desván">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "La instalación del Raspberry Pi" "Conectando y codificando" >}}

{{< section "-sub" >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

### Conecta el sensor al Raspberry Pi

- VCC a 5v (pin 2 or 4)

- GRD a GRD (pin 6 or 9)

- OUT a GPIO4 (pin 7)

Después de la conexión, abra su editor de pitón preferido y copie el siguiente bloque de código. Introduzca los datos de conexión para el usuario y el pase, y guarde el archivo.

Utilizo Free Mobile y así me conecto a la API de Free SMS para enviar mensajes de texto. Pensaría que la mayoría de las otras redes móviles tienen un servicio similar.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-code" %}}

``` python
#!/usr/bin/python3
import urllib.request
from gpiozero import MotionSensor

pir_mice = MotionSensor(4)
url = "https://smsapi.free-mobile.fr/sendmsg?user=********&pass=********&msg=Mouse+Detected"

while True:
    pir_mice.wait_for_motion()
    print("Mouse!")
    urllib.request.urlopen(url)
    pir_mice.wait_for_no_motion()

```

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% quote %}}
Y eso es todo, sólo tienes que ejecutar el script python en Python Shell y esperar una alerta del ratón en tu teléfono.

He estado usando este sistema de alerta temprana desde hace un par de años, y con él, hemos sido capaces de lidiar con los ratones tan pronto como empiezan a moverse.

Ahora estoy trabajando en una versión portátil usando una placa esp8266, para usar en las dependencias.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
