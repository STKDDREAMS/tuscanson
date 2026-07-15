# Tuscan Son — Website

A single-page site for Tuscan Son (Century City, Los Angeles): pure-white base,
off-white sections, and accent tones pulled from the sunflower logo (brick red,
sunflower gold, olive green).

## Structure

Everything lives in `index.html` (HTML + CSS + JS, no build step) with the logo
in `assets/logo.png`. Section order:

1. Hero — framed white hero with the sunflower medallion, logo, and CTAs
2. Ticker — scrolling values strip (made in house, garden patio, …)
3. Dish gallery — auto-scrolling marquee; hovering pauses it, tapping a dish
   jumps to that menu category
4. About — chef story, quote band, career timeline, community badges
5. Location — info card with live "Open now" pill (LA time) + Google map
6. Menu — tabbed paper menu
7. Catering & gift cards
8. Footer

## Swapping in real photos

Dish cards and the chef portrait currently use inline illustrations /
placeholder art so the site looks finished without photography:

- **Dish card**: inside each `.dish-art`, replace the `<svg>` with
  `<img src="assets/your-dish.jpg" alt="Dish name">` — the arch crop and hover
  zoom keep working.
- **Chef portrait**: in `.about-portrait .in`, replace the `.ph-art` div with
  `<img src="assets/chef.jpg" alt="Chef Massimo Ormani">`.

## Editing the menu

All menu content is in the `MENU` array at the bottom of `index.html`
(category → items with name `n`, description `d`, optional `note`).
