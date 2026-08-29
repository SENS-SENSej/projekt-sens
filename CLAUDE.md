# SENS — Brief startowy dla Claude Code

Ten plik to skrót kontekstu z długiej rozmowy roboczej nad projektem SENS. Przeczytaj go w całości zanim cokolwiek zmienisz w repo.

## Co to jest SENS

Ruch obywatelsko-technokratyczny + platforma civic tech. Misja: obniżyć polaryzację polityczną, pokazując ludziom twarde, policzalne skutki konkretnych przepisów — bez opowiadania im, co mają myśleć. Model: SPRAWDŹ → ZROZUM → ZAGŁOSUJ → ZAPROPONUJ. Docelowo: media (Sensej) → narzędzia → społeczność → wspólne zasady → Konstytucja SENS. Nie budujemy partii politycznej na start.

**Ton:** chłodny, matematyczny, "Dobra. Sprawdźmy." Zero żargonu IT w warstwie widocznej dla użytkownika (dawne "SENS OS" zostało odrzucone jako zbyt technokratyczne). Grafit/antracyt + elektryczny błękit/emerald, font mono tylko dla liczb.

## Struktura repo (stan wiedzy z rozmowy)

- `index.html` — strona główna (hero, 3 filary: LICZYMY/AUDYTUJEMY/PROJEKTUJEMY, karta modułu Case #001, sekcja Laboratorium Państwa, sekcja Konstytucja SENS, transparentność/GitHub link)
- `klif.html` — SENS Case #001: Efekt Klifu (ryczałt 2026) — **golden master, status: zamknięty po GATE 2, czeka na GATE 3 (testy na żywych ludziach)**
- `stawki_2025_2026.json` — jedyne źródło prawdy dla stawek/progów/wzorów. Kalkulatory MAJĄ czytać stąd, nie z zahardkodowanych wartości w HTML.
- `SENS_CASE_001_IMPLEMENTATION_SPEC.md` — kontrakt wdrożeniowy dla Case #001 (wireframe, dane, lista zakazanych zmian)
- Dokumenty metodologii (v0.1 → v0.3) — historia decyzji, nie musisz ich czytać w całości, ale zasady poniżej są ich destylatem.

## TWARDE ZASADY — obowiązują przy KAŻDEJ zmianie w repo

1. **Źródło każdego faktu.** Żadna liczba, data, artykuł ustawy — bez linku, daty i dokładnego miejsca w źródle. Jeśli nie możesz podać konkretnego linku — nie wpisuj tego jako fakt.
2. **Argumenty tylko od realnych, nazwanych aktorów.** Nigdy nie wymyślaj, "co ktoś by powiedział". Brak źródła = jawna luka ("Czego nie wiemy"), nie fabrykacja.
3. **Red Team przed publikacją.** Każda nowa treść merytoryczna wymaga niezależnej weryfikacji źródeł, nie tylko "brzmi sensownie".
4. **Reprezentatywność głosowań.** Zawsze "użytkownicy SENS, próba niereprezentatywna, n=X". Nigdy "Polacy uważają".
5. **Wynik może zaprzeczać naszej tezie — publikujemy i tak.**
6. **SLA dla zgłoszeń użytkowników** ("Nie przekonałeś mnie") — przegląd tygodniowy, jawny próg eskalacji.
7. **Jeśli źródło potwierdza A, nie wolno oznaczyć jako zweryfikowane A+B.** Realny dokument użyty jako kotwica dla niepotwierdzonej tezy = fabrykacja w przebraniu, nawet jeśli numer dokumentu jest prawdziwy.

**Absolutny zakaz:** dodawania własnych argumentów/źródeł/faktów przy edycji Case'ów, "logicznego uzupełniania" braków, tworzenia nowych podstaw prawnych, zmiany metodologii bez pytania. **Jeśli czegoś brakuje: zostaw `<!-- SENS-QUESTION: [opis] -->` i zatrzymaj się — nie zgaduj.**

## Rzeczy złapane w audycie — NIE POWTARZAJ ICH

| ❌ | Dlaczego to problem |
|---|---|
| "Zarobienie 1 zł kosztuje Cię X zł" | Za szerokie uproszczenie — używaj porównania dwóch scenariuszy |
| Przypisywanie ustawodawcy motywacji bez źródła (np. "chciał chronić prostotę księgowości") | Dwa razy fabrykowane w tej rozmowie, raz z realnym numerem druku sejmowego jako fałszywą kotwicą |
| Konkretny numer ustępu ustawy bez potwierdzenia w tekście pierwotnym | Kilka razy pomylone (np. art. 81 ust. 2i vs 2j) — w razie wątpliwości opisuj mechanizm słownie, bez numeru |
| Dane z poprzedniego roku podane jako aktualne (stawki 2025 jako "2026") | Realny błąd w Case #002 (opłata mocowa, OZE) — zawsze sprawdzaj okres obowiązywania w źródle |
| Liczby z artykułów/blogów jako "zweryfikowane" | Dopuszczalne tylko jako source niższej pewności, jawnie oznaczone — pierwotne źródło (ustawa/URE/ZUS/GUS) ma pierwszeństwo |
| Wybieranie górnej granicy przedziału bez uzasadnienia (żeby liczba brzmiała mocniej) | Zdarzyło się przy stawkach dystrybucji energii — zawsze podawaj metodologię wyboru punktu w zakresie |

## Status Case'ów (na dziś)

- **Case #001 (Efekt Klifu):** GATE 1 ✅, GATE 2 ✅ (kod zgodny ze spec). **GATE 3 w toku** — czekamy na feedback od realnych testerów (protokół: zero kontekstu, 4 pytania w 5s/20s/40s/60s). **Nie modyfikuj `klif.html` merytorycznie, dopóki nie wrócą wyniki testów**, chyba że Arek wyraźnie o to poprosi.
- **Case #002 (Prąd):** **Tryb research-only.** Nie buduj UX, CLAIM-u ani posta. Pierwotna przesłanka ("cena zamrożona 500 zł/MWh") była nieaktualna — mrożenie cen skończyło się 31.12.2025. Aktualna, potwierdzona rama: cena energii w 2026 r. spadła (495,16 zł/MWh), ale rachunek rośnie z powodu droższej dystrybucji. Trwa budowa `SOURCE-000X` dla taryf G11 pięciu głównych OSD — każda liczba musi być przypięta do konkretnej decyzji URE/tabeli taryfowej, nie do agregatora.

## Workflow wielomodelowy (kontekst, nie do zmiany bez pytania Arka)

Podział ról: Claude = researcher/źródła + Red Team, GPT = drugi audyt niezależny, Gemini = builder/UX/kod po zatwierdzeniu źródeł. Żaden pojedynczy model nie certyfikuje sam siebie. Jeśli pracujesz jako Claude Code w tym repo, trzymaj się roli odpowiedniej do zadania, które dostałeś od Arka — a jeśli zadanie miesza szukanie źródeł z pisaniem kodu, rozdziel to na etapy zamiast robić oba naraz.
