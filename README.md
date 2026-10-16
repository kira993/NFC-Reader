# Celebrity Cruises Visitor Card Logger

A single-page tool for logging NFC card UIDs for visitor cards on board. Any ship in the fleet can use it. It runs entirely in the browser. Nothing is uploaded anywhere.

The settings start at cards **EQ V900 to EQ V999** (100 cards), and each ship can set its own prefix and range. Tap each card on the phone, the UID is saved against the current card number, and the page moves to the next one. When you are done, export the list to Excel. 

**Open the tool:** `https://kira993.github.io/NFC-Reader/index.html`

Open that link in **Chrome on Android** with NFC turned on.

---

## How to use it

1. Open the link in Chrome on your Android phone.
2. Turn on NFC in the phone settings if it is off.
3. Tap **Start NFC scanning**. Chrome may ask for NFC permission the first time. Allow it.
4. Hold the card flat against the back of the phone. The big label shows which card is next.
5. Each successful tap saves the UID and moves to the next card. The phone vibrates briefly.
6. When all cards are done, tap **Export to Excel**. You get an `.xlsx` file with these columns: card number, UID, scan time.

### Fixing mistakes

| Situation | What to do |
|---|---|
| Saved the wrong card | **Undo last** removes the most recent scan. |
| Need to go back to a specific card | Tap its number in the grid, then scan again. A new scan replaces the old UID. |
| A card is missing or damaged | **Skip card** moves on. Skipped cards stay empty in the export. |
| Same card tapped twice | The page rejects a UID that is already saved under another card and tells you which one. |

### No NFC? Use the input field

Type or paste a UID into the field and press Enter. A USB or Bluetooth NFC reader that types into the field also works: each scan saves and advances.

### Copy instead of download

**Copy table** puts the whole list on the clipboard. Paste it into Excel starting at cell A1.

---

## Settings

Tap the cog in the top right corner.

- **Card name prefix**, **First number**, **Last number**: define the cards you need. For example, prefix `EQ V`, first `900`, last `999` gives EQ V900 to EQ V999. A different batch could be `EQ V`, `1000` to `1049`.
- Cards you already saved are kept when you change the range. Cards outside the new range are hidden and left out of the export. They come back if you widen the range again.
- The range can hold up to 2000 cards.
- **Logo and site icon**: choose your own logo image. It appears next to the title and is used as the browser tab icon on that device.

Scanning stops when you open Settings. Tap **Start NFC scanning** again after you tap **Done**.

### Showing the logo on every device

Settings only stores the logo on the phone where you chose it. To show a logo for everyone who opens the link, add an image file named `logo.png` to the repository next to `index.html`. The page picks it up automatically, and it also becomes the tab icon. A logo chosen in Settings takes priority on that device.

Use a logo you have the right to use, for example the one from your company's brand resources.

---

## Using it on other ships

Every ship can open the same link. Each phone keeps its own scans and settings, so open Settings first and enter that ship's card prefix and number range. Export the Excel file from the phone that did the scanning.

---

## About the UID

NFC cards do not have a MAC address. What the phone reads is the card's **UID**, a hex serial number such as `04:A1:B2:C3:D4:E5:F6`. That is the value saved in the export.

---

## Good to know

- Progress is stored in the browser on the phone, for the address you opened. Always use the same link, and **export every 20 cards or so** to keep a copy. Clearing the browser's site data erases progress.
- NFC reading works only in Chrome on Android, and only over `https://`. That is why this page is hosted on GitHub Pages. Opening the HTML file directly from phone storage does not work.
- Chrome's NFC support does not read every card type. Older MIFARE Classic cards may not read at all. If a card will not scan, test it with an NFC app that shows the UID and paste the UID into the field.
- On iPhone, Safari and Chrome cannot read NFC from a web page. Use the input field with a reader, or an Android phone.

---

## Publish it on GitHub Pages

1. Create a new GitHub repository, for example `eq-card-logger`. A public repository works on the free plan.
2. Upload these files to the repository root:
   - `index.html` (the card logger page, named exactly `index.html`)
   - `README.md` (this file)
   - `logo.png` (optional, your logo)
3. In the repository, go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
5. Choose branch **main** and folder **/ (root)**, then click **Save**.
6. Wait one to two minutes. The page then shows your link at the top of the Pages settings:
   `https://YOUR-USERNAME.github.io/eq-card-logger/`
7. Open that link on the phone in Chrome and replace the placeholder link at the top of this README with it.

The page contains no passwords or personal data, and everything is saved on the device. If you want the repository private, GitHub Pages from a private repository needs a paid GitHub plan.

### Updating the page later

Upload a new `index.html` to the repository, replacing the old one. Pages republishes within a minute or two. Saved progress and settings are kept, because they are tied to the address, not the file version.
