# SENS RAPID CHECK — PROTOKÓŁ v0.1

*Zaprojektowany po krytyce pięciu słabości pierwotnej koncepcji (opóźnienie źródeł, ryzyko dot. nazwanych osób, brak kontroli doboru kolejki, napięcie szybkość/Red Team, brak granicy fakt/osąd). Każda z tych pięciu rzeczy ma tu swoje rozwiązanie — nie są to dodatki kosmetyczne, tylko warunki, bez których system nie powinien ruszyć.*

---

## KROK 0 — Filtr wejściowy (NOWY, przed jakimkolwiek RAPID CHECK)

Zanim jakiekolwiek twierdzenie wejdzie do kolejki, przechodzi przez trzy pytania. To jest bezpiecznik przeciw punktowi 5 krytyki.

```
1. Czy twierdzenie da się sprowadzić do faktu/liczby/tekstu/daty/cytatu?
   NIE → nie wchodzi do RAPID. To jest osąd wartościujący (np. "słuszne",
   "sprawiedliwe", "uzasadnione") — RAPID go nie rozstrzyga. Można co najwyżej
   rozbić na sprawdzalne fakty składowe i jawnie odmówić oceny całości.

2. Czy istnieje już opublikowane źródło pierwotne (nie zapowiedź, nie plotka)?
   NIE → automatyczny werdykt: 🟡 NIE ROZSTRZYGNIĘTE (ŹRÓDŁO JESZCZE NIE
   ISTNIEJE), z jawną datą "sprawdź ponownie po [przewidywana data publikacji
   dokumentu]". To NIE jest porażka systemu — to jest uczciwa odpowiedź na
   fizyczne ograniczenie (dokumenty nie powstają szybciej niż w 10 minut).

3. Czy dotyczy wprost, po imieniu i nazwisku, motywacji lub charakteru
   konkretnej osoby (nie jej wypowiedzi, tylko jej samej)?
   TAK → nie wchodzi do RAPID. Sprawdzamy TWIERDZENIA, nie osoby.
```

Dopiero twierdzenie, które przejdzie przez trzy "NIE" w pytaniu 1 i 3 oraz "TAK" w pytaniu 2, wchodzi do właściwego RAPID CHECK.

---

## KROK 1 — Log doboru kolejki (NOWY, rozwiązuje punkt 3 krytyki)

Każde RAPID, niezależnie od wyniku, zapisuje się w `lab/rapid/RAPID-QUEUE.md` z polem:

```
Skąd trafiło do kolejki: [zgłoszenie użytkownika / media / Sensej zauważył / inne]
Kto zaproponował sprawdzenie: [Arek / Claude / GPT / Gemini / społeczność]
```

**Raz w miesiącu** — nie po każdym RAPID, żeby nie zabijać tempa — ktoś (Arek albo GPT jako Red Team) robi jeden przegląd: czy sprawdzane twierdzenia skupiają się wokół jednej strony sporu politycznego. To nie jest kontrola pojedynczego werdyktu — to kontrola **wzorca w czasie**, jedyny realny sposób złapania stronniczości, która nie wynika ze złej metodologii, tylko ze złego doboru tematów.

---

## KROK 2 — RAPID CHECK właściwy

Format z brief'u zostaje w większości bez zmian — jest dobry. Dodane pola oznaczone **(NOWE)**.

```markdown
# RAPID-[NUMER]

## 1. INPUT
**Wypowiedź:** "[dokładny cytat]"
**Autor:** [...]
**Źródło wypowiedzi:** [...]
**Data wypowiedzi:** [...]
**(NOWE) Skąd w kolejce:** [zgłoszenie / media / Sensej / inne — kto zaproponował]

## 2. FILTR WEJŚCIOWY (KROK 0)
**(NOWE) Czy sprowadzalne do faktu/liczby/tekstu?** [TAK/NIE — jeśli NIE, STOP tutaj]
**(NOWE) Czy istnieje opublikowane źródło pierwotne?** [TAK/NIE — jeśli NIE, STOP, werdykt automatyczny 🟡]
**(NOWE) Czy dotyczy osoby, nie twierdzenia?** [TAK/NIE — jeśli TAK, STOP tutaj]

## 3. CLAIM
**Badane twierdzenie (jedno, wąskie):** [...]
**Typ:** [FAKT / PRAWO / LICZBA / PRZYCZYNOWOŚĆ / INTENCJA]
**(NOWE) Jeśli typ = PRZYCZYNOWOŚĆ lub INTENCJA:** rozbij na twierdzenie
  faktyczne + oddzielny wniosek przyczynowy. Werdykt dotyczy TYLKO faktu.

## 4. DOWÓD
**Źródło pierwotne:** [...] **Data źródła:** [...] **Okres obowiązywania:** [...]
**Fragment rozstrzygający:** [...]

## 5. KONTRARGUMENT
**Najsilniejszy argument przeciwko werdyktowi:** [...]
**Czy zmienia wynik?** [TAK/NIE]

## 6. WERDYKT (merytoryczny)
🟢 POTWIERDZONE / 🔴 OBALONE / 🟡 NIE ROZSTRZYGNIĘTE
**Dlaczego:** [...]
**Czy werdykt dotyczy WYŁĄCZNIE wąskiego faktu z pkt 3, nie całego sporu?**
  [potwierdź jawnie — to jest test na "nie orzekamy więcej niż wynika ze źródła"]

## 6a. STATUS PUBLIKACJI (NOWE, osobne od werdyktu — poprawka GPT)
⚪ DRAFT / 🟠 HUMAN REVIEW / 🟢 PUBLISHABLE / 🔴 BLOCKED

Zasada: werdykt merytoryczny i decyzja "czy można to wrzucić na X" to dwie
różne rzeczy. 🔴 OBALONE nie oznacza automatycznie 🟢 PUBLISHABLE — jeśli
twierdzenie nazywa realną osobę, status startuje jako 🟠 HUMAN REVIEW
niezależnie od tego, jak pewny jest werdykt merytoryczny.

## 6b. IMPACT / PRIORYTET (NOWE — poprawka GPT)
A — bardzo wysoki / B — wysoki / C — średni / D — niski
**Uzasadnienie:** [dlaczego taki priorytet — np. "dotyczy decyzji wpływającej
na miliony gospodarstw domowych" vs "pomyłka w dacie bez dalszych skutków"]

## 7. SAMO-RED-TEAM PRZED PUBLIKACJĄ (NOWE — rozwiązuje punkt 4 krytyki)
Zanim oznaczysz "gotowe do publikacji: TAK", odpowiedz sobie:
- Czy werdykt nazywa realną osobę jako "kłamiącą", czy tylko ocenia twierdzenie? [musi być drugie]
- Czy dałoby się to samo powiedzieć o twierdzeniu z przeciwnej strony sporu,
  gdyby było tak samo błędne? [musi być TAK — test spójności]
- Czy ktoś, kto się z werdyktem nie zgadza, mógłby wskazać źródło, którego nie sprawdziłem? [jeśli tak — nie publikuj, dokończ research]

## 8. PUBLIKACJA
**Gotowe do publikacji:** [TAK / NIE]
**Jednozdaniowy werdykt dla Senseja:** [...]
**Źródło:** [...]
**Czas badania:** [...] min
```

