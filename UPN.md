# C/C++

---

## Kazalo

- [C/C++](#cc)
  - [Kazalo](#kazalo)
  - [Prevajalniki in tolmači](#prevajalniki-in-tolmači)
  - [Izgled programa](#izgled-programa)
  - [Spremenljivke in konstante](#spremenljivke-in-konstante)
  - [Operatorji](#operatorji)
  - [Komentarji](#komentarji)
  - [Vhod/izhod (I/O) funkcije in tokovi](#vhodizhod-io-funkcije-in-tokovi)
  - [Konverzija podatkovnih tipov](#konverzija-podatkovnih-tipov)
  - [Pogojni stavki](#pogojni-stavki)
  - [Gnezdeni pogojni stavki](#gnezdeni-pogojni-stavki)
  - [Stavek switch](#stavek-switch)
  - [Naključna (random) cela števila](#naključna-random-cela-števila)
  - [Zanke](#zanke)
  - [Break in continue](#break-in-continue)
  - [Funkcije](#funkcije)

---

## Prevajalniki in tolmači

- Prevajalnik (compiler):
  - Prevede celo kodo
  - Izpiše vse napake v kodi
  - Program lahko izvedemo šele, ko odpravimo vse napake
- Tolmač (interpreter):
  - Prevaja vsako vrstico posebej
  - Preveri ali je v vrstici napaka, če je ni, se ukaz izvede
- Sintaksa:
  - Način na katerega mora biti ukaz napisan
  - Preverja jo prevajalnik/tolmač
- Semantika:
  - Logika pri zaporedju ukazov
  - Prevajalnik/tolmač je ne more preveriti
- Izvedba programa:
  1. Napišemo kodo v jeziku C/C++
  2. C/C++ koda se prevede v strojno kodo
  3. S programom se povežejo (linkajo) potrebne funkcije/knjižnice
  4. Program se izvede

---

## Izgled programa

```cpp
//dodajanje knjižnic
#include <iostream>

//funkcije ali prototipi funkcij
void izpis(char tabela_nizov[][21], int n);

//glavna (main) funkcija - s to funkcijo se program začne izvajati
int main() {
    /*
    telo funkcije
    */
    return 0; //0 pomeni, da se je program uspešno izvedel
}
```
Vsak ukaz se zaključi s podpičjem ( ; ) z izjemo predprocesorskih ukazov (to so ukazi, ki se začnejo z #, npr. #include) in nekaterih ukazov kot so if stavek, while zanka in podobno.

---

## Spremenljivke in konstante

- Spremenljivka:
  - Prostor v pomnilniku, kamor zapisujemo določene vrednosti
  - Da bi lahko zasedla prostor v pomnilniku, jo moramo deklarirati
  - Sintaksa deklaracije: `podatkovni_tip ime_spremenljivke;`
  - Primer deklaracije: `int stevilo;`
  - Velikost zavzetega prostora je odvisna od podatkovnega tipa
  - Osnovni podatkovni tipi:
    - char (znak) - 1 bajt
    - int (celo število) - 4 bajti
    - float (realno število) - 4 bajti
    - double (realno število) - 8 bajtov
    - bool (boolean, 0/1, true/false) - 1 bajt
  - unsigned (nepredznačeno), short, long
  - Ime spremenljivke lahko vsebuje:
    - Male in velike črke brez šumnikov
    - Podčrto
    - Števke, vendar ne na prvem mestu
  - Inicializacija spremenljivke pomeni, da spremenljivki določimo začetno vrednost
  - Primer inicializacije: `int stevilo; stevilo = 5;` ali `int stevilo = 5;`
- Konstanta:
  - Mora biti takoj inicializirana
  - Vrednosti kasneje v programu ne moremo spremeniti
  - Sintaksa: `const int PI = 3.14;`

---

## Operatorji

- Prireditveni:
  - = (določanje vrednosti)
- Aritmetični:
  - \+ (seštevanje)
  - \- (odštevanje)
  - \* (množenje)
  - / (deljenje)
  - % (ostanek pri deljenju)
- Primerjalni:
  - \> (levo je večje od desnega)
  - < (levo je manjše od desnega)
  - \>= (levo je večje ali enako desnemu)
  - <= (levo je manjše ali enako desnemu)
  - == (primerjanje vrednosti, levo je enako desnemu)
  - != (primerjanje vrednosti, levo ni enako desnemu)
- Logični:
  - && (in)
  - || (ali)
  - ! (zanikanje)
- Hitri:
  - += (levemu se prišteje vrednost desnega)
  - -= (levemu se odšteje vrednost desnega)
  - *= (levo se zmnoži z desnim)
  - /= (levo postane količnik levega in desnega)
  - %= (levo postane vrednost ostanka med levim in desnim)
- Inkrement in dekrement:
  - Preinkrement/predekrement: `++i/--i` (najprej se vrednost poveča/zmanjša, nato se izvedejo ostale operacije v ukazu)
  - Postinkrement/postdekrement: `i++/i--` (najprej se izvedejo ostale operacije v ukazu, nato se vrednost poveča/zmanjša)
- Pogojni operator: `(pogoj) ? (koda če pogoj drži) : (koda če pogoj ne drži);`
  
---

## Komentarji

Komentarje lahko uporabljamo, da si zapišemo kaj kakšen del kode naredi ali da začasno preprečimo, da se koda izvede.
- Enovrstični komentar:
  ```cpp                      
  //cout >> "besedilo"; - ta koda ne dela, popravi kasneje!!!
  ...
  ```
- Večvrstični komentar:
  ```cpp
  int main() {
    int x[10];
    int n = 10;
    /*
    vpis(x, n);
    izpis(x, n);
    */
    return 0;
  }
  ```

---

## Vhod/izhod (I/O) funkcije in tokovi

- C (funkcije):
  - Za uporabo spodnjih funkcij moramo v program dodati knjižnico stdio.h (#include <stdio.h>)
  - Branje:
    - `scanf("%s", &ime_spremenljivke);`
    - %s - format
    - & - referenca
  - Pisanje: `printf("Besedilo %s več besedila", ime_spremenljivke);`
- C++ (tokovi):
  - Za uporabo tokov moramo v program dodati knjižnico iostream (#include <iostream>)
  - Branje:
    - `cin >> ime_spremenljivke;`
    - `cin >> s1 >> s2 >> s3;`
  - Pisanje:
    - `cout << ime_spremenljivke;`
    - `cout << "Besedilo " << ime_spremenljivke << " več besedila";`

---

## Konverzija podatkovnih tipov

- Avtomatska: char -> int, ('A' == 65)
- Prisiljena (casting):
  ```cpp
  int x, y;
  cin >> x >> y;
  cout << (float)x / y; //rezultat je izpisan kot realno število
  ```
  Podatkovnih tipov spremenljivkam ne moramo spreminjati, kar pomeni, da s castingom ne spremenimo podatkovnega tipa spremenljivke temveč le njeno vrednost, ki se uporabi le v operaciji, v kateri smo izvedli casting.

---

## Pogojni stavki

- If:
  - Če je pogoj veljaven (true), se izvede blok ukazov, če ni veljaven (false), se blok ukazov ne izvede
  - Sintaksa:
    ```cpp
    if (pogoj) {
      /*
      blok ukazov
      */
    }
    ```
  - Primer:
    ```cpp
    if (i < 5) {
      cout << i << " je manjse od 1";
      i++;
    }
    ```
    Če je v bloku ukazov le en ukaz, lahko izpustimo zavite oklepaje ( {} ).
    ```cpp
    if (i < 5)
      i++;
    if (i > 5) i--;
    ```
- If else:
  - Če je pogoj veljaven, se izvede blok ukazov pod if, če ni, se izvede blok ukazov pod else
  - Sintaksa:
    ```cpp
    if (pogoj) {
      //blok ukazov
    } else {
      //blok ukazov
    }
    ```
  - Primer:
    ```cpp
    if (starost > 16)
      cout << "Dovolj si star, da lahko opravljas vozniski izpit!";
    else
      cout << "Nazalost bos moral se malo pocakati";
    ```
- If else if:
  - Če je prvi pogoj veljaven, se izvede blok ukazov pod if, če je veljaven drugi pogoj, se izvede blok ukazov pod else if, če ni noben od pogojev veljaven, se izvede blok ukazov pod else
  - Lahko imamo neomejeno število else if-ov
  - Sintaksa:
    ```cpp
    if (pogoj) {
      //blok ukazov
    } else if (pogoj2) {
      //blok ukazov
    } else if ... {
    } else {
      //blok ukazov
    }
    ```
  - Primer:
    ```cpp
    if (i == 0)
      cout << "Dober dan!";
    else if (i == 1)
      cout << "Pozdravljen!";
    else if (i == 2)
      cout << "Živijo!";
    else
      cout << ":)";
    ```

---

## Gnezdeni pogojni stavki

Pogojne stavke lahko gnezdimo, to pomeni, da lahko znotraj bloka ukazov if stavka uporabimo še en if stavek.
- Primer:
  ```cpp
  if (i < 10) {
    if (i < 5) {
      if (i == 1) i++;
      cout << "i je manj od 5";
    }
    if (i == 7) cout << i;
  }
  ```

---

## Stavek switch

- Ko switch najde case z ustrezno vrednostjo, se izvedejo vsi ukazi med tem casom in breakom
- Če breaka na koncu casa ni, se izvedejo vsi ukazi za casom
- V switchu lahko preverjamo vrednosti, ki so podatkovnega tipa int, char ali bool
- Sintaksa:
  ```cpp
  switch (ime_spremenljivke ali izraz) {
    case vrednost1:
      //blok ukazov
      break;
    case vrednost2:
      //blok ukazov
      break;
    ...
    default:
      //blok ukazov
  }
  ```
- Primer:
  ```cpp
  switch (ocena) {
    case 1:
      i1++;
      break;
    case 2:
      i2++;
      break;
    case 3:
      i3++;
      break;
    case 4;
      i4++;
      break;
    case 5:
      i5++;
      break;
    default:
      nps++;
  }
  ```
  Če za več vrednosti želimo izvesti isti ukaz lahko naredimo naslednje:
  ```cpp
  switch (ocena) {
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
      i++;
      break;
    default:
      nps++;
  }
  ```

---

## Naključna (random) cela števila

Za uporabo funkcije rand moramo v program dodati knjižnici cstdlib in ctime.
- Primer:
  ```cpp
  #include <iostream>
  #include <cstdlib>
  #include <ctime>

  using namespace std;

  int main() {
    srand(time(NULL)); //če želimo res naključna števila, moramo narediti to na začetku programa oziroma pred uporabo funkcije rand()
    int x = rand() % (300 - (-100)) + (-100); //naključno število iz intervala [-100, 300)
    cout << x;
  }
  ```

---

## Zanke

- Omogočajo nam ponavljanje blokov ukazov
- Ponavljanje se izvaja dokler je pogoj veljaven
- Zanke lahko tudi gnezdimo
- For:
  - Delovanje: Izvede se inicializacija, nato se preveri pogoj. Če je veljaven, se izvede blok ukazov. Zatem se izvede korak zanke in se nadaljuje s preverjanjem pogoja. Če je pogoj neveljaven, se izvajanje zanke prekine.
  - Sintaksa:
    ```cpp
    for (inicializacija; pogoj; korak zanke) {
      //blok ukazov
    }
    ```
  - Primer:
    ```cpp
    for (int i = 0; i < 10; i++)
      for (int j = 0; j < 10; j++)
        cout << i << j << endl;
    ```
- While:
  - Sintaksa:
    ```cpp
    while (pogoj) {
      //blok ukazov
    }
    ```
  - Primer:
    ```cpp
    while (i < 10) {
      cout << i << endl;
      i++;
    }
    ```
- Do while:
  - Pri do while zanki se pogoj preverja na koncu, zato se zanka vedno vsaj enkrat izvede
  - Sintaksa:
    ```cpp
    do {
      //blok ukazov
    } while (pogoj);
    ```
  - Primer:
    ```cpp
    do {
      cin >> i;
      cout << i << endl;
    } while (i != 0);
    ```

---

## Break in continue

- Break: prekine izvajanje zanke
- Continue: preskoči izvajanje ukazov, ki se nahajajo za njim in nadaljuje izvajanje zanke
- Primer:
  ```cpp
  while (i < 10) {
    if (i == 8) break; //zanka se konča, ko je i == 8
    for (int j = 0; j < 10; j++) {
      if (j == 3) continue; //zanka ne izpiše i, ko je j == 3
      cout << i;
    }
    i++;
  }
  ```

---

## Funkcije
- Funkcija je del kode, ki nekaj naredi
- Omogoča večjo preglednost kode
- Funkcijo lahko večkrat kličemo
- Sintaksa deklaracije (prototip):
  ```cpp
  return_type ime_funkcije(seznam_vhodnih_parametrov);
  ```
- Sintaksa definicije:
  ```cpp
  return_type ime_funkcije(seznam_vhodnih_parametrov) {
    /*
    telo funkcije
    */
  }
  ```
- Return_type je lahko void, kar pomeni da funkcija ne vrne ničesar, ali pa podatkovni tip npr. int ali char, kar pomeni, da ima vrednost, ki jo iz funkcije vrnemo, podatkovni tip return_type
- Seznam vhodnih parametrov so spremenljivke, ki jih lahko podamo v funkcijo, določiti jim moramo podatkovni tip in ime, lahko jim določimo tudi privzeto vrednost
- Primeri:
  ```cpp
  void izpis(string ime = "Neznanec", int starost) {
    cout << ime << starost << endl;
  }
  /*
  klic funkcije - izpis("Janez", 40);
  funkcije ne vrne ničesar
  */

  int vsota(int x, int y) {
    return x + y;
  }
  /*
  klic funkcije - vsota(3, 7);
  funkcija ne izpiše ničesar, vrne vrednost s podatkovnim tipom int, lahko jo shranimo v spremenljivko
  klic in shramba v spremenljivko - int v = vsota(3, 7);
  */
  ```