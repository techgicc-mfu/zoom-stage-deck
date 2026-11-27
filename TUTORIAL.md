# Step-by-Step Setup & Stage Performance Guide 🎸📖

> **A comprehensive tutorial for connecting, configuring, and performing with Zoom Stage Deck, Zoom MultiStomp (MS-50G / MS-60B / MS-70CDR), and M-VAVE Chocolate Plus.**

---

## ⚠️ MANDATORY DISCLAIMER & SAFETY WARNING

> [!CAUTION]
> **USE AT YOUR OWN RISK!**
> 
> This software is an independent, community-developed application built via clean-room reverse engineering of the Zoom MultiStomp USB MIDI protocol and M-VAVE Bluetooth Low Energy / SysEx communication. It is **not** manufactured, sponsored, or endorsed by **Zoom Corporation** or **M-VAVE / Sinco Intelligent Technology Co., Ltd.**
>
> By using this software, you explicitly acknowledge and accept the following inherent risks:
>
> 1. **Possibility of Device Bricking or Freezing:**
>    Sending raw MIDI System Exclusive (SysEx) messages and binary program memory dumps directly to hardware microcontrollers can potentially cause a device to freeze, enter an unbootable state, or corrupt internal EEPROM memory. Disrupting power, unplugging cables during an active memory transmission, or software errors can result in an unresponsive pedal requiring hardware recovery or firmware reflashing.
>
> 2. **Loss or Permanent Deletion of Saved Patches:**
>    Writing patches, syncing scenes, or saving preset buffers over USB MIDI can **overwrite existing user patches** on your pedal without confirmation. If you overwrite a custom tone that has not been backed up, **it cannot be recovered**.
>
> 3. **Hardware & Warranty Disclaimer:**
>    Neither the author nor any contributors assume any responsibility or liability for damages, corrupted presets, hardware failures, audio dropouts during live gigs, loss of data, or voided manufacturer warranties. **You are solely responsible for testing your setup thoroughly in a safe rehearsal environment before relying on it live.**

---

## 🛡️ Step 0: Mandatory Patch Backup (Safety First)

**DO NOT skip this step!** Before connecting Zoom Stage Deck for the first time, back up all 50 patches from your Zoom MultiStomp.

1. **Option A — Official Backup Tools (Recommended):**
   * Download and install **ToneLib Zoom** or official **Zoom GuitarLab / Effect Manager** on your PC/Mac.
   * Connect your Zoom MultiStomp with a standard USB Mini-B cable.
   * Export a complete `.g5p` / `.zdl` / library backup file to your computer's hard drive and cloud storage.
2. **Option B — Built-in Backup:**
   * In Zoom Stage Deck, open **Settings & MIDI** (`⚙️` icon).
   * Click **Sync All 50 Presets**. The application will pull all patch memories into your local cache.

---

## 🧰 Required Hardware & Equipment

| Item | Description | Notes |
| :--- | :--- | :--- |
| **Zoom MultiStomp** | Zoom MS-50G (v3.0/v3.1), MS-60B, or MS-70CDR | Ensure firmware is updated to official v3.00 or v3.10 |
| **USB Data Cable** | USB Type-A to Mini-B (Male) | Must be a **data sync** cable, not a power-only charging cable |
| **USB-OTG Adapter** | USB Type-C (or Micro-USB) to USB-A Female | Required for Android phone connection |
| **M-VAVE Chocolate Plus** | 4-button wireless Bluetooth MIDI footswitch | Direct BLE support (`FootCtrlPlus`) |
| **Android Device / PC** | Android 8.0+ (Tested on Android 11 / MIUI 12.5+) or PC | Chrome, Edge, or Opera for Web version; APK for Android |
| **Power Supply** | Isolated 9V DC pedal power or fresh AA batteries | **Crucial:** Never let pedal batteries die during a MIDI write! |

---

## 📱 Phase 1: Android Setup & Connections

### Step 1: Install the Android App
1. Transfer `ZoomStageDeck.apk` to your phone's storage.
2. Open your phone's file manager and tap `ZoomStageDeck.apk`.
3. If prompted, allow **"Install from unknown sources"**.
4. Tap **Install** and complete setup.

### Step 2: Enable Location & Bluetooth (Crucial for Android 11 / MIUI)
> [!IMPORTANT]
> On Android 11, MIUI 12.5, and older Android versions, the operating system's security architecture requires **Location (GPS)** to be switched **ON** for apps to discover Bluetooth Low Energy (BLE) MIDI devices.
1. Swipe down your Android Quick Settings panel.
2. Turn **Bluetooth ON**.
3. Turn **Location (GPS) ON**.

### Step 3: Pair the M-VAVE Chocolate Plus
1. Turn on your M-VAVE Chocolate Plus using the toggle switch on the back (**set to HOST or USB/BLE**).
2. The front screen will display `0` or bank indicator, and the Bluetooth LED will flash.
3. Open your phone's **Settings > Bluetooth**.
4. Look for **`FootCtrlPlus`** (or `Chocolate`) under Available Devices and tap to pair.
5. Once paired, it will appear under *Paired Devices*.

### Step 4: Connect Zoom MS-50G via USB-OTG
1. Power your Zoom MS-50G with a 9V DC adapter or fresh AA batteries.
2. Plug the USB Mini-B end into the back of the Zoom MS-50G.
3. Plug the USB-A end into your **USB-OTG adapter**.
4. Plug the USB-OTG adapter into your phone's Type-C port.
5. *(MIUI/ColorOS/OxygenOS users)*: If your phone requires manual OTG activation, go to **Settings > Additional Settings > OTG Connection** and turn it **ON**.
6. When Android prompts *"Open Zoom Stage Deck to handle this USB device?"*, tap **OK**.

---

## 🎛️ Phase 2: Launching & Configuring the App

