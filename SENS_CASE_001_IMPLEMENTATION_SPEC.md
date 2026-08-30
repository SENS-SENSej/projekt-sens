# SENS_CASE_001_IMPLEMENTATION_SPEC
*Golden Master. Przekazywane do kodowania. Wersja zamknięta po GATE 1 (Metodologia v0.3 + wireframe + trzy niezależne rundy audytu prawnego i matematycznego).*

---

## CZĘŚĆ 1 — KONTRAKT IMPLEMENTACYJNY

**Zadanie:** zakoduj dokładnie poniższą specyfikację jako `klif.html` (lub zaktualizowany moduł w istniejącym pliku).

**Wolno:**
- implementować UX, interakcje, animacje, responsywność,
- stosować ustalone liczby i wzory,
- stosować ustalone teksty co do słowa,
- poprawiać czytelność wizualną (kolory, spacing, typografia) w ramach stylu SENS OS ustalonego wcześniej.

**Nie wolno:**
- dodawać własnych argumentów, źródeł, faktów ani liczb,
- "logicznie uzupełniać" brakujących informacji,
- zmieniać sformułowań w sposób modyfikujący ich znaczenie prawne/matematyczne,
- tworzyć nowych podstaw prawnych ani numerów ustępów,
- zmieniać metodologii lub struktury sekcji.

**Jeśli czegoś brakuje w specyfikacji: STOP.** Zostaw w kodzie widoczny znacznik `<!-- SENS-QUESTION: [opisz braki] -->` w odpowiednim miejscu i zgłoś to zamiast zgadywać albo dopisywać. Kod z takim znacznikiem nie jest gotowy do publikacji, ale jest lepszy niż kod z cichym domysłem.

---

## CZĘŚĆ 2 — FINALNY WIREFRAME (5 sekcji)

### Sekcja 1 — Co się dzieje?

**Nagłówek:**
> Przekroczenie progu przychodu o 1 zł może podnieść roczną składkę zdrowotną o kilka tysięcy złotych.

**Opis:**
> W systemie ryczałtowym składka zdrowotna nie rośnie proporcjonalnie od każdej zarobionej złotówki. Przekroczenie progu przychodu zmienia podstawę wymiaru dla całego roku rozliczeniowego.

### Sekcja 2 — Sprawdź swój koszt

**Pola wejściowe:**
1. Roczny przychód (narastająco) — suwak + pole numeryczne, domyślnie 60 001 zł
2. Stawka ryczałtu — dropdown: 17% / 15% / 14% / 12% (domyślna) / 10% / 8,5% / 5,5% / 3%

**Wynik dynamiczny — WERSJA POPRAWIONA (porównanie scenariuszy, nie "1 zł = X zł"):**

```
Przychód: [wartość użytkownika]              Próg: [I/II/III]

Roczna składka według tego progu:            [wartość] zł

Dla porównania — przy przychodzie
nieprzekraczającym poprzedniego progu:        [wartość niższego progu] zł

Różnica:                                      +[różnica] zł (brutto)

* Odliczenie: 50% zapłaconej rocznej składki pomniejsza podstawę
  opodatkowania (przychód) przy Twojej stawce ryczałtu.
  Ulga na tej różnicy: [wartość] zł

Realny koszt roczny po uldze:                 +[wynik netto] zł
```

**Komunikat strefy (aktywny tylko blisko granicy progu, ±5000 zł):**
> 🔴 Jesteś w strefie granicznej progu [X] zł. Zobacz dokładnie, co to oznacza dla Twojego rozliczenia rocznego, powyżej.

*(Usunięte celowo: sformułowanie "przekroczyłeś próg o 1 zł, kosztowało Cię to X zł" — zastąpione porównaniem dwóch scenariuszy, zgodnie z korektą z ostatniej rundy audytu.)*

### Sekcja 3 — Dlaczego tak jest?

**FAKTY SYSTEMOWE:**
- [FAKT] Podstawa prawna: art. 81 ust. 2e oraz ust. 2f ustawy o świadczeniach opieki zdrowotnej finansowanych ze środków publicznych określają trzy progi przychodu (do 60 000 zł / 60 000–300 000 zł / powyżej 300 000 zł) i odpowiadające im podstawy wymiaru (60% / 100% / 180% przeciętnego wynagrodzenia).
- [FAKT] Mechanizm rozliczenia rocznego: jeśli suma miesięcznych składek zapłaconych w trakcie roku jest niższa niż składka wyliczona od ostatecznej rocznej podstawy (bo przychód przekroczył próg), przedsiębiorca dopłaca różnicę przy rozliczeniu rocznym. Jeśli zapłacił więcej — należy mu się zwrot. *(Mechanizm uregulowany w art. 81 ustawy o świadczeniach opieki zdrowotnej — bez podawania konkretnego numeru ustępu w treści widocznej dla użytkownika, zgodnie z ostatnią decyzją audytu.)*

