🌍 Sprachen: [🇺🇸 English](https://github.com/Dreamdancer100/GLX-Photo-Manager-Nextcloud-App-/blob/main/README.md) | [🇩🇪 Deutsch](https://github.com/Dreamdancer100/GLX-Photo-Manager-Nextcloud-App-/blob/main/README.de.md)

<div align="center">

<img src="./glx-photo-zentrale.png" alt="GLX-Photo-Manager" width="48" />

# GLX-Photo-Manager #

### Photo library organizer · Nextcloud App

*Brings order to grown photo collections — count, inspect, recover missing dates, convert, deduplicate and sort into folders you name yourself.* 📸

![Platform](https://img.shields.io/badge/platform-Nextcloud-0082C9)
![Type](https://img.shields.io/badge/type-Nextcloud%20App-red)
![Made by](https://img.shields.io/badge/made%20by-Dreamdancer100-8b0000)

</div>

---

## ✨ What it does

Photo collections grow. Files arrive from an iPhone, from Google Photos, from an old PC, from a backup drive — and end up in one giant folder, or in year folders with thousands of files each. Capture dates get lost along the way, the same picture exists three times, and HEIC files won't open anywhere.

**GLX-Photo-Manager** works through all of that, step by step, inside your own Nextcloud. Nothing leaves your server. ⚡

### 🧭 Eight steps, in order

| # | Step | What happens |
|:---:|:---|:---|
| 1 | 🔧 **Server tools** | Checks the helper programs, shows a copy-ready command for anything missing |
| 2 | 🔍 **Inspect library** | Reads every folder and file into the app's own index |
| 3 | 📊 **Findings** | Counts, storage used, HEIC, Live Photos, videos, files without a date |
| 4 | 📁 **Folder proposal** | Groups consecutive shooting days into events |
| 5 | 🛠️ **Tools** | HEIC → JPG, Live Photo → JPG, duplicate finder |
| 6 | 📦 **Sort in** | Creates the folders and moves the files — with dry run and undo |
| 7 | 🕐 **Recover dates** | From the file name, or from neighbouring images |
| 8 | 🧹 **Clean up** | System junk, empty folders, orphaned clips, wrong extensions |

---

## 📦 Installation

1. ⬇️ Download the latest release from the [Releases](../../releases).
2. 📂 Unpack it into your Nextcloud `apps` folder:

```bash
cd /var/www/nextcloud/apps
unzip -o glxphotos_x.y.z.zip
chown -R www-data:www-data glxphotos
sudo -u www-data php /var/www/nextcloud/occ app:enable glxphotos
```

3. 🖱️ Open **Photo-Zentrale** from the app menu.

### 🗂️ Helper programs on the server

Step 1 checks these and tells you what's missing. Everything except the first one is optional — the app simply does less without it.

| Program | Needed for |
|:---|:---|
| 🧩 **PHP EXIF** | Capture dates from JPEG files |
| 🏷️ **exiftool** | Capture dates from HEIC, RAW and video files, including Apple-specific fields |
| 🖼️ **ImageMagick + HEIF** | Converting HEIC images to JPG |
| 🎞️ **ffmpeg** | Pulling the still frame out of a Live Photo |

> 💡 The app cannot install these itself — it runs as a restricted user. It shows you the exact command, or runs it over **your own SSH access** if you provide it.

---

## 🚀 Usage

1. 🔍 Pick your photo folder and run **"Durchsehen starten"**. The first run reads everything; later runs only pick up what changed.
2. 📊 Look at the findings. The number that matters most is **files without a capture date** — those can't be sorted by date.
3. 🕐 If that number is high, run **Recover dates**. The file name alone often brings back thousands.
4. 🛠️ Convert HEIC and Live Photos if you want them readable everywhere. Originals stay until you delete them explicitly.
5. 📦 Run the **dry run** first. It shows every folder that would be created and where each file would go — without touching anything.
6. ✅ Then sort in. Every move is logged, and **"Alles rückgängig machen"** puts everything back.

---

## 🔒 What it will never do

- ❌ **Overwrite a file.** If a name already exists in the target, it gets numbered.
- ❌ **Delete without proof.** Originals are only removed where the converted file demonstrably sits next to them.
- ❌ **Delete without asking twice.** Every destructive button asks, then asks again.
- ❌ **Touch files behind Nextcloud's back.** Everything goes through Nextcloud's own file API, so previews, shares and comments stay intact.

---

## ⚠️ Notes

- 🕐 **Files without a capture date** aren't broken — forwarded pictures, downloads and screenshots never had one, and copying strips it from others. They stay where they are.
- 🔄 **Don't sort while the desktop client is syncing.** Both sides would move files at once and you'd get conflict copies.
- 🌐 Over a **network share** you see changes immediately; the Nextcloud desktop client picks them up with its next sync.
- 📈 The first run on a large collection takes a while. Every later run is an **incremental sync** and only reads what's new.

---

## 💡 Why I built it

Roughly 20,000 files across two decades, spread over iPhone exports, an old gallery and half a dozen backups — with three quarters of them missing their capture date. Sorting that by hand was never going to happen. So the machine does it, and I decide the names. 🎉

*Have fun sorting your photos!* 🙌

---

## 🔗 More about this app

👉 **[GLX-Photo-Manager on gordonx.de](https://gordonx.de/glx-photo-zentrale-nextcloud-app/)** — description, screenshots and download.

👉 **<a href="https://gordonx.de/glx-photo-zentrale-nextcloud-app/" target="_blank">GLX-Photo-Manager on gordonx.de</a>** — description, screenshots and download.

---

<div align="center">

Made with ❤️ by **Gordon Lehmann**

</div>
