# 4IP — Homepage (Reordered)

Στατικός ιστότοπος (single-page) της αρχικής σελίδας 4IP, έτοιμος για δημοσίευση μέσω **GitHub Pages**.
Η σελίδα είναι πιστή αναπαραγωγή του Claude Design preview `4IP Homepage - Reordered.dc.html`.

## Δομή αρχείων

```
.
├── index.html                          # Η αρχική σελίδα (πρώην "4IP Homepage - Reordered.dc.html")
├── support.js                          # Claude Design runtime (κάνει render το <x-dc> template)
├── image-slot.js                       # Component για τα placeholder slots των φωτογραφιών ομάδας
├── 4iP-logo.svg                        # Λογότυπο στο intro splash
├── 4iP-Intro-poster.png                # Poster/fallback εικόνα του intro
├── 4iP-Hero-AI-message-embedded.html   # Το intro hero (φορτώνεται σε iframe στην αρχή)
├── uploads/
│   └── logo2-transparent.png           # Λογότυπο στο header (nav)
├── .nojekyll                           # Απενεργοποιεί το Jekyll processing στο GitHub Pages
└── README.md
```

## Πώς λειτουργεί

Η `index.html` δεν είναι απλό στατικό HTML: περιέχει ένα `<x-dc>` template που «ζωντανεύει» από το
`support.js` στον browser (χρησιμοποιεί React/Babel που φορτώνονται από CDN). Γι' αυτό η σελίδα
**πρέπει να σερβίρεται μέσω HTTP server** (όπως το GitHub Pages) — δεν αρκεί διπλό-κλικ στο αρχείο
(το `file://` μπλοκάρει τα απαραίτητα fetch requests).

## Απαιτήσεις internet (runtime)

Η σελίδα φορτώνει τα εξής από εξωτερικές πηγές κατά την εκτέλεση (δουλεύουν κανονικά στο GitHub Pages):

- **React / ReactDOM / Babel** — από CDN (μέσω `support.js`)
- **Google Fonts** — IBM Plex Sans, Inter, IBM Plex Mono
- **Three.js & GSAP** — για το intro hero animation
- **Media του intro** (βίντεο + εικόνες) — από CDN (`cloudfront.net`)

> Σημείωση: το intro με ήχο ξεκινά με το πρώτο click του χρήστη, επειδή οι browsers μπλοκάρουν το
> autoplay με ήχο. Αυτή είναι κανονική συμπεριφορά, ίδια με το πρωτότυπο preview.

## Τοπική δοκιμή (προαιρετικά)

```bash
# Python 3
python -m http.server 8000
# ή Node
npx serve .
```

Άνοιξε `http://localhost:8000` στον browser.
