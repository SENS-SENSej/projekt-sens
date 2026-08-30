# RAPID-0003 (prawdziwe, aktualne twierdzenie — test tempa "Sensej w czasie rzeczywistym")

## 1. INPUT
**Wypowiedź:** "Prognozowana stopa bezrobocia na koniec 2027 r. ma wynieść 6,0 proc." — Minister finansów i gospodarki Andrzej Domański, przy okazji odniósł się też do stanu bieżącego: "Według danych GUS wskaźnik ten na koniec lipca wyniósł 5,8 proc."
**Autor:** Andrzej Domański, minister finansów i gospodarki.
**Źródło wypowiedzi:** Konferencja po posiedzeniu Rady Ministrów ws. projektu budżetu na 2027 r., relacja PolsatNews.pl.
**Data wypowiedzi:** 28 sierpnia 2026 r. (publikacja artykułu; wypowiedź "2 dni temu" względem daty dzisiejszej, 30 sierpnia 2026 r.)
**Skąd w kolejce:** Samodzielnie znalezione przez Claude na polecenie testowe (RAPID-0003, wymóg: świeże, prawdziwe, nie z tematu Zondacrypto).

## 2. FILTR WEJŚCIOWY (KROK 0)
**Czy sprowadzalne do faktu/liczby?** TAK — konkretna liczba (5,8%) przypisana konkretnemu okresowi (koniec lipca 2026) i konkretnemu źródłu (GUS).
**Czy istnieje opublikowane źródło pierwotne?** TAK — GUS publikuje comiesięczny biuletyn "Sytuacja społeczno-gospodarcza kraju".
**Czy dotyczy osoby, nie twierdzenia?** NIE.
→ **Wchodzi do RAPID CHECK.**

## 3. CLAIM
**Badane twierdzenie (jedno, wąskie):** Stopa bezrobocia rejestrowanego w Polsce na koniec lipca 2026 r. wyniosła 5,8%, zgodnie z danymi GUS.
**Typ:** LICZBA / STATYSTYKA

## 4. DOWÓD
**Źródło pierwotne:** Główny Urząd Statystyczny, biuletyn "Sytuacja społeczno-gospodarcza kraju — Rynek pracy", publikacja z 25.08.2026 r.
**Fragment rozstrzygający:** "Stopa bezrobocia rejestrowanego, podobnie jak przed miesiącem wyniosła 5,8% i wzrosła 0,4 p.proc. w stosunku do analogicznego okresu ub. roku."
**Data źródła:** 25 sierpnia 2026 r. **Okres, którego dotyczy:** lipiec 2026 r.
**Potwierdzenie niezależne:** Ten sam wynik (5,8%, bez zmian względem czerwca) potwierdzają niezależnie cztery dodatkowe redakcje (Bankier.pl, Interia Biznes, Infotuba, Super Biznes), wszystkie powołujące się na ten sam komunikat GUS z 25 sierpnia.

## 5. KONTRARGUMENT
**Najsilniejszy argument przeciwko werdyktowi:** Istnieje **druga, równolegle publikowana miara** — stopa bezrobocia wg metodologii BAEL (Eurostat), która za II kwartał 2026 r. wynosi 3,2%, czyli zupełnie inna liczba. Ktoś mógłby zarzucić ministrowi "manipulację wyborem wskaźnika" (wybór wyższej z dwóch dostępnych miar). To jednak **nie podważa** samego sprawdzanego twierdzenia — minister wprost powołał się na "dane GUS" dotyczące stopy bezrobocia **rejestrowanego**, a nie na BAEL, więc porównanie jest właściwe. Dodatkowo warto odnotować: wcześniejszy szacunek Ministerstwa Rodziny, Pracy i Polityki Społecznej mówił o 5,9%, a ostateczny odczyt GUS (5,8%) okazał się nieco niższy — czyli minister w wypowiedzi cytował już **poprawiony, ostateczny** wynik, nie wcześniejszy szacunek resortowy.
**Czy zmienia wynik?** NIE.

## 6. WERDYKT (merytoryczny)
🟢 POTWIERDZONE
**Dlaczego:** Liczba, okres i źródło podane przez ministra zgadzają się dokładnie z oficjalnym komunikatem GUS z 25 sierpnia 2026 r., niezależnie potwierdzonym przez pięć redakcji.
**Czy werdykt dotyczy WYŁĄCZNIE wąskiego faktu, nie całego sporu?** TAK. Nie oceniam tu, czy prognoza na 6,0% na koniec 2027 r. się sprawdzi (to twierdzenie o przyszłości, nieweryfikowalne dziś) ani czy polityka gospodarcza rządu jest słuszna — wyłącznie czy przywołana liczba za lipiec 2026 jest zgodna z GUS.

## 6a. STATUS PUBLIKACJI
🟠 HUMAN REVIEW (zgodnie z zasadą "każdy RAPID w fazie walidacji przechodzi przez człowieka", nie ze względu na kontrowersyjność — treść jest merytorycznie spokojna, nienazywająca nikogo w sposób negatywny).

## 6b. IMPACT / PRIORYTET
C — średni. Solidny, dobrze potwierdzony fakt makroekonomiczny, ale niska "temperatura" sporu — to nie jest twierdzenie kwestionowane przez kogokolwiek, raczej neutralna aktualizacja danych.

## 7. SAMO-RED-TEAM PRZED PUBLIKACJĄ
- Czy werdykt nazywa realną osobę jako "kłamiącą"? NIE — wypowiedź ministra jest potwierdzona, nie obalona.
- Czy to samo powiedzielibyśmy o przeciwnej stronie sporu? Nie dotyczy — to nie jest twierdzenie sporne między stronami politycznymi, tylko odczyt statystyczny.
- Czy ktoś mógłby wskazać źródło, którego nie sprawdziłem? Sprawdziłem źródło pierwotne (GUS) bezpośrednio, nie tylko przez pośredników — wysoka pewność.

## 8. PUBLIKACJA
**Gotowe do publikacji:** TAK (po przeglądzie Arka zgodnie z zasadą fazy walidacyjnej).
**Jednozdaniowy werdykt dla Senseja:** "Sprawdziliśmy: minister Domański poprawnie zacytował dane GUS — stopa bezrobocia rejestrowanego w lipcu 2026 r. rzeczywiście wyniosła 5,8%."
**Źródło:** stat.gov.pl (GUS), biuletyn "Sytuacja społeczno-gospodarcza kraju" z 25.08.2026.
**Czas badania:** ok. 9 minut od rozpoczęcia szukania twierdzenia do gotowego werdyktu (mieści się w założonym oknie 5-10 min).

## WYNIK TESTU TEMPA
✅ **Pierwszy przypadek mieszczący się w docelowym czasie.** W przeciwieństwie do RAPID-0001 (prawo, wymagające odróżniania wersji ustaw — 12 min) i RAPID-0002 (odrzucone na starcie — 90 sek), twierdzenie **statystyczne z jednym, jasno zidentyfikowanym źródłem instytucjonalnym (GUS)** dało się sprawdzić w założonym oknie czasowym. To sugeruje wstępny wzorzec: **typ twierdzenia silnie koreluje z czasem sprawdzenia** — statystyki z jednego źródła = szybko, treść ustaw wymagająca odróżnienia wersji = wolniej. Warto to obserwować na kolejnych przypadkach, nie wyciągać wniosku z n=1.
