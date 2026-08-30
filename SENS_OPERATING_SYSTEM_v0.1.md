# SENS OPERATING SYSTEM v0.1
*Jeden, kompletny standard operacyjny. Koniec fazy eksperymentalnej — ten dokument jest przeznaczony do wdrożenia, nie do kolejnej rundy poprawek. Wersja finalna do audytu GO/NO-GO, nie do dalszego "dłubania".*

---

## 0. Cel tego dokumentu

Zastępuje wszystkie wcześniejsze dokumenty robocze (Metodologia v0.1-v0.3, RAPID Protokół v0.1, pięć RAPID CHECKów, RETRO-001) jednym, praktycznym standardem. Jeśli coś tu jest sprzeczne z wcześniejszymi dokumentami — ten dokument wygrywa. Wcześniejsze dokumenty zostają w repo jako historia decyzji (`lab/archiwum/`), nie jako obowiązujący proces.

---

## 1. Architektura SENS

```
SENS
│
├── 1. LAB (zaplecze dowodowe — nigdy samo w sobie nie jest produktem)
│   ├── sources/      — SOURCE-XXXX
│   ├── claims/        — CLAIM-XXXX
│   ├── cases/          — pełne Case'y (Efekt Klifu = Case #001)
│   ├── rapid/           — RAPID-XXXX + queue
│   └── archiwum/          — zamrożone wersje robocze metodologii
│
├── 2. SENSEJ (warstwa publiczna — jedyne miejsce, gdzie SENS mówi do ludzi)
│   ├── X / Facebook / Shorts
│   └── odpowiedzi na zgłoszenia społeczności
│
├── 3. NARZĘDZIA (produkty samodzielne)
│   ├── klif.html (Case #001)
│   └── przyszłe kalkulatory/Case'y
│
└── 4. COMMUNITY
    ├── zgłoszenia tematów ("Podeślij Sensejowi")
    └── "Nie przekonałeś mnie" / propozycje wariantów
```

Zasada podstawowa: LAB produkuje dowód. Sensej publikuje wynik. Nigdy odwrotnie.

---

## 2. Pięć Zasad Fundamentalnych (niezmienne, nie podlegają kolejnym rundom audytu)

1. **Źródło każdego faktu.** Link, data, dokładne miejsce. Bez tego — nie wchodzi jako FAKT.
2. **Argumenty tylko od realnych, nazwanych aktorów.** Brak źródła = jawna luka, nie fabrykacja.
3. **Red Team przed publikacją wysokiego ryzyka** (patrz §6 — kiedy dokładnie wymagany).
4. **Reprezentatywność.** "Użytkownicy SENS, n=X", nigdy "Polacy uważają".
5. **Wynik może zaprzeczać naszej tezie — publikujemy i tak.**