**CO WIEMY (FAKT):**
> Przedsiębiorca może wybrać opłacanie stałej składki miesięcznej w oparciu o przychód z poprzedniego roku (tzw. metoda uproszczona, art. 81 ust. 2h), co pozwala zachować stałą kwotę raty w trakcie roku.

**CZEGO NIE WIEMY (LUKA ŹRÓDŁOWA):**
> W dostępnej dokumentacji legislacyjnej nie znaleźliśmy analizy wyjaśniającej, dlaczego wybrano sztywne progi kwotowe generujące skok obciążenia, zamiast mechanizmu ciągłego. Nie przypisujemy więc tej motywacji projektodawcy.

**ARGUMENT PRZECIW (RYNEK/EKSPERCI):**
> Sztywne progi tworzą tzw. efekt klifu — skok obciążenia jest nieproporcjonalny do wygenerowanego przychodu. *(Źródło: analizy branżowe, m.in. vatax.pl.)*
>
> *(Usunięte celowo: klauzula o "wstrzymywaniu fakturowania pod koniec roku" — niepotwierdzona źródłowo, patrz Część 4.)*

**PYTANIE DO CIEBIE:**
> Czy istnienie uproszczonej metody rozliczenia wystarczająco łagodzi problem efektu klifu — czy to za mało, skoro i tak trzeba w końcu rozliczyć się od realnego przychodu za cały rok?

**Link:** `[ ℹ️ Pokaż, jak to sprawdziliśmy ]` → rozwija źródła pierwotne, wzory, log Red Teamu (patrz Część 3).

### Sekcja 4 — Co można zrobić inaczej?

**Warianty (kolejność losowa przy renderowaniu):**
- **A:** Składka płynna proporcjonalna (wyższa stawka tylko od nadwyżki ponad próg).
- **B:** Strefa buforowa wokół progów (łagodne przejście ±2000 zł).
- **C:** Zachowanie progów z wymogiem automatycznych powiadomień ostrzegawczych (CEIDG/ZUS).

**Głosowanie:** przycisk "Zagłosuj" → wynik widoczny dopiero po oddaniu głosu.

**Wyniki (etykieta obowiązkowa):**
> Głosy użytkowników SENS (próba niereprezentatywna, n = [dynamiczne]):
> A — [%] / B — [%] / C — [%]

**Interakcja zwrotna:**
- `[ Nie przekonałeś mnie ]` → formularz z kategoriami: brakujące dane / zły argument / niezgoda z założeniem / niewiarygodne źródło / mam kontrargument / inny powód.
- `[ Zaproponuj własny wariant rozwiązania ]` → pole otwarte, trafia do "Laboratorium Państwa".
- Widoczna informacja SLA: *"Zgłoszenia audytujemy w każdy poniedziałek. Merytoryczne poprawki trafiają do publicznego rejestru zmian."*

### Sekcja 5 — Hipoteza ustrojowa

**Status:** DO DALSZEJ DEBATY // Powiązanie: Case #001

**Nagłówek:**
> HIPOTEZA: Ciągłość Obciążeń Publicznych

**Pytanie otwierające:**
> Czy w prawie podatkowym i składkowym powinien istnieć bezpiecznik uniemożliwiający gwałtowny wzrost obciążenia wskutek minimalnego przekroczenia progu?

**Proponowana zasada (wyraźnie oznaczona jako propozycja, nie ustalony fakt):**
> "Żadna danina publiczna ani składka nie powinna powodować skokowego wzrostu obciążenia w wyniku nominalnego wzrostu przychodu lub dochodu brutto."

**CTA:** `[ Wejdź do dyskusji nad tą zasadą → ]`

---

## CZĘŚĆ 3 — FINALNE DANE I MATEMATYKA

*(Pełna tabela — patrz `SENS-metodologia-0.3-i-audyt-matematyczny.md`, sekcja "Audyt Matematyczny". Poniżej wyciąg operacyjny do kalkulatora.)*

