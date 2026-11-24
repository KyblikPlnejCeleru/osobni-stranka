# Zpráva o přístupnosti

Stránka **potok – student, který tvoří přístupný web** je navržená tak, aby splňovala
**WCAG 2.2 úroveň AA** (všech 55 kritérií úrovní A a AA; kritérium 4.1.1 Parsing
bylo ve verzi 2.2 odstraněno, proto se nevyhodnocuje).

## Použité postupy a nástroje

- **Lighthouse** (Chrome DevTools, kategorie Accessibility): výchozí skóre 95, nález
  `color-contrast` opraven (viz nález 1). Po opravě již audit nehlásí žádný vážný
  nález.
- **W3C Nu HTML Checker**: `index.html` prošel bez chyb a upozornění.
- **axe-core** (součást Lighthouse): použit pro automatickou kontrolu kontrastu,
  alternativ, názvů odkazů, struktury a pořadí nadpisů.
- **WAVE**: rozšíření nebylo v dostupném prostředí k dispozici; ekvivalentní
  automatická kontrola byla provedena pomocí axe-core/Lighthouse a doplněna ručně.
- **Ruční kontrola**: klávesnice (Tab, Shift+Tab, Enter), pořadí fokusu, viditelnost
  fokusu, skip link, přiblížení 200 % a 400 %, emulace `prefers-color-scheme`,
  `prefers-contrast`, `prefers-reduced-motion`, `prefers-reduced-transparency`
  a `forced-colors` v DevTools (včetně kombinace tmavý režim + vyšší kontrast).
- **Čtečka obrazovky**: struktura (landmarky, nadpisy, seznamy, tabulka s `caption`
  a `scope`) byla ověřena pomocí accessibility stromu v DevTools.

Stavy: **Splněno** = kritérium je na stránce implementováno; **Nevztahuje se** =
stránka neobsahuje příslušný typ obsahu ani interakci. Žádné kritérium není ve
stavu *Nesplněno*.

## 1. Vnímatelnost

| Kritérium | Úroveň | Stav | Zdůvodnění |
| --- | --- | --- | --- |
| 1.1.1 Non-text Content | A | Splněno | Sdílené obrázky mají výstižné `alt`; dekorativní hvězdička má `alt=""`, SVG mají `role="img"` a popisek. |
| 1.2.1 Audio-only and Video-only | A | Nevztahuje se | Stránka neobsahuje audio ani video. |
| 1.2.2 Captions (Prerecorded) | A | Nevztahuje se | Stránka neobsahuje synchronizované médium. |
| 1.2.3 Audio Description or Media Alternative | A | Nevztahuje se | Stránka neobsahuje video. |
| 1.2.4 Captions (Live) | AA | Nevztahuje se | Stránka neobsahuje živé vysílání. |
| 1.2.5 Audio Description (Prerecorded) | AA | Nevztahuje se | Stránka neobsahuje video s audiostopou. |
| 1.3.1 Info and Relationships | A | Splněno | `header`, `nav`, `main`, `section`, `footer`, seznamy a tabulka s `caption` a `th scope`. |
| 1.3.2 Meaningful Sequence | A | Splněno | Pořadí v DOM je stejné jako vizuální pořadí; obsah není přesouván pomocí CSS. |
| 1.3.3 Sensory Characteristics | A | Splněno | Pokyny ani odkazy nespoléhají na barvu, tvar ani polohu. |
| 1.3.4 Orientation | AA | Splněno | Rozvržení je tekuté, žádné uzamčení orientace. |
| 1.3.5 Identify Input Purpose | AA | Nevztahuje se | Stránka nemá formulářová pole. |
| 1.4.1 Use of Color | A | Splněno | Odkazy jsou podtržené, fokus má outline, hover mění i tvar (posunutí), nejen barvu. |
| 1.4.2 Audio Control | A | Nevztahuje se | Stránka nepřehrává zvuk. |
| 1.4.3 Contrast (Minimum) | AA | Splněno | Text splňuje 4,5:1 v obou schématech; tlačítko opraveno commitem `14aeff7`. |
| 1.4.4 Resize Text | AA | Splněno | Velikosti jsou v `rem`/`em`, zoom 200 % i 400 % funguje bez ztráty obsahu. |
| 1.4.5 Images of Text | AA | Splněno | Všechny texty jsou skutečný text; ilustrace neobsahují text. |
| 1.4.10 Reflow | AA | Splněno | Mobile-first rozvržení, `max-width: 100 %`, žádný vodorovný posuvník stránky. |
| 1.4.11 Non-text Contrast | AA | Splněno | Okraje `#767676`/`#a0aab5` a 3px fokusový outline mají ≥ 3:1. |
| 1.4.12 Text Spacing | AA | Splněno | Řádkování 1,6, mezery v `rem`, `overflow-wrap: anywhere` u tabulky; nic se nepřekrývá. |
| 1.4.13 Content on Hover or Focus | AA | Nevztahuje se | Stránka nemá tooltipy ani vyskakovací obsah při hover/focus. |

## 2. Ovladatelnost

