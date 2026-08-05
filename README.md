# DBD Streamer Tool by Vossy

Ein offline-fähiges Windows-Desktop-Tool für **Dead by Daylight**: durchsuchbares Archiv aller Realms & Maps, live einblendbare Map-Vorschau als OBS-Browserquelle, und Steuerung per Chat-Befehl über Streamer.bot – gebaut für Streamer, die schnell die aktuelle Map zeigen wollen, ohne den Stream zu unterbrechen.

Gebaut mit **C# / WPF / .NET 8**, läuft komplett lokal, keine Internetverbindung zur Laufzeit nötig.

---

## Inhalt

- [Funktionsübersicht](#funktionsübersicht)
- [Kartenarchiv](#kartenarchiv)
- [Suche & Navigation](#suche--navigation)
- [Map-Vorschau (angedockt & Popout)](#map-vorschau-angedockt--popout)
- [OBS-Integration](#obs-integration)
- [Streamer.bot-Integration](#streamerbot-integration)
- [Einstellungen](#einstellungen)
- [Mehrsprachigkeit](#mehrsprachigkeit)
- [Sonstiges](#sonstiges)
- [Technischer Aufbau](#technischer-aufbau)
- [Installation & Build](#installation--build)

---

## Funktionsübersicht

- 📚 Vollständiges Archiv aller **21 Realms** und **58 Maps** aus Dead by Daylight, inklusive Bildern
- 🔍 Sofortsuche über alle Maps hinweg, auf Deutsch und Englisch
- 🖼️ Live-Vorschau einer ausgewählten Map – angedockt im Hauptfenster oder als frei verschiebbares, unabhängiges Popup-Fenster
- 🎥 Eingebaute **OBS-Browserquelle** mit transparentem Hintergrund, die sich automatisch aktualisiert
- 🤖 **Streamer.bot-Integration**: jede der 58 Maps per eigenem Chat-Befehl aufrufbar
- 🌐 Vollständige Lokalisierung (Deutsch/Englisch), umschaltbar per Flaggen-Dropdown
- ⚙️ Einstellungsseite mit Schalter für "Vorschau-Fenster immer im Vordergrund"
- 🔗 Direktlinks zu Twitch- und Discord-Kanal
- 🖥️ Läuft nach dem ersten Build komplett offline

---

## Kartenarchiv

- Alle 21 Realms (z. B. Autohaven Wreckers, Crotus Prenn Asylum, MacMillan Estate, Hawkins, Silent Hill, Raccoon City u. v. m.) mit jeweils allen zugehörigen Maps
- Jede Map hat ein reales Vorschaubild (WebP/GIF/PNG/JPG-Unterstützung, auch ohne native WPF-Unterstützung für diese Formate)
- Deutsche Namen basieren, wo vorhanden, auf den offiziellen Übersetzungen aus dem deutschen DbD-Wiki; lizenzierte/branded Realms (Silent Hill, Stranger Things/Hawkins, Resident Evil/Raccoon City, Halloween/Haddonfield, FNAF, Léry's, Alien/Toba Landing) bleiben bewusst auf Englisch, wie im echten Spiel üblich

## Suche & Navigation

- Sidebar im Stil moderner Chat-/Notiz-Apps: alle Realms aufklappbar, unabhängig von der Auswahl
- Große, zentrierte Suchleiste auf der Startseite; wandert beim Tippen automatisch nach oben in die kompakte Kopfzeilen-Ansicht
- Live-Filterung über alle Realms und Maps hinweg (Deutsch & Englisch durchsuchbar)
- Hervorgehobener "Startseite"/"Home"-Button in der Sidebar

## Map-Vorschau (angedockt & Popout)

- Klick auf eine Map öffnet sie standardmäßig in einem **angedockten Panel** rechts neben der Kachelansicht (Breite per Drag verstellbar)
- Über einen Popout-Button lässt sich die Vorschau in ein **eigenständiges, frei verschiebbares Fenster** herauslösen
- Popout-Fenster ist bewusst **nicht** an das Hauptfenster gekoppelt (kein gemeinsames Vordergrund-Erzwingen) und aktualisiert sich automatisch, wenn im Hauptfenster eine andere Map angeklickt wird – ganz ohne es neu zu öffnen
- Bildgröße passt sich beim Verändern der Fenstergröße automatisch an (Seitenverhältnis bleibt erhalten)

## OBS-Integration

- Die App startet automatisch einen lokalen Server, der die aktuell ausgewählte Map als HTML-Overlay mit **transparentem Hintergrund** ausliefert
- Direkt als **Browserquelle** in OBS Studio einbindbar – aktualisiert sich live, sobald im Programm eine andere Map gewählt wird
- Läuft ausschließlich auf `localhost`, es wird nichts ins Internet gesendet

## Streamer.bot-Integration

- Jede der 58 Maps lässt sich über einen eigenen Chat-Befehl öffnen (z. B. `!badham-preschool`)
- Kommunikation läuft über eine simple, dateibasierte Schnittstelle – funktioniert zuverlässig auch in eingeschränkten Script-Umgebungen ohne Netzwerk-Zugriff
- Fertiger C#-Code, eine CSV mit allen 58 Befehlen (Trigger, ID, deutscher & englischer Name) sowie eine vollständige Schritt-für-Schritt-Anleitung liegen im Ordner `Streamerbot/` bei

## Einstellungen

- Eigene Einstellungsseite, erreichbar über das Zahnrad-Symbol
- Schalter **"Vorschau-Fenster immer im Vordergrund"**: hält ausschließlich das ausgekoppelte Popup-Fenster über allen anderen Programmen sichtbar (praktisch beim Wechsel zwischen Programmen während des Streams) – das Hauptfenster ist davon nicht betroffen

## Mehrsprachigkeit

- Vollständig lokalisiert auf Deutsch und Englisch
- Umschaltbar über ein Flaggen-Dropdown-Menü, wirkt sofort auf die gesamte Oberfläche (Sidebar, Suchergebnisse, Vorschau, Einstellungen, OBS-Popup)

## Sonstiges

- Direktlinks zu Twitch- (`twitch.tv/avossyfue`) und Discord-Kanal, als reine Icon-Buttons ohne Text unten links im Hauptfenster
- Durchgängiges dunkles Farbschema

---

## Technischer Aufbau

| Bereich | Technologie |
|---|---|
| UI-Framework | WPF (.NET 8, C#) |
| Bildverarbeitung | SixLabors.ImageSharp (WebP/GIF-Unterstützung) |
| Lokaler Server (OBS-Overlay) | `System.Net.HttpListener` |
| Datenhaltung | JSON (`Data/maps.json`, `Data/strings.json`) |
| Streamer.bot-Anbindung | dateibasierter Befehlskanal (`System.IO`) |

Das Programm läuft nach dem ersten Kompilieren vollständig offline – es werden keine Daten an Dritte gesendet.

## Installation & Build

Eine ausführliche Schritt-für-Schritt-Anleitung (Voraussetzungen, Projekt öffnen, Bauen, Weitergeben als eigenständige `.exe`) liegt in [`README.md`](./README.md).

---

<sub>Nicht offiziell mit Behaviour Interactive oder Dead by Daylight verbunden. Alle Marken- und Produktnamen gehören ihren jeweiligen Eigentümern.</sub>
