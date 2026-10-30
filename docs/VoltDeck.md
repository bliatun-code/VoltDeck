# VoltDeck

[Display gallery: Deck and Digital with/without a picture, settings and telemetry sources](Display-gallery.md)

## Features

- Full-screen dashboard with radio-theme, black or custom background.
- Active model name and optional reuse of the selected model image.
- Pack voltage, current, consumed or remaining mAh, and remaining percent.
- Battery colors: green above 40%, yellow at 40% or lower, orange at 35%
  or lower, and red at 30% or lower.
- Low-battery alert at 30% or lower with a selectable WAV and repeat interval.
- Receiver signal and voltage readings, transmitter battery and a timer.
- Configurable lower deck: a custom source, RPM, electrical input power,
  average cell voltage, or supported combinations.
- Numeric or retro LCD meter presentation.
- Measured RPM or a clearly labelled KV-and-voltage estimate.
- Optional per-model flight counter and bounded RF history.
- Source-named RSSI/VFR readings and independent visual signal profiles.

See the [illustrated configuration guide](Configuration.md) or the
[Norwegian guide](Konfigurasjon-norsk.md) for settings and illustrated examples.

## Installation

Download [VoltDeck-2026.10-v11.zip](https://github.com/bliatun-code/VoltDeck/releases/download/voltdeck-2026.10-v11/VoltDeck-2026.10-v11.zip) from the
[release assets](https://github.com/bliatun-code/VoltDeck/releases/tag/voltdeck-2026.10-v11). Use the named widget package,
not the automatically generated repository source archive. The same ZIP supports
Suite and manual installation.

- **FrSky Suite:** Connect the radio, open **Lua library**, choose **Install Lua scripts**, select the ZIP and click **Install scripts**. Suite installs the files into `/scripts/VoltDeck/`.
- **Manual:** Extract the ZIP, create `/scripts/VoltDeck/` on the radio's script drive and copy all five extracted files into it:

```text
scripts/
  VoltDeck/
    main.lua
    ethos_lua_manifest.json
    INSTALL.txt
    LICENSE
    NOTICE.md
```

Restart ETHOS after installation.
On first installation, create a full-screen widget area and select **VoltDeck**. Select your model's
telemetry sources and enter its battery capacity in the widget configuration.
Open **Configure widget** from the widget menu and check the version at the top.
Suite displays this release as **26.10.11**.
If Suite's installed entry has not refreshed, leave and reopen **Lua library**.

If the widget still shows an older version after restarting, reconnect the radio,
remove only `/scripts/VoltDeck/main.luac` and restart ETHOS again.

Before updating, back up the ETHOS model, all `/scripts/vc3*.cfg` files and a complete filename list. Keep the configured widget and `.dat` flight counters. Read [VD8 backup and rollback](Configuration.md#vd8-backup-and-rollback) before installing v11.

## Display style and model picture

Choose **Display style = Deck** for the upright batteries and familiar instruments. **Digital** offers another instrument view focused on battery, current, consumption and power, with **Instrument focus: Power** shown as information. Deck is the default for new models and settings from versions before Digital. Previously saved Deck/Digital choices are retained.

**Image source** is independent in both styles: **Selected model**, **Image file** or **Hidden**. Hidden gives the picture area to larger readings. In Deck, a selected model picture keeps the familiar composition. A failed image keeps its area and shows the error; missing telemetry also retains instrument positions.

Changing style or image does not change calculation methods, telemetry sources, units, alerts, acceptance or flight logging. Inactive fields retain their saved values.

**Full screen:** The widget area must fill the radio's complete LCD, including on radios with a lower resolution. A split area shows **Full screen required**; choose a full-screen area to restore the instruments. **Screen size unavailable** means the LCD dimensions could not be read; the app retries automatically. Selected sources and settings are retained.

## Upgrading and rollback

Before upgrading, make a complete backup of the SD card and ETHOS model storage, including every settings and flight-counter copy. Valid settings from versions before Digital open with **Deck** as the default. Previously saved Deck/Digital choices, source selections and counts are retained. Do not delete cfg/dat files to change display style.

VoltDeck v11 reads VD5/VD6/VD7 settings and writes **VD8** during normal saving, even with the default floor. **v10 cannot read VD8.** Returning to v10 requires reinstalling its program and restoring the original ETHOS model and exact original 0/1/2-file cfg-pair state, including missing counterparts. Archive the current state first; remove only exact model-specific files proved absent before the upgrade. Follow [VD8 backup and rollback](Configuration.md#vd8-backup-and-rollback). **Display style = Deck** changes presentation and does not downgrade settings.

## Remaining battery

Use consumed mAh and enter the actual battery capacity:

```text
remaining percent = 100 * (capacity - consumed mAh) / capacity
```

The displayed result is limited to 0 through 100 percent. With **Consumed mAh**,
VoltDeck first checks the counter against a stable, low-current voltage reference.
The check needs 10 seconds of valid readings within a 0.20 V range for the whole
pack. Current must be nonnegative and within the check limit. The limit scales
at 0.15 C (`3 × capacity / 20000 A`), with **Battery → Idle current floor**
selectable from 0.30 to 1.50 A in 0.10 A steps and an overall 1.50 A cap.
The effective limit is `min(1.50, max(selected floor, 3 × capacity / 20000))` A.
With the default 0.30 A floor, 450 mAh allows 0.30 A, 2500 mAh allows 0.375 A
and 4000 mAh allows 0.60 A. The field is active only with Consumed mAh.
A changed floor requires a fresh ten-second check while retaining consumption,
reset protection, timers, sessions and counts. ARM does not gate this check, and there is no separate
waiting period after an interrupted window.
Until the pack is checked, remaining charge shows **--**. Differences above
10 and no more than 20 percentage points require explicit confirmation; larger
differences stay blocked. The larger difference against the window's lowest
and highest voltage decides the result. See [the illustrated pack check](Configuration.md#check-before-showing-remaining-charge)
for its measurement conditions and the LiFe confirmation.
Reset the consumption counter when connecting a new or recharged battery.
An incorrect pack capacity or a counter left over from a previous pack
makes this percentage incorrect.

With **Consumed mAh**, acceptance lasts for the battery connection; voltage sag
during flight does not repeat the comparison. A long pack-telemetry loss or a radio restart requires
a new check. If consumption unexpectedly falls, remaining charge becomes unknown
and explicit counter acceptance is required after checking the battery and reading.
**Accept battery counter...** shows progress, remaining blockers and whether
the counter estimate is higher or lower than the voltage reference. It does
not reset the sensor.

Check that the pack is fully charged before every flight. Compare reported
consumption with charger refill over several flights and follow any supported
ESC calibration procedure. A passed check does not guarantee a landing reserve.

A percent telemetry source or an approximate voltage estimate can be
selected instead. Voltage under load is not a direct measurement of
remaining battery charge. Missing readings are shown as dashes.
The optional remaining-mAh display retains its own counter-reset guard with
either method; accepting it requires a valid ARM OFF indication and does not
change the main percentage. See the configuration guide for the readings required.

## RPM, power and cell voltage

Measured RPM requires an appropriate telemetry source.
KV multiplied by live pack voltage is a speed potential estimate, not
measured shaft RPM. Propeller load and other losses are not automatically
known; any correction factor must come from measurements.

Electrical input power is pack voltage multiplied by current.
Average cell voltage is pack voltage divided by the configured cell count;
it cannot identify an individual weak cell.

## Model settings and backups

Settings and flight counts are saved separately for each model. Keep the model,
widget settings and flight-counter files together in your backup when updating
or moving to another SD card. Last-flight graphs and statistics are cleared
when the radio restarts.

## Model image

Runtime images are chosen by the user; none are required by the widget.
The Ultimate AMR picture is optional example artwork. See [NOTICE](../NOTICE.md)
for its terms of use.
290 x 191 pixels is the widget's preferred image size. The aspect ratio is
preserved. Large image dimensions can use too much radio memory even when
the PNG file is small.

## Flight log limitations

Choose **Flight log** in Home. Open **Diagnostics** with the bottom-right button,
also available when the log is empty. Turn the wheel right to select the button,
then short-press, or touch it directly. **RTN** returns from the log or diagnostics
to Dashboard; close any open menu first. Another RTN uses ETHOS's normal navigation.
The background stays still while Home is open, for up to 30 seconds; telemetry,
alerts and logging continue. See [Widget actions](Configuration.md#widget-actions).

Flight detection uses configured arm/throttle conditions, a minimum
duration and a high-throttle interval. An optional airborne gate can improve
filtering. A long armed bench test can still qualify without a suitable gate.

One connected-pack session can count at most once. Motor disarming or disabling
the airborne gate pauses qualification/flight time, without clearing the count
latch, statistics or RF history. Valid pack voltage returning before the loss
delay resumes that same session. Only continuous missing/invalid/non-positive
pack voltage for **Pack loss delay** ends it (default 10 s, configurable 3-120 s).

An extended telemetry loss can look like a battery disconnect, and a swap shorter
than the configured delay cannot reliably be detected. Increase the delay, for
example to 30 s, where needed. Logging must remain enabled to detect pack changes;
battery changes while logging is disabled or the radio is off are not observed.

The last qualified log remains visible after aircraft power-off and while a new
candidate qualifies. The new candidate replaces it only on successful qualification.
Qualification and flight time exclude pauses caused by disarming, a closed
airborne gate or missing pack voltage; graph elapsed time includes them.
Radio restart clears these statistics and graphs.

RF graph colors are visual thresholds, not changes to the radio's alarms.

Graphs retain brief signal drops and show gaps when readings are missing.
Live traces can take a few seconds to update.

### Automatic flight-log view

In **Flight log**, enable **Auto-open log** (default Off) and set **Extra log
delay** (default 5 s, range 0-120 s). This is additional time after **Pack loss
delay**, not a replacement for it. With 10 s + 5 s, the log opens about 15 s
after continuous loss of valid pack voltage. Zero extra delay opens it when
the qualified session ends.

Only a newly completed qualified flight triggers the change. Missing telemetry
at startup, short outages and rejected bench candidates do not. Returning valid
pack voltage, changing model, disabling logging/auto-open, preview, opening
configuration or manually choosing a view cancels a pending change. It happens
once per completed flight; returning to Dashboard will not reopen the same log.
This changes the view inside VoltDeck, not the radio's active main page.

## RF sources and profiles

The selected source's name and unit remain visible without a live
reading. RF accepts only dB and %. Flight graphs may use separate sources
and pin source/name/unit at flight start. Frequency labels do not identify
the protocol.

RF signal profiles: ACCESS/TD/TW uses RSSI 35/32 dB; ACCST uses 45/42 dB;
Custom uses independent limits per slot. VFR presets use 95% early quality
and 50% low. The 95% marker is a widget visual choice, not a native alarm
default. See [FrSky telemetry documentation](https://ethos-doc.frsky-rc.com/model-setup/telemetry/).

Editing a custom limit selects Custom. Native alarms are untouched.

The airborne gate is optional when set to **---**. **Always On** keeps this
gate open. A valid arm condition is still required, together with the configured
voltage, throttle and qualification-time conditions.
