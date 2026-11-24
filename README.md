# Osobní stránka – potok

Osobní webová stránka vytvořená jako školní projekt.

## Obsah

- Úvod, sekce O mně, tři projekty, přehled dovedností a kontakt.
- Sémantické HTML, plná ovladatelnost klávesnicí a dodržení WCAG 2.2 AA.
- Rozvržení a barvy se přizpůsobují nastavení uživatele (media rules).

## Media rules

| Pravilo | Co se mění a proč |
| --- | --- |
| Šířka okna | Tři zlomy (40/60/80 em) mění navigaci ze sloupce na řádek a rozvržení karet i sekce O mně, aby se stránka vešla od telefonu po široký monitor bez vodorovného posuvníku. |
| Tmavý režim | `prefers-color-scheme` přepíná CSS proměnné, `color-scheme` a barvy posuvníků, aby text i ovládací prvky měly v obou schématech dostatečný kontrast. |
| Vyšší kontrast | `prefers-contrast: more` zvyšuje kontrast textu na AAA, zesiluje okraje, podtrhuje odkazy a odebírá přechody a obrázky za textem. |
| Omezený pohyb | TODO |
| Průhlednost | TODO |
| Vynucené barvy | TODO |
| Kombinace tmavý režim + vyšší kontrast | Spojená podmínka `and` nastaví černé pozadí, bílý text a žluté odkazy, aby obě nastavení fungovala zároveň. |

## Nasazení

TODO: odkaz na GitHub Pages.
