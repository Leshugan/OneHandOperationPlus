<h1 align="center">One Hand Operation + Port</h1>

<p align="center">
  <b>Русский</b> · <a href="README.en.md">English</a> · <a href="README.es.md">Español</a>
</p>

<p align="center">
  <a href="https://github.com/Leshugan/OneHandOperationPlusPort/raw/main/OneHandOperationPlusPort.apk"><b>⬇ Скачать OneHandOperationPlusPort.apk</b></a>
</p>

<p align="center">
  <a href="https://github.com/Leshugan">Мой GitHub</a> · <a href="https://t.me/Windrux">Канал Windrux в Telegram</a>
</p>

Порт фирменного приложения Samsung **One Hand Operation +** (версия 9.3.13.0) из Good Lock на телефоны других производителей. Оригинал запускается только на Samsung и опирается на закрытые функции One UI — здесь они заменены стандартными средствами Android, поэтому жесты с краёв экрана работают и на OnePlus, Xiaomi, Pixel и других.

Проведите пальцем от левого или правого края экрана — и выполнится назначенное действие: «Назад», «Домой», «Недавние», шторка уведомлений, снимок экрана, блокировка, быстрые инструменты и многое другое. Все настройки, анимации и оформление — как в оригинале.

## Установка

1. Установите `OneHandOperationPlusPort.apk`.
2. Откройте **Настройки → Спец. возможности** и включите службу **One Hand Operation +**.
   Если пункт серый — откройте сведения о приложении, нажмите ⋮ → **Разрешить ограниченные настройки** и повторите.
3. Откройте приложение и включите главный переключатель.

**Shizuku (по желанию).** Если на телефоне запущен [Shizuku](https://shizuku.rikka.app/), приложение само попросит доступ и после разрешения:
- выдаст себе нужные разрешения и уберёт себя из экономии батареи;
- само включит службу спец. возможностей;
- будет нажимать системные кнопки напрямую — надёжнее и с полной поддержкой долгих нажатий.

Без Shizuku всё основное тоже работает.

## Что важно знать

- Требуется Android 14 или новее.
- Окна приложения не показываются в списке недавних: так их нельзя случайно смахнуть, а системный «чистильщик» не выключит жесты.
- Функции, завязанные только на сервисы Samsung (Routines, чехлы, поиск Samsung и т. п.), на других телефонах ничего не делают.
- Проверено на OnePlus Ace 6T (OxygenOS 16, Android 16).

**Лицензия:** само приложение One Hand Operation + — собственность Samsung Electronics, проект с Samsung не связан. Мою часть (скрипты переделки и слой совместимости) используйте как хотите — единственное условие: указывайте меня как автора.

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
