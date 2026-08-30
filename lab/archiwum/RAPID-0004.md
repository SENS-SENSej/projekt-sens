# RAPID-0004 (twierdzenie liczbowe — okazało się testem "sprzecznych źródeł", nie prostym błędem)

## 1. INPUT
**Wypowiedź:** Twierdzenie, że 4,9% luki VAT (rok 2022) było "najniższym odnotowanym poziomem" tego wskaźnika.
**Autor:** Janusz Cichoń, Klub Parlamentarny Koalicja Obywatelska.
**Źródło wypowiedzi:** Wystąpienie sejmowe/senackie, zweryfikowane pierwotnie przez niezależny watchdog "Mądrości polityków".
**Data wypowiedzi:** 31 lipca 2026 r.
**Skąd w kolejce:** Samodzielnie znalezione przez Claude przy poszukiwaniu przykładu błędnego twierdzenia liczbowego (test #4 z macierzy GPT).

## 2. FILTR WEJŚCIOWY (KROK 0)
**Czy sprowadzalne do faktu/liczby?** TAK.
**Czy istnieje opublikowane źródło pierwotne?** TAK — ale (patrz niżej) **więcej niż jedno, wzajemnie niespójne**.
**Czy dotyczy osoby, nie twierdzenia?** NIE.
→ Wchodzi do RAPID CHECK.

## 3. CLAIM
**Badane twierdzenie:** 4,9% luki VAT (za 2022 r.) było najniższym odnotowanym poziomem tego wskaźnika w Polsce.
**Typ:** LICZBA / STATYSTYKA

## 4. DOWÓD — I PROBLEM, KTÓRY SIĘ UJAWNIŁ

Znalazłem **trzy różne, oficjalne zestawy danych** o luce VAT dla lat 2021-2022, pochodzące z różnych komunikatów Ministerstwa Finansów w różnym czasie:

| Publikacja MF | Rok 2021 | Rok 2022 |
|---|---|---|
| Komunikat MF, grudzień 2022 (Program Konwergencji – aktualizacja 2022) | 4,3% | — (jeszcze nie podano) |
| Szacunki MF z kwietnia 2023 r. (cytowane przez dorzeczy.pl, 2023) | 3,1% | 4,9% |
| "Biała Księga finansów publicznych 2016-2023" (MF, kwiecień 2024) | 2,6% | 7,3% |

**Ten sam wskaźnik za te same lata ma trzy różne wartości w trzech różnych oficjalnych publikacjach tego samego ministerstwa**, opublikowanych w różnym czasie. Nie jest to sprzeczność między MF a kimś z zewnątrz — to seria **rewizji metodologii i szacunków w czasie** (m.in. zmiana podejścia na system ESA/rachunki narodowe, o czym MF wprost informuje na gov.pl).

## 5. KONTRARGUMENT
**Najsilniejszy argument przeciwko prostemu werdyktowi:** Jeśli senator Cichoń opierał się na szacunkach z kwietnia 2023 r. (3,1% w 2021, 4,9% w 2022) — dokładnie tych, które zacytował watchdog weryfikujący jego wypowiedź — to **w obrębie tego konkretnego zestawu danych** jego twierdzenie "4,9% było najniższym poziomem" jest błędne, bo 3,1% (rok wcześniej) było niższe. Ale jeśli ktoś broniłby wypowiedzi, mógłby argumentować, że w międzyczasie MF samo zrewidowało te dane (Biała Księga 2024 podaje inne liczby) — więc "aktualny", najnowszy oficjalny szacunek MF dla 2021 r. to już nie 3,1%, tylko 2,6%, co nadal jest niższe niż 4,9%, więc **wniosek się nie zmienia niezależnie od tego, którą wersję danych MF przyjmiemy** — w każdej z nich rok 2021 miał niższą lukę VAT niż 2022.
**Czy zmienia wynik?** NIE — we wszystkich trzech wersjach MF, wartość dla 2022 r. (4,9% lub 7,3%, zależnie od wydania) jest **wyższa**, nie niższa, niż wartość dla 2021 r. Twierdzenie "4,9% to najniższy poziom" nie broni się w żadnej z trzech oficjalnych wersji.

## 6. WERDYKT (merytoryczny)
🔴 OBALONE
**Dlaczego:** Niezależnie od tego, którą z trzech oficjalnych rewizji danych Ministerstwa Finansów przyjmiemy, rok 2021 miał niższą lukę VAT niż rok 2022 (4,9%) — więc 4,9% nie mogło być "najniższym odnotowanym poziomem". To jest rzadki przypadek, w którym werdykt jest odporny na niespójność źródeł, bo wniosek jest identyczny we wszystkich trzech wersjach.
**Czy werdykt dotyczy WYŁĄCZNIE wąskiego faktu, nie całego sporu?** TAK. Nie oceniam całościowo polityki podatkowej żadnego rządu, tylko wąskie twierdzenie "to był rekord".

## 6a. STATUS PUBLIKACJI
🟠 HUMAN REVIEW — twierdzenie nazywa konkretnego, realnego polityka i orzeka, że jego wypowiedź była błędna. Zgodnie z protokołem, wymaga przeglądu przed publikacją niezależnie od pewności werdyktu merytorycznego.

## 6b. IMPACT / PRIORYTET
C — średni. Techniczna nieścisłość statystyczna, nie fundamentalny spór ekonomiczny.

## 7. SAMO-RED-TEAM PRZED PUBLIKACJĄ
- Czy werdykt nazywa realną osobę jako "kłamiącą"? NIE — mówi "twierdzenie było błędne", nie "polityk kłamał"; nie przypisuję intencji.
- Czy to samo powiedzielibyśmy o przeciwnej stronie sporu? TAK — dokładnie tę samą metodę zastosowałem do RAPID-0003 (sprawdzenie ministra rządu) i tutaj (sprawdzenie senator opozycji wobec obecnego rządu — a raczej krytyka poprzedniej ekipy, kontekst polityczny wymaga doprecyzowania przed publikacją).
- Czy ktoś mógłby wskazać źródło, którego nie sprawdziłem? MOŻLIWE — nie dotarłem do samego stenogramu wypowiedzi Cichonia (opieram się na cytacie z watchdogu), i nie sprawdziłem, na którą dokładnie publikację MF senator się powoływał. **To jest realne ograniczenie.**

## 8. PUBLIKACJA
**Gotowe do publikacji:** NIE — wymaga (a) dotarcia do oryginalnego stenogramu, żeby potwierdzić dokładny kontekst wypowiedzi, (b) przeglądu Arka.
**Jednozdaniowy werdykt dla Senseja (wersja robocza):** "Sprawdziliśmy: MF publikowało trzy różne szacunki luki VAT za te same lata, ale we wszystkich trzech rok 2022 wypada gorzej niż 2021 — więc 4,9% nie mogło być rekordowo niskim poziomem."
**Źródło:** gov.pl/web/finanse (komunikaty MF z grudnia 2022, kwietnia 2023 i Biała Księga 2024), dorzeczy.pl.
**Czas badania:** ok. 16 minut — najdłuższy dotychczasowy przypadek, z powodu konieczności rozplątania trzech niespójnych rewizji tej samej statystyki.

## WYNIK TESTU PROTOKOŁU
🔴 **Werdykt merytoryczny: OBALONE — i tym razem system faktycznie to powiedział, nie złagodził.** Ale ważniejszy wniosek jest inny: **to, co miało być prostym testem "błędna liczba", okazało się w praniu testem "sprzeczne źródła"** — realne twierdzenia rzadko układają się schludnie w jedną kategorię z macierzy testowej. To samo w sobie jest wartościową daną do kalibracji: kategorie testowe to przybliżenie, nie gwarancja, że rzeczywistość się w nie grzecznie wpasuje.
