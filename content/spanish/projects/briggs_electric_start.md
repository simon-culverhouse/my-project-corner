---
title: "Reemplazando la batería InStart"
sub_title: "Alternativa a la batería de InStart de Briggs & Stratton"
date: 2020-07-22T22:13:10+02:00
slug: "reemplazando-batería-instart"
images:
    - instart_lawnmower/instart-lidl11-320.jpg
    - instart_lawnmower/instart-lidl11-640.jpg


summary: "Ahorrar dinero adaptando una batería recargable barata Lidl para usarla con un cortacésped InStart Briggs & Stratton..."
btn_txt: "Comienza"
categories:
    - casa y jardin
    - impresion en 3d
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "instart_lawnmower/instart-lidl11" "1280" "960" "640" "320" "adaptador de batería acabado para el cortacésped Briggs & Stratton Instart" "Terminado y listo para empezar">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
En un reciente viaje al supermercado local encontré una cortadora de césped en oferta especial, con un 50% de descuento. En el mercado de un nuevo cortacésped una reducción de 430 a 215 euros era una oferta demasiado buena como para rechazarla.

Sin embargo, la razón por la que estaba en oferta era porque era un modelo de arranque eléctrico de Briggs & Stratton, ¡y habían perdido la batería y el cargador! Lo compré de improviso, pensando que compraría una batería y un cargador y aún así ahorraría mucho.

¡No había apostado por el coste de una batería y un cargador de repuesto que costaba alrededor de 140 euros!

{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% section_textbox "-clear" %}}

#### Mi solución

Decidí tratar de adaptar una de las baterías de mis herramientas eléctricas existentes para hacer el trabajo. Investigando encontré que un mini cortador de setos de Lidl tenía un paquete de baterías recargables que era muy similar en voltaje y corriente al modelo Briggs & Stratton.

Al probar la batería Lidl descubrí otro problema, la batería InStart de Briggs & Stratton tiene 3 terminales. Positivo, negativo y un tercer terminal que sirve como interruptor para el botón de arranque (o llave). Cuando el positivo y el negativo de la batería de repuesto se conectan sin usar el tercer terminal, el motor de arranque gira continuamente.

Iba a necesitar encontrar una forma de evitar este problema

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "Primera etapa" "Diseñando y produciendo el modelo 3D" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

#### Diseño de TinkerCad

Decidí modelar el adaptador de la batería en dos partes, una parte se encajaría en el soporte de la batería del cortacésped y la segunda sujetaría la batería Lidl.

La razón principal para producir en dos partes es facilitar el proceso de impresión. Como una sola unidad, se necesitaría una cantidad significativamente mayor de soporte de impresión.

***

El primer paso fue modelar una réplica de la batería del InStart. Tomando medidas del cortacésped modelé un bloque que daba acceso a los pines positivos y negativos. También incorporé un gran agujero para aceptar el adaptador de la batería Lidl

La segunda parte del diseño era un soporte para la batería Lidl que encajaría en el primer modelo como se muestra a continuación. Este modelo tiene un cilindro central para el resorte y agujeros para las conexiones eléctricas.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl12" "1280" "960" "640" "320" "modelo de tinkercad de la parte principal" "Modelo de batería InStart">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl13" "1280" "960" "640" "320" "modelo de tinkercad de parte del adaptador" "Adaptador de batería Lidl">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl14" "1280" "960" "640" "320" "modelo de piezas ensambladas de Tinkercad" "Piezas ensambladas en TinkerCad">}}
{{< /third_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Segunda etapa" "3d imprimiendo las partes" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

#### El bloque principal

Impreso en PLA al revés con una resolución de 0,2 mm y un 20% de relleno. Añadiendo soporte para las dos ranuras laterales.

{{% /half_text %}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl02" "1280" "960" "640" "320" "Parte principal impresa en 3d para el adaptador de la batería">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### El adaptador

De nuevo impreso en PLA con una resolución de 0,2 mm y un 20% de relleno. Se ha añadido soporte para el anillo de localización de altura.

{{% /half_text %}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl03" "1280" "960" "640" "320" "Parte del adaptador impreso en 3d para el adaptador de la batería">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{< image "instart_lawnmower/instart-lidl04" "1280" "960" "640" "320" "adaptador de batería acabado para el cortacésped Briggs & Stratton Instart" "Partes impresas ensambladas">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

El diseño y los archivos de impresión pueden ser descargados en **[Thingiverse](https://www.thingiverse.com/thing:4565535)**, o usando el botón de abajo.
***
{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< download_box text="Haga clic en el botón para descargar los archivos stl" link="instart_lawnmower/battery_adaptor.zip" buttonText="Descargar archivos de impresión" >}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Etapa final" "Conexiones del terminal de la batería" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% quote %}}
Para hacer las conexiones entre la batería Lidl y los terminales Briggs y Stratton utilicé algunas tiras de cobre recuperadas de un viejo adaptador de luz.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

Además de insertar los terminales de cobre, añadí un muelle de compresión de 30 mm de largo x 6 mm de diámetro en el agujero central.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl05" "1280" "960" "640" "320" "insertando los terminales de la batería y el resorte">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl07" "1280" "960" "640" "320" "insertando los terminales de la batería">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

Los terminales de cobre se sueldan para terminar la unidad.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl06" "1280" "960" "640" "320" "conectando los terminales de la batería">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl08" "1280" "960" "640" "320" "conectando y soldando los terminales de la batería">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section_header "Arrancar el cortacésped" "Usando el adaptador de batería Briggs & Stratton Lidl" >}}

{{< section "-sub" >}}


{{< section_row "-top" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl10" "1280" "960" "640" "320" "El adaptador de batería Briggs & Stratton Lidl en el cortacésped" "Deslice el adaptador en su lugar">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl11" "1280" "960" "640" "320" "El adaptador de batería Briggs & Stratton listo para usar" "Inserte la batería Lidl y está listo para empezar">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% quote %}}
El siguiente video de YouTube muestra cómo funciona. La batería tiende a rebotar un poco si se deja en el adaptador, así que la saco mientras uso el cortacésped.

Aparte de eso, funciona muy bien.

{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< youtube sM8bHVu_H6M >}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}
