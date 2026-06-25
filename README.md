# 🦁 Natembea Expeditions — Website

Kenya's premier safari and adventure website. Built in vanilla JavaScript — no frameworks, no build tools, instant deployment via GitHub + Cloudflare Pages.

---

## 📁 Project Structure

```
natembea/
├── index.html          ← Entry point (shell HTML)
├── css/
│   └── styles.css      ← All styling (logo colors: Navy #1B3F6B · Gold #F5B800)
├── js/
│   ├── data.js         ← ⭐ ALL CONTENT LIVES HERE — edit this to update the site
│   └── app.js          ← Renders everything from data.js
├── assets/             ← Put logo, favicon, images here
│   └── (your logo files)
├── _headers            ← Cloudflare security & caching headers
├── .gitignore
└── README.md
```

---

## ✏️ How to Edit the Site

**All content is in `js/data.js`.** You never need to touch `app.js` or `styles.css` for content changes.

### Change contact details:
```js
brand: {
  email:    "hello@natembea.co.ke",
  phone:    "+254 712 345 678",
  whatsapp: "254712345678",   // ← no + sign, no spaces
  location: "Westlands, Nairobi, Kenya",
}
```

### Add or change a tour:
```js
tours: [
  {
    badge: "Safari",
    name:  "My New Tour",
    tagline: "Short catchy line",
    desc:  "Longer description...",
    price: "From KES 75,000",
    duration: "4 Days · 3 Nights",
    highlights: ["Thing 1", "Thing 2", "Thing 3", "Thing 4"],
    image: "https://images.unsplash.com/photo-XXXX?w=800&q=80",
    accent: "#C9920A",
  },
  // ...
]
```

### Add a gallery photo:
```js
gallery: [
  {
    image: "https://images.unsplash.com/photo-XXXX?w=800&q=80",
    caption: "Description of photo",
    large: false,   // ← set true for the big featured slot (only one)
  },
]
```

---

## 🚀 Deploy to GitHub + Cloudflare Pages

### Step 1 — Push to GitHub

1. Create a new repo on [github.com](https://github.com) — name it `natembea-website`
2. In your terminal (or GitHub Desktop):

```bash
cd natembea
git init
git add .
git commit -m "Initial commit — Natembea Expeditions website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/natembea-website.git
git push -u origin main
```

### Step 2 — Connect to Cloudflare Pages

1. Go to [dash.cloudflare.com](https://dash.cloudflare.com)
2. Click **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**
3. Select your `natembea-website` repository
4. Build settings:
   - **Framework preset:** `None`
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/` *(or leave blank)*
5. Click **Save and Deploy**

That's it. Cloudflare will give you a free `natembea-website.pages.dev` URL instantly.

### Step 3 — Add Your Custom Domain

1. In Cloudflare Pages → your project → **Custom domains**
2. Add `natembea.co.ke` and `www.natembea.co.ke`
3. Follow the DNS instructions (point your domain's nameservers to Cloudflare)

---

## 🔄 How Updates Work (Once Live)

```bash
# Make your edits to js/data.js
git add .
git commit -m "Updated tour prices and added new testimonial"
git push
```

Cloudflare auto-deploys in ~30 seconds. No build step needed.

---

## 📬 Making the Contact Form Actually Send Emails

The form currently simulates a submission. To wire it to real email:

### Option A — Formspree (easiest, free tier)
1. Sign up at [formspree.io](https://formspree.io)
2. Create a form, get your endpoint URL (e.g. `https://formspree.io/f/xyzabc`)
3. In `js/app.js`, find `handleFormSubmit` and replace the `setTimeout` with:

```js
const res = await fetch('https://formspree.io/f/YOUR_ID', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    name: firstName + ' ' + lastName,
    email, phone, tour, travelDate, groupSize, message
  })
});
if (res.ok) {
  // show success
}
```

### Option B — EmailJS (send directly from browser)
1. Sign up at [emailjs.com](https://emailjs.com)
2. Follow their browser SDK docs — no backend needed

### Option C — Cloudflare Workers (full control, free)
- Write a Worker function that receives the POST and forwards to your Gmail/Outlook

---

## 🎨 Brand Colors

| Color      | Hex       | Usage                        |
|------------|-----------|------------------------------|
| Navy       | `#1B3F6B` | Primary brand, buttons, text |
| Gold       | `#F5B800` | Accents, CTA buttons, stars  |
| Navy Deep  | `#0F2540` | Hero bg, footer, dark sections |
| Gold Dark  | `#C9920A` | Eyebrow text, hover states   |
| Cream      | `#FAF7F2` | Page background              |

---

## 📱 Features

- ✅ Fully responsive — mobile, tablet, desktop
- ✅ Real wildlife photos (Unsplash)
- ✅ Lightbox gallery
- ✅ Scroll animations
- ✅ Floating WhatsApp button
- ✅ Contact form with tour pre-selection
- ✅ SEO meta tags + Open Graph
- ✅ Accessible (ARIA labels, keyboard navigation)
- ✅ Zero dependencies — no npm, no node_modules
- ✅ Cloudflare CDN-optimised headers

---

## 🦁 Made with love for Natembea Expeditions, Nairobi, Kenya.
