# Ledger – iPhone expense tracker

One file (`index.html`), no build step, no server. Data lives in the browser's storage on your iPhone.

## 1. Open in VS Code
1. Put this folder anywhere, then `File → Open Folder`.
2. Install the **Live Server** extension and click **Go Live** to preview.
3. Test the hand-off in the browser: `http://127.0.0.1:5500/?amount=250&cat=Food&note=Lunch`

Currency: edit `CURRENCY` and `LOCALE` at the top of the script (default INR / en-IN). Categories: edit `CATS`.

## 2. Deploy (pick one, all free)
- **Netlify Drop**: go to app.netlify.com/drop and drag this folder in. You get a live https link in seconds.
- **Vercel**: `npx vercel --prod` inside the folder.
- **GitHub Pages**: push to a repo, then Settings → Pages → deploy from `main`.

Your link will look like `https://your-site.netlify.app/`. Use it in the Shortcut below.

## 3. Build the Shortcut ("Log Expense")
Shortcuts app → **+** → add these actions in order:

1. **Ask for Input** – Input type *Number*, prompt `Amount`. Rename its result variable to **Amount**.
2. **Choose from List** – items: Food, Groceries, Transport, Bills, Shopping, Other. Result variable: **Category**.
3. **Ask for Input** – Input type *Text*, prompt `Note (optional)`. Variable: **Note**.
4. **Current Date**, then **Format Date** with format *Custom* `yyyy-MM-dd`. Variable: **Date**.
5. **URL Encode** the **Note** (Text action → URL Encode). Variable: **EncNote**.
6. **Text**:
   `https://your-site.netlify.app/?amount=[Amount]&cat=[Category]&note=[EncNote]&date=[Date]`
   (tap each `[...]` and pick the variable from the bar)
7. **Open URLs** with that Text.

Tip: if Category contains spaces later, add a URL Encode for it too.

## 4. Trigger on double-tap of the back
Settings → Accessibility → Touch → **Back Tap** → **Double Tap** → choose **Log Expense**.

## Good to know
- Always view the dashboard in **Safari**. A Home Screen copy has separate storage and will not see entries logged through the Shortcut.
- Use **Back up data** now and then; clearing Safari website data would erase entries.
- Reloading the page does not duplicate an entry (the URL is cleaned after saving).
