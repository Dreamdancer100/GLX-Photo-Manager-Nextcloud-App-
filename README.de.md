🌍 Sprachen: [🇺🇸 English](https://github.com/Dreamdancer100/GLX-Photo-Manager/blob/main/README.md) | [🇩🇪 Deutsch](https://github.com/Dreamdancer100/GLX-Photo-Manager/blob/main/README.de.md#)

<div align="center">

<img src="./glx-photo-zentrale.png" alt="GLX-Photo-Manager" width="48" />

# GLX-Photo-Manager #

### Ordnung für Fotosammlungen · Nextcloud-App

*Bringt Ordnung in gewachsene Fotosammlungen — zählen, prüfen, fehlende Aufnahmedaten retten, umwandeln, Doubletten finden und in selbst benannte Ordner einsortieren.* 📸

![Plattform](https://img.shields.io/badge/plattform-Nextcloud-0082C9)
![Art](https://img.shields.io/badge/art-Nextcloud%20App-red)
![Von](https://img.shields.io/badge/von-Dreamdancer100-8b0000)

</div>

---

## ✨ Was es macht

Fotosammlungen wachsen. Die Bilder kommen vom iPhone, aus Google Fotos, vom alten Rechner, von einer Sicherungsplatte — und landen in einem einzigen riesigen Ordner oder in Jahresordnern mit tausenden Dateien. Unterwegs geht das Aufnahmedatum verloren, dasselbe Bild liegt dreimal herum, und HEIC-Dateien lassen sich nirgends öffnen.

**GLX-Photo-Manager** arbeitet das Schritt für Schritt ab, in deiner eigenen Nextcloud. Nichts verlässt deinen Server. ⚡

### 🧭 Acht Schritte, der Reihe nach

| # | Schritt | Was passiert |
|:---:|:---|:---|
| 1 | 🔧 **Werkzeuge** | Prüft die Hilfsprogramme, zeigt zu jedem fehlenden den fertigen Befehl |
| 2 | 🔍 **Durchsehen** | Liest alle Ordner und Dateien in das eigene Verzeichnis der App |
| 3 | 📊 **Auswertung** | Anzahl, Speicherplatz, HEIC, Live-Fotos, Videos, Bilder ohne Datum |
| 4 | 📁 **Ordnervorschlag** | Fasst zusammenhängende Aufnahmetage zu Ereignissen zusammen |
| 5 | 🛠️ **Werkzeuge** | HEIC → JPG, Live-Foto → JPG, Doublettenprüfer |
| 6 | 📦 **Einsortieren** | Legt die Ordner an und verschiebt — mit Probelauf und Rückgängig |
| 7 | 🕐 **Datum retten** | Aus dem Dateinamen oder von den Nachbarbildern |
| 8 | 🧹 **Aufräumen** | Systemmüll, leere Ordner, verwaiste Filme, falsche Endungen |

---

## 📦 Installation

1. ⬇️ Aktuelle Fassung aus den [Releases](../../releases) herunterladen.
2. 📂 In den `apps`-Ordner der Nextcloud entpacken:

```bash
cd /var/www/nextcloud/apps
unzip -o glxphotos_x.y.z.zip
chown -R www-data:www-data glxphotos
sudo -u www-data php /var/www/nextcloud/occ app:enable glxphotos
```

3. 🖱️ Im App-Menü **Photo-Zentrale** öffnen.

### 🗂️ Hilfsprogramme auf dem Server

Schritt 1 prüft sie und sagt dir, was fehlt. Bis auf das erste sind alle freiwillig — die App kann ohne sie nur weniger.

| Programm | Wird gebraucht für |
|:---|:---|
| 🧩 **PHP EXIF** | Aufnahmedatum aus JPEG-Dateien |
| 🏷️ **exiftool** | Aufnahmedatum aus HEIC, RAW und Videos, samt Apple-eigener Felder |
| 🖼️ **ImageMagick + HEIF** | Umwandlung von HEIC-Bildern in JPG |
| 🎞️ **ffmpeg** | Standbild aus einem Live-Foto herausholen |

> 💡 Die App kann diese Programme nicht selbst installieren — sie läuft als eingeschränkter Benutzer. Sie zeigt dir den genauen Befehl, oder führt ihn über **deinen eigenen SSH-Zugang** aus, wenn du ihn hinterlegst.

---

## 🚀 Bedienung

1. 🔍 Bilderordner auswählen und **„Durchsehen starten"**. Der erste Lauf liest alles, jeder weitere nur noch Neues und Geändertes.
2. 📊 Auswertung ansehen. Die wichtigste Zahl ist **ohne Aufnahmedatum** — diese Bilder lassen sich nicht nach Datum einsortieren.
3. 🕐 Ist die Zahl hoch, **Datum retten** laufen lassen. Allein der Dateiname bringt oft tausende zurück.
4. 🛠️ HEIC und Live-Fotos umwandeln, wenn sie überall lesbar sein sollen. Die Ursprünge bleiben liegen, bis du sie ausdrücklich löschst.
5. 📦 Erst den **Probelauf**. Er zeigt jeden Ordner, der angelegt würde, und wohin jede Datei käme — ohne etwas anzufassen.
6. ✅ Dann einsortieren. Jede Verschiebung wird protokolliert, **„Alles rückgängig machen"** dreht sie zurück.

---

## 🔒 Was die App niemals tut

- ❌ **Eine Datei überschreiben.** Gibt es den Namen im Ziel schon, wird durchnummeriert.
- ❌ **Ohne Nachweis löschen.** Ursprünge verschwinden nur dort, wo die umgewandelte Datei nachweislich daneben liegt.
- ❌ **Ohne doppelte Rückfrage löschen.** Jeder löschende Knopf fragt, und fragt dann noch einmal.
- ❌ **An Nextcloud vorbei arbeiten.** Alles läuft über Nextclouds eigene Dateiverwaltung, damit Vorschaubilder, Freigaben und Kommentare erhalten bleiben.

---

## ⚠️ Hinweise

- 🕐 **Bilder ohne Aufnahmedatum** sind nicht kaputt — weitergeleitete Bilder, Downloads und Bildschirmfotos hatten nie eines, und beim Kopieren geht es anderen verloren. Sie bleiben liegen, wo sie sind.
- 🔄 **Nicht sortieren, während der Rechner synchronisiert.** Sonst schieben beide Seiten gleichzeitig, und es entstehen Konfliktdateien.
- 🌐 Über ein **Netzlaufwerk** siehst du Änderungen sofort; die Nextcloud-Integration am Rechner zieht sie mit der nächsten Synchronisierung nach.
- 📈 Der erste Lauf über eine große Sammlung dauert. Jeder weitere ist ein **Abgleich** und liest nur, was neu ist.

---

## 💡 Warum ich es gebaut habe

Rund 20.000 Dateien aus zwei Jahrzehnten, verteilt über iPhone-Ausfuhren, eine alte Galerie und ein halbes Dutzend Sicherungen — und bei drei Vierteln davon fehlte das Aufnahmedatum. Das von Hand zu sortieren wäre nie passiert. Also macht es die Maschine, und ich vergebe die Namen. 🎉

*Viel Spaß beim Sortieren!* 🙌

---

## 🔗 Mehr zu dieser App

👉 **[GLX-Photo-Manager auf gordonx.de](https://gordonx.de/)** — Beschreibung, Bilder und Download.

---

<div align="center">

Mit ❤️ gemacht von **Gordon Lehmann**

</div>
