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

## Probleme rezolvate

## Concluzii

În problemele de simulare, de obicei, este destul de ușor să îți dai seama ce trebuie să faci, dar implementarea, uneori, nu este așa de ușoară precum pare. Pentru ca implementările a acestor probleme să vi se pară mai ușoare, recomandăm să rezolvați cât mai multe probleme de implementare/simulare, eventual și unele la care este de scris mai mult.

## Probleme suplimentare


* [Probleme de implementare de pe kilonova](https://kilonova.ro/tags/290)

## Resurse suplimentare

* [Simulation - USACO Guide](https://usaco.guide/bronze/simulation)
* [Verificarea unor proprietati - pbinfo](https://www.pbinfo.ro/articole/5586/verificarea-unor-proprietati)
