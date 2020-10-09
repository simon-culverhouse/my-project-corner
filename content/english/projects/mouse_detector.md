---
title: "Mouse early warning system"
sub_title: "Detecting mouse invasion with a Raspberry Pi"
date: 2020-09-22T16:42:23+02:00
slug: "raspberry-pi-mouse-detector"
images:
    - mouse_detector/mouse-detector06-320.jpg
    - mouse_detector/mouse-detector06-640.jpg
summary: "In this project, I've set up an infrared motion sensor connected to a Raspberry Pi. When movement is detected a text message alert is sent to my mo..."
btn_txt: "Make One"
categories:
    - raspberry pi

description: "Make a mouse detector using a PIR motion sensor and a Raspberry Pi. Know instantly when mice are moving into your house"

---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "mouse_detector/mouse-detector06" "1280" "960" "640" "320" "The finished mouse detector using a Raspberry Pi" "The mouse detection system">}}
{{< /section >}}

<!-- QUOTE -->
{{< section "-multi" >}}
{{% quote %}}
In this project, I've set up a PIR motion sensor connected to a Raspberry Pi to act as an early warning mouse detecter system.

When movement is detected a text message alert is sent to my mobile phone, telling me to get the mouse traps out!

{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

#### The Mouse Problem

Living in the countryside, in a stone-built house mouse infestation can be a problem. The biggest issue is that by the time we know that they are in the house, for example, we see one or food in the larder starts to get nibbled, we're infested.

We find that mouse invasion occurs at various times throughout the year. Having traps permanently in place means checking regularly to see if they have caught anything. As these are in the roofspace (where the mice tend to arrive first), it's not easy and so doesn't get done.

{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% list %}}

***

> #### ***Required Parts***

- Raspberry Pi
- HC-SR501 PIR Motion sensor
- Plastic electrical cable connector box
- Length of 4 core telephone cable
- Dupont connectors

{{% /list %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "The PIR Motion Sensor" "Building the box" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

Using a 22mm wood drill bit, make a hole in the lid of the plastic cable box.

Although the diameter of the motion sensor dome is 24mm, I've found that the 22mm drill makes a bigger hole when drilling plastic. Once cleaned up, it's a perfect fit.

{{% /half_text %}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector03" "1280" "960" "640" "320" "Drilling the hole for the mouse detector motion sensor">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

### Assemble the motion sensor box

Make up the cable to connect the sensor box to the Raspberry Pi. I am connecting to an existing Pi which is around 3 meters away.

Cut 3 female/female Dupont wires in half, and solder to each end of the length of cable (making sure the colors correspond at each end). Protect from short circuits with heat shrink or electrical tape.

Using a hot glue gun (or just glue), fix the infrared sensor to the lid. Pass one end of the cable through the side hole, and connect to the sensor.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector04" "1280" "960" "640" "320" "making the cable for the mouse detector" "Make the cable">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector05" "1280" "960" "640" "320" "Using hot glue to attach the mouse detector motion sensor" "Hot glue the sensor">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "mouse_detector/mouse-detector01" "1280" "960" "640" "320" "Wiring the mouse detector motion sensor" "Connecting">}}
{{< /third_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector02" "1280" "960" "640" "320" "The finished mouse detector motion sensor box" "Finished unit">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "mouse_detector/mouse-detector07" "1280" "960" "640" "320" "The finished mouse detector motion sensor box in the attic" "The motion sensor screwed to a rafter in the loft">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Raspberry Pi Set-up" "Connecting and coding" >}}

{{< section "-sub" >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

### Connect the sensor to the Raspberry Pi

- VCC to 5v (pin 2 or 4)

- GRD to GRD (pin 6 or 9)

- OUT to GPIO4 (pin 7)

After connection, open your preferred python editor and copy the following code block. Enter your connection details for user and pass, and save the file.

I use Free Mobile and so connect to the Free SMS API to send text messages. I would think most other mobile networks have a similar service.

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
And that's it, just run the python script in Python Shell and wait for a mouse alert on your phone.

I've been using this early warning system for a couple of years now, and with it, we have been able to deal with the mice as soon as they start to move in.

I am now working on a portable version using a esp8266 board, to use in outbuildings.

{{% /quote %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
