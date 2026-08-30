# RAPID-RETRO-001
*Analiza retrospektywna RAPID-0001 do RAPID-0004. Zgodnie z poleceniem: wyłącznie diagnoza i rekomendacje — protokół v0.1 pozostaje niezmieniony do czasu osobnej decyzji.*

---

## Dane wejściowe (skrót czterech przypadków)

| # | Typ | Czas | Werdykt | Publikacja | Kluczowy problem |
|---|---|---|---|---|---|
| 0001 | Prawo/ustawa | ~12 min | 🟢 (wąski) | 🟠 | brak finalnego numeru artykułu; dwie wersje ustawy do odróżnienia |
| 0002 | Osąd wartościujący | ~90 sek | STOP (Krok 0) | 🔴 | brak — zadziałało zgodnie z projektem |
| 0003 | Statystyka/GUS | ~9 min | 🟢 | 🟠 | brak — jedyny przypadek w pełni "czysty" |
| 0004 | Statystyka/MF | ~16 min | 🔴 (warunkowo mocny) | 🔴 (blokada) | trzy sprzeczne rewizje źródła + brak stenogramu wypowiedzi |

---

## 1. Co zadziałało?

- **Krok 0 działa jako bezpiecznik, nie jako formalność.** W RAPID-0002 zatrzymał proces w 90 sekund, zanim doszło do próby ważenia argumentów politycznych. To jest najważniejszy pojedynczy wynik z czterech testów — dowód, że filtr wejściowy nie jest tylko checklistą na papierze.
- **Samo-red-team (Krok 7) wychwycił realne luki w dwóch z trzech przypadków, które przeszły dalej** (0001: brak numeru artykułu; 0004: brak stenogramu). W żadnym przypadku nie "wygładziłem" werdyktu, żeby ukryć niepewność.
- **Rozdzielenie werdyktu merytorycznego od statusu publikacji okazało się konieczne w praktyce, nie tylko w teorii** — RAPID-0004 pokazał to najdobitniej: mocny werdykt o liczbie, zablokowana publikacja o osobie, bo to naprawdę są dwie różne rzeczy z różnym progiem dowodowym.
- **Kontrargument (Krok 5) faktycznie zmieniał zakres werdyktu**, nie był rytuałem — w 0001 zawęził claim, w 0004 wzmocnił werdykt (pokazując, że jest odporny na wybór wersji danych).

## 2. Co nie zadziałało?

- **Żaden z czterech przypadków nie zmieścił się czysto w jednej kategorii testowej z macierzy.** RAPID-0004 miał być testem "błędna liczba", a okazał się testem "sprzeczne źródła". Kategorie z macierzy to dobre narzędzie projektowe, ale rzeczywiste twierdzenia mieszają typy częściej, niż zakładaliśmy.
- **Czas 5-10 minut sprawdził się tylko w 1 na 4 przypadków** (RAPID-0003). To nie jest duża próba, ale już podważa założenie, że to będzie modalny czas, nie wyjątek.
- **Nie miałem gdzie "zaparkować" przypadku, który wymaga więcej czasu niż RAPID, ale mniej niż pełny Case.** RAPID-0001 i RAPID-0004 zostały wciśnięte w format RAPID, mimo że oba przekroczyły założone okno — nie dlatego, że się ociągałem, tylko dlatego, że złożoność źródeł tego wymagała.

## 3. Ile faktycznie trwała weryfikacja?

Średnia (n=4, wyłączając 0002 jako inny typ zadania): (12+9+16)/3 ≈ **12,3 minuty** dla przypadków, które przeszły przez Krok 0. Mediana: 12 minut. **Żaden z trzech "pełnych" RAPIDów nie zmieścił się w dolnej połowie założonego okna (5-7 min)** — wszystkie były bliżej lub powyżej górnej granicy.

## 4. Gdzie traciliśmy czas?

Dwa różne źródła opóźnienia, wyraźnie odmienne:
- **Odróżnianie wersji/wydań tego samego dokumentu w czasie** (0001: dwie wersje ustawy; 0004: trzy rewizje statystyki MF) — to jest systematyczny, powtarzalny koszt, nie przypadek jednorazowy.
- **Docieranie do źródła pierwotnego, a nie wtórnego** (0003 był szybki właśnie dlatego, że GUS ma jeden, łatwo dostępny, regularnie publikowany biuletyn — nie trzeba było niczego odróżniać w czasie).

