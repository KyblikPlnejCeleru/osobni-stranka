# Osobní stránka – potok

Osobní webová stránka vytvořená jako školní projekt se zaměřením na sémantické HTML,
CSS media rules a přístupnost podle WCAG 2.2 AA.

**Nasazená verze:** <https://kyblikplnejceleru.github.io/osobni-stranka/>

## Obsah

- Úvod, sekce O mně (včetně citátu o pozornosti), tři projekty s obrázky,
  přehled dovedností v tabulce a kontakt.
- Sémantické HTML, jediný `h1`, logická struktura nadpisů, skip link a plná
  ovladatelnost klávesnicí.
- Text a rozestupy v relativních jednotkách, použitelnost od nejmenšího telefonu
  po široký monitor a při přiblížení 200 % i 400 %.
- Podrobné vyhodnocení kritérií a nálezy jsou v [ACCESSIBILITY.md](ACCESSIBILITY.md).

## Struktura repozitáře

| Cesta | Obsah |
| --- | --- |
| `index.html` | Sémantický obsah stránky |
| `css/style.css` | Základní styly a všech šest povinných media rules včetně kombinace |
| `assets/img/` | Ilustrace (SVG) s popisným nebo prázdným `alt` |
| `ACCESSIBILITY.md` | Zpráva o přístupnosti, 55 kritérií WCAG 2.2 A/AA a nálezy |
| `.github/workflows/pages.yml` | Automatické nasazení na GitHub Pages po pushi do `main` |

## Media rules

| Pravilo | Co se mění a proč |
| --- | --- |
| Šířka okna | Tři zlomy (40/60/80 em) mění navigaci ze sloupce na řádek a rozvržení karet i sekce O mně, aby se stránka vešla od telefonu po široký monitor bez vodorovného posuvníku. |
| Tmavý režim | `prefers-color-scheme` přepíná CSS proměnné, `color-scheme` a barvy posuvníků, aby text i ovládací prvky měly v obou schématech dostatečný kontrast. |
| Vyšší kontrast | `prefers-contrast: more` zvyšuje kontrast textu na AAA, zesiluje okraje, podtrhuje odkazy a odebírá přechody a obrázky za textem. |
| Omezený pohyb | `prefers-reduced-motion: reduce` vypne plynulé scrollování, animaci karet i přechody odkazů; žádná informace není sdílena jen pohybem. |
| Průhlednost | `prefers-reduced-transparency: reduce` nahrazuje průhledná pozadí karet a rozostření plnými barvami a výraznějším okrajem. |
| Vynucené barvy | `forced-colors: active` používá systémové barvy (Canvas, CanvasText, LinkText, Highlight) a nahrazuje stíny okraji karet, tlačítek i fokusu. |
| Kombinace tmavý režim + vyšší kontrast | Spojená podmínka `and` nastaví černé pozadí, bílý text a žluté odkazy, aby obě nastavení fungovala zároveň. |

Každé pravidlo bylo vyvíjeno ve vlastní větvi a sloučeno pull requestem; v historii
je také vyřešený cvičný konflikt (merge commit se dvěma rodiči).

## Nasazení

Stránka se nasazuje automaticky po každém pushi do `main` pomocí GitHub Actions
(`Settings → Pages → Source: GitHub Actions`). Workflow lze spustit i ručně v záložce
Actions přes `workflow_dispatch`.

## Jak ověřit media rules v DevTools

1. Otevřete stránku a stiskněte **F12**.
2. Stiskněte **Ctrl+Shift+P** (macOS **Cmd+Shift+P**), napište `Show Rendering` a vyberte panel Rendering.
3. V sekci **Emulate CSS media feature** postupně nastavte:
   - `prefers-color-scheme: dark`,
   - `prefers-contrast: more`,
   - `prefers-reduced-motion: reduce`,
   - `prefers-reduced-transparency: reduce`,
   - `forced-colors: active`.
4. Kombinaci dvou nastavení ověříte tak, že necháte zaškrtnuté `prefers-color-scheme: dark`
   a zároveň `prefers-contrast: more`.
5. Změňte šířku okna (např. 320 px, 768 px, 1440 px) a zkontrolujte, že se navigace
   přeskupí a neobjeví se vodorovný posuvník.

## Vývoj

```sh
git clone https://github.com/KyblikPlnejCeleru/osobni-stranka.git
cd osobni-stranka
# otevřete index.html v prohlížeči nebo spusťte libovolný statický server
```

Před nasazením ověřte stránku v DevTools: Lighthouse (Accessibility), Rendering
(emulace media features), klávesnici a přiblížení 200/400 %.
