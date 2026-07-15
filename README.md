# Tuscan Son — Website

A single-page site for Tuscan Son (Century City, Los Angeles): pure-white base,
neutral off-white sections (no beige), and accents pulled from the sunflower
logo — brick red and olive green, with a bit of orange and minimal yellow.

## Structure

Everything lives in `index.html` (HTML + CSS + JS, no build step) with the logo
in `assets/logo.png`. The main scroll is kept short and minimal — longer
content lives in popups. Section order:

1. Hero — framed white hero with the flower logo medallion and
   "Upscale food in a casual setting" tagline
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

The three popups are native `<dialog>` elements at the bottom of
`index.html` (`#modal-story`, `#modal-visit`, `#modal-catering`). Any
element with `data-modal="<dialog-id>"` opens one. They close via the ✕
button, the backdrop, or Escape. On phones they open as bottom sheets.

## Swapping in real photos

Photo slots currently use neutral placeholder art so the site looks finished
without photography:

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
