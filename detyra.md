# Detyra për ushtrime

---

Të vizatohet bllok diagrami për gjetjen e shumës së numrave çift nga $2$ deri në $n$.

---

Të shkruhet programi i plotë i cili shfaq tekstin e mëposhtëm në ekran. Të përfshihen të gjitha elementet e programit (include, main, return).

```text
Gjuha Programuese

C++
```

---

Të shkruhet programi që lexon nga tastiera tre numra me presje dhjetore, dhe pastaj shtyp në ekran mesatarën e tyre.

---

Çfarë do të shfaqet në ekran kur të ekzekutohet kodi i mëposhtëm?

```cpp
int a = 6;
int b = 9;
int c = 3 * a + 2 * (b + 3);
cout << 1 + c % 5;
```

---

Të shkruhet programi i cili lexon nga tastiera numrat e plotë $c$ dhe $d$ dhe shfaq në ekran vlerën e shprehjes $-4\times (5c+d+2)+3$.

---

Të shkruhet programi që lexon nga tastiera rrezën `r` dhe shtyp në ekran perimetrin dhe sipërfaqen e rrethit.

---

Çfarë shfaqet kur të ekzekutohet kodi?

```cpp
#include <iostream>
using namespace std;

int main() {
  int a = 13;
  int b = 4;
  int c = a + b - (a - 3) * 2 + 13;
  cout << c % 10;
}
```

---

Të shkruhet programi i cili llogarit vlerën e numrit real $y$. Vlera reale $x$ të lexohet nga tastiera.

$$
y = \begin{cases}
2x+3 & \text{kur}\ x > 8 \\
5 - x & \text{kur}\ 0 \leq x \leq 8 \\
\frac{x}{5} & \text{kur}\ x < 0 \\
\end{cases}
$$

---

Të shkruhet programi që lexon nga tastiera një numër. Të tregohet a plotëpjestohet ky numër me `2`, `3`, dhe `5`.

---

Të shkruhet programi i cili lexon një numër `x` dhe e shtyp vlerën absolute të tij në 10 hapësira të mbushura me karakterin `+`.

---

Çfarë shfaqet kur të ekzekutohet kodi?

```cpp
#include <iostream>
using namespace std;

int main() {
  int a = 5;
  int b = 13;
  if (a * 2 >= b) {
    cout << b % a;
  } else {
    cout << a + b % 3;
  }
}
```

---

Çfarë do të shfaqet në ekran kur të ekzekutohet kodi i mëposhtëm?

```cpp
int x = 15;
int y = 2 * (x - 5);
int z = (x + 1 > y) ? (1 - x) : (-x - y);
cout << "Rezultati:" << endl;
cout << setfill('+') << setw(5) << (z >= 0 ? z : -z);
```

---

Çfarë shfaqet në ekran nëse janë dhënë numrat e plotë $a=13, b=4, c=9$?

```cpp
switch (a / 2) {
  case 5:  cout << b + c + 1; break;
  case 6:  cout << c - a;     break;
  case 7:  cout << b - c;     break;
  default: cout << a + b + c; break;
}
```

---

Të shkruhet programi që shtyp numrat nga `3` deri `27` por duke kapërcyer të gjithë numrat që plotëpjestohen me `4`.

---

Të shkruhet unaza e cila shtyp numrat nga $3$ deri në $17$, por duke kapërcyer numrin $11$.

---

Të shkruhet programi që shtyp numrat nga `1` deri `15` por duke kapërcyer të  numrat `2`, `6`, `13`.

---

Të llogaritet vlera sipas formulës:

$$
P = 3 + \prod_{i=2}^{n}{(5i + 1)}
$$

---

Të llogaritet vlera sipas formulës:

$$
S = 17 + 2 \times \sum_{i=1}^{n}{i^2}
$$

---

Të deklarohet vargu me 6 numra të plotë dhe të mbushet nga tastiera. Pastaj të llogaritet minimumi, maksimumi, shuma, mesatarja e këtij vargu dhe të shtypen në ekran.

---

Të deklarohet vargu me 7 numra me presje dhjetore. Të tregohet sa elemente në këtë varg janë $\geq 7$.

---

