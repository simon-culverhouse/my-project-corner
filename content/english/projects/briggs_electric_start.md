---
title: "Replacing InStart Battery"
sub_title: "Alternative to Briggs & Stratton InStart Battery"
date: 2020-07-22T22:13:10+02:00
slug: "instart-battery-alternative"
images:
    - instart_lawnmower/instart-lidl11-320.jpg
    - instart_lawnmower/instart-lidl11-640.jpg


summary: "Saving money by adapting a cheap Lidl rechargeable battery to be used with an InStart Briggs & Stratton lawnmower..."
btn_txt: "Start mowing"
categories:
    - house & garden
    - 3d printing
---

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{< image "instart_lawnmower/instart-lidl11" "1280" "960" "640" "320" "finished battery adaptor for briggs & stratton instart lawnmower" "Finished and ready to start">}}
{{< /section >}}

{{< section "-multi" >}}
{{% quote %}}
On a recent trip to the local supermarket I found a Lawnmower on special offer, 50% off. In the market for a new lawnmower a reduction from 430€ to 215€ was too good an offer to refuse.

However the reason it was on offer was because it was a Briggs & Stratton electric start model, and they had lost the battery and charger! I purchased it on the spur of the moment, thinking that I would buy a battery and charger and still make a huge saving.

I hadn't banked on the cost of a replacement battery and charger costing in the region of 140€!

{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{% section_textbox "-clear" %}}

#### My Solution

I decided to try to adapt one of my existing power tool batteries to do the job. On investigation I found that a mini hedge cutter from Lidl had a rechargeable battery pack that was very similar in voltage and current as the Briggs & Stratton model.

When testing the Lidl battery I discovered another problem, the Briggs & Stratton InStart battery has 3 terminals. Positive, negative and a third terminal which serves as a switch for the start button (or key). When the positive and negative of the replacement battery are connected without using the third terminal the starter motor turns continuously.

I was going to need to find a way around this issue

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section_header "First stage" "Designing and producing the 3d model" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-clear" %}}

#### TinkerCad Design

I decided to model the battery adaptor in two parts, one part would slot into the lawnmower battery holder and the second would hold the Lidl battery.

The main reason for producing in two parts is to facilitate the printing process. As one unit, there would need to be a significantly larger amount of print support needed.

***

The first step was to model a replica of the InStart battery pack. Taking measurements from the lawnmower I modelled a block which gave access to the positive and negative pins. Also incorporating a large hole to accept the adaptor for the Lidl battery

The second part of the design was a holder for the Lidl battery which would slot into the first model as shown below. This model has a central cylinder for the spring and holes for the electrical connections.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl12" "1280" "960" "640" "320" "tinkercad model of main part" "InStart battery model">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl13" "1280" "960" "640" "320" "tinkercad model of adaptor part" "Lidl battery adaptor">}}
{{< /third_image >}}
{{< third_image >}}
{{< image "instart_lawnmower/instart-lidl14" "1280" "960" "640" "320" "tinkercad model of assembled parts" "Parts assembled in TinkerCad">}}
{{< /third_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}
{{< section_header "Second stage" "3d printing the Parts" >}}

{{< section "-sub" >}}

{{< section_row "-top" >}}
{{% half_text %}}

#### The Main Block

Printed in PLA upside down with a 0.2mm resolution and 20% infill. Adding support for the two side slots.

{{% /half_text %}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl02" "1280" "960" "640" "320" "3d printed main part for battery adaptor">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section_row "-multi" >}}
{{% half_text %}}

#### The Adaptor

Again printed in PLA with a 0.2mm resolution and 20% infill. Support added for the height location ring.

{{% /half_text %}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl03" "1280" "960" "640" "320" "3d printed adaptor part for battery adaptor">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{< image "instart_lawnmower/instart-lidl04" "1280" "960" "640" "320" "finished battery adaptor for briggs & stratton instart lawnmower" "Printed parts assembled">}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

***

The design and print files can be downloaded on **[Thingiverse](https://www.thingiverse.com/thing:4565535)**, or by using the button below.
***
{{% /section_textbox %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< download_box text="Click on button to download stl files" link="instart_lawnmower/battery_adaptor.zip" buttonText="Download print files" >}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}

{{< section_header "Final stage" "Battery Terminal Connections" >}}

{{< section "-sub" >}}

{{< section "-top" >}}
{{% quote %}}
To make the connections between the Lidl battery and the Briggs and Stratton terminals I used some copper strips salvaged from an old light fitting adaptor.
{{% /quote %}}
{{< /section >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

As well as the inserting the copper terminals, I added a 30mm long x 6mm diameter compression spring into the center hole.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl05" "1280" "960" "640" "320" "inserting battery terminals and spring">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl07" "1280" "960" "640" "320" "inserting battery terminals">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% section_textbox "-clear" %}}

The copper terminals are then soldered to finish the unit.

{{% /section_textbox %}}
{{< /section >}}

{{< section_row "-multi-end" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl06" "1280" "960" "640" "320" "connecting battery terminals">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl08" "1280" "960" "640" "320" "connecting and soldering the battery terminals">}}
{{< /half_image >}}
{{< /section_row >}}

{{< /section >}}
{{< /section_main >}}

{{< section_main >}}

{{< section_header "Starting the mower" "Using the Briggs & Stratton Lidl battery adaptor" >}}

{{< section "-sub" >}}


{{< section_row "-top" >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl10" "1280" "960" "640" "320" "The Briggs & Stratton Lidl battery adaptor on the lawnmower" "Slide the adaptor into place">}}
{{< /half_image >}}
{{< half_image >}}
{{< image "instart_lawnmower/instart-lidl11" "1280" "960" "640" "320" "The Briggs & Stratton battery adaptor ready to use" "Insert the Lidl battery and it's ready to start">}}
{{< /half_image >}}
{{< /section_row >}}

{{< section "-multi" >}}
{{% quote %}}
The YouTube clip below shows how it works. The battery tends to bounce around a bit if left in the adaptor, so I take it out while using the mower.

Other than that, it works really well.

{{% /quote %}}
{{< /section >}}

{{< section "-multi-end" >}}
{{< youtube sM8bHVu_H6M >}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}
