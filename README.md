# Kaala Mithra AI Store — Website + Admin Dashboard

Two separate files. Customers only ever see the website. The dashboard is for the admin only.

## Files

- **`index.html` — the customer website.** The full storefront: 17 built-in products,
  27 sidebar categories, search, filters, cart, Design-your-QR, bulk order and
  account panels. It contains **no dashboard code and no link to the dashboard** —
  a customer browsing the website cannot discover the dashboard from it.
- **`dashboard.html` — the admin panel only.** Open it directly (it is not linked
  from the website). It starts with a password screen, then a product form, a
  list of your added products with Delete, and a Publish button.
- **This README.**

## Opening the dashboard
Open dashboard.html **directly in a real browser (Chrome)** after downloading it — do not rely on an in-app preview. Previews typically block both browser storage and file downloads, which makes added products vanish on reload and Publish silently do nothing. The dashboard now warns you on screen in both cases instead of failing silently.

## How to update the website

1. Open `dashboard.html` in a browser and enter the admin code (see below).
2. Add products with the form: name, price (₹), category, optional image.
   Added products appear in the list below the form; Delete removes them.
3. Click **Publish to website**. It downloads TWO files:
   - `index.html` — the customer website with your added products baked in.
   - `dashboard.html` — the admin panel with the same updated product list baked
     in, so the next round never loses previously published products.
4. Replace **both** files on your hosting with the downloaded copies, then push
   to GitHub (or re-upload wherever the site lives). If your browser asks about
   multiple downloads, allow it.

## How to change the admin code

Open `dashboard.html` in a text editor and find, near the top of the script:

```js
/* CHANGE THIS CODE TO YOUR OWN: this is the admin gate code for the dashboard. */
const ADMIN_CODE = "admin123";
```

Replace `admin123` with your own code and save. The default code is `admin123`.

## Honest notes (please read)

- **The password screen is a casual gate, not real login security.** The code is
  stored in the dashboard file itself, so anyone who reads the file's source can
  find it. It keeps casual visitors out, but it is not protection against
  someone determined. Real admin accounts need a backend with proper logins.
- **Added products live in your browser until you Publish.** The dashboard saves
  additions in the browser's local storage, which does not travel with the file.
  Publish (step 3 above) is what makes them permanent in the website files.
- **Published products become permanent.** Once published, a product is part of
  the website itself and can no longer be deleted from the dashboard — only
  products added after the last Publish can be deleted there. To remove a
  published product, edit the product list in the files directly.
- **No links between the files.** The website never links to the dashboard, and
  the dashboard never links to the website. The only bridge is Publish.
- **One category quirk:** a custom product assigned to "Customized Gifts" only
  appears under that sidebar filter if its title contains Keychain, Tote Bag,
  Hoodie, Plush Toy or Vanity Pouch (that filter matches by title keywords).
  The other 26 categories match by exact category and work normally. Custom
  products carry material type "Custom", so they do not appear under
  material-type filters, only under their category.
