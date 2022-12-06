# BD RESTAURANT

---

## Spis treści
1. [O projekcie](https://github.com/AdrianCh24/BD#o-projekcie)
2. [Zbudowany z](https://github.com/AdrianCh24/BD#zbudowany-z)
  * [Narzędzia](https://github.com/AdrianCh24/BD#narz%C4%99dzia)
3. [Pierwsze kroki](https://github.com/AdrianCh24/BD#pierwsze-kroki)
  * [Wymagania wstępne](https://github.com/AdrianCh24/BD#wymagania-wst%C4%99pne)
  * [Łączenie z bazą danych](https://github.com/AdrianCh24/BD#%C5%82%C4%85czenie-z-baz%C4%85-danych)
4. [Jak kożystać z tej bazy danych](https://github.com/AdrianCh24/BD#jak-korzysta%C4%87-z-tej-bazy-danych)
  * [Projektowanie tabel w bazie danych](https://github.com/AdrianCh24/BD#projektowanie-tabel-w-bazie-danych)
  * [Cel bazy danych](https://github.com/AdrianCh24/BD#cel-bazy-danych)
  * [Implementacja programów](https://github.com/AdrianCh24/BD#implementacja-program%C3%B3w)
  * [Wczytanie danych do bazy](https://github.com/AdrianCh24/BD#wczytanie-danych-do-bazy)
5. [Problemy](https://github.com/AdrianCh24/BD#problemy)
6. [Kontakt](https://github.com/AdrianCh24/BD#kontakt)

## O projekcie 

Jest to projekt transakcyjnej bazy danych dla restauracji.

Cel projektu:

1. Nauka projektowania bazy danych
2. Nauka programowania bazy dabych Oracle za pomocą języka PL/SQL
3. Projekt ma pomódz mi w znalezieniu pracy jako młodszy programista

## Zbudowany z

Technologia Oracle jest używana do projektowania, wypełniania i wdrażania głównych funkcji.

### Narzędzia:

* `Autonomous Database` `ver.18c`
* `PL/SQL`
* `SQL`
* `Data Modeler`
* `SQL Developer`

## Pierwsze kroki

### Wymagania wstępne

Pobierz `SQL Developer` ze strony producenta Oracle.
`SQL Developer` to aplikacja kliencka firmy Oracle przeznaczona do pracy z bazami danych.

### Łączenie z bazą danych 

* Stwórz urzytkownika `restaurant` i nadaj mu uprawnienia. 
* Aby to zrobić uruchom skrypt z plikiem `create_user` będąc zalogowanym na urzytkownika `system`. 
* Możesz też skopiować zawartość pliku do `SQL Developer`.
* Dodaj nowe połączenie w `SQL Developer`. 
* Dla okiena `Username` wpisz **restaurant** a dla okna `Password` **123**. 
* `Connection Type` powinien być ustawiony na wrtość **TNS** a `Network Alias` na odpowiendni kontener domyślnie **XEPDB1**.
* Naciśnij okno `Test` jeśli zobaczysz komunikat **Status: Sukces** połączenie jest prawidłowo skonfigurowane.
* Zapisz połączenie. Możesz od tej pory zalogować się na urzytkownika **restaurant**.

## Jak korzystać z tej bazy danych

### Projektowanie tabel w bazie danych 

* Tabele z relacjami i constraint-ami zostały zaprojektowane w narzędziu `Data Modeler`. 
* Przy pomocy tego narzędzia wygenerowałem gotowy model fizyczny gotowy do zaimplementowania w `SQL Developer`.
* Ze swojej strony dla odpowiednich kluczy głównych nadałem generator id. Dzięki czemu to baza banych sama będzie generować nowe id oszczędzając nam pracy.
* Gotowy plik z kodem tworzącym tabele jest pod nazwą **restaurant_ddl**.

### Cel bazy danych 

Baza danych ma na swoim celu ułatwić zarządzanie danymi w restauracji i czerpać z nich korzyści. W tym celu stworzyłem dwie paczki z programami które krótko zaprezentuje.

Paczka **wstaw** ma ułatwić wprowadzanie danych do bazy:

* **produkt** ma wprowadzać produkty które są wykorzystywane do produkcji dań i napojów
* **dostawca** ma zapisać wszystkich dostępnych dostawców z jakimi współpracuje (lub nie) restauracja wraz i ich numerami telefonów i kont bakowych
* **pozycja_menu** ma zapisać każdą pozycje z menu wraz z ceną i podatkiem vat które są w karcie menu
* **receptura** ma zapisać jakie produkty i ich ilość wchodzą w skład dań i napojów
* **pracownik** ma zapisać aktualnie pracujących pracowników i ich przełożonych wraz z wynagrodzeniem 
* **dostawa** ma zapisać jakie produkty, w jakiej cenie i z jakim podatkiem vat dostarczają dostawcy do restauracji
* **zamowienie** ma zapisać przyjęte zamówienia kelnerów na dania i napoje 

Paczka **pokaz** ma za zadanie czerpanie korzyści z posiadania bazy danych:

* **receptura** ma pokazać recepture na wybraną przez nas pozycje z menu
* **magazym** ma pokazać aktualny stan magazynowy
* **koszt** ma pokazać koszt wyprodukowania wybranej przez nas pozycji z menu na podstawie średniej wartości produktów dostarczanych przez dostawców
* **wartość** ma pokazać jaka powinna być cena wybranej przez nas pozycji z menu uwzględniając koszt produkcji i podatek vat
* **zejscie_dan** ma pokazać szacowaną ilość produktów i dań jaka może zostać sprzedana danego dnia ma podstawie średniej z sprzedaży z ostatnich 7 dni i uwzględnieniu odpowienio dużego zapasu (x2)
* **lista_zakupow** ma pokazać liste produktów jaka powinna zastać zamówiona na podstawie aktualnego stanu magazynowego i średniej z sprzedaży z odpowienio dużym zapasam towaru (x3,5)
* **utarg** utarg restauracji z wstazanej ilości dni 

### Implementacja programów

Aby w odpowiedniej kolejności zainplementować programy do bazy danych załaduj skrypty w odpowiedniej kolejmości:

1. `restaurant_ddl`
2. `view and procedure`
3. `package_wstaw`
4. `package_body_wstaw`
5. `package_pokaz`
6. `package_body_pokaz`
7. `package_trg_a_job`
8. `package_body_trg_a_job`
9. `triggers`
10. `job`

### Wczytanie danych do bazy

Przygotowałem dane które wypełniają tabele i pozwalają przeprowadzić testy programów. Przygotowane dane wykorzystują paczkę **wstaw** więc jest ona niezbędna do załadowania danych.
Aby załadować dane do bazy wykonaj skrypt **data_restaurant**

## Problemy 

Jeśli wykryjesz jakieś problemy w działaniu programów daj znać.

## Kontakt

Adrian Chyliński
