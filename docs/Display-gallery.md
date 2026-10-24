# VoltDeck — display and telemetry gallery

[Home](../README.md) | [Norsk](Visningsgalleri-norsk.md) | [Configuration](Configuration.md)

Genuine **800 × 480 captures from the X20RS simulator, ETHOS 26.1.2**, running stable VoltDeck 2026.10-v9. Instruments and aircraft images are drawn by the app in the simulator. Telemetry values are controlled illustrations; no physical receiver or sensor was connected. The settings beneath each example explain how to configure that view.

## Deck and Digital, with and without a picture

<table>
<tr>
<td><a href="images/native-voltdeck-deck-photo.png"><img src="images/native-voltdeck-deck-photo.png" alt="Deck / model picture" width="400"></a><br><b>Deck / model picture</b></td>
<td><a href="images/native-voltdeck-deck-hidden.png"><img src="images/native-voltdeck-deck-hidden.png" alt="Deck / Hidden" width="400"></a><br><b>Deck / Hidden</b></td>
</tr>
<tr>
<td><a href="images/native-voltdeck-digital-photo.png"><img src="images/native-voltdeck-digital-photo.png" alt="Digital / model picture" width="400"></a><br><b>Digital / model picture</b></td>
<td><a href="images/native-voltdeck-digital-hidden.png"><img src="images/native-voltdeck-digital-hidden.png" alt="Digital / Hidden" width="400"></a><br><b>Digital / Hidden</b></td>
</tr>
</table>

Choose **Appearance > Display style = Deck / Digital**, then **Image source = Image file / Selected model / Hidden**. These captures use Image file. Selected model uses the same picture area with the ETHOS model image. Only explicit Hidden reallocates that area; an image error does not. Deck is the default. Style and picture choices never change sources or calculation methods.

## Choices in the app

Open the widget menu and choose **Configure widget > Appearance**. **Display style** and **Image source** are independent. Set source pickers to telemetry actually discovered on your radio; the illustrative readings do not assign sensors automatically.

<table>
<tr>
<td><img src="images/native-voltdeck-style-choices.png" alt="Display style: Deck / Digital"><br><b>Display style</b></td>
<td><img src="images/native-voltdeck-image-choices.png" alt="Image source: Selected model / Image file / Hidden"><br><b>Image source</b></td>
</tr>
</table>

The main views use **Lower deck > Show = RPM + W + cell**, **Meter style = Retro LCD**, **Custom source = ESC temperature**, **Custom label = ESC TEMP**, **Custom position = 3**, **Custom min/max = 0/150**, **Decimals (-1 auto) = 0**, **Remaining from = Consumed mAh**, **mAh display = Remaining** and **RPM value = Measured RPM**. **RPM scale = Manual**, **RPM max = 12000** and **Watt max = 1500**. Chemistry and capacity are given below. With a picture/Digital, Custom occupies one of the three slots; Deck + Hidden also shows the cell field.

## Aircraft, readings and telemetry

The aircraft is an **Ultimate AMR 60 electric biplane**. The example pack is **6S Lipo, 3300 mAh**. The main four views use 22.8 V, 24.5 A, 620 mAh consumed, 2680 mAh remaining and 81%. Mechanical RPM is 8300 and ESC temperature is 57 °C. These are an illustrative sensor installation, not measurements of this aircraft.

| Program role | Reading represented in this example | Suitable installation |
| --- | --- | --- |
| Pack voltage | Pack voltage — V | Compatible ESC telemetry, UniSens-E or a voltage/current sensor |
| Pack current | Propulsion current — A | Compatible ESC, UniSens-E or FAS current sensor |
| Consumed mAh | Accumulated pack consumption — mAh | ESC/UniSens-E consumption, or ETHOS Consumption calculated from current |
| RPM | Corrected mechanical motor/propeller speed — rpm | ESC RPM or a compatible RPM sensor; configure pole/gearing conversion upstream |
| Custom | ESC temperature — °C | The ESC temperature channel; this is not motor or cylinder temperature |
| RX / TX | Receiver/transmitter battery voltage — V | Receiver and radio sources |
| RF1 / RF2 | VFR 2.4G / VFR 900M — % | Two actual discovered RF sources |
| Flight time | ETHOS timer — s | Selected model timer |

