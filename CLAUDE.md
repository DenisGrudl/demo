# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projekt

Jednoduché HTML nástroje — vše v jednom souboru, žádný build, žádné závislosti.

Hostováno přes GitHub Pages: `https://denisgrudl.github.io/demo/`

## Architektura `rabaty.html`

Jediný soubor (~850 řádků) s inline CSS, HTML a JS. Žádné externí knihovny.

**Data:** Ukládají se v `localStorage` pod klíči `rb3_dealers` a `rb3_products`. Při prvním načtení se inicializují z konstanty `INIT_PRODUCTS` (předvyplněný seznam přípravků Simply).

**Hlavní datové struktury:**
- `dealers[]` — `{ id, name }`
- `products[]` — `{ id, dealerId, name, akce, objednano, bonusSlibeny, bonusAdmin, notes, dodavky[], bonusyPrijate[], done }`
- `dodavky` / `bonusyPrijate` — pole záznamů `{ id, date, qty, note, imported }`

**Tok aplikace:**
1. Úvodní obrazovka (`#dealerScreen`) — výběr dealera kartičkami
2. Po výběru se zobrazí `#tableView` — tabulka produktů filtrovaná dle `activeDealerId`
3. Klik na řádek rozbalí detail panel s editací polí a přidáváním záznamů

**Klíčové funkce:**
- `showDealerScreen()` / `selectDealer(id)` — přepínání obrazovek
- `renderTable()` — překreslí tabulku produktů
- `renderDetailPanel(p)` — vrací HTML detailu produktu
- `getStatus(p)` — vrací stav (`empty`, `active`, `pending-bonus`, `pending-admin`, `done`)
- `load()` / `save(data)` — čtení/zápis do localStorage

## Pravidla

- Pouze čistý HTML, CSS, JavaScript — žádné frameworky
- Vše v jednom souboru
- Uživatelka není programátorka — změny musí být přímočaré a bez technického žargonu
