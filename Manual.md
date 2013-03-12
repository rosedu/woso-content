World of SO
============

I. Informații de bază
---------------------

Un jucător poate avea la un moment dat: puncte și karma points.

Punctele reprezintă singurul criteriu care determină ordinea în clasament, iar karma-points sunt folosite pentru a reflecta karma adusă în jurul cursului de Sisteme de Operare.

Fiecare jucător are un level, care are importanță în timpul de rulare al unei provocări. Toți jucătorii pornesc cu level 1, urmând ca acesta să crească la atingerea anumitor punctaje.

II. Întrebarea zilei (Question of the Day)
------------------------------------------

În fiecare zi este desemnată o întrebarela care se poate răspunde în orice moment al zilei respective, cu mențiunea că răspunsul corect în intervalul orar 00:00-11:59 este echivalent cu obținerea a 50 puncte, iar în intervalul 12:00-23:59 cu 30 puncte. Întrebarea are multiple variante de răspuns, dintre care una singură este corectă.

III. Provocări (Challenges)
---------------------------

Provocarea este modul în care doi jucători pot concura pentru obținerea de puncte prin răspunsul la un număr de întrebări comune. O provocare constă din 5 întrebări (au pondere egală în calcularea câstigătorului) cu variante multiple și cu mai multe variante de răspuns corecte.

Un jucător poate lansa o singură provocare în fiecare zi însă poate să accepte oricâte.

Costul lansării sau acceptării unei provocări este de 30 de puncte. Pentru a fi rulată, o provocare trebuie să fie acceptată. Rularea provocării trebuie realizată pe parcursul aceleiași zile. Dacă la finalul zilei, cel puțin unul dintre jucători nu a rulat provocarea, atunci aceasta este anulată, iar cele 30 de puncte puse în joc sunt returnate fiecărui jucător. O provocare poate fi rulată asincron și fiecare dintre cei doi jucători are un timp maxim propriu de rulare a provocării, dependent de level-ul său în momentul respectiv. La level 1, timpul este de 5 minute, urmând ca acesta să scadă cu 5 secunde per level.

Punctele obținute în urma provocării țin cont de diferența de nivel dintre cei doi competitori și de rasele din care fac parte. Un adversar de nivel apropiat dintr-o altă rasă va însemna obținerea mai multor puncte. Un adversar de nivel mai mic din aceeași clasă va înseamna obținerea mai puținor puncte.

Pentru a fi rulată, o provocare trebuie să fie acceptată. Rularea provocării trebuie realizată pe parcursul aceleiași zile. Dacă la finalul zilei, cel puțin unul dintre jucători nu a rulat provocarea, atunci aceasta este anulată, iar cele 30 de puncte puse în joc sunt returnate fiecărui jucător.

O provocare poate fi rulată asincron și fiecare dintre cei doi jucători are un timp maxim propriu de rulare a provocării, dependent de level-ul său în momentul respectiv. La level 1, timpul este de 5 minute, urmând ca acesta să scadă cu 5 secunde per level.

Cele 5 întrebări ale unei provocări au pondere egală - valoarea 100. Se poate obține, astfel, maxim valoarea 500 pentru un challenge. Se compară valorile obținute de cei doi concurenți și cel cu valoarea mai mare câștigă. Timpul în care se răspunde la cele 5 întrebări nu are impact în matematica punctelor; nu are relevanță dacă termini în 30 de secunde sau în 4 minute și 59 de secunde.

Pentru o întrebare dată se calculează punctajul ponderat la răspunsurile corecte și incorecte, după formula:

  Punctaj_intrebare = (NRCU / NRC - NRGU/NRG) * 100

unde:

* NRCU - numărul de răspunsuri corecte furnizate (checked) de utilizator/concurent
* NRC - numărul total de răspunsuri corecte ale întrebării
* NRGU - numărul de răspunsuri greșite furnizate (checked) de utilizator/concurent
* NRG - numărul total de răspunsuri greșite ale întrebării

Înmulțirea cu 100 se realizează din rațiuni de rotunjire pentru numerele fracționare.

