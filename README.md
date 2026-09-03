# DBD Tools by aVossyfue

Ein Windows-Desktop-Tool für **Dead by Daylight**-Streamer: durchsuchbares Karten-Archiv mit Live-Vorschau als OBS-Browserquelle, 1v1-Timer, Rang-Overlay, ein Killer-/Survivor-Randomizer, eine Freundesliste mit gemeinsamer Map-Auswahl in Echtzeit, sowie Steuerung per Chat-Befehl über Streamer.bot oder direkt per Stream Deck.

Gebaut mit **C# / WPF / .NET 8**. Läuft nach der Installation komplett lokal – ein Konto (Discord/Twitch-Login) wird nur für die Freundesliste/Lobby-Funktion gebraucht, alles andere funktioniert ohne Anmeldung und ohne Internetverbindung.

---

## Inhalt

- [Funktionsübersicht](#funktionsübersicht)
- [Clockcalls – Karten-Archiv](#clockcalls--karten-archiv)
- [Map-Vorschau (angedockt & Popout)](#map-vorschau-angedockt--popout)
- [OBS-Integration](#obs-integration)
- [Freundesliste & Lobby](#freundesliste--lobby)
- [1v1 Timer](#1v1-timer)
- [Rang-Overlay](#rang-overlay)
- [Randomizer](#randomizer)
- [Streamer.bot-Integration](#streamerbot-integration)
- [Stream Deck-Plugin](#stream-deck-plugin)
- [Einstellungen](#einstellungen)
- [Mehrsprachigkeit](#mehrsprachigkeit)
- [Auto-Update](#auto-update)
- [Technischer Aufbau](#technischer-aufbau)
- [Installation & Build](#installation--build)

---

## Funktionsübersicht

- 📚 Vollständiges Archiv aller **21 Realms** und **58 Maps**, inklusive Bildern und Live-Suche
- 🖼️ Live-Vorschau einer Map – angedockt im Hauptfenster oder als frei verschiebbares Popup, plus **OBS-Browserquelle** mit transparentem Hintergrund
- 👥 **Freundesliste** mit Discord-/Twitch-Login, Online-Status, echten Profilbildern und einer **Lobby**, in der eine Kartenauswahl live mit Freunden geteilt wird
- ⏱️ **1v1 Timer** für Duelle, mit Punktestand, individuellen Farben und eigenem Overlay-Link für OBS
- 🏆 **Rang-Overlay** für Killer & Survivor mit allen 20 Rangstufen als echte Grafiken, live steuerbar per Hotkey oder aus Streamer.bot heraus
- 🎲 **Randomizer** für Killer (inkl. killerspezifischer Addons) und Survivor (Item + passende Addons + 4 Perks), mit Slot-Maschinen-Effekt und einer Verwaltungsansicht, um einzelne Perks gezielt auszuschließen
- 🤖 **Streamer.bot-Integration**: jede Map per eigenem Chat-Befehl aufrufbar
- 🎛️ **Stream Deck-Plugin** zur direkten Steuerung ohne Umweg über den Chat
- 🔄 Eingebautes Auto-Update über GitHub Releases
- ⚙️ Einstellungs-Cloud-Sync über das eigene Konto (Sprache, Overlay-Größe u. a.)
- 🌐 Vollständig lokalisiert: **Deutsch, Englisch, Spanisch, Russisch, Französisch**
- 🖥️ Läuft nach der Installation komplett offline (bis auf Login/Lobby/Update-Check)

---

## Clockcalls – Karten-Archiv

- Kopfzeile mit Zurück-Button, darunter eine Tab-Leiste: **Maps** und **Lobby**
- Der "Maps"-Tab zeigt beim Überfahren mit der Maus ein Dropdown mit allen Realm-Kategorien, **Favoriten** immer an erster Stelle
- Ohne aktiven Filter werden standardmäßig alle Maps alphabetisch sortiert angezeigt
- Live-Suche über Realms **und** Maps gleichzeitig, mehrsprachig durchsuchbar
- Maps lassen sich per Sternchen als Favorit markieren

## Map-Vorschau (angedockt & Popout)

- Klick auf eine Map öffnet sie standardmäßig in einem angedockten Panel rechts neben der Kachelansicht (Breite per Drag verstellbar)
- Über einen Popout-Button lässt sich die Vorschau in ein eigenständiges, frei verschiebbares Fenster herauslösen – aktualisiert sich automatisch, sobald im Hauptfenster eine andere Map gewählt wird
- Weder das Popout-Fenster noch Benachrichtigungen holen dabei das laufende Spiel aus dem Fokus

## OBS-Integration

- Lokaler Server liefert die aktuell gewählte Map als HTML-Overlay mit transparentem Hintergrund aus – direkt als Browserquelle in OBS einbindbar, aktualisiert sich live
- Eigene Overlay-Links auch für den 1v1-Timer und das Rang-Overlay, jeweils über die Einstellungen kopierbar
- Läuft ausschließlich auf `localhost`, es wird nichts ins Internet gesendet

## Freundesliste & Lobby

- Anmeldung mit Discord oder Twitch – bewusst optional, der Rest der App funktioniert ohne Login weiter
- Freunde werden über einen individuellen 6-stelligen Freundescode oder per Nutzernamen-Suche hinzugefügt
- Echte Profilbilder (Discord-/Twitch-Avatar), eigenes Bild jederzeit änderbar inklusive Zuschnitt direkt im Popup
- Eigener Anzeigename unabhängig vom Discord-/Twitch-Namen wählbar
- Online-/Abwesend-/Offline-Status je Freund, live aktualisiert ("Abwesend" nach 5 Minuten Inaktivität)
- Benachrichtigungen-Tab sammelt offene Freundschaftsanfragen und Lobby-Einladungen an einem Ort, inklusive Zählungs-Badge am Freundesliste-Symbol, im Taskleisten- und im Tray-Symbol
- **Lobby**: öffnet sich automatisch, sobald der erste Freund eingeladen wird – kein manuelles Erstellen nötig. Mitglieder erscheinen als Bubbles mit Avatar und Krone für den Lobbyführer. Der Lobbyführer kann Mitglieder entfernen, die Berechtigung "Maps für alle ändern" vergeben und die Führung per Kontextmenü übertragen
- Anmelde-Sitzungen werden Windows-verschlüsselt (DPAPI) gespeichert, eigenes URL-Schema (`dbdtools://`) für den Login-Rücksprung

## 1v1 Timer

- Zwei parallele Timer mit Start/Zurücksetzen/Tauschen
- Punktestand für beide Spieler, inklusive Killer-/Survivor-Symbolen, die beim Tauschen automatisch mitwechseln
- Frei wählbare Namens-Hintergrund- und Akzentfarben, Overlay-Skalierung einstellbar
- Frei belegbarer Hotkey zum Starten/Stoppen, auch außerhalb der App
- Eigener OBS-Overlay-Link

## Rang-Overlay

- Killer- und Survivor-Rang unabhängig voneinander einstellbar, alle 20 Rangstufen (Ash IV bis Iridescent I) als echte, individuelle Grafiken
- Anzeige per Streamer.bot-Chat-Befehl oder direkt in der App per +1/-1/Reset steuerbar
- Eigener OBS-Overlay-Link, Anzeigemodus (Killer/Survivor/Beide) einstellbar

## Randomizer

- Zwei Tabs: **Survivor** und **Killer**, jeweils mit eigenem Auslose-Ergebnis
- Survivor: 1 Item (inkl. Seltenheitsstufe) + 2 passende Addons + 4 Perks
- Killer: 1 Killer (aus allen 44 Killern) + 2 **killerspezifische** Addons + 4 Perks – Addons passen dabei garantiert nur zum jeweils gezogenen Killer
- Checkboxen legen fest, was ausgelost werden soll; nicht ausgewählte Bereiche werden komplett ausgeblendet statt leer angezeigt
- Slot-Maschinen-Effekt beim Auslosen, Ergebnis-Überschrift zeigt beim Killer-Tab automatisch den gezogenen Namen
- Eigenes Verwaltungsfenster, um einzelne Perks (z. B. noch nicht freigeschaltete) gezielt von der Auslosung auszuschließen, mit Bildvorschau und Suche

## Streamer.bot-Integration

- Jede der 58 Maps sowie das Rang-Overlay lassen sich über eigene Chat-Befehle steuern (z. B. `!badham-preschool`)
- Kommunikation läuft über eine simple, dateibasierte Schnittstelle – funktioniert zuverlässig auch in eingeschränkten Script-Umgebungen ohne Netzwerk-Zugriff
- Fertiger C#-Code, eine CSV mit allen Befehlen sowie eine vollständige Schritt-für-Schritt-Anleitung liegen im Ordner `Streamerbot/` bei

## Stream Deck-Plugin

- Eigenes Elgato Stream-Deck-Plugin (`StreamDeck/com.avossyfue.dbdtools.streamDeckPlugin`) zur direkten Steuerung von Tasten aus, ganz ohne Streamer.bot
- Wird bei jedem App-Update automatisch mit aktualisiert, falls installiert

## Einstellungen

- Eigenes Einstellungsfenster mit mehreren Tabs (Allgemein, Clockcalls, 1v1 Timer, Rang-Overlay)
- **Einstellungs-Cloud-Sync**: eine bewusst ausgewählte, geräteunabhängige Teilmenge der Einstellungen (Sprache, Overlay-Größe/Transparenz, Update-Intervall u. a. – keine Hotkeys oder Monitor-Zuordnungen) synchronisiert sich automatisch über das eigene Konto
- Frei wählbarer Zielmonitor, Skalierung und Transparenz für das Karten-Overlay
- "Vorschau-Fenster immer im Vordergrund"-Schalter für das ausgekoppelte Popup
- Minimieren in den Tray, automatische Map-Erkennung ein-/ausschaltbar

## Mehrsprachigkeit

- Vollständig lokalisiert: **Deutsch, Englisch, Spanisch, Russisch, Französisch**
- Umschaltbar per Flaggen-Auswahl in den Einstellungen, deutsche Kartennamen basieren wo vorhanden auf den offiziellen Übersetzungen aus dem deutschen DbD-Wiki

## Auto-Update

- Prüft automatisch (oder manuell über die Einstellungen) auf neue Versionen über GitHub Releases
- Lädt das Update herunter und wendet es beim nächsten Neustart über ein separates Updater-Hilfsprogramm an, damit die laufende App dabei nicht im Weg steht

---

## Technischer Aufbau

- **C# / WPF / .NET 8**, `net8.0-windows`
- Datenhaltung als JSON (`Data/*.json`), keine Datenbank
- Lokaler HTTP-Server für alle OBS-Overlays (Maps, 1v1-Timer, Rang)
- Freunde/Lobby: Supabase (Anmeldung & Profile) + Ably (Echtzeit-Präsenz/Nachrichten)
- Eigenständige Zusatzprojekte in derselben Solution: `DbDMapArchiv.Installer`, `DbDMapArchiv.Updater`, `DbDMapArchiv.Uninstaller`

## Installation & Build

**Fertige Installation:** Installer von den [Releases](../../releases) laden und ausführen – installiert bei Bedarf automatisch die passende .NET-Runtime mit.