| Kritérium | Úroveň | Stav | Zdůvodnění |
| --- | --- | --- | --- |
| 2.1.1 Keyboard | A | Splněno | Všechny interakce jsou nativní odkazy; žádné JavaScriptové zástupce. |
| 2.1.2 No Keyboard Trap | A | Splněno | Žádné modalní okno ani fokusová past; skip link umožňuje únik. |
| 2.1.4 Character Key Shortcuts | A | Nevztahuje se | Žádné klávesové zkratky. |
| 2.2.1 Timing Adjustable | A | Nevztahuje se | Žádné časové limity. |
| 2.2.2 Pause, Stop, Hide | A | Splněno | Animace karet trvá 400 ms jednorázově a lze ji vypnout přes `prefers-reduced-motion`. |
| 2.3.1 Three Flashes or Below Threshold | A | Splněno | Žádné blikání ani záblesky. |
| 2.4.1 Bypass Blocks | A | Splněno | Skip link „Přeskočit na hlavní obsah“ jako první prvek stránky. |
| 2.4.2 Page Titled | A | Splněno | `<title>potok – student, který tvoří přístupný web</title>`. |
| 2.4.3 Focus Order | A | Splněno | Pořadí Tab odpovídá logickému pořadí obsahu. |
| 2.4.4 Link Purpose (In Context) | A | Splněno | Navigační i kontaktní odkazy mají výstižný text. |
| 2.4.5 Multiple Ways | AA | Splněno | Hlavní navigace, skip link a odkazy v patičce. |
| 2.4.6 Headings and Labels | AA | Splněno | Jeden `h1`, sekce `h2`, karty `h3`, navigace má `aria-label`. |
| 2.4.7 Focus Visible | AA | Splněno | `:focus-visible` = 3px outline s 3px offsetem; vynucené barvy používají `Highlight`. |
| 2.4.11 Focus Not Obscured (Minimum) | AA | Splněno | `scroll-padding-top: 12rem`/`6rem` brání zakrytí fokusu lepivou hlavičkou (oprava `46dc041`). |
| 2.5.1 Pointer Gestures | A | Nevztahuje se | Žádné gesta ani multitouch. |
| 2.5.2 Pointer Cancellation | A | Splněno | Odkazy fungují standardně po uvolnění tlačítka myši, bez custom handlerů. |
| 2.5.3 Label in Name | A | Splněno | Viditelný text odkazů je zároveň jejich přístupným názvem. |
| 2.5.4 Motion Actuation | A | Nevztahuje se | Stránka nereaguje na pohyb zařízení. |
| 2.5.7 Dragging Movements | AA | Nevztahuje se | Žádné ovládání tažením. |
| 2.5.8 Target Size (Minimum) | AA | Splněno | Odkazy v navigaci a tlačítko mají `min-height`/`min-width: 2.75rem` (44 px). |

## 3. Srozumitelnost

| Kritérium | Úroveň | Stav | Zdůvodnění |
| --- | --- | --- | --- |
| 3.1.1 Language of Page | A | Splněno | `<html lang="cs">`. |
| 3.1.2 Language of Parts | AA | Splněno | Citace je v češtině; cizí názvy (GitHub, WCAG) jsou zavedené výrazy, ne cizojazyčná věta. |
| 3.2.1 On Focus | A | Splněno | Zaostření jen zvýrazní prvek, nemění kontext ani rozvržení. |
| 3.2.2 On Input | A | Nevztahuje se | Stránka nemá vstupy, které by měnily kontext. |
| 3.2.3 Consistent Navigation | AA | Splněno | Jediná stránka, navigace se na všech částech stejná. |
| 3.2.4 Consistent Identification | AA | Splněno | Projekty a kontakt jsou pojmenovány stejně v kartách, navigaci i patičce. |
| 3.2.6 Consistent Help | A | Splněno | Kontakt a odkaz na zprávu o přístupnosti jsou trvale v patičce i v sekci Kontakt. |
| 3.3.1 Error Identification | A | Nevztahuje se | Žádné formuláře, tudíž žádné chyby vstupu. |
| 3.3.2 Labels or Instructions | A | Nevztahuje se | Žádné formuláře ani pole vyžadující pokyny. |
| 3.3.3 Error Suggestion | AA | Nevztahuje se | Žádné chyby vstupu. |
| 3.3.4 Error Prevention | AA | Nevztahuje se | Žádné právní, finanční ani datové transakce. |
| 3.3.7 Redundant Entry | A | Nevztahuje se | Stránka nevyžaduje opakované zadávání údajů. |
| 3.3.8 Accessible Authentication (Minimum) | AA | Nevztahuje se | Žádné přihlašování ani CAPTCHA. |

## 4. Robustnost

| Kritérium | Úroveň | Stav | Zdůvodnění |
| --- | --- | --- | --- |
| 4.1.2 Name, Role, Value | A | Splněno | Sémantické HTML, odkazy mají název, obrázky `alt`, tabulka `caption` a `scope`. |
| 4.1.3 Status Messages | AA | Nevztahuje se | Obsah se sám od sebe nemění, žádné `aria-live` oblasti nejsou potřeba. |

## Nálezy a opravy

| # | Nález | Oprava (commit) |
| --- | --- | --- |
| 1 | Lighthouse (axe `color-contrast`, impact serious): tlačítko „Podívat se na moje projekty“ mělo v tmavém schématu světlý text `#f5f7fa` na žlutém pozadí `#ffd166`, kontrast pouze 1,34:1. | `14aeff7` |
