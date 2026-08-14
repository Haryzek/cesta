# TODO — Moje cesta

Pracovní seznam. **README popisuje, jak věci jsou; tenhle soubor, co se má stát.**
Když se něco vyřídí, škrtá se odsud — a pokud to změnilo pravidlo, doplní se do README.

Dělení je podle toho, **kdo to musí utáhnout**, ne podle oblasti. Nahoře jsou věci,
kde je potřeba Bobova hlava nebo ruka a nikdo je za něj neudělá.

---

## 🫏 Pro vrchního osla

Věci, kde rozhoduje Bobův úsudek, jeho hlas nebo jeho přístupy. Claude umí připravit
podklad, seznam nebo návrh — ale poslední slovo je Bobovo.

### Obsah

- [ ] **Triplet přerámování — jádro appky.** Pokrytí je 4 clustery ze 116
      (`cl_0001`, `cl_0008`, `cl_0013`, `cl_0031`). Jde z Bobových Excel seznamů,
      ne z textových promptů. *Tohle je největší kus nehotové práce v projektu.*
- [ ] **Obsahová kontrola cvičení, dávka po dávce.** 71 cvičení je strukturálně
      čistých, ale věcně a jazykově neprověřených. Kontroluje se samonosnost,
      věrnost Bobovým formulacím, úplnost postupů, kvalita deníkových otázek
      a tónová pestrost. Strojově to nejde. Doporučené pořadí: oddíl 04 jako
      etalon, pak 05–11. Práce na několik sezení.
- [ ] **Rozhodnout o `diary_exercise`.** Vyplněný je u 41 cvičení, podklad má
      ale jen 25 značek. SPEC §17 říká „vlastní deník jen u cvičení s unikátním
      obsahem". Claude umí těch 16 navíc vypsat — posoudit, jestli nejde o vatu,
      musí Bob.
- [ ] **Zadat, jestli projet perexy článků.** U cvičení se to udělalo (8 přepsaných
      z 71). U 112 článků se perexy zatím nikdo nedíval stejným metrem.

### Schémata

- [ ] **Závěrečná revize schémat u clusterů s čerstvým modelem.** Bob je přiřazoval
      ručně přes čtyři modely v pěti kolech, ale je to pár měsíců a mezitím
      přibyl silnější model. Plán: nechat přehodnotit, pak osobně zkontrolovat.
      Clusterů se do té doby nikdo nedotýká.

      **Vstup z měření (14. 8. 2026)** — porovnání „jak silně schéma vstupuje do
      profilu" vs. „kolik obsahu je pro něj dosažitelné přes pozice 1–2":

      | schéma | clusterů | dosažitelný obsah |
      |---|---|---|
      | ENTGRAND | 14 | **4 — a všechno jen otázky** (0 článků, 0 cvičení, 0 inspirací) |
      | UNFAIR | 5 | 4 |
      | PUNIT | 17 | 11 |

      Může to být díra v obsahu, může to být přeřazení v clusterech. Revize to rozsoudí.

### Vizuál

- [ ] **Barvy — „overhaul do veselejší atmosféry".** Design systém z 17. 7. 2026 je
      odladěný základ, ale paleta na tenhle posun pořád čeká. Bobovo rozhodnutí.
- [ ] **Karty Přerámování.** Čekají na doladění — větší karty, výraznější věty.

### Provoz

- [ ] **Ověřit embed `cesta.html` do Miowebu.** Jediné, co nikdo jiný
      neotestuje — je potřeba reálná WordPress stránka. Záložní `cesta_prototyp.html`
      už neexistuje (smazán 14. 8. 2026), takže když embed nepůjde, řeší se to
      úpravou kompletní verze, ne návratem ke staré.

### Model dat

