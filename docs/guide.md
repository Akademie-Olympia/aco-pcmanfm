# PCManFM – grafischer Dateimanager

PCManFM ist der schnelle, schlanke Dateimanager für Maus-Arbeit: Datenträger einhängen, Dateien ziehen,
Vorschaubilder ansehen. Er ergänzt [Yazi](https://aco-yazi.readthedocs.io/en/latest/), den Dateimanager im Terminal.

| Aufgabe | Werkzeug |
| --- | --- |
| Schnell navigieren, Dateien tippen, umbenennen im Stapel | Yazi ({kbd}`Super + Y`) |
| Datenträger, Drag & Drop, Vorschaubilder | PCManFM ({kbd}`Super + E`) |

## Zusammenspiel der Pakete

- **`aco-arch-dotfiles-pcmanfm`** – Fensterverhalten (diese Seite).
- **[libfm](https://aco-libfm.readthedocs.io/en/latest/)** – Papierkorb, Terminal, Symbolgrößen, Seitenleiste.
- **[GTK 3](https://aco-gtk3.readthedocs.io/en/latest/)** – Farben und Schrift.

Alle drei sind Abhängigkeiten; `pacman -S aco-arch-dotfiles-pcmanfm` holt sie mit.

## Was dieses Paket festlegt (`default/pcmanfm.conf`)

| Schlüssel | Wert | Wirkung |
| --- | --- | --- |
| `maximized` | `1` | Startet maximiert (Hyprland tiled ohnehin) |
| `view_mode` | `icon` | Symbolansicht; `list`, `compact`, `thumbnail` sind möglich |
| `show_hidden` | `0` | Versteckte Dateien aus ({kbd}`Strg + H` schaltet um) |
| `sort` | `name;ascending;` | Nach Name aufsteigend |
| `side_pane_mode` | `places` | Orte links; alternativ `dirtree` |
| `toolbar` | `newtab;navigation;home;` | Reiter, Vor/Zurück/Hoch, Home |
| `show_statusbar` | `1` | Statuszeile mit Dateianzahl und Größe |
| `always_show_tabs` | `0` | Reiterleiste erst bei mehr als einem Reiter |
| `mount_on_startup` / `mount_removable` / `autorun` | `1` | Datenträger automatisch einhängen |
| `close_on_unmount` | `1` | Fenster schließt, wenn der angezeigte Datenträger ausgehängt wird |

## Bedienung

| Taste | Aktion |
| --- | --- |
| {kbd}`Strg + T` / {kbd}`Strg + W` | Neuer / geschlossener Reiter |
| {kbd}`Alt + ←` / {kbd}`Alt + →` / {kbd}`Alt + ↑` | Zurück / vor / hoch |
| {kbd}`Strg + L` | Adresse eintippen |
| {kbd}`F2` | Umbenennen |
| {kbd}`Strg + H` | Versteckte Dateien ein/aus |
| {kbd}`Entf` / {kbd}`Shift + Entf` | Papierkorb / endgültig löschen |
| {kbd}`F4` | Terminal im aktuellen Ordner |

## Typische Änderungen

```ini
# ~/.config/pcmanfm/default/pcmanfm.conf
view_mode=list        # Listenansicht statt Symbole
show_hidden=1         # Versteckte Dateien immer zeigen
side_pane_mode=dirtree
```

## Fehlersuche

- **Datenträger erscheint nicht:** `gvfs` und `udisks2` müssen laufen; ohne sie kann PCManFM nichts einhängen.
- **Fenster zu klein/groß:** Unter Hyprland entscheidet das Tiling; `win_width`/`win_height` gelten nur schwebend.
- **Hell statt dunkel:** [GTK 3](https://aco-gtk3.readthedocs.io/en/latest/) prüfen.

## Anpassen und zurücksetzen

`~/.config/pcmanfm` ist ein Link auf deine bearbeitbare Kopie unter
`~/.local/share/arch-dotfiles/config/pcmanfm/`. Dort kannst du alles ändern; `pacman -Syu` überschreibt
deine Änderungen **nicht**. Bringt ein Update neue Vorgaben mit, landen sie als `.pacnew`-Datei neben deiner
Version, und du übernimmst, was du willst (`aco sync` führt zusammen, `aco status` zeigt den Zustand).
Zurück zu den Vorgaben: `aco deactivate pcmanfm` stellt die früheren Einstellungen wieder her,
`aco install pcmanfm` aktiviert die Paketvorgaben erneut.