**559 W** is electrical input power, 22.8 × 24.5. It is not shaft power. **3.80 V** is average cell voltage, 22.8 / 6; it is not the lowest individual cell.

A percent method requires a real remaining-charge **%** source. Voltage estimate needs pack **V**, chemistry and cell count. The independent remaining-mAh field still requires trustworthy consumed **mAh** and capacity with either method. The examples deliberately show different charge percentages for these methods; they are not accuracy comparisons.

Compatible installations include [FrSky FAS100 ADV](https://frskyna.com/products/frsky-adv-fas100-current-sensor) for voltage/current and [SM UniSens-E](https://www.sm-modellbau.de/UniSens-E) for electric-drive telemetry. A V/A sensor does not automatically provide a consumed-mAh counter: use an actual counter or [ETHOS Consumption](https://ethos-doc.frsky-rc.com/model-setup/telemetry/#consumption-sensor). Check the actual FrSky output and units for your sensor/firmware; names are examples, not an automatic sensor assignment.

## Lower deck

All eight choices are shown with **Numeric** and **Retro LCD**. Lower deck remains available in Digital. **Deck + Hidden** can show RPM, W, average cell voltage and Custom together; photo Deck and Digital keep three slots when Custom is added. Custom position sets the order.

| Lower deck | Required readings |
| --- | --- |
| Only Custom | Custom numeric source + correct unit |
| RPM | Measured mechanical rpm, or explicitly selected KV estimate |
| Watts | Pack V + propulsion A |
| Cell volts | Pack V + series-cell count (average) |
| Voltage estimate | Pack V + chemistry + series-cell count |
| RPM + Watts | RPM + pack V + propulsion A |
| RPM + W + cell | RPM + pack V + propulsion A + cell count |
| Hidden | No lower instruments; consumers used by battery/log/alerts still apply |

### Numeric

<details>
<summary>Only Custom / Numeric</summary>

![Only Custom / Numeric](images/native-voltdeck-lower-1-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Only Custom**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 3**.

</details>

<details>
<summary>RPM / Numeric</summary>

![RPM / Numeric](images/native-voltdeck-lower-2-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Watts / Numeric</summary>

![Watts / Numeric](images/native-voltdeck-lower-3-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Watts**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Cell volts / Numeric</summary>

![Cell volts / Numeric](images/native-voltdeck-lower-4-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Cell volts**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Voltage estimate / Numeric</summary>

![Voltage estimate / Numeric](images/native-voltdeck-lower-5-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Voltage estimate**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>RPM + Watts / Numeric</summary>

![RPM + Watts / Numeric](images/native-voltdeck-lower-6-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + Watts**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>RPM + W + cell / Numeric</summary>

![RPM + W + cell / Numeric](images/native-voltdeck-lower-7-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Hidden / Numeric</summary>

![Hidden / Numeric](images/native-voltdeck-lower-8-numeric.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Hidden**; **Meter style = Numeric**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

### Retro LCD

<details>
<summary>Only Custom / Retro LCD</summary>

![Only Custom / Retro LCD](images/native-voltdeck-lower-1-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Only Custom**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 3**.

</details>

<details>
<summary>RPM / Retro LCD</summary>

![RPM / Retro LCD](images/native-voltdeck-lower-2-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Watts / Retro LCD</summary>

![Watts / Retro LCD](images/native-voltdeck-lower-3-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Watts**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Cell volts / Retro LCD</summary>

![Cell volts / Retro LCD](images/native-voltdeck-lower-4-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Cell volts**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Voltage estimate / Retro LCD</summary>

![Voltage estimate / Retro LCD](images/native-voltdeck-lower-5-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Voltage estimate**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>RPM + Watts / Retro LCD</summary>

![RPM + Watts / Retro LCD](images/native-voltdeck-lower-6-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + Watts**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>RPM + W + cell / Retro LCD</summary>

![RPM + W + cell / Retro LCD](images/native-voltdeck-lower-7-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Hidden / Retro LCD</summary>

![Hidden / Retro LCD](images/native-voltdeck-lower-8-retro.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = Hidden**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

## Custom placement

<details>
<summary>RPM + Watts + Custom / position 1</summary>

![RPM + Watts + Custom / position 1](images/native-voltdeck-custom-position-1.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + Watts**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 1**.

</details>

<details>
<summary>RPM + Watts + Custom / position 2</summary>

![RPM + Watts + Custom / position 2](images/native-voltdeck-custom-position-2.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + Watts**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 2**.

</details>

<details>
<summary>RPM + Watts + Custom / position 3</summary>

![RPM + Watts + Custom / position 3](images/native-voltdeck-custom-position-3.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + Watts**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 3**.

</details>

## Battery methods

<details>
<summary>Consumed mAh</summary>

![Consumed mAh](images/native-voltdeck-battery-method-1.png)

Settings: **Display style = Digital**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Percent sensor</summary>

![Percent sensor](images/native-voltdeck-battery-method-2.png)

Settings: **Display style = Digital**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = % sensor**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

<details>
<summary>Voltage estimate</summary>

![Voltage estimate](images/native-voltdeck-battery-method-3.png)

Settings: **Display style = Digital**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Voltage estimate**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

## mAh

<details>
<summary>Remaining mAh</summary>

![Remaining mAh](images/native-voltdeck-remaining-capacity.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 3**.

</details>

<details>
<summary>Consumed mAh</summary>

![Consumed mAh](images/native-voltdeck-consumed-capacity.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Consumed**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 3**.

</details>

## RPM

<details>
<summary>KV estimate, not measured RPM</summary>

![KV estimate, not measured RPM](images/native-voltdeck-kv-estimate.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = KV x volts (est.)**; **Motor KV = 500**; **Estimate factor = 90%**.

</details>

<details>
<summary>Measured mechanical RPM</summary>

![Measured mechanical RPM](images/native-voltdeck-measured-rpm.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

## Theme and colors

<details>
<summary>Radio theme</summary>

![Radio theme](images/native-voltdeck-radio-theme.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Background = Radio theme**.

</details>

<details>
<summary>Custom background/accent</summary>

![Custom background/accent](images/native-voltdeck-custom-theme.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Background = Custom**.

</details>

## Missing data and warnings

<details>
<summary>Configured source unavailable</summary>

![Configured source unavailable](images/native-voltdeck-missing-telemetry.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**; **Custom = ESC temperature (°C)**; **Custom position = 3**.

</details>

<details>
<summary>Low battery</summary>

![Low battery](images/native-voltdeck-low-battery.png)

Settings: **Display style = Deck**; **Image source = Hidden**; **Lower deck > Show = RPM + W + cell**; **Meter style = Retro LCD**; **Remaining from = Consumed mAh**; **mAh display = Remaining**; **RPM value = Measured RPM**.

</details>

## Other choices and source dependencies

This gallery covers the distinct display choices, rather than every combination of arbitrary colors, sensor names and readings. **Radio theme / Black / Custom**, an accent color and optional font can be set independently. Leave Font file blank for native ETHOS fonts. Full screen means the radio’s complete LCD, including at a lower resolution.

Battery types are **Lipo / LiHV / Li-ion / LiFe**. RPM scaling can be manual or follow motor KV and the pack; a KV estimate is labelled and is not a measurement. Meter limits, red zone, Custom unit/decimals, RF profiles, alerts and flight logging are covered in the configuration guide.

Inactive fields retain their values. A source may still be required for calculation, alarm or logging when a display is hidden. Missing measurements remain unknown, not zero or full. The actual Synthetic preview warning remains intact; turn Preview off for normal use. See the [configuration guide](Configuration.md) for the complete field reference and [NOTICE](../NOTICE.md) for aircraft artwork.
