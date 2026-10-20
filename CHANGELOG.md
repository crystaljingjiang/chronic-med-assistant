# Changelog

## [2.1.0] - 2026-10-20

### Added
- Deep links for every screen (`#plan`, `#inventory`, `#refill`, `#health`, `#ai`, `#ai/check`, `#settings`).
- The chosen font size is saved and restored on reload.
- Full-screen layout on real phones (viewports narrower than 500px). On desktop, the phone frame shrinks to fit shorter windows so the tab bar stays visible.
- README, product brief (`docs/PRODUCT.md`), screenshots, license and `.gitignore`.

### Fixed
- The countdown card's content jumped up about 50px after a dose was confirmed.
- Text typed into the AI chat was inserted as HTML. It is now escaped.
- `**bold**` in chat answers showed as literal asterisks.
- The chat didn't scroll to the newest message. It now scrolls in its own box.
- The font-size setting showed 大字 as selected while the page was at standard size.
- The interaction checker reported "no interactions" when fewer than 2 drugs were selected.
- The Home follow-up alert said 3 days to the 3 May visit. From the 24 April demo date it is 9 days.

## [2.0.0] - 2026-04-24

- First version of the prototype with the Home, Plan, Inventory, Refill, AI and Health tabs, plus large-font settings.
