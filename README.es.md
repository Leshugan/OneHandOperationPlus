<h1 align="center">One Hand Operation + Port</h1>

<p align="center">
  <a href="README.md">Русский</a> · <a href="README.en.md">English</a> · <b>Español</b>
</p>

<p align="center">
  <a href="https://github.com/Leshugan/OneHandOperationPlusPort/raw/main/OneHandOperationPlusPort.apk"><b>⬇ Descargar OneHandOperationPlusPort.apk</b></a>
</p>

<p align="center">
  <a href="https://github.com/Leshugan">Mi GitHub</a> · <a href="https://t.me/Windrux">Canal Windrux en Telegram</a>
</p>

Un port de **One Hand Operation +** de Samsung (versión 9.3.13.0), de Good Lock, para teléfonos de otros fabricantes. El original solo funciona en Samsung y depende de funciones privadas de One UI; aquí se han sustituido por medios estándar de Android, así que los gestos desde los bordes de la pantalla funcionan también en OnePlus, Xiaomi, Pixel y otros.

Desliza desde el borde izquierdo o derecho de la pantalla y se ejecutará la acción asignada: Atrás, Inicio, Recientes, panel de notificaciones, captura de pantalla, bloqueo, herramientas rápidas y mucho más. Todos los ajustes, las animaciones y el aspecto son los mismos que en el original.

## Instalación

1. Instala `OneHandOperationPlusPort.apk`.
2. Abre **Ajustes → Accesibilidad** y activa el servicio **One Hand Operation +**.
   Si la opción aparece en gris, abre la información de la aplicación, toca ⋮ → **Permitir ajustes restringidos** e inténtalo de nuevo.
3. Abre la aplicación y activa el interruptor principal.

**Shizuku (opcional).** Si [Shizuku](https://shizuku.rikka.app/) está en ejecución en el teléfono, la aplicación pedirá acceso por sí sola y, una vez concedido:
- se otorgará los permisos necesarios y se quitará de la optimización de batería;
- activará por sí sola su servicio de accesibilidad;
- pulsará las teclas del sistema directamente: más fiable y con soporte completo de pulsaciones largas.

Todo lo esencial funciona también sin Shizuku.

## A tener en cuenta

- Se necesita Android 14 o posterior.
- Las ventanas de la aplicación no aparecen en Recientes: así no se pueden cerrar por accidente y el limpiador del sistema no desactivará los gestos.
- Las funciones que dependen solo de servicios de Samsung (Routines, fundas, búsqueda de Samsung, etc.) no hacen nada en otros teléfonos.
- Probado en OnePlus Ace 6T (OxygenOS 16, Android 16).

**Licencia:** One Hand Operation + es propiedad de Samsung Electronics; este proyecto no está afiliado a Samsung. Mi parte (los scripts del port y la capa de compatibilidad): haz lo que quieras con ella. La única condición es mencionarme como autor.

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
