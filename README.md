# Garden Log

A single-file, offline-capable garden journal and planner: harvests (weighed or just counted), planned plantings (what, where, when), recurring spray/feeding programs, an agenda with Done / Snooze / Skip, calendar export for phone alerts, a to-scale bed map, and local weather.

**Live app:** https://erlendjohnson-netizen.github.io/Garden-general/

## Privacy
All data stays in your browser (localStorage). Nothing is uploaded. Use **Dashboard → Backup & Restore** to export a JSON backup; it's the only copy outside your phone.

Network calls: Open-Meteo (weather + place lookup) and OpenStreetMap Nominatim (street-address lookup), using only the location you enter.

## Files
| File | Purpose |
|---|---|
| `index.html` | The whole app |
| `manifest.json` | Install metadata (name, icons, colors) |
| `sw.js` | Service worker — offline support. Bump `VERSION` when `index.html` changes |
| `icons/` | App icons (placeholder art) |

## Reminders on your phone
Plan → 📅 Calendar exports an `.ics` file with your programs (as repeating events), planting steps and scheduled treatments, each with an alert. On Android, each agenda item also has a 📅 button that opens Google Calendar. Re-export after changing schedules.

## Install on a phone
- **Android (Chrome):** menu ⋮ → *Install app*.
- **iPhone (Safari):** Share → *Add to Home Screen*.

## Path to the app stores
1. **Google Play:** package this PWA as a Trusted Web Activity with [PWABuilder](https://www.pwabuilder.com) (needs a Play developer account and a `/.well-known/assetlinks.json` on the site).
2. **Apple App Store:** wrap with Capacitor (or PWABuilder's iOS package). Apple rejects thin website wrappers, so native touches matter: photo capture, local notifications for care reminders, iCloud/Files backup.
3. Before either, move storage from localStorage to IndexedDB (or Capacitor Preferences/SQLite) so photos and years of data fit and survive OS storage clean-up.
