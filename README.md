# BD RESTAURANT

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
* Dla okiena `Username` wpisz 'restaurant' a dla okna `Password` '123'. 
* `Connection Type` powinien być ustawiony na wrtość 'TNS' a `Network Alias` na odpowiendni kontener domyślnie 'XEPDB1'.
* Naciśnij okno `Test` jeśli zobaczysz komunikat 'Status: Sukces' połączenie jest prawidłowo skonfigurowane.
* Zapisz połączenie. Możesz od tej pory zalogować się na urzytkownika 'restaurant'.