---

## Workflow: Claude → SENS LAB → Sensej

```
Zgłoszenie/twierdzenie
        ↓
   KROK 0 (filtr wejściowy) — Claude, ~1 min
        ↓
   [odrzucone / 🟡 automatyczne / wchodzi dalej]
        ↓
   KROK 2 (RAPID CHECK właściwy) — Claude, 5-10 min
        ↓
   KROK 7 (samo-red-team) — Claude, w ramach tych samych 10 min
        ↓
   "gotowe do publikacji: TAK" + werdykt nazywa realną osobę?
        ↓ TAK                              ↓ NIE
   krótki przegląd Arka                Sensej publikuje od razu
   przed publikacją (2 min)
        ↓
   Sensej publikuje
```

To rozwiązuje napięcie z punktu 4: **nie każde RAPID przechodzi pełny wielomodelowy Red Team** (zabiłoby to szybkość), ale każde RAPID przechodzi samo-red-team w ramach tych samych 10 minut, a te, które nazywają realną osobę — dodatkowo krótki przegląd człowieka (nie kolejnego modelu) przed publikacją. To jest proporcjonalne do ryzyka, nie jednolite dla wszystkiego.

---

## Kiedy zatrzymać i oznaczyć UNRESOLVED

- Źródło pierwotne nie istnieje jeszcze publicznie (patrz Krok 0, pytanie 2).
- Po ok. 10 minutach szukania nie znaleziono rozstrzygającego fragmentu.
- Twierdzenie okazuje się w trakcie analizy być typu PRZYCZYNOWOŚĆ/INTENCJA bez możliwości rozbicia na czysty fakt.
- Dwa źródła pierwotne wprost sobie zaprzeczają, a nie ma sposobu ustalić, które jest aktualne/nadrzędne.

W każdym z tych przypadków: 🟡, z jawnym powodem — nigdy cichy brak publikacji.

---

## Struktura plików (przyjęta z brief'u, bez zmian — jest dobra)

```
lab/
├── claims/
├── sources/
├── questions/
├── templates/
│   ├── template-claim.md
│   ├── template-source.md
│   └── template-rapid-check.md   ← wersja z Kroku 2 powyżej
└── rapid/
    ├── README.md
    ├── RAPID-PROTOCOL.md          ← ten dokument
    ├── RAPID-QUEUE.md             ← log doboru kolejki (Krok 1)
    └── results/
        └── RAPID-0001.md, RAPID-0002.md, ...
```

---

## Pierwszy test — macierz testowa (10 przypadków, zgodnie z propozycją GPT)

Zanim zbudujemy cokolwiek więcej: 10-20 realnych RAPID CHECKÓW, ale **nie przypadkowych** — dobranych tak, żeby sprawdzić każdą ścieżkę protokołu:

| # | Typ przypadku | Oczekiwany wynik |
|---|---|---|
| 1 | Prosty fakt liczbowy z gotowym źródłem | 🟢 |
| 2 | Fałszywa liczba zestawiona ze źródłem | 🔴 |
| 3 | Treść konkretnego przepisu ustawy | 🟢/🔴 |
| 4 | Cytat polityka zestawiony ze stenogramem | 🟢/🔴 |
| 5 | Twierdzenie o czymś, co jeszcze nie ma źródła pierwotnego | 🟡 (automatyczne, Krok 0) |
| 6 | Czysty osąd wartościujący ("słuszne", "sprawiedliwe") | STOP na Kroku 0 |
| 7 | Twierdzenie o intencji polityka | STOP / rozbicie na fakt |
| 8 | Twierdzenie przyczynowe ("X spowodowało Y") | rozbicie na fakt + wniosek osobno |
| 9 | Twierdzenie o świeżym wydarzeniu | 🟢/🔴 (test realnego tempa) |
| 10 | Dwa źródła wzajemnie sprzeczne | 🟡 z uzasadnieniem |

Dopiero po przejściu tej dziesiątki oceniamy: ile % realnych, sensownych twierdzeń da się rzetelnie sklasyfikować w 5-10 minut. Wynik 80% i 40% są oba wartościowe — chodzi o poznanie granicy, nie o potwierdzenie założenia.
