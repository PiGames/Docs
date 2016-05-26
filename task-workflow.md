#Workflow
Do pracy używamy serwisu [Trello](trello.com), każdy członek **PiGames** powinien posiadać tam konto i dołączyć do odpowiedniego 
teamu poprzez link podany w kanale projektu na *Slacku*.

Wszelkie sugestie mile widziane.


##Stany projektu
Każde zadanie (task) może znajdować się w jednej z 3 list:

1. *Todo* - czyli rzeczy do zrobienia, zazwyczaj to będą puste słowa kluczowe do tasków; później dodam ich więcej
2. *Doing* - taski które są w trakcie robienia, posiadają one element Task List, czyli prostą listę subtasków które musicie wykonać, w momencie gdy wykonacie jakąś część zadania w tej liście to oznaczacie to jako zrobione
3. *Done* - rzeczy zrobione, tutaj trafiają wszystkie rzeczy, które mają status "complete ..."

####Możliwe zmiany stanów
**Jedynie *Project Manager* oraz jego *Zastępca* mogą dokonywać transferu pomiędzy Stanami!**

LHS | Kierunek | RHS | Powód
---: | :---: | :--- | :---
Todo | -> | Doing | Task został zaplanowany i przydzielony człownkowi teamu
Doing | -> | Done | Task został zrobiony i zatwierdzony przez osobę odpowiedzialną za CR
Doing | <- | Done | Mimo CR zaistniał błąd krytyczny, który wymaga natychmiastowych poprawek

##Status zadania (etykiety)
Każde zadanie może mieć jednocześnie aktywnie **tylko jedną** etykietę.

Status | Kto ustawia ten stan? | Opis
---: | :---: | :---
None | CT | tylko zadania w stanie *Todo*
Pending | CT | task przydzielony, oczekuje na jego podniesienie przez osobę odpowiedzialną za jego wykonanie
W.I.P | wykonawca zadania | oznacza że osoba(y) odpowiedzialna pracuje(ą) nad zadaniem
Ready | wykonawca zadania | oznaczenie pracy jako wykonanej, dajecie znać że kod oczekuje na CR
Complete | CT | kod przeszedł przez CR; zadanie wykonane
Bug | CT | CR niezaliczony, wymagane przejście do *W.I.P* i wykonanie poprawek

Przez *wykonawcę zadania* rozumiemy osobę odpowiedzialną za jego wykonanie, czyli osobę która ma przypiosane konkretne zadanie. 
Przez *CT (Code Tester)* rozumiemy osobę odpowiedzialną za przeprowadzenie *CR (Code Review)*, zazwyczaj to *Project Manager* lub inna wyznaczona osoba.

####Model zmiany statusu zadania
*None* -> *Pending* -> *W.I.P* -> *Ready* (<- *Bug* ) -> *Complete*

##Przykład
Posłużymy się tutaj przykładową osobą (Jan Kowalski [JK]), która otrzyma jakieś zadanie i będzie musiała je wykonać, 
jak powinny wyglądać akcje JK oraz Team Leadera [TL] (który jest w tym przypadku także CT) przy użyciu Trello?

#####Spotkanie projektowe
1. **JK** zostaje wybrany przez **TL** do wykonania zadania
2. **TL** uzupełnia task o Task Listę, dodaje potrzebne materiały do taska (np informacje objaśniające co trzeba zrobić), przenosi go z *Todo* do *Doing* oraz ustawia status zadania (etykietę) na *Pending*

#####Wykonanie zadania
1. **JK** zapoznaje się z listą rzeczy do zrobienia i w momencie gdy zacznie prace zmienia status zadania na *W.I.P*
2. **JK** w momencie wykonania WSZYSTKICH zadań z Task Listy zmienia status na *Ready*
3. **TL** sprawdza kod / kompletność wykonania zadania; załóżmy że kod nie spełnia oczekiwań więc task otrzymuje status *Bug*
4. **JK** zapoznaje się z listą błędów, task listą i PODNOSI zadanie jeszcze raz zmieniając status na: *W.I.P*
5. **JK** po poprawieniu błędów, wypełnieniu zadań z task list zmienia status zadania na *Ready*
6. **TL** sprawdza kod / kompletność wykonania zadania; załóżmy że teraz wszystko jest ok: następuje zmiana statusu zadania na *Complete* oraz zmiany stanu na *Done*



Log z trello jest dostępny pod #tasklog-trello 
Jeżeli macie jakieś pomysły na usprawnienie tego systemu, pytania, ... to śmiało piszcie
Postarajcie się dołączyć do teamu na Trello jak najszybciej
