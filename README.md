# VoltDeck
A full-screen battery, telemetry and power dashboard for FrSky ETHOS 1.6.6 and 26.1.2.

**VoltDeck 2026.10-v9: latest release.**

Physical radio testing of this version passed.

[Download VoltDeck-2026.10-v9.zip](https://github.com/bliatun-code/VoltDeck/releases/download/voltdeck-2026.10-v9/VoltDeck-2026.10-v9.zip) | [Release notes](https://github.com/bliatun-code/VoltDeck/releases/tag/voltdeck-2026.10-v9)

<table>
<tr>
<td><img src="docs/images/native-voltdeck-deck-photo.png" alt="Deck / model picture" width="400"><br><b>Deck / model picture</b></td>
<td><img src="docs/images/native-voltdeck-deck-hidden.png" alt="Deck / Hidden" width="400"><br><b>Deck / Hidden</b></td>
</tr>
<tr>
<td><img src="docs/images/native-voltdeck-digital-photo.png" alt="Digital Power / model picture" width="400"><br><b>Digital Power / model picture</b></td>
<td><img src="docs/images/native-voltdeck-digital-hidden.png" alt="Digital Power / Hidden" width="400"><br><b>Digital Power / Hidden</b></td>
</tr>
</table>

Genuine X20RS / ETHOS 26.1.2 simulator captures of the current stable version, with controlled illustrative telemetry. No physical sensors were connected.

[Full display gallery and sensor setups](docs/Display-gallery.md) |
[Norsk visningsgalleri](docs/Visningsgalleri-norsk.md) |
[Illustrated configuration guide](docs/Configuration.md) |
[Norsk veiledning](docs/Konfigurasjon-norsk.md) |
[Installation and usage](docs/VoltDeck.md) |
[Lua source](scripts/VoltDeck/main.lua)

Ultimate AMR 60: 6S Lipo / 3300 mAh, measured RPM and ESC temperature. See the gallery for exact program choices, source roles and units.

## Display style and model picture

Choose **Display style = Deck** for the upright batteries and familiar instruments. **Digital** offers another instrument view focused on battery, current, consumption and power, with **Instrument focus: Power** shown as information. Deck is the default for new models and settings from versions before Digital. Previously saved Deck/Digital choices are retained.

**Image source** is independent in both styles: **Selected model**, **Image file** or **Hidden**. Hidden gives the picture area to larger readings. In Deck, a selected model picture keeps the familiar composition. A failed image keeps its area and shows the error; missing telemetry also retains instrument positions.

Changing style or image does not change calculation methods, telemetry sources, units, alerts, acceptance or flight logging. Inactive fields retain their saved values.

**Full screen:** The widget area must fill the radio's complete LCD, including on radios with a lower resolution. A split area shows **Full screen required**; choose a full-screen area to restore the instruments. **Screen size unavailable** means the LCD dimensions could not be read; the app retries automatically. Selected sources and settings are retained.

## Choose your lower deck

<table>
<tr>
<td><img src="docs/images/native-voltdeck-lower-2-retro.png" alt="Retro LCD measured RPM"><br><b>Retro LCD RPM</b><br>Segmented scale and session peak.</td>
<td><img src="docs/images/native-voltdeck-lower-6-retro.png" alt="Retro LCD RPM and Watts"><br><b>RPM + Watts</b><br>Measured speed beside calculated electrical input power.</td>
</tr>
<tr>
<td><img src="docs/images/native-voltdeck-lower-7-retro.png" alt="RPM Watts and average cell voltage"><br><b>Three values</b><br>RPM, Watts and average cell voltage.</td>
<td><img src="docs/images/flight-log-vfr.png" alt="Illustrative flight summary and VFR graphs"><br><b>Flight summary</b><br>Peaks, duration and bounded RF history.</td>
</tr>
<tr>
<td><img src="docs/images/native-voltdeck-custom-position-3.png" alt="RPM Watts and Custom temperature"><br><b>Custom alongside RPM + Watts</b><br>Add a numeric sensor and choose its position.</td>
<td><img src="docs/images/native-voltdeck-lower-4-numeric.png" alt="Average cell voltage"><br><b>Cell voltage</b><br>Scale and colours follow the selected battery type.</td>
</tr>
</table>

## Highlights

- Deck and Digital display styles, with an independent model-picture choice.
- Active model name and optional reuse of its selected model picture.
- Radio theme, black or user-selected background and accent colors.
- Remaining battery from consumed mAh; optional percent source or voltage estimate.
- Green / yellow / orange / red battery thresholds and configurable low-battery WAV.
- Measured RPM, a labelled KV estimate, Watts, average cell voltage or custom telemetry.
- Numeric and retro LCD Lower deck presentation; Deck with Hidden image can show RPM, Watts, cell voltage and Custom together.
- Custom telemetry alongside a preset, with a choice of row 1, 2 or 3.
- Optional per-model flight counter, session peaks and last-flight RF graphs.
- Optional automatic flight-log opening after sustained pack-voltage loss.
- Source-named RSSI/VFR readings, correct inactive units and per-slot visual profiles.
- Uses native ETHOS fonts and your selected model picture.

## Install VoltDeck

Download [VoltDeck-2026.10-v9.zip](https://github.com/bliatun-code/VoltDeck/releases/download/voltdeck-2026.10-v9/VoltDeck-2026.10-v9.zip) from the release assets, not GitHub's automatically generated source archive. The same ZIP supports both methods:

- **FrSky Suite:** Connect the radio, open **Lua library**, choose **Install Lua scripts**, select the ZIP and click **Install scripts**.
- **Manual:** Extract the ZIP, create `/scripts/VoltDeck/` on the radio's script drive and copy all extracted files into it. The final Lua path is `/scripts/VoltDeck/main.lua`.

Restart ETHOS after installation.
On first installation, select **VoltDeck** in a full-screen widget area and follow the
[illustrated guide](docs/Configuration.md) for your model's sources and battery settings.
Open **Configure widget** from the widget menu and check the version at the top.
Suite displays this release as **26.10.9**.
If Suite's installed entry has not refreshed, leave and reopen **Lua library**.
If the widget still shows an older version after restarting, follow the
[installation troubleshooting](docs/VoltDeck.md#installation).

Back up the SD card and ETHOS model storage together before updating. Keep the configured
widget and existing cfg/dat files; saved settings, sources and flight counts are retained.
See [upgrading and rollback](docs/VoltDeck.md#upgrading-and-rollback) before returning to an older release.

## Pack sessions and last flight

Motor disarming pauses qualification/flight time but retains the same pack
session, its statistics and RF history. Rearming does not count another flight.
Only continuous loss of valid positive pack voltage for **Pack loss delay**
ends the session (default 10 s; adjustable 3-120 s).

The last qualified log stays visible after disconnecting the aircraft and while
the next flight is qualifying. It is replaced only when that next flight qualifies.
These logs stay in RAM, not across a radio restart. RF graphs include motor pauses;
the flight-time figure only accumulates while all qualification gates pass.
An extended telemetry loss can resemble a disconnected battery; choose a longer
delay, for example 30 s, if needed.

![Last qualified log remains while the next flight qualifies](docs/images/flight-next-qualifying.png)

The previous flight log remains visible while the next flight qualifies.
[See all four transitions](docs/Configuration.md#illustrated-pack-session-transitions).

Open **Flight log** from the five-choice Home menu. Its bottom-right **Diagnostics**
button shows the logging conditions, even with no recorded flight. **RTN** returns
from either view to Dashboard. See the [menu walkthrough](docs/Configuration.md#widget-actions).

### Optional automatic flight log

Enable **Auto-open log** under **Flight log** (default Off), then set
**Extra log delay** (default 5 s, range 0-120 s). This additional delay starts
after **Pack loss delay** completes a qualified session. Returning pack voltage
or a manual view/settings change cancels pending navigation.
See the [configuration guide](docs/Configuration.md#automatic-flight-log-view).

## RF names and visual profiles

Names follow the selected source, for example **RSSI 2.4G** or **VFR 900M**.
Dashboard and flight-log sources can differ. Choose a preset for your protocol
or set custom visual limits. Graphs retain brief signal drops and show gaps
when readings are missing.
See the [RF explanation](docs/Configuration.md#vfr-graphs-instead-of-rssi).

## Safety and compatibility

Keep native telemetry alarms, failsafe and pre-flight checks enabled.
An armed bench run can still qualify as a flight; use an appropriate airborne
gate when possible. The widget's graph colors do not configure radio alarms.
Check the sources and settings on your own model when using other radio or
firmware combinations.

## License

VoltDeck is available under [MIT](LICENSE). The example artwork has separate
terms described in [NOTICE](NOTICE.md).


## Deck family

| App | Best suited to | Main instruments |
| --- | --- | --- |
| [VoltDeck](https://github.com/bliatun-code/VoltDeck) | Electric powered models | Flight-pack capacity, current, electrical power and motor telemetry. |
| [GasDeck](https://github.com/bliatun-code/GasDeck) | Gasoline powered models | Receiver batteries, engine RPM, temperatures and fuel. |
| [SoarDeck](https://github.com/bliatun-code/SoarDeck) | Sailplanes and motor gliders | Altitude, vario, history and motor-battery capacity when applicable. |

Each project has its own repository, illustrated guides and releases.
