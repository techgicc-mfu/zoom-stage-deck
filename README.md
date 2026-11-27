# Zoom Stage Deck 🎸🎛️

> **Visual Stage Pedalboard, Scene Controller & Mobile Rig for Zoom MultiStomp (MS-50G / MS-60B / MS-70CDR) and M-VAVE Chocolate Plus.**

Zoom Stage Deck turns your Zoom MultiStomp pedal into a modern, visual, stage-ready guitar rig with instant **Scene switching**, direct **Stompbox control**, and seamless wireless integration with the **M-VAVE Chocolate Plus** Bluetooth footswitch.

Available as a **Web App**, an **Electron Desktop App**, and an **Android App (.apk)** with native USB-OTG and Bluetooth Low Energy (BLE) MIDI bridges.

---

> [!CAUTION]
> **⚠️ WARNING & DISCLAIMER — USE AT YOUR OWN RISK!**
> This application communicates directly with your Zoom MultiStomp pedal and M-VAVE footswitch hardware via clean-room reverse-engineered MIDI SysEx protocols and raw memory buffers. 
> * **Risk of Device Freeze/Bricking:** Pulling cables or losing power during transmission can cause pedals to freeze or corrupt memory.
> * **Risk of Patch Deletion:** Writing or syncing can overwrite saved presets. **Always back up all 50 patches before using this software.**
> * Read the complete safety guide and setup instructions in **[TUTORIAL.md](TUTORIAL.md)** before proceeding.

---

## 📖 [Read the Step-by-Step Tutorial & Safety Guide (TUTORIAL.md)](TUTORIAL.md)

For complete hardware connections, Android/MIUI setup, M-VAVE Chocolate Plus pairing, and emergency recovery, see **[TUTORIAL.md](TUTORIAL.md)**.

---

## 🌟 Key Features

### 1. 🎚️ 3 Performance Modes
* **SCENES Mode:** 4 instant scenes per preset (*Clean Base, Rhythm, Lead Boost, Ambient*). One tap on footswitch A–D instantaneously toggles bypass states and recalls saved knob positions across all 6 pedal slots.
* **STOMP Mode:** Maps footswitches A–D directly to your favorite stompboxes in the chain. Includes large, illuminated status LEDs and unobstructed pedal artwork.
* **PRESET Mode:** Scroll through banks and patches with instant full-chain visualization.

### 2. 📱 Android App with Native BLE & USB-OTG
* **Direct Bluetooth LE GATT Client:** Connects directly to the M-VAVE Chocolate Plus (`FootCtrlPlus`) without third-party MIDI routing apps.
* **Optimized for Android 11 & MIUI 12.5+:** Full edge-to-edge immersive full-screen display, safe-area padding, and automatic Location/Bluetooth permission handling.
* **USB-OTG Support:** Plug your Zoom MS-50G directly into your phone via a USB-OTG adapter.

### 3. 🎛️ Clean-Room Zoom MultiStomp Protocol
* **Bidirectional Sync:** Real-time parameter editing, patch dumps, and program changes.
* **146-Byte Buffer Encoding (0x28):** Accurately encodes Zoom patch buffers including slots 4–6 and sideloaded community effects.
* **Hardware DSP Safety & Auto-THRU:** Monitors DSP load in real time. If a patch exceeds DSP limits, overflowing delays/reverbs automatically transition to THRU mode to prevent hardware audio muting.
* **Exact Amp & Cab Modeling:** Correctly maps all 9 amp parameters and converts CAB bitfield indices across all factory and sideloaded models.

### 4. 🎛️ Studio Parameter Pop-Up Sheet
* Tap **Edit** on any pedal to open a full-screen studio console.
* Smooth touch sliders for real-time knob adjustments.
* Quick slot switcher (`S1` through `S6`) to edit your entire chain without closing the modal.
* Fast search across 172+ Zoom MS-50G effects and ZDL modules.

---

## 🏗️ Project Architecture

```
zoom-stage-deck-visual/
├── src/                          # Core ES Module application
│   ├── app.js                    # UI state, event handling & rendering
│   ├── zoom-midi.js              # Web MIDI & Android bridge MIDI engine
│   ├── zoom-patch.js             # 146-byte MultiStomp binary patch codec
│   ├── chocolate-midi.js         # M-VAVE Chocolate Plus SysEx & chord logic
│   ├── ms50g-effects.js          # Catalog of 172 Zoom effects, cabs & params
│   ├── zoom-effects-db.js        # Hardware DSP loads and effect definitions
│   └── mock-data.js              # Offline simulation presets & test fixtures
├── assets/                       # Authentic pedal, amp, and cabinet artwork
├── android-app/                  # Native Android wrapper project (Kotlin)
│   └── app/src/main/
│       ├── kotlin/               # MainActivity.kt (BLE GATT & USB-OTG bridge)
│       └── assets/               # Bundled web application assets
├── test/                         # Comprehensive unit test suite (48 tests)
├── electron-main.cjs             # Electron desktop entrypoint
├── preload.cjs                   # Electron IPC & fullscreen bridge
├── index.html                    # Single-page stage application markup
└── styles.css                    # Responsive stage UI & mobile landscape CSS
```

---

## 🚀 Getting Started

### Prerequisites
* [Node.js](https://nodejs.org/) (v18 or newer recommended)
* A Web MIDI compatible browser (Google Chrome, Microsoft Edge, or Opera) or Android device
* (Optional) Zoom MS-50G, MS-70CDR, or MS-60B connected via USB
* (Optional) M-VAVE Chocolate Plus footswitch

### Running Locally (Web)
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/zoom-stage-deck.git
cd zoom-stage-deck

# Install dependencies
npm install

# Run the test suite
npm test

# Launch desktop app with Electron
npm start
```
Or simply open `index.html` in Chrome or Edge over `localhost` (or host it on GitHub Pages / Vercel / Netlify).

### Building the Android APK
```bash
cd android-app

# Set your Java 17+ JDK path (e.g. Android Studio JBR)
set JAVA_HOME=C:\Program Files\Android\Android Studio\jbr

# Assemble debug APK
gradlew.bat assembleDebug
```
The compiled APK will be generated at:
`android-app/app/build/outputs/apk/debug/app-debug.apk`

---

## 🦶 Footswitch Setup (M-VAVE Chocolate Plus)

1. Turn on your M-VAVE Chocolate Plus in **Bluetooth (BLE)** mode.
2. Pair it with your Android phone or PC.
3. Open **Zoom Stage Deck**:
   - The app will automatically detect `FootCtrlPlus` and connect.
   - Footswitches **A, B, C, D** map directly to **Scenes 1–4** (in SCENES mode) or **Stomps 1–4** (in STOMP mode).
   - Pressing **A + B** triggers **Patch −**.
   - Pressing **C + D** triggers **Patch +**.

---

## 🧪 Testing

The project includes 48 comprehensive unit tests validating protocol accuracy, memory safety, and DSP handling:

```bash
node --test test/*.test.js
```

All 48 tests pass:
* Bit-perfect 146-byte patch serialization.
* M-VAVE Chocolate Plus SysEx and chord detection.
* DSP load calculations and auto-THRU protection.
* Bidirectional Web MIDI message handling.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
Zoom MultiStomp, MS-50G, MS-60B, and MS-70CDR are trademarks of Zoom Corporation. This project is an independent community development and is not affiliated with or endorsed by Zoom Corporation or M-VAVE.
