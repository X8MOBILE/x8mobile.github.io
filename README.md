# X8 Mobile: daily price list page

Live page: https://irfanthaj.github.io/x8/

A shop owner scans the QR, types their shop name and WhatsApp number, saves our
number, and sends us a ready-made hello on WhatsApp. Their details go into the
**X8 Customers** Google Sheet by themselves.

> **Important:** never rename this repo ("x8") or the GitHub username ("irfanthaj").
> The address would change and every printed QR code would stop working.

---

## Change the text

All words on the page are in **strings.js**, one block per language
(`en`, `ar`, `ml`, `hi`, `ur`, `bn`). Change only the text between the quotes.
`{shop}` becomes the customer's shop name.

To edit: open https://github.com/irfanthaj/x8/blob/main/strings.js, click the pencil ✏️,
change the text, then click **Commit changes**. The page updates in about a minute.

Area names are at the bottom of the same file.

## Change the WhatsApp number

The number appears in these places:

1. **index.html**: search for `96566568747` (`wa:` setting and the Android link) and
   `+965 6656 8747` (what people see).
2. **x8-mobile.vcf**: the `TEL` line.
3. The WhatsApp message wording is in **index.html**, in the `message` function
   (always English).

After changing the number, the printed QR still works: it points to the page, not the number.

---

## How staff use the Sheet

Open **X8 Customers** in Google Sheets.

- Every new shop appears as a **yellow row**.
- **Status** shows *Started* (filled the form) or *Done* (also opened WhatsApp to say hello).
- In the **Tier** column, pick **Bulk**, **Normal** or **Low**.
- That's all. The yellow goes away, the **Contact name** fills in
  (for example `B - Al Noor Mobile – Fahaheel`), and the contact is saved in
  Google Contacts on the main phone with the labels **X8 Customers** and **X8 Bulk / Normal / Low**.
- Change the tier later and the contact is renamed and moved to the new label.
  No duplicates are made.
- If the same shop scans again, its row is updated, not copied.

Do not edit the hidden last column (Contact ID). The contact sync uses it.

To make WhatsApp broadcast lists by tier: in the phone's Contacts app, open the
label (for example **X8 Bulk**) to see the shops in that group.

The script lives inside the Sheet: **Extensions → Apps Script**.

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