## 5. Jakie typy claimów nadają się do czystego RAPID (≤10 min)?

Na podstawie n=4 (ostrożnie, mała próba): twierdzenia oparte na **jednym, regularnie publikowanym źródle instytucjonalnym bez historii rewizji** (jak comiesięczny biuletyn GUS). To jest węższa kategoria niż pierwotnie zakładany "RAPID dla większości bieżących twierdzeń".

## 6. Jakie typy powinny automatycznie trafiać do rozszerzonej weryfikacji?

- Twierdzenia dotyczące **treści aktów prawnych, które były nowelizowane/procedowane w kilku wersjach** w krótkim czasie.
- Twierdzenia dotyczące **statystyk podlegających znanej historii rewizji metodologicznej** (VAT gap, ale też np. rewizje PKB, rewizje danych o zatrudnieniu).
- Każdy przypadek, w którym **pierwsze wyszukiwanie źródła zwraca więcej niż jedną liczbę dla tego samego okresu**.

## 7. Kiedy trzeba powiedzieć "nie rozstrzygamy"?

Cztery testy nie dały jeszcze przykładu prawdziwego 🟡 (RAPID-0002 to STOP na Kroku 0, kategoria inna niż 🟡 z powodu braku źródła). To jest luka w naszej próbie — nie wiemy jeszcze, jak w praktyce wygląda przypadek "źródło istnieje, ale jest niejednoznaczne nawet po dotarciu do niego". Rekomendacja: kolejny test celowo pod tę kategorię.

## 8. Jakie minimalne źródła muszą istnieć przed werdyktem?

RAPID-0004 pokazuje przypadek graniczny: **werdykt o fakcie (liczbie) był możliwy bez dotarcia do stenogramu, ale werdykt o wypowiedzi (przypisanie błędu konkretnej osobie) już nie.** To sugeruje, że protokół powinien osobno traktować "przedmiot sprawdzenia" (liczba/fakt w oderwaniu od kontekstu) i "podmiot wypowiedzi" (czy na pewno ta osoba to powiedziała, w tym kontekście, powołując się na to źródło) — obecnie oba są zlane w jeden Krok 3 (CLAIM).

## 9. Czy obecny HUMAN REVIEW jest wystarczający?

Częściowo. HUMAN REVIEW jako pojedyncza etykieta nie odróżnia **"sprawdź, czy ton jest odpowiedni przed publikacją"** (RAPID-0003, niska stawka) od **"sprawdź, czy w ogóle mamy prawo to opublikować, bo brakuje ogniwa dowodowego"** (RAPID-0004, wyższa stawka, inny rodzaj problemu). To są różne rodzaje przeglądu, wymagające różnej uwagi od Arka.

## 10. Czy trzeba zmienić protokół v0.1?

**Diagnoza wskazuje na tak, ale to nie jest moja decyzja — zgodnie z poleceniem, nie zmieniam nic teraz.** Trzy konkretne kandydatury do rozważenia w ewentualnym v0.2, żadna nie wdrożona:

1. **Trzeci poziom czasowy między RAPID a Case** (propozycja GPT: "RAPID+", 10-30 min, dla przypadków ze sprzecznymi/rewidowanymi źródłami) — dane z tej retrospektywy wspierają tę propozycję: 3 z 4 przypadków przekroczyły okno RAPID z jasnego, powtarzalnego powodu, nie z przypadku.
2. **Rozdzielenie w szablonie "faktu" od "wypowiedzi"** jako osobnych pól, nie jednego CLAIM-u — żeby uniknąć sytuacji z RAPID-0004, gdzie trzeba było ręcznie rozplątywać te dwie rzeczy post factum.
3. **Podtypy statusu HUMAN REVIEW** (np. "przegląd tonu" vs. "przegląd kompletności dowodu") — żeby Arek wiedział, czego dokładnie od niego oczekujemy przy każdym przeglądzie, zamiast jednej ogólnej etykiety.

**Rekomendacja końcowa:** cztery przypadki to za mało, żeby formalnie przechodzić na v0.2, ale wystarczająco dużo, żeby świadomie zaplanować kolejne testy pod kątem luk zidentyfikowanych w punktach 5-7 (brak przykładu czystego 🟡, brak przykładu "czystego RAPID" spoza jednej wąskiej kategorii źródłowej) — zanim podejmiemy decyzję o zmianie protokołu.