1. Launch **Zoom Stage Deck**.
2. The app will launch in full-screen immersive mode.
3. Check the Top Status Bar:
   * **Zoom Status Dot:** Turns **Green** (`ZOOM MS Series Connected`).
   * **Footswitch Chip:** Automatically detects and displays **`⚡ FootCtrlPlus`** in green.
4. If either device is not automatically selected:
   * Tap the **Settings (`⚙️`)** icon in the top right.
   * Under **USB MIDI Connection**, select `ZOOM Corporation ZOOM MS Series`.
   * Under **M-VAVE Chocolate Plus**, select `FootCtrlPlus (Connected Bluetooth)`.
   * Tap **Auto-Configure Chocolate Plus** (it will confirm: `✓ FootCtrlPlus active via Bluetooth LE`).
   * Tap **Save & Close**.

---

## 🎸 Phase 3: Stage Performance Modes

Use the top tab selector to switch between the 3 stage modes:

```
[ PRESET ]   [ STOMP ]   [ SCENES ]
```

### 1. SCENES Mode (Recommended for Live Gigs)
Scenes let you change the bypass states and parameter values of multiple pedals simultaneously with a single tap of your foot:
* **Footswitch A (Switch 1):** Scene 1 — *Clean Base* (Compressor + Mild Chorus + Reverb).
* **Footswitch B (Switch 2):** Scene 2 — *Rhythm* (Overdrive + Amp Combo + Plate Reverb).
* **Footswitch C (Switch 3):** Scene 3 — *Lead Boost* (High Gain + Delay + Solo Level Boost).
* **Footswitch D (Switch 4):** Scene 4 — *Ambient* (Long Tape Echo + Shimmer Reverb).

#### How to Program & Save Your Own Scenes:
1. Tap any pedal on screen to turn it **ON** (glowing LED) or **OFF** (dimmed).
2. Tap **Edit** on any pedal to tweak drive, level, time, or mix.
3. When your tone sounds right, tap **Save Here** on the target Scene pad (Scene 1, 2, 3, or 4).
4. That scene now permanently remembers which pedals are active and their exact knob values for this preset!

---

### 2. STOMP Mode (Traditional Pedalboard Feel)
Stomp mode gives you 4 direct footswitches under your foot, just like having 4 individual stompbox pedals:
* **Switch A:** Stomp Slot 1 (e.g. Compressor / Boost)
* **Switch B:** Stomp Slot 2 (e.g. Overdrive / Distortion)
* **Switch C:** Stomp Slot 4 (e.g. Chorus / Modulation)
* **Switch D:** Stomp Slot 5 (e.g. Delay)
* Tapping Switch A–D instantly toggles that specific pedal ON or OFF with live LED status.

---

### 3. PRESET Mode & Bank Navigation
* Displays the complete 6-slot chain in serial order.
* **Switch A–D:** Directly selects Preset 1, 2, 3, or 4 within the current bank.
* **Bank Up / Down:** Tap `[` / `]` on screen, or use Chocolate Plus dual-switch chords:
  * Press **A + B together**: Steps down to **Previous Patch / Bank**.
  * Press **C + D together**: Steps up to **Next Patch / Bank**.

---

## 🎚️ Phase 4: Studio Parameter Pop-Up Editor

When you tap **Edit** on any pedal card, a full-screen studio console opens:
* **Slot Tabs (S1 – S6):** Tap any slot pill at the top to jump between pedals in the chain without exiting.
* **Reorder Pedals (◀ Move / Move ▶):** Shift pedal order in the Zoom chain (e.g., move Reverb before Delay, or move Overdrive before Amp).
* **Effect Model Selector:** Fast dropdown with category filtering (Dynamics, Drive, Amp, Mod, Delay, Reverb) and search across all 172 MultiStomp effects.
* **Parameter Sliders:** Touch-friendly faders with high-precision numeric values.
* **DSP Safety Monitor:** Live DSP load bar. If your chain approaches 100%, the app flags heavy effects and protects delay tails from being abruptly clipped.
* **Done (✕):** Tap to close the pop-up and return immediately to the live stage view.

---

## 🚨 Phase 5: Troubleshooting & Emergency Recovery

### Issue 1: Zoom Pedal shows "DSP FULL" or Audio Mutes
* **Cause:** The Zoom MultiStomp DSP chip cannot run too many complex algorithms (e.g. Amp + Heavy Reverb + Dual Delay) simultaneously.
* **Solution:**
  1. The app automatically flags overflowing slots with **DSP FULL · THRU** to maintain sound output.
  2. Tap **Unmute Patch** in the app footer. This transmits a clean, uncorrupted patch buffer to restore audio output.
  3. Replace one heavy delay or reverb with an analog-style or single delay model.

### Issue 2: Chocolate Plus is not detected on Android
* **Check 1:** Ensure **Location (GPS)** is turned ON in Android Quick Settings (mandatory on Android 11 / MIUI 12.5).
* **Check 2:** Open phone Settings > Bluetooth > Unpair `FootCtrlPlus` > Re-pair.
* **Check 3:** In the app Settings dialog, tap **Scan Footswitch**.

### Issue 3: Emergency Pedal Recovery (Factory Reset)
If your Zoom MultiStomp ever locks up, freezes, or fails to boot:
1. Unplug the USB cable and power cable from the Zoom pedal.
2. Press and **HOLD DOWN** the pedal footswitch while plugging the 9V power cable back in.
3. The display will show **"All System Reset"**.
4. Select **YES** using the cursor keys and press the center footswitch.
5. The pedal will restore factory memory.
6. Reconnect to your computer and restore your backed-up patches from **Step 0**.

---

*Always rehearse with your complete rig before performing live. Keep your cables securely routed and ensure reliable power at all times!*
