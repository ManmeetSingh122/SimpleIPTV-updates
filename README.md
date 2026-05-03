# SimpleIPTV — Updates

This repository hosts update metadata and release APKs for the **SimpleIPTV** Android TV app.

---

## How updates work

The app checks `version.json` on every launch. If the `versionCode` in the file is higher than the installed version, an update dialog appears automatically. The user can tap **Update Now** to download and install, or **Later** to skip.

---

## Releasing an update

1. Bump `versionCode` and `versionName` in `app/build.gradle.kts`
2. Build a signed release APK — `Build → Generate Signed APK → Release`
3. Create a GitHub Release tagged `vX.X` and attach the APK as `app-release.apk`
4. Update `version.json` in this repo with the new `versionCode`, `versionName`, `releaseNotes`, and `apkUrl`
5. Push `version.json` — users will see the update dialog on next launch

---

## version.json format

```json
{
  "versionCode": 3,
  "versionName": "4.0",
  "releaseNotes": "- What changed\n- Another change",
  "apkUrl": "https://github.com/ManmeetSingh122/SimpleIPTV-updates/releases/download/v4.0/app-release.apk"
}
```

`versionCode` must be a plain integer, incremented by 1 each release.

---

## Credits

**SimpleIPTV** is built using the following open source projects:

| Library | Purpose | License |
|---|---|---|
| [AndroidX Media3 / ExoPlayer](https://github.com/androidx/media) | Video playback engine | Apache 2.0 |
| [OkHttp](https://github.com/square/okhttp) | HTTP networking | Apache 2.0 |
| [Coil](https://github.com/coil-kt/coil) | Image loading & caching | Apache 2.0 |
| [iptv-org/iptv](https://github.com/iptv-org/iptv) | Community IPTV stream index | Unlicense |
| [AndroidX RecyclerView](https://developer.android.com/jetpack/androidx/releases/recyclerview) | Channel list | Apache 2.0 |
| [AndroidX ConstraintLayout](https://developer.android.com/jetpack/androidx/releases/constraintlayout) | UI layouts | Apache 2.0 |
| [AndroidX Lifecycle / ViewModel](https://developer.android.com/jetpack/androidx/releases/lifecycle) | State management | Apache 2.0 |
| [Kotlin Coroutines](https://github.com/Kotlin/kotlinx.coroutines) | Async operations | Apache 2.0 |

Stream URL data sourced from [iptv-org/iptv](https://github.com/iptv-org/iptv) — a community-maintained collection of publicly known IPTV streams. All stream URLs belong to their respective owners.

---

## Changelog

### v3.5 (versionCode 2)
- Complete UI redesign — deep navy theme, premium modern look
- Smooth sidebar slide-in/out animation
- Channel fade transition on switch
- Favorites — long-press OK on any channel to save
- Search — type while sidebar is open to filter channels
- Live clock in sidebar header
- Channel name preview in number input overlay
- Faster list updates with AsyncListDiffer
- Improved banner with slide-up animation and group/favorite indicators
- Bug fixes and performance improvements

### v3.0 (versionCode 1)
- Auto URL refresh from iptv-org on every launch
- Settings screen — quality, buffer size, auto-refresh interval, stall detection
- Stall detection — warns if stream freezes silently
- Remember last watched channel across restarts
- Channel logos loaded from M3U tvg-logo tags
- Group/category filter tabs
- M3U URL input — load any remote playlist
- Channel count and last updated time in sidebar
- Info button shows channel banner
- Play/Pause, FF/Rewind remote key support
- In-app update system