```
PRZECIĘTNE_WYNAGRODZENIE_2026 = 9228.64  // GUS, komunikat 22.01.2026

TIERS = [
  { próg: "I",   przychód_do: 60000,              podstawa_pct: 0.60, składka_mies: 498.35,  składka_rocz: 5980.20  },
  { próg: "II",  przychód_od: 60000.01, do: 300000, podstawa_pct: 1.00, składka_mies: 830.58,  składka_rocz: 9966.96  },
  { próg: "III", przychód_od: 300000.01,            podstawa_pct: 1.80, składka_mies: 1495.04, składka_rocz: 17940.48 }
]

RÓŻNICA_BRUTTO(próg_niższy, próg_wyższy) = składka_rocz(wyższy) - składka_rocz(niższy)
// I→II: 3986.76 zł | II→III: 7973.52 zł

ULGA(różnica_brutto, stawka_ryczałtu) = 0.5 * różnica_brutto * stawka_ryczałtu
WYNIK_NETTO = różnica_brutto - ULGA

STAWKI_RYCZAŁTU = [0.17, 0.15, 0.14, 0.12, 0.10, 0.085, 0.055, 0.03]
```

**Źródła danych wejściowych** — patrz `stawki_2025_2026.json` (plik istniejący w repo, węzeł `efekt_klifu_ryczalt_2026`) — silnik kalkulatora ma czytać stamtąd, nie z zahardkodowanych wartości w HTML, zgodnie z pierwotnym ustaleniem o jednym źródle prawdy.

---

## CZĘŚĆ 4 — ZABRONIONE ZMIANY (rzeczy złapane w audycie, nie do powtórzenia)

| ❌ Zakazane | ✅ Zamiast tego |
|---|---|
| "Zarobienie 1 zł kosztuje Cię 3 986,76 zł" | Porównanie dwóch scenariuszy + różnica (Sekcja 2) |
| Twierdzenie, że przedsiębiorcy "wstrzymują fakturowanie pod koniec roku" | Tylko: "skok obciążenia jest nieproporcjonalny do przychodu" |
| Przypisywanie ustawodawcy motywacji "ochrony prostoty księgowej" bez źródła | "Czego nie wiemy" — jawna luka źródłowa |
| Numer ustępu dla mechanizmu dopłaty/zwrotu (2i, 2j) w treści widocznej dla użytkownika | Opis słowny bez numeru ustępu |
| "Polacy uważają..." / ekstrapolacja wyników głosowania na populację | "Użytkownicy SENS, próba niereprezentatywna, n=..." |
| Fabrykowanie cytatu z realnego dokumentu (np. Druk 1532) | Cytat tylko z dosłownie zweryfikowanym fragmentem lub brak twierdzenia |
| Nazwanie hipotezy "Zasadą Konstytucji SENS" po jednym Case'ie | "Hipoteza ustrojowa — do dalszej debaty" |
| Skrócona stopka bez pełnego disclaimera | Pełny tekst: *"Narzędzie ma charakter edukacyjny i poglądowy — nie stanowi porady podatkowej ani prawnej. Nie uwzględnia innych ulg, składek społecznych ani indywidualnej sytuacji podatnika."* |

**`red_team_log` — wpis RT-001 (do umieszczenia w warstwie "Pokaż, jak to sprawdziliśmy"):**
> Wersja robocza przypisywała mechanizm rozliczenia rocznego do art. 81 ust. 2i. Po weryfikacji ustalono, że 2i dotyczy zwrotu (nadpłaty), a 2j dopłaty — właściwym kierunkiem dla Efektu Klifu byłoby 2j. Jednak wobec nowelizacji z 2025 r. wprowadzającej równoległe podustępy (2hd–2hl) z odrębną numeracją, zdecydowano nie podawać konkretnego numeru ustępu w treści publicznej — opisano mechanizm słownie. Zasada zastosowana: precyzja tylko wtedy, gdy jest pewna.

---

## CZĘŚĆ 5 — GATE 2 (nowość względem propozycji GPT)

*Kontrakt implementacyjny nie kończy procesu — kończy go weryfikacja, że został dotrzymany.*

Po otrzymaniu kodu od Gemini, przed pokazaniem go komukolwiek poza zespołem, wymagane jest:

1. **Diff merytoryczny** — porównanie każdego widocznego dla użytkownika zdania w kodzie z Częścią 2 tego dokumentu, zdanie po zdaniu.
2. **Sprawdzenie listy zakazanych zmian (Część 4)** — czy żadna z nich nie wróciła w nowej formie (to już się zdarzyło dwukrotnie w tej rozmowie — raz jako "Argument ZA #2", raz jako "A teraz druga strona").
3. **Wyszukanie znaczników `SENS-QUESTION`** — jeśli są, oznacza to, że Gemini trafił na lukę i prawidłowo się zatrzymał — wymaga to decyzji zespołu, nie ignorowania.
4. **Walidacja techniczna** — składnia, responsywność, działanie kalkulatora na rzeczywistych danych z `stawki_2025_2026.json`.

**Dopiero po przejściu GATE 2 Case #001 staje się "golden masterem"** — wzorcem do powielenia na Case #002 (Paliwo), #003 (Prąd), itd.