- [ ] **Celková doba a frekvence cvičení.** `duration` zůstává jedno číslo = jedno
      provedení (banner). Celková doba praktikování („průběžně 1–2 týdny") čeká na
      rozšíření datového modelu o samostatná volitelná pole. Zatím to žije v textu
      Info, blok „Uvedení do praxe“.

---

## 🤝 Spolu

Potřebuje domluvu, pak už to Claude dotáhne.

- [ ] **Admin nástroj — přestavba od nuly.** `cesta_admin.html` je zastaralý
      a rozešel se s realitou (špatné prefixy, třímístný padding, nezná triplet).
      Hlavní věc k předělání: přerámování musí být **cluster-scoped**, ne plochý
      globální seznam. Rámcový návrh je v `CLAUDE.md`.

---

## 🔧 Na Claudovi

Mechanika, nepotřebuje Bobovo rozhodnutí — jen se to musí udělat.

- [ ] **Telefonní čísla v krizovce udělat klikací.** Markdown parser neumí odkazy,
      ale renderer už čísla detekuje (`mc-tel`) — stačí je zabalit do `tel:`.
      V krizi to má reálnou hodnotu.
- [ ] **Zrušit berličku `stripDupHeading`.** Data jsou teď čistá a funkce je nečinná.
      Drží se jen pro fázi generování z promptů; až budou prompty spolehlivé, pryč.
      *(`pullDuration`, dřívější druhá berlička, je už smazaná.)*
- [ ] **Commit a push.** V pracovním stromu visí nasazená data, oprava rendereru,
      `tagy.json` a dokumentace.

---

## Nedávno vyřízené

Držet krátké — jen věci, na které se bude někdo ptát „a tohle jsme řešili?".

- **14. 8. 2026 — `cesta_prototyp.html` smazán.** Mrtvá větev, Bob ho odstranil
  z lokálu. Zůstává v historii gitu. Rozcestník `index.html` má nově jedinou
  kartu — druhý odkaz vedl na smazaný prototyp a třetí na admin přesunutý do
  `local/.old/`, obojí by po nasazení bylo 404.

- **14. 8. 2026 — Oddíly a řetězy nasazené, model z 11 na 13 souborů.**
  `sections.json` (11 oddílů) a `chains.json` (4 řetězy) jsou v `data/`,
  referenční integrita s cvičeními ověřená. README je popisuje včetně pravidla
  o slepování deníků a chování badge řetězu. **Renderer je zatím ignoruje** —
  sekce „Moje cesta" a badge řetězu se budou stavět samostatně.
- **14. 8. 2026 — Úklid složek.** `cesta_admin.html` do `local/.old/`, zdrojové
  `sec_*.md` do `sections_wip/_podklad/` (zdroj pravdy je `sections.json`),
  smazán duplikát `articles.json` v `articles_wip/` a zámek po PowerPointu.
  Opravené odkazy na neexistující soubory v CLAUDE.md, README i SPEC —
  ověřeno strojově, že žádný dokument neukazuje do prázdna.

- **14. 8. 2026 — Motta u oddílů zrušená.** `sections.json` mělo 10 blokových
  citací (`>`) — po jedné nad každou Praxí a dvě v Teorii. Vyhozeny celé, ne
  přerenderovány: byla to výbava tiskové cvičebnice a v appce by z nich při
  rozšiřování o nové oddíly zůstal dluh (dvě kategorie oddílů, s mottem a bez).
  Citát má v appce vlastní místo — sekci Inspirace. Odpadla tím i potřeba
  komponenty v rendereru pro `>`, který markdown parser neumí.

- **14. 8. 2026 — `source_url` / `show_link` zprovozněné.** `show_link` znamená
  „text je zkrácený o víc než 20 %", ne „máme URL". U 71 článků ze 112 se pod
  tělem vykreslí tichý řádek „Celý článek na blogu", odkaz jde do nového panelu.
  Pravidlo i chování popsané v README u `articles.json`.

- **14. 8. 2026 — Tagy sjednocené.** 93 rozjetých tagů → 56, slovník je nově
  společný pro celou appku a leží v `tagy.json` v kořeni. Zrušeny všechny tři
  staré kopie seznamu (`local/_tags/*.txt`, SPEC §12, natvrdo v lintu) — právě
  rozejití kopií způsobilo, že se slovník rozjel dvakrát.
- **14. 8. 2026 — Schémata u obsahu srovnána na 3.** Clustery mají dál 5 (čtou se
  všechny při stavbě profilu), obsah 3 (skóruje se z pozic 1–2, třetí je rezerva).
  Pozice 1–2 se ořezem nezměnily ani u jedné položky, výstup doporučovadla je
  identický.
- **14. 8. 2026 — Cvičení a články nasazené do `data/`.** 71 cvičení, 112 článků.
- **14. 8. 2026 — Oprava číslování kroků v rendereru.** Číslovaný seznam přerušený
  podnadpisem začínal znovu od 1 (`ex_0049` i `ex_0021`). Parser teď respektuje
  číslo prvního zdrojového kroku.
