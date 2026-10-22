# Voice Button for Kiosk Satellite

A round microphone button that floats on top of Kiosk Satellite's screensaver. Tap it and the assistant starts listening, the same as saying the wake word.

The plugin only draws the button and fires a gesture trigger. Kiosk Satellite's own **Start a voice command** action does the listening, so nothing here touches the microphone.

## Set up

1. **Settings > Plugin Manager**: turn on **Enable Plugins**, choose **Add plugin**, paste this repository's URL, **Preview**, then **Trust and install**. Enable it.
2. **Settings > Gestures > Add**: pick **Plugin trigger > Mic button tapped**, then the action **Start a voice command**.
3. Start the screensaver (kiosk menu > Start Screensaver) and tap the button.

## Settings

| Setting | Default | Notes |
| --- | --- | --- |
| Show the button | Screensaver only | **Always** keeps it over the dashboard too |
| Hide while the assistant is busy | on | Hidden while Voice Satellite listens, thinks or answers |
| Corner | Bottom right | Or bottom left, top right, top left, bottom centre |
| Button size | 72 dp | 40 to 160 |
| Distance from the edge | 20 dp | |
| Icon | mdi:microphone | Any Material Design Icon |
| Icon colour / Button colour | white / black | |
| Button opacity | 45 % | 0 shows the icon alone |
| Thin outline | on | |

The plugin also offers a **Press the mic button** action, so the same thing can be put in the kiosk drawer or exposed to Home Assistant from the plugin's page.

## Notes

- The button is drawn in the same layer as the voice overlay, above clock, photo and weather screensavers. The **Black** screensaver's cover sits above that layer, so the button does not show there.
- Lockdown Mode and Kiosk Mode's **Disable Gestures** silence plugin triggers, so the tap does nothing while they are on.

## Build

Releases are built by the included GitHub Actions workflow: publish a release with a tag such as `v1.0.0` and it attaches the plugin ZIP, manifest and checksum. To build locally you need Python 3, JDK 17+ and an Android SDK with a platform and build-tools:

```
python3 tools/test.py
python3 tools/build.py
```

The ZIP lands in `dist/`. Install it with **Plugin Manager > Developer Tools > Install from ZIP**.

The SDK and build tools come from [jxlarrea/kiosk-satellite-plugins](https://github.com/jxlarrea/kiosk-satellite-plugins) (Apache-2.0).
