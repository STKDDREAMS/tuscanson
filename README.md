# Tuscan Son — Website

A single-page site for Tuscan Son (Century City, Los Angeles): pure-white base,
neutral off-white sections (no beige), and accents pulled from the sunflower
logo — brick red and olive green, with a bit of orange and minimal yellow.

## Structure

Everything lives in `index.html` (HTML + CSS + JS, no build step) with the logo
in `assets/logo.png`. Section order:

1. Hero — framed white hero with the flower logo medallion and
   "Upscale food in a casual setting" tagline
2. Pictures with words — three photo cards (made in house / straight from
   Italy / upscale, but easy)
3. Ticker — scrolling values strip (made in house, upscale food, straight
   from Italy, free & easy parking, easy accessibility, no reservations)
4. Dish gallery — auto-scrolling marquee; hovering pauses it, tapping a dish
   jumps to that menu category
5. About Us — the full story, quote band, career timeline, and the
   "We live here too" community section
6. Location — info card with live "Open now" pill (LA time) + Google map
7. Menu — paper-style tabbed menu, no prices (sharables / brunch / lunch /
   dinner / wines & beer / house made bakery)
8. Order & Catering — pickup/delivery, catering details, gift cards
9. Footer

## Swapping in real photos

Photo slots currently use neutral placeholder art so the site looks finished
without photography:

- **Pictures with words**: in each `.picword`, replace the `.ph-art` div with
  `<img src="assets/your-photo.jpg" alt="...">` — the caption overlay keeps
  working on top of the photo.
- **Dish cards**: inside each `.dish-art`, replace the `<svg>` with
  `<img src="assets/your-dish.jpg" alt="Dish name">` — the arch crop and hover
  zoom keep working.
- **Chef portrait**: in `.about-portrait .in`, replace the `.ph-art` div with
  `<img src="assets/chef.jpg" alt="Chef Massimo Ormani">`.
- **Community photo**: in `.community-photo`, same swap.

## Editing the menu

All menu content is in the `MENU` array at the bottom of `index.html`
(category → items with name `n`, description `d`, optional `note`).
The menu is intentionally price-free.
