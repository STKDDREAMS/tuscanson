# Tuscan Son — Website

A single-page site for Tuscan Son (Century City, Los Angeles): pure-white base,
neutral off-white sections (no beige), and accents pulled from the sunflower
logo — brick red and olive green, with a bit of orange and minimal yellow.

## Structure

Everything lives in `index.html` (HTML + CSS + JS, no build step) with the logo
in `assets/logo.png`. The main scroll is kept short and minimal — longer
content lives in popups. Section order:

1. Hero — big centered logo with the "Upscale food in a casual setting"
   tagline, flanked by two arched photo slots (they drop below the text
   as a 2-up row on mobile)
2. Pictures with words — three photo cards (made in house / straight from
   Italy / upscale, but easy); a swipeable row on mobile
3. Ticker — scrolling values strip (made in house, upscale food, straight
   from Italy, free & easy parking, easy accessibility, no reservations)
4. Dish gallery — auto-scrolling marquee on desktop (hover pauses it),
   a native swipe row on touch devices; tapping a dish jumps to that
   menu category
5. About — short teaser; the **Read Our Story** popup holds the full story,
   the chef's quote, the career timeline, and the community section
6. Location — compact info card with live "Open now" pill (LA time);
   the **Map & More Info** popup holds the Google map (loaded only when
   opened), email, parking, accessibility, good-to-know, and social links
7. Menu — paper-style tabbed menu, no prices (sharables / brunch / lunch /
   dinner / wines & beer / house made bakery)
8. Order & Catering — pickup/delivery and catering cards (details in the
   **Details** popup) plus gift cards
9. Footer

## Popups

The popups are native `<dialog>` elements at the bottom of `index.html`
(`#modal-story`, `#modal-visit`, `#modal-catering`, `#modal-order`). Any
element with `data-modal="<dialog-id>"` opens one. They close via the ✕
button, the backdrop, Escape, or the phone's back gesture (each open popup
pushes a history entry). On phones they open as bottom sheets.

`#modal-order` is the **Order & Catering chooser**: the nav, drawer, and
footer "Order & Catering" links open it so guests pick Pickup & Delivery /
Catering / Gift Cards before leaving for Square. Plain "Order Online"
buttons intentionally stay direct links.

## Smart flows

- **Deep links**: `#popup-order`, `#popup-story`, `#popup-visit`,
  `#popup-catering` open that popup on load; `#menu=dinner` (any category
  id) opens the menu on that category.
- **Dish cards** carry `data-item` keys matching `k:` keys in the `MENU`
  array — tapping a dish scrolls to that exact dish and flashes it.
- **Menu**: prev/next links under the paper, arrow keys on the tabs, and
  horizontal swipe on the paper (touch) all change category; a polite
  live region announces changes to screen readers.
- **Live hours**: `renderHours()` (LA time, refreshed every minute) drives
  the location pill, the order popup status line, and the quick-bar dot —
  including a "Closes soon" state in the last 45 minutes.
- **Mobile quick-bar**: on phones, a bottom bar (Menu · Order · Call)
  slides in after the hero scrolls away and hides while popups are open.
- **Menu JSON-LD** (`schema.org/Menu`) is generated from the same `MENU`
  array at load, so search engines always see the current menu.
- **Logo variants**: `assets/logo-400.png` and `assets/logo-1120.png` are
  resized+quantized from `assets/logo.png` and served via `srcset`.

## Swapping in real photos

Photo slots currently use neutral placeholder art so the site looks finished
without photography:

- **Hero photos**: in each `.hero-photo`, replace the `.ph-art` div with
  `<img src="assets/your-photo.jpg" alt="...">` — the arch crop keeps working.
- **Pictures with words**: in each `.picword`, replace the `.ph-art` div with
  `<img src="assets/your-photo.jpg" alt="...">` — the caption overlay keeps
  working on top of the photo.
- **Dish cards**: inside each `.dish-art`, replace the `<svg>` with
  `<img src="assets/your-dish.jpg" alt="Dish name">` — the arch crop and hover
  zoom keep working.
- **Chef portrait**: in `#modal-story .modal-photo`, replace the `.ph-art`
  div with `<img src="assets/chef.jpg" alt="Chef Massimo Ormani">`.

## Editing the menu

All menu content is in the `MENU` array at the bottom of `index.html`
(category → items with name `n`, description `d`, optional `note`).
The menu is intentionally price-free.
