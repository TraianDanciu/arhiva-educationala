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



## Concluzii

## Probleme suplimentare

* [Probleme de implementare de pe kilonova](https://kilonova.ro/tags/290)

## Resurse suplimentare

* [Simulation - USACO Guide](https://usaco.guide/bronze/simulation)
* [Verificarea unor proprietati - pbinfo](https://www.pbinfo.ro/articole/5586/verificarea-unor-proprietati)
