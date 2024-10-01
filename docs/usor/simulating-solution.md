---
tags:
    - C++
    - implementare
    - optimizare
    - simulare
---

## Introducere

Unele probleme nu ne cer doar rezultatul final, ci si unele rezultate pe care le obtinem pe parcurs. O simulare necesita $3$ lucruri:
1. O stare care poate fi descrisa in mod unic, prin niste variabile
2. O masura de timp, un tact (care de obicei, este definita de problema)
3. O bucla cu o conditie de oprire

O simulare arata astfel:
```cpp
gata = 1;
while (!gata) {
    <folosim starea ca sa facem ceva>
    <avansam la urmatorul pas, trece un tact>
    if (<conditie de oprire>) {
        gata = 1;
    }
}
```

!!! note "Observație"
    Multe probleme de clasa a V-a și de clasa a VI-a (matrice) necesita simularea soluției.

## Problema exemplu - [simulare](https://kilonova.ro/problems/3237)

În această problemă, cum cere și titlul, trebuie doar să simulăm procesul descris. De fiecare dată când citim o direcție, avansăm în acel mod, creștem suma cu valoarea de la poziția obținută și o afișăm.

Sursa de 100 de puncte:
```cpp
#include <iostream>

const int MAXN = 1'000;
const char T_NORD = 'N';
const char T_EST = 'E';
const char T_SUD = 'S';
const char T_VEST = 'V';

int mat[MAXN][MAXN], q, x, y;

void fastReadWrite() {
    std::ios_base::sync_with_stdio(0);
    std::cin.tie(0);
    std::cout.tie(0);
}

void readMatrix() {
    int i, j, n, m;
    std::cin >> n >> m >> q >> x >> y;
    x--; // noi indexam de la 0
    y--;
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            std::cin >> mat[i][j];
        }
    }
}

void simulateRoad() {
    int i, dir;
    long long sum;
    while (!isalpha(dir = std::cin.get())); // gasim prima litera (prima directie)
    sum = 0;
    for (i = 0; i < q; i++) {
        if (dir == T_NORD) {
            x--;
        }
        else if (dir == T_EST) {
            y++;
        }
        else if (dir == T_SUD) {
            x++;
        }
        else { // T_VEST
            y--;
        }

        sum += mat[x][y];
        std::cout << sum << " ";

        dir = std::cin.get();
    }
    std::cout << "\n";
}

int main() {
    fastReadWrite();
    readMatrix();
    simulateRoad();
    return 0;
}
```

## Optimizarea unei simulări

La unele probleme, chiar dacă nu ne este cerut rezultatul pe parcursul simulării, nu se poate găsi o altă soluție decât simularea. Majoritatea problemelor de acest fel, în care simularea nu intră în timp, este necesară optimizarea simulării.

### Optimizarea prin găsirea unei perioade

TO-DO

### Optimizarea prin găsirea unei formule care generează stările următoare

TO-DO

## Probleme rezolvate

TO-DO

## Concluzii

În problemele de simulare, de obicei, este destul de ușor să îți dai seama ce trebuie să faci, dar implementarea, uneori, nu este așa de ușoară precum pare. Pentru ca implementările a acestor probleme să vi se pară mai ușoare, recomandăm să rezolvați cât mai multe probleme de implementare/simulare, eventual și unele la care este de scris mai mult.

Problemele de optimizare sunt, în mare parte, din categoriile prezentate. Dar, la unele probleme, sunt necesare alte observații care duc la o optimizare mai puțin obișnuită.

## Probleme suplimentare

* [robinson - ONI 2005 VI](https://kilonova.ro/problems/1221) - problema rezolvata
* [joc - ONI 2011 VI](https://kilonova.ro/problems/1363)
* [furnica - OJI 2007 VI](https://kilonova.ro/problems/763)
* [oua - ONI 2007 VI](https://kilonova.ro/problems/1268)
* [tren - OJI 2010 V](https://kilonova.ro/problems/796) - problema rezolvata
* [circular - OJI 2022 X](https://kilonova.ro/problems/284)
* [gcl - Baraj 2018 Juniori](https://kilonova.ro/problems/1091) (O problemă la care este mult de scris, dar care vă ajută să vă organizați codul mai bine și vă îmbunătățește abilitățile de implementare)
* [medalion - ONI 2012 VI](https://kilonova.ro/problems/1387) (Trebuie să simulați cum se construiește o spirală)
* [tinta - ONI 2014 VI](https://kilonova.ro/problems/1435)
* [robinhood - ONI 2024 V](https://kilonova.ro/problems/2637)
* [galbeni - OJI 2013 VI](https://kilonova.ro/problems/402) - cred ca pe asta o fac problema exemplu la perioada
* [numere - OJI 2008 V](https://kilonova.ro/problems/772) (necesită cunoștința perioadei [Pisano](https://en.wikipedia.org/wiki/Pisano_period))
* [cartofi - OJI 2021 VIII](https://kilonova.ro/problems/936)
* [seif - Lot 2022 Juniori](https://kilonova.ro/problems/1818)
* [asort - Baraj 2016 Juniori](https://kilonova.ro/problems/1084) - pe asta o fac problema exemplu la formula
* [loopover - Lot 2022 Juniori](https://kilonova.ro/problems/1823)
* [Probleme de forță brută de pe kilonova](https://kilonova.ro/tags/323)
* [Probleme de periodicitate de pe kilonova](https://kilonova.ro/tags/502)
* [Alte probleme de implementare de pe kilonova](https://kilonova.ro/tags/290)

## Resurse suplimentare

* [Simulation - USACO Guide](https://usaco.guide/bronze/simulation)
* [Verificarea unor proprietati - pbinfo](https://www.pbinfo.ro/articole/5586/verificarea-unor-proprietati)
* [Simulare - algopedia](https://www.algopedia.ro/wiki/index.php/Clasa_a_VI-a_lec%C8%9Bia_14_-_20_dec_2018#Simulare)
