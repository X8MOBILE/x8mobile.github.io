# X8 Mobile: daily price list page

Live page: https://x8mobile.github.io/

A shop owner scans the QR, types their shop name and WhatsApp number, saves our
number, and sends us a ready-made hello on WhatsApp. Their details go into the
**X8 Customers** Google Sheet by themselves.

> **Important:** never rename the GitHub organization ("x8mobile") or this repo
> ("x8mobile.github.io"). The address would change and every printed QR code would stop working.

---

## Change the text

All words on the page are in **strings.js**, one block per language
(`en`, `ar`, `ml`, `hi`, `ur`, `bn`). Change only the text between the quotes.
`{shop}` becomes the customer's shop name.

To edit: open https://github.com/x8mobile/x8mobile.github.io/blob/main/strings.js, click the pencil ✏️,
change the text, then click **Commit changes**. The page updates in about a minute.

Area names are at the bottom of the same file (40 key areas across all 6 governorates).
The page shows areas and salesmen in A–Z order by itself (Arabic in Arabic order), with
**Other** always last, so new names can be added anywhere in the list.

## Salesman names

**Area** and **Salesman** must be answered: the customer cannot continue until they
pick an area and the salesman who visited them. It goes into the **Area** and
**Salesman** columns of the Sheet.

In **Area**, choosing **Other** opens a box where the customer must type their area;
the typed name goes into the Sheet.

**Block** must be answered too (number keypad; "Block 12" or "قطعة ١٢" is saved as 12).
**Building / complex** (optional) is for the shopping complex or building name, for
example "Al Muthanna Complex". They go into the **Block** and **Building / Complex**
columns of the Sheet.

To change the names, edit this line in **strings.js**:

    window.X8_STAFF = ["Taj", "Riyas Mangalore", "Ali", "Faheem", "Suhail", "Rizwan", "Yusuf"];

A salesman can also send a shop their own link, so their name is filled in already:
`https://x8mobile.github.io/?by=Rashid`

## Change the WhatsApp number

The number appears in these places:

1. **index.html**: search for `96566568747` (`wa:` setting) and
   `+965 6656 8747` (what people see).
2. **x8-mobile.vcf**: the `TEL` line.
3. The WhatsApp message wording is in **index.html**, in the `message` function
   (always English).

After changing the number, the printed QR still works: it points to the page, not the number.

---

## How staff use the Sheet

Open **X8 Customers** in Google Sheets.

- Every new shop appears as a **yellow row**.
- **Salesman** shows who visited the shop.
- **Status** shows *Started* (filled the form) or *Done* (also opened WhatsApp to say hello).
- In the **Tier** column, pick **Bulk**, **Normal** or **Low**.
- That's all. The yellow goes away, the **Contact name** fills in
  (for example `B - Al Noor Mobile – Fahaheel`), and the contact is saved in
  the Google Contacts of **x8mobilekwt@gmail.com** (and so on the iPhone signed in to it) with the labels **X8 Customers** and **X8 Bulk / Normal / Low**.
- Change the tier later and the contact is renamed and moved to the new label.
  No duplicates are made.
- **One row per number.** When a customer types a number that already finished
  registering, the page tells them "This number is already registered" and nothing is
  added to the Sheet. (A number that only started before is allowed to finish.)

Do not edit the hidden last column (Contact ID). The contact sync uses it.

**Removing a customer:** right-click the row number on the left → **Delete row**.
(Clearing the cells with backspace leaves an empty row.) This does not delete the
contact from the phone. To remove it there too:

- **iPhone:** Contacts → open the contact → **Edit** → scroll down → **Delete Contact** → **Delete Contact**.
- **Computer:** https://contacts.google.com (as x8mobilekwt@gmail.com) → tick the contact → ⋮ → **Delete**.

Delete the Sheet row as well, otherwise **X8 → Save all contacts** would create it again.

**Contacts go to whichever Google account last ran `setup`** (now x8mobilekwt@gmail.com).
To move them to another account, share the Sheet with it, open Extensions → Apps Script
as that account, and run `setup`.

To make WhatsApp broadcast lists by tier: in the phone's Contacts app, open the
label (for example **X8 Bulk**) to see the shops in that group.

The script lives inside the Sheet: **Extensions → Apps Script**.

## Saving our number on Android

A web page cannot put a contact straight into an Android phone, so Android always
downloads a small contact file. The page shows the steps: tap **Open** at the bottom,
then **Save** / **Import**. Some phones (for example Vivo) open the Files app first;
then tap **x8-mobile.vcf** and **Save**. On Android the number on the page can also be
tapped to open the dialer with **Create new contact**.

---

## WhatsApp Business greeting message

On the main phone: **WhatsApp Business → Settings → Business tools → Greeting message**.
Turn it on, choose **Everyone**, and paste:

> Thank you, you're all set with X8. Your price list will come to you here. Need anything? Just reply to this chat.

---

## Printing

- **x8-card-A6.pdf**: card for sales staff (105 × 148 mm). Print on thick matte card.
- **x8-sticker-5cm.pdf**: 5 cm round sticker. Ask the printer to cut along the blue circle.
- **x8-qr.svg** / **x8-qr.png**: the QR alone, for anything else.
  Keep it at least 2 cm wide, with the white border around it.