Dodatkowo, Zasada 7 (z incydentu Argument ZA #2): jeśli źródło potwierdza A, nie wolno oznaczyć jako zweryfikowane A+B. Realny dokument użyty jako kotwica dla niepotwierdzonej tezy jest fabrykacją w przebraniu.

---

## 3. Kontrakty danych LAB (formaty plików)

### SOURCE-XXXX
```
Identyfikator, pełna nazwa dokumentu, instytucja, data wydania,
data weryfikacji, bezpośredni URL, dokładny fragment/miejsce,
czego dowodzi, czego NIE dowodzi, powiązane CLAIM/CASE/RAPID.
```

### CLAIM-XXXX
```
Twierdzenie wyjściowe → atomy dowodowe (ATOM-A, ATOM-B...) →
każdy atom: źródło + status (VERIFIED/UNPROVEN) → werdykt zbiorczy
(np. "VERIFIED CORE" jeśli nie wszystkie atomy potwierdzone).
```

### RAPID-XXXX
```
Input (wypowiedź, autor, źródło, data) → Filtr wejściowy (Krok 0) →
Claim (rozbity na atomy, jeśli mieszany typ) → Dowód → Kontrargument →
Werdykt merytoryczny (🟢/🔴/🟡) → Status publikacji (⚪/🟠/🟢/🔴,
NIEZALEŻNY od werdyktu) → Impact (A-D) → Samo-red-team → Publikacja.
```

### CASE (pełny, jak Case #001)
14-modułowy schemat danych z `SENS_CASE_001_IMPLEMENTATION_SPEC.md` — bez zmian, ten format jest już zwalidowany przez GATE 1/2/3.

---

## 4. Krok 0 — Filtr wejściowy (obowiązuje dla RAPID i dla Case'ów)

```
1. Czy sprowadzalne do faktu/liczby/tekstu/daty/cytatu?
   NIE → to jest osąd wartościujący. Nie wchodzi. Można rozbić na
   sprawdzalne atomy składowe (patrz §5), ale całości się nie ocenia.

2. Czy istnieje już opublikowane źródło pierwotne?
   NIE → automatyczne 🟡, z datą "sprawdź ponownie po [data]".

3. Czy dotyczy wprost charakteru/motywacji konkretnej osoby
   (nie jej wypowiedzi)?
   TAK → nie wchodzi. Sprawdzamy twierdzenia, nie ludzi.
   (Rozróżnienie: "ustawa X wprowadza kompetencję Y" — to FAKT, wchodzi,
   nawet jeśli podane emocjonalnym tonem. "Polityk chciał przez to zaszkodzić
   grupie Z" — to już jest o motywacji, nie wchodzi. Granica leży
   między skutkiem/treścią decyzji a przypisywaniem intencji.)
```

---

## 5. Atomizacja twierdzeń mieszanych

Twierdzenie polityczne rzadko jest jednym atomem. Standardowy rozkład:

- **ATOM FAKT** — sprawdzalne wprost (liczba, tekst, data).
- **ATOM PRZYCZYNOWOŚĆ/INTENCJA** — rozbić na fakt + wniosek; werdykt dotyczy tylko faktu, wniosek zostaje osobno oznaczony jako niesprawdzony, jeśli nie ma na niego bezpośredniego dowodu.
- **ATOM OSĄD** — nie wchodzi w ogóle (§4, pkt 1).

Realny przykład z testów: "wzrost inflacji spowodowany głównie VAT" → ATOM-A (fakt: inflacja wzrosła z 2,5% do 3,0%, 🟢) + ATOM-B (przyczynowość: "głównie VAT", 🟡 — bo GUS nie publikuje oficjalnej dekompozycji, a analitycy podają rozbieżne, nieporównywalne szacunki). Werdykt na poziomie całego twierdzenia = werdykt najsłabszego atomu, jeśli atomy są prezentowane łącznie w jednym materiale.

---

## 6. Poziomy czasowe — RAPID / RAPID+ / CASE

Z pięciu wykonanych testów: tylko 1 z 5 (statystyka z jednego źródła instytucjonalnego, GUS) zmieściła się w 5-10 min. Pozostałe wymagały 12-16 min z jasnych, powtarzalnych powodów (odróżnianie wersji dokumentów w czasie, rozplątywanie rewizji danych). Wniosek wdrożony na stałe:

| Poziom | Czas | Kiedy |
|---|---|---|
| RAPID | ≤10 min (**wskaźnik orientacyjny — przekroczenie nie jest błędem procesu**, tylko sygnałem do rozważenia RAPID+) | jedno źródło instytucjonalne, brak historii rewizji, prosty fakt/cytat/przepis |
| RAPID+ | 10-30 min | wersje aktu prawnego do odróżnienia, rewidowane statystyki, kilka źródeł do uzgodnienia |
| CASE | godziny/dni | wymaga GATE 1/2/3, kalkulatora, głosowania, Hipotezy Ustrojowej |

Nie ma kategorii pośredniej między RAPID+ a Case. Jeśli coś przekracza 30 minut i nadal nie ma werdyktu — to jest kandydat na Case, nie na dłuższy RAPID.

---

## 7. Werdykt merytoryczny vs. Status publikacji (rozdzielone na stałe)

To jest jedna z dwóch najważniejszych korekt strukturalnych z fazy testowej — nie podlega dalszej dyskusji.

```
WERDYKT: 🟢 POTWIERDZONE / 🔴 OBALONE / 🟡 NIE ROZSTRZYGNIĘTE
PUBLIKACJA: ⚪ DRAFT / 🟠 HUMAN REVIEW / 🟢 PUBLISHABLE / 🔴 BLOCKED
```

Zasada: werdykt o FAKCIE i werdykt o WYPOWIEDZI KONKRETNEJ OSOBY to dwa różne progi dowodowe. Można mieć mocny werdykt o liczbie (🔴 OBALONE) i jednocześnie zablokowaną publikację, jeśli brakuje potwierdzenia, że dana osoba rzeczywiście powiedziała to w tym kontekście, powołując się na to źródło (przypadek z RAPID-0004).

HUMAN REVIEW ma dwa podtypy, nie jeden ogólny:
- Przegląd tonu — treść jest pewna, sprawdzamy tylko, czy sformułowanie jest odpowiednie.
- Przegląd kompletności dowodu — brakuje ogniwa łańcucha (np. stenogramu), wyższa stawka.

---

## 8. Impact / Priorytet

```
A — bardzo wysoki / B — wysoki / C — średni / D — niski
```

Ustala kolejność pracy przy więcej niż jednym zgłoszeniu naraz. Nie wpływa na rygor dowodowy — nawet priorytet D przechodzi pełny Krok 0.

---

## 9. Wybór tematów — ochrona przed stronniczością zbiorczą

Każdy RAPID/Case zapisuje w `RAPID-QUEUE.md`: skąd trafiło do kolejki, kto zaproponował. Raz w miesiącu (nie częściej — nie blokuje tempa) przegląd wzorca: czy sprawdzane twierdzenia skupiają się wokół jednej strony sporu politycznego. To jest kontrola trendu w czasie, nie pojedynczej decyzji.

Docelowo (nie teraz): automatyczna ekstrakcja z X/FB/YouTube do kolejki. Kiedy powstanie — comiesięczny audyt musi objąć też to, co algorytm pomija, nie tylko to, co ludzie zgłaszają ręcznie.

---

## 10. Obsługa osób publicznych — zasady stałe

- Werdykt ocenia twierdzenie, nigdy nie nazywa nikogo "kłamiącym" — używamy "twierdzenie jest błędne/niepotwierdzone", nie orzekamy o intencji.
- Test spójności obowiązkowy: czy to samo powiedzielibyśmy o twierdzeniu z przeciwnej strony sporu, gdyby było tak samo błędne? Jeśli nie — nie publikujemy.
- Każde RAPID/Case nazywające realną osobę = automatycznie 🟠 HUMAN REVIEW, niezależnie od pewności werdyktu.
- Nigdy nie publikujemy oceny sporu, który sprowadza się do osądu wartościującego (weto słuszne/niesłuszne, ustawa dobra/zła) — tylko atomy faktyczne składowe.

---

## 11. Materiał dla Senseja — format i ton

Z każdego RAPID/Case: jedno zdanie werdyktu, nie esej. Wzór:

> "Sprawdziliśmy: [twierdzenie]. [Wynik]. Źródło: [instytucja]."

Bez "obie strony mają trochę racji" jako domyślnej ucieczki. Bez eseju tam, gdzie wystarczy zdanie. Jeśli werdykt to 🟡 — mówimy to wprost i z dumą, nie jako porażkę: "Sprawdziliśmy X. Źródła się nie zgadzają / dowód nie istnieje jeszcze publicznie. Nie rozstrzygamy." To jest część marki, nie jej słabość.

---

## 12. Eskalacja

```
RAPID → jeśli przekracza 10 min z jasnego powodu → RAPID+
RAPID+ → jeśli przekracza 30 min lub wymaga kalkulatora/głosowania → CASE
CASE → pełny GATE 1 (metodologia+źródła) → GATE 2 (zgodność kodu ze spec)
     → GATE 3 (test na realnych użytkownikach)
```

Żaden poziom nie jest pomijany w górę. Case zawsze przechodzi przez GATE 1/2/3 w całości, niezależnie od tego, czy "wygląda na prosty".

---

## 13. Archiwizacja i samokorekta

`red_team_log` przy każdym Case/RAPID z realną korektą w toku pracy — nie ukrywamy, że coś zostało poprawione, pokazujemy to jako dowód działania procesu (przykład: RT-001 przy Case #001, korekta cytowania mechanizmu rozliczenia rocznego).

Od teraz: nowy problem znaleziony podczas realnej pracy = wpis `ISSUE-XXX` w `lab/issues.md`, nie automatyczna przebudowa protokołu. Protokół zmienia się dopiero, gdy ten sam problem powtórzy się co najmniej trzykrotnie w realnej pracy (nie w testach zaprojektowanych pod ten problem). To jest twarda bariera przeciw nieskończonej pętli projektowania.

---

## 14. Co NIE wchodzi w życie teraz (świadomie odłożone, nie zapomniane)

- Automatyczny SENS INBOX / scraper X — dopiero po udowodnieniu procesu ręcznie.
- RAPID v0.2 jako formalna wersja — nie ma potrzeby numerować kolejnej wersji, dopóki §13 nie wymusi zmiany.
- Case #002 (Prąd) w pełnej formie — zostaje w trybie research-only do czasu, aż ktoś ręcznie zdecyduje o przejściu do GATE 1.
- Kolejne testy walidacyjne RAPID (006, 007...) — pięć wykonanych testów pokryło: fakt prosty, osąd odrzucony, statystyka czysta, sprzeczne źródła, przyczynowość mieszana. To wystarczająca próba do startu.

---

## STATUS: GOTOWE DO AUDYTU GO/NO-GO

Ten dokument jest kompletny w zakresie wymaganym do codziennego działania. Przekazać do jednego, kompleksowego przeglądu (Gemini lub GPT) z pytaniem o błędy krytyczne/istotne/drobne i werdykt GO/NO-GO — bez dalszego projektowania równoległego.