Është dhënë vargu i mëposhtëm $v$. Të shkruhet programi i cili shfaq numrin e elementeve që janë më të mëdhenj ose baraz me $8$ ($\geq 8$).

```cpp
const int n = 7;
int v[n] = { 5, 11, 2, 1, 17, 9, 8 };
```

Rezultati në ekran duhet të dalë:

```text
Numri i elementeve: 4
```

---

Çfarë do të shfaqet në ekran kur të ekzekutohet kodi i mëposhtëm?

```cpp
int v[5] = { 5, 2, 4, -2, -4 };
int c = 0;
for (int i = 0; i < 5; i++) {
  c += v[i] + 2;
}

cout << c + v[2] - v[4] << endl;
```

---

Të deklarohet matrica katrore e madhësisë `n` (merreni sipas dëshirës). Të mbushet kjo matricë nga tastiera. Pastaj të llogaritet shuma e anëtarëve në diagonale, nën diagonale, si dhe mbi diagonale të kësaj matrice si dhe të shfaqen këto rezultate në ekran.

---

Të shkruhet funksioni `kaKaluar(p)` i cili merr numrin e pikëve $p$ (`int`) dhe kthen nëse kalohet provimi me ato pikë ($p \geq 50$).

**Ndihmesë:** Tipi i kthimit duhet të jetë `bool`.

---

Të shkruhet funksioni `max(a,b)` i cili merr dy numra dhe kthen numrin më të madh nga këta.

---

Të shkruhet funksionet `eshteCift(x)` dhe `eshteTek(x)` qe tregojnë nëse $x$ është çift/tek.

---

Të shkruhet funksioni `f(a,b,c,x)` sipas formulës:

$$
f(a,b,c,x) = ax^2 + bx + c
$$

---

Çfarë shfaqet kur ekzekutohet ky kod?

```cpp
#include <iostream>

int f1() {
  int a = 25;
  return 13;
}

int f2(int b) {
  int a = 13;
  return b;
}

int f3(int a) {
  return a + 1;
}

int main() {
  int a = -3;
  std::cout << f2(f3(a));
}
```

---

Të llogaritet shprehja e mëposhtme duke definuar dhe përdorur funksionin `shuma`.

$$
S = \sum_{i=3}^{8}{i} + \sum_{i=2}^{6}{i}
$$

---

Të shkruhet funksioni që llogarit dhe kthen mesatarën e vektorit të numrave të plotë.

---

Të shkruhen funskionet e mbingarkuara `min(a,b)`. Njëri kthen minimumin e numrave të plotë ndërsa tjetri të numrave me presje.


---

Çfarë shfaqet kur ekzekutohet ky kod?

```cpp
#include <iostream>

int f1(int a) {
  a = a + 5;
  return 7;
}
int f2(int c) {
  return c - 1;
}
int main() {
  int a = 3;
  int c = f1(a);
  std::cout << f2(c);
}
```

---

Çfarë shfaqet kur ekzekutohet ky kod?

```cpp
#include <iostream>

int f(int x) {
  return x + 3;
}
double f(double x) {
  return 2 * x;
}
int main() {
  std::cout << f((double)f(7));
}
```

---

1. Të deklarohet numërimi `Muaji` i cili ka vlerat $\text{janar} = 1, \text{shkurt} = 2, \dots$
2. Të deklarohet numërimi `Stina` e cila ka vlerat $\text{pranvere}, \text{vere}, \text{vjeshte}, \text{dimer}$
3. Të shkruhet funksioni `merrStinen` i cili pranon një `Muaji` dhe kthen `Stina` e atij muajit.
4. Të shkruhet funksioni `shfaqStinen` i cili pranon një `Stina` dhe e shfaq në ekran.
5. Të thirren funksionet me $m=\text{prill}$

---

Të deklarohet struktura `laptopi=(gbram, gbdisk, cpu)` ku `cpu` eshte numërim `{ i3, i5, i7 }`. Të shkruhet funksioni `void specifikat(laptopi L)` i cili shtyp në ekran specifikat e laptopit. Në `main` të deklarohen dy variabla të tipit `laptopi` me vlera sipas dëshirës dhe të thirret funksioni `specifikat`.
