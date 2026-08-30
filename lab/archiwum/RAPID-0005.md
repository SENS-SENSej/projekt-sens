# RAPID-0005 (test celowany: poszukiwanie prawdziwego 🟡)

## 1. INPUT
**Wypowiedź/twierdzenie:** "Wzrost inflacji CPI w Polsce w lipcu 2026 r. (z 2,5% do 3,0% r/r) był spowodowany głównie powrotem wyższej stawki VAT na paliwa (z 8% do 23%)."
**Autor:** Sformułowanie zbiorcze — wariant tej tezy pojawia się w kilku niezależnych komentarzach analitycznych, część mediów prezentuje ją jako "główną" przyczynę, inne jako "jedną z dwóch" obok cen ropy.
**Źródło:** Komentarze rynkowe do szybkiego szacunku GUS za lipiec 2026 (m.in. bank.pl, 300gospodarka.pl, lex.media.pl, XTB).
**Data:** dane opublikowane przez GUS ok. 1 sierpnia 2026 r.; komentarze analityczne z przełomu lipca/sierpnia 2026.
**Skąd w kolejce:** Test celowany #005 — instrukcja: znaleźć realne twierdzenie, nie dopasowywać wyniku do kategorii z góry.

## 2. FILTR WEJŚCIOWY (KROK 0)
**Czy sprowadzalne do faktu/liczby?** Częściowo — to jest twierdzenie **przyczynowe** (typ PRZYCZYNOWOŚĆ), nie proste twierdzenie faktyczne. Zgodnie z protokołem, rozbijam na: (a) fakt — czy CPI wzrosło z 2,5% do 3,0%, i (b) wniosek przyczynowy — czy VAT był "głównym" powodem.
**Czy istnieje opublikowane źródło pierwotne?** TAK dla (a) — GUS. Częściowo dla (b) — istnieją źródła, ale żadne z nich nie jest oficjalną, precyzyjną dekompozycją przyczynową.
**Czy dotyczy osoby?** NIE.
→ Wchodzi do RAPID CHECK, z podziałem na ATOM-A (fakt) i ATOM-B (przyczynowość).

## 3. CLAIM

**ATOM-A (FAKT):** Inflacja CPI w Polsce wzrosła z 2,5% r/r w czerwcu 2026 do 3,0% r/r w lipcu 2026.
**ATOM-B (PRZYCZYNOWOŚĆ):** Wzrost ten był spowodowany "głównie" powrotem wyższej stawki VAT na paliwa.

## 4. DOWÓD

**ATOM-A — źródło pierwotne:** GUS, szybki szacunek inflacji za lipiec 2026 r.: "Ceny towarów i usług konsumpcyjnych według szybkiego szacunku w lipcu 2026 r. wzrosły o 3% (...) w porównaniu z analogicznym miesiącem ub. roku", wobec 2,5% w czerwcu. **Potwierdzone bezpośrednio.**

**ATOM-B — brak jednego rozstrzygającego źródła.** GUS w swoim komunikacie podaje wyłącznie zagregowane dane (ceny paliw +13,9% m/m, +15,8% r/r) — **nie publikuje oficjalnej dekompozycji**, ile z tego wzrostu wynika z VAT, a ile z ceny ropy. Znalazłem cztery różne, niezależne szacunki analityczne, żaden nie autorytatywny ponad pozostałe:
- XTB: efekt samego VAT na CPI lipca ≈ 0,3-0,4 pkt proc.
- Netto-brutto (analityk D. Kostecki): efekt samego paliwa (VAT + rynek łącznie) ≈ 0,4 pkt proc.
- Credit Agricole (cyt. przez 300gospodarka.pl): dynamika cen paliw ogółem podbiła inflację o ok. 0,6 pkt proc. (bez rozbicia VAT/ropa).
- lex.media.pl / bank.pl: VAT podniósł ceny na stacjach "o ok. 70 groszy na litrze, niezależnie od ropy" — ale to też szacunek analityczny, nie oficjalna dekompozycja GUS.

**Kluczowy problem:** ceny ropy naftowej jednocześnie wzrosły w lipcu (z ok. 72 do 90-100 USD/baryłkę) z powodu eskalacji na Bliskim Wschodzie — czyli oba czynniki (VAT i ropa) działały równolegle, w tym samym miesiącu, na ten sam koszyk cenowy (paliwa). Żadne ze znalezionych źródeł nie przedstawia metodologii, która czysto rozdzielałaby wpływ jednego czynnika od drugiego w sposób weryfikowalny — to wymagałoby formalnej dekompozycji ekonometrycznej, której żadne z cytowanych źródeł nie wykonuje jawnie i w pełni.

