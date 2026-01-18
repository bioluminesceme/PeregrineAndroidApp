# PeregrineApp 

A native Android app that allows you to connect your stenography keyboard (USB NKRO) to your android device.
With the use of your own Plover JSON dictionary.


> **Warning**  
This app  has only been tested with my split steno Peregrine keyboard on a Motorola Egde 60 Pro. 
Use at your own risk. Do not use this for important notes - it's meant for practice only (for now).
I am a slow typer still (20WPM) but the lag should be minimal even at higher speeds (can anyone confirm?)

## Features

- **USB Gemini PR Protocol** - Works with any steno keyboard that outputs Gemini PR over USB serial (Georgi, Uni, Multisteno, Peregrine, etc.)
- **Plover-compatible dictionaries** - Import and use standard Plover JSON dictionaries
- **Real-time translation** - Tested and working well so far.
- **Multiple dictionaries** - Load multiple dictionaries with priority ordering like in Plover (tested with 1 dictionary in use)
- **File management** - Create, save, and manage steno documents. Autosave every X minutes. Auto filenaming when you click the save icon (manual renaming is.. buggy)
- **Adjustable font size** - 12sp to 32sp for comfortable reading
- **Stroke display** - See recent strokes in raw steno and their translations (if you have a slow phone or don't need this, turn it off, since it saves some processing power)
- **Auto-save** - Configurable auto-save interval

## Requirements

- Android 12+ (API 31+)
- USB OTG support
- USB-C or micro-USB OTG adapter
- Gemini PR compatible steno keyboard

## Supported Keyboards

Any keyboard that outputs Gemini PR protocol over USB serial at 9600 baud:

- Georgi
- Uni v3/v4
- Multisteno
- Splitography
- QMK keyboards with Gemini PR enabled
- Other Gemini PR compatible devices

## Installation

1. Download the APK from [Releases](https://github.com/bioluminesceme/PeregrineAndroidApp/releases)
2. Enable "Install from unknown sources" for your file manager if it asks you
3. Install the APK
4. Allow Google to scan it, continue installation when it's confirmed safe.
5. Connect your steno keyboard via USB OTG adapter (either before or after you launch the app, shouldn't matter. Your phone will likely ask you if you want to open the Peregrine app now that a steno keyboard is connected)
6. Grant permission when prompted

## Usage

1. **Add a dictionary**: Go to Settings > Dictionaries > tap + to import a Plover JSON dictionary. Without a dictionary you'll see raw steno or nothing when you type. You can add the same json file Plover uses.
2. **Connect keyboard**: Plug in your steno keyboard via USB (Bluetooth untested)
3. **Start typing**: The app will automatically connect, it will show at the bottom which keyboard is connected with a green dot, your steno strokes will be automatically translated using your dictionary.

## Dictionary Format

Standard Plover JSON format, example:

```json
{
  "STENO/STROKES/HERE": "translation text here",
  "PHUL/TEU/PHREBGS": "multiplex",
  "TP-PL": "{.}",
  "SKP": "and"
}
```

Supports Plover formatting commands:
- `{.}` `{?}` `{!}` - Sentence-ending punctuation
- `{,}` `{;}` `{:}` - Other punctuation
- `{^}` - Suppress space
- `{^ing}` - Suffix (attaches to previous word)
- `{pre^}` - Prefix (next word attaches)
- `{^~|\n^}` - Glue with newline
- `{-|}` - Capitalize next word
- `{*}` - Delete last stroke
- `{#Return}` - Newline (R-R)

## Known Issues

- **App may crash when connecting keyboard**: 
- If the app crashes when you plug in your steno keyboard, just reopen the app. It should work on the second try.
- File renaming is buggy as hell, just click the save icon and it will give it an automated name with a timestamp.
- NOT VERY WELL TESTED AT ALL YET

## License

All Rights Reserved. See [LICENSE](LICENSE) for details.

## Acknowledgments

- [Plover](https://www.openstenoproject.org/plover/) - Open source stenography software
- [usb-serial-for-android](https://github.com/mik3y/usb-serial-for-android) - USB serial library
- The Open Steno Project community
