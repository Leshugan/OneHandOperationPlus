<h1 align="center">One Hand Operation + Port</h1>

<p align="center">
  <a href="README.md">Русский</a> · <b>English</b> · <a href="README.es.md">Español</a>
</p>

<p align="center">
  <a href="https://github.com/Leshugan/OneHandOperationPlusPort/raw/main/OneHandOperationPlusPort.apk"><b>⬇ Download OneHandOperationPlusPort.apk</b></a>
</p>

<p align="center">
  <a href="https://github.com/Leshugan">My GitHub</a> · <a href="https://t.me/Windrux">Windrux channel on Telegram</a>
</p>

A port of Samsung's **One Hand Operation +** (version 9.3.13.0) from Good Lock to phones from other manufacturers. The original only runs on Samsung and relies on private One UI features — here they are replaced with standard Android means, so edge gestures work on OnePlus, Xiaomi, Pixel and others too.

Swipe from the left or right edge of the screen and the assigned action runs: Back, Home, Recents, notification shade, screenshot, lock screen, quick tools and much more. All settings, animations and the look are the same as in the original.

## Installation

1. Install `OneHandOperationPlusPort.apk`.
2. Open **Settings → Accessibility** and turn on the **One Hand Operation +** service.
   If the item is greyed out, open the app info, tap ⋮ → **Allow restricted settings** and try again.
3. Open the app and turn on the main switch.

**Shizuku (optional).** If [Shizuku](https://shizuku.rikka.app/) is running on the phone, the app asks for access by itself, and once allowed it:
- grants itself the permissions it needs and removes itself from battery optimisation;
- turns on its accessibility service by itself;
- presses system keys directly — more reliable, with full long-press support.

Everything essential works without Shizuku as well.

## Good to know

- Android 14 or newer is required.
- The app's windows are not shown in Recents: this way they can't be swiped away by accident, and the system task cleaner won't switch the gestures off.
- Features that depend only on Samsung services (Routines, covers, Samsung search, etc.) do nothing on other phones.
- Tested on OnePlus Ace 6T (OxygenOS 16, Android 16).

**License:** One Hand Operation + itself is the property of Samsung Electronics; this project is not affiliated with Samsung. My part (the porting scripts and the compatibility layer) — do whatever you want with it. The only condition is to credit me as the author.

---

<details>
<summary>Build · Сборка · Compilación</summary>

Windows + JDK 17+, Android SDK build-tools 36, Python 3. Unpack `OneHandOperationPlusPort_src.zip`, then put next to `build.ps1`:

- `orig.apk` — One Hand Operation + 9.3.13.0 (`com.samsung.android.sidegesturepad`);
- `apktool.jar` — Apktool 2.10.0;
- `libs\` — `api.jar`, `provider.jar`, `aidl.jar`, `shared.jar` (Shizuku API 13.1.5) and `hab.jar` (HiddenApiBypass 6.1), taken from their `.aar` files;
- `key.jks` — your own signing key (created automatically if missing).

```powershell
powershell -ExecutionPolicy Bypass -File build.ps1   # → OneHandOperation.apk
```

`patch.py` redirects One UI-only framework calls to the `compat\sgpx` layer (accessibility overlays, input via Shizuku or accessibility, safe settings/provider access); `res.py` adds the accessibility service, Shizuku provider and stock-Android theme colours. `chk\` + `refs.py` produce `missing.txt` — the list of Samsung framework members absent on the target phone.

</details>

<details>
<summary>Third-party · Сторонние компоненты · Componentes de terceros</summary>

- One Hand Operation + — © Samsung Electronics
- [Shizuku API](https://github.com/RikkaApps/Shizuku-API) — Apache-2.0
- [HiddenApiBypass](https://github.com/LSPosed/AndroidHiddenApiBypass) — Apache-2.0
- [Apktool](https://github.com/iBotPeaches/Apktool) — Apache-2.0

</details>