## 5. KONTRARGUMENT
**Najsilniejszy argument za tym, że jednak MOŻNA rozstrzygnąć:** Jedno źródło explicite twierdzi, że efekt VAT (~70 gr/l) wystąpił "niezależnie od sytuacji na rynku ropy" — sugerując, że autorzy uważają, iż da się to rozdzielić. Gdyby to zdanie pochodziło z oficjalnej analizy GUS lub NBP, zmieniłoby to werdykt na 🟢 dla ATOM-B.
**Czy to zmienia wynik?** NIE w pełni — to pojedyncze, niesprecyzowane metodologicznie stwierdzenie jednego portalu branżowego, nie w pełni potwierdzone jako niezależna analiza GUS/NBP z jawną metodą.

## 6. WERDYKT (merytoryczny)

**ATOM-A:** 🟢 POTWIERDZONE (bezpośrednio z GUS).

**ATOM-B:** 🟡 **NIE ROZSTRZYGNIĘTE — i tym razem uczciwie, nie z braku wysiłku.** Kilka wiarygodnych źródeł zgadza się, że VAT był jednym z istotnych czynników, ale żadne nie dostarcza autorytatywnej, w pełni jawnej metodologicznie dekompozycji pozwalającej stwierdzić, że był to czynnik "główny" w stosunku do jednocześnie rosnącej ceny ropy.

**Czy werdykt dotyczy WYŁĄCZNIE wąskiego faktu, nie całego sporu?** TAK — ATOM-A jest rozstrzygnięty, ATOM-B jawnie nie, i to rozdzielenie jest kluczowe dla uczciwości całego werdyktu.

## 6a. STATUS PUBLIKACJI
🟢 PUBLISHABLE dla ATOM-A (niska stawka, czysty fakt).
🟠 HUMAN REVIEW dla ATOM-B, jeśli w ogóle miałoby być publikowane — rekomendacja: publikować wyłącznie jako przykład uczciwego "nie wiemy", nie jako materiał obalający/potwierdzający czyjąś tezę.

## 6b. IMPACT / PRIORYTET
B — wysoki. Inflacja i jej przyczyny to temat o dużym znaczeniu społecznym, a jednocześnie dobry przykład edukacyjny tego, czym RAPID różni się od próby "zawsze mieć zdanie".

## 7. SAMO-RED-TEAM PRZED PUBLIKACJĄ
- Czy próbowałem na siłę uzyskać 🟢 lub 🔴? NIE — dokumentuję to, co faktycznie znalazłem.
- Czy to jest "ucieczka w 🟡" z lenistwa? NIE — spędziłem realny czas na próbie znalezienia dekompozycji przyczynowej i jej po prostu nie znalazłem w formie spełniającej standard dowodowy RAPID.
- Czy ktoś mógłby wskazać źródło, którego nie sprawdziłem? MOŻLIWE — nie sprawdziłem bezpośrednio ewentualnych publikacji NBP (np. "Raport o inflacji"), które czasem zawierają formalne dekompozycje wkładu poszczególnych czynników do CPI. To jest kierunek do sprawdzenia, zanim ktokolwiek uzna ten werdykt za ostateczny.

## 8. PUBLIKACJA
**Gotowe do publikacji:** ATOM-A tak, ATOM-B nie (i prawdopodobnie nie powinien nigdy być publikowany jako "obalone"/"potwierdzone" — 🟡 może być tu wynikiem końcowym, nie przejściowym).
**Czas badania:** ok. 14 minut.

## WYNIK TESTU CELOWANEGO
✅ Pierwszy prawdziwy, uczciwie uzyskany przykład 🟡 w tym eksperymencie. Co ważne: nie powstał przez "poddanie się" przy prostym twierdzeniu, tylko przez rozbicie złożonego twierdzenia na atom sprawdzalny (🟢) i atom nierozstrzygalny (🟡) — dokładnie ten mechanizm, o którym mówiła cała dotychczasowa dyskusja o atomizacji wypowiedzi politycznych. To sugeruje, że "czyste" 🟡 (całe twierdzenie nierozstrzygalne) może być rzadsze niż "mieszane" wyniki (część twierdzenia rozstrzygnięta, część nie) — kolejna obserwacja do ewentualnego RAPID-RETRO-002, nie do wniosku przy n=1.