Astfel, pentru o întrebare cu 7 variante de răspuns, dintre care 4 corecte și 3 greșite:

* dacă un utilizator selectează 2 variante corecte (și dor atât), va obține

	Punctaj_intrebare = (2/4 - 0/3) * 100 = 50

* dacă un utilizator selectează toate cele 4 variante corecte, va obține

	Punctaj_intrebare = (4/4 - 0/3) * 100 = 100

* dacă un utilizator selectează 3 variante corecte și 2 greșite, va obține

	Punctaj_intrebare = (3/4 - 2/3) * 100 = 9

* dacă un utilizator selectează 2 variante greșite, va obține

	Punctaj_intrebare = (0/4 - 2/3) * 100 = -66 (punctaj negativ)

* dacă un utilizator selectează toate cele 3 variante greșite, va obține

	Punctaj_intrebare = (0/4 - 3/3) * 100 = -100 (punctaj negativ)

* dacă un utilizator face check pe toate variantele

	Punctaj_intrebare = (4/4 - 3/3) * 100 = 0 (punctaj nul)

Dacă cei doi concurenți obțin același rezultat, cele 30 de  puncte puse în joc sunt returnate fiecăruia.

Numărul de puncte obținut de câștigător se calculează după formula:

	30 + min[30 + N, (30 + N) * Y / X]

unde
* N = punctaj bonus(20 pentru aceeași serie, 30 pentru serii diferite)
* X = punctajul câștigătorului
* Y = punctajul celui care pierde

Exemple
* exemplul 1: Gigel are 500 de puncte, iar colegul lui de serie, Martinel, are 5000 de puncte. Martinel câștigă provocarea împotriva lui Gigel și astfel va câștiga:

	30 + min(30 + 20, (30 + 20) * 500 / 5000) = 30(cele puse în joc) + min(50,  5) = 35

* exemplul 2: Vasilică are 700 de puncte și câștigă provocarea împotriva colegului său dintr-o altă serie care are 7000 de puncte. Astfel, Vasilică o să câștige:

	30 + min(30 + 30, (30 + 30) * 7000 / 700) = 30(cele puse în joc) + min(60, 600) = 90

Pentru a preveni "farming"-ul de puncte, jocul limitează provocările cu jucători aflați la o anumită distanță în clasament. Presupunem că un jucător X provoacă un jucător Y. Fie D diferența de poziție dintre X și Y (în modul). Jocul impune următoarele:
* Dacă D <= 10, atunci X îl poate provoca pe Y și în ziua următoare.
* Dacă 10 < D <= 20, atunci X îl poate provoca pe Y peste două zile (nu îl poate provoca în ziua următoare).
* Dacă 20 < D <= 30, atunci X îl poate provoca pe Y peste trei zile (nu îl poate provoca în următoarele două zile).
* ...
* Dacă 60 < D (fără limită superioară), atunci nu îl poate provoca în următoarele 6 zile (provocarea poate avea loc doar la nivel de săptămână, în acest caz).

IV. Capture-The-Flag Quests
----------------

TODO


V. Mesaje
-----------

Platforma pune la dispoziție un modul pentru transmiterea mesajelor private. Astfel, puteți comunica mult mai ușor cu ceilalți jucători.

VI. Altele
------------

Punctajele prag pentru nivele sunt:
* Nivel 2: 920p
* Nivel 3: 1670p
* Nivel 4: 2770p
* Nivel 5: 4420p
* Nivel 6: 10670p
* Nivel 7: 16320p
* Nivel 8: 24820p
* Nivel 9: 37620p

Pentru a raporta probleme și buguri ale WoSO, vă rugăm să folosiți issue tracker-ele din GitHub. Informații despre cum se pot raporta bug-uri se găsesc [aici] [1].
[1]: https://github.com/rosedu/woso-content/wiki/Cum-Raportez-un-bug%3F "aici"

Pentru întrebări, discuții, observații legate de joc, vom folosi lista WoSO: so@cursuri.cs.pub.ro. Urmăriți și știrile afișate în cadrul paginii de știri a portalului WoSO.
