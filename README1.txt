Pentru implementarea bancului de registri s-au utilizat variabile de tip reg care stocheaza valorile acestora. Iesirea este calculata asincron in functie de adresa primita la intrare si afisata la frontul pozitiv de ceas.

Modulul de decriptare a cifrului Caesar s-a implementat folosind o varibila de tip reg pentru a stoca cate un caracter pe rand, urmand ca din acesta sa se scada valorea cheii de decriptare si sa fie afisat la output.

Modulul de decriptare a cifrului Scytale s-a implementat folosind trei stari: 
					- reset: stare in care sunt initializate cu valorile corespunzatore fiecare variabila auxiliara
					- prelucrare_data: stare in care are loc colectarea datelor si stocare acestora intr-un vector de dimensiune maxima permisa (50 caractere)
					- decriptare: starea  in care are loc decriptarea datelor primite la intrare, pentru decriptare s-au folosit 2 variabile de tip reg () una pentru calcularea indexului de afisare si una pentru a contoriza rundele de criptare (echivalente idenxilor pentru linie si coloana din reprezentarea matriceala)

Modului de decriptare a cifrului Zig-Zag s-a implementat folosind 3 stari:
					- reset: stare in care sunt initializate cu valorile corespunzatoare toate variabilele intermediare
					- prelucrare_date: stare in care are loc decriptarea datelor si stocare acestora intr-un vector de dimensiune maxima permisa (50 caractere)
					- decriptare: analizand modul de criptare Zig-Zag, s-au folosint 3 varibile care stocheaza valoarea urmatoarei afisari de pe fiecare linie, acesta sunt initializate in functie de dimensiunea cheii la prima intrare in starea de decriptare. Pentru a contoriza linia de pe care urmeaza sa fie afisat la iesire, s-a folosit o variabila reg care este incrementata sau decrementata in functie de directia de afisare, directia este data de o varibila de semn, care este negata odata ce contorul de linie ajunge la extremetitati (0, 2/3). 

Demultiplexorul: Pentru implementarea demultiplexorului s-a utilizat o variabila de tip reg pentru stocarea datelor de la intrare si o variabila de tip reg care este intarziata 4 cicli de ceas pentru a semnala liberul la afisarea datelor (4 cicli deoare primirea datelor se face pe frontul pozitiv al ceasului master, iar afisarea incepe la finalul ciclului master, care este echivalent cu trecea a 4 cicluri slave de ceas). S-a folosit un contor pentru a calcula indexul de inceput al octetului care urmeaza sa fie afisat.

Multiplexorul: Pentru implementarea multiplexorului s-a optat pentru o logica dupa ceasul de la intrare. Astfel s-au folosit variabile reg pentru stocare datelor de la intrare (3 vars) si un indicator (got_input) care semnaleaza momentul din care se pot scoate datele pe interfata de iesire. Pentru afisarea datelor la iesire s-a folosit un case dupa semnalul de select. 