# Gjuhë Programuese - Java 3

---

## Përsëritje

1. Çfarë janë **tipet**?
2. Çfarë janë **variablat**?
3. Çfarë janë **shprehjet**?

--

1. **Tipi** është lloji i të dhënës, psh. tekst, numër, vërtetësi, etj.
2. **Variablat** na mundësojnë ruajtjen e të dhënave në memorie.
3. **Shprehje** është gjithçka që ka tip dhe vlerë.

---

## Formatimi, kushtëzimet, bllok diagramet

---

## Shtypja e formatuar

Në librarinë `<iomanip>` (input output manipulators) ekzistojnë disa manipulatorë për formatimin e daljes në `cout`.

---

<!-- .slide: style="font-size: 0.7em" -->

Manipulatori|Alternativa|Kuptimi
-|-|-
setw(n)|cout.width(n)|Shkruaj rezultatin në `n` karaktere, duke shtuar karaktere mbushëse (mostra) nëse ka nevojë.
setfill(c)|cout.fill(c)|Hapësirat e shtuara mbushi me karakterin `c` - mostrën.
setprecision(n)|cout.precision(n)|Kufizo numrat me presje në `n` shifra.
setbase(base)|-|Vendos bazën e numrave të shtypur.

---

**Shembull:**

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
  cout << setfill('*')
       << setw(10)
       << 15
       << endl;
  return 0;
}
```

Na shfaqet:

```text
********15
```

---

**Mënyrat e precizitetit**

Supozojmë që streami (`cout`) ka precizitetin $n$. Kemi tri lloje të shfaqjes së numrave me presje.

1. default - kufizohet dalja në `n` shifra total (para dhe pas presjes).
2. **`std::fixed`** - kufizohet dalja në `n` shifra pas presjes. 
3. **`std::scientific`** - kufizohet dalja në `n` shifra pas presjes, ndërsa pjesa e plotë gjithmonë është 1 shifrore. Eksponenti përdoret për ta lëvizur presjen.

---

**Detyrë:** Të bëhet shkëmbimi i valutës nga euro (€) në dollar ($) nëse rata e këmbimit jepet nga tastiera. Rezultati të shfaqet në 2 shifra pas presjes.

```text
Jepni vleren ne euro: 250
Jepni raten e shkembimit: 1.16
Vlera ne dollar: $290.00
```

**Bonus:** Vlerës finale t'i zvogëlohet tarifa `2%` dhe të shfaqet në ekran.

--

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
  double euro, dollar, rata;
  cout << "Jepni vleren ne euro: ";
  cin  >> euro;
  cout << "Jepni raten e shkembimit: ";
  cin  >> rata;
  dollar = euro * rata;
  cout << "Vlera ne dollar: $"
       << setprecision(2) << fixed
       << dollar << endl;
  return 0;
}
```

---

**Detyrë:** Të shfaqen rezultatet e provimit në formë tabele si në vijim. Të përdoret manipulatori `setw` dhe `setfill`.

```text
Lenda...................Nota
Matematike................10
Fizike.....................7
Gjuhe Programuese..........8
```

**Bonus:** Të vizatohet me [box-drawing character](https://en.wikipedia.org/wiki/Box-drawing_character#DOS):

```text
╔══════════════════════╦════╗
║Lenda                 ║Nota║
╠══════════════════════╬════╣
║Matematike            ║  10║
║Fizike                ║   7║
║Gjuhe Programuese     ║   8║
╚══════════════════════╩════╝
```

--

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
  cout.fill('.');
  cout << setw(20) << left << "Lenda"
       << setw(8) << right << "Nota" << endl;
  cout << setw(20) << left << "Matematike"
       << setw(8) << right << 10 << endl;
  cout << setw(20) << left << "Fizike"
       << setw(8) << right << 7 << endl;
  cout << setw(20) << left << "Gjuhe Programuese"
       << setw(8) << right << 8 << endl;
  return 0;
}
```

---

## Shprehjet e vërtetësisë

Çdo gjë që ka përgjigjen **po** ose **jo** është **shprehje e vërtetësisë** (shprehje booleane).

---

## Operatorët e krahasimit

<!-- .slide: style="font-size: 0.7em" -->

Këta operatorë krahasojnë shprehjet dhe kthejnë vlerë booleane.

Operatori|Kuptimi
-|-
`a == b`|A janë të barabarta ana e majtë dhe e djathtë?
`a > b`|A është ana e majtë më e madhe se ana e djathtë?
`a >= b`|A është ana e majtë më e madhe ose baraz me anën e djathtë?
`a < b`|A është ana e majtë më e vogël se ana e djathtë?
`a <= b`|A është ana e majtë më e vogël ose baraz me anën e djathtë?

---

## Operatorët logjik

Veprojnë me **shprehje booleane**.

Operatori|Kuptimi
-|-
`a && b`|Kthen `true` kur **`a` dhe `b`** janë true.
`a ∣∣ b`|Kthen `true` kur **`a` ose `b`** janë true.
`!a`|Kthen të **kundërtën e `a`**.

---

Përparësia e operatorëve logjik:

1. Negacioni `!`
2. Dhe logjike `&&`
3. Ose logjike `||`

Përmes kllapave mund të caktojmë përparësi tjetër.

```cpp
a && !(b || c)
```

---

## Kushtëzimet

Mundësojnë ekzekutimin e një **blloku të urdhërave** vetëm nëse vlen kushti.

```cpp
if (kushti) {
  blloku;
}
```

**Kushti** duhet të jetë **shprehje e vërtetësisë** (bool).

--

**Rikujtim:** Bllok të kodit e quajmë vargun e urdhërave të mbështjellur me kllapa gjarpërore.

```cpp
{
  urdher;
  urdher;
  urdher;
}
```

---

**Shembull:**

```cpp
if (piket >= 50) {
  cout << "Keni kaluar provimin." << endl;
}
```

---

Kushtëzimi me dy degëzime:

```cpp
if (kushti) {
  blloku1;
} else {
  blloku2;
}
```

Nëse vlen **kushti**, ekzekutohet **blloku1**, nëse nuk vlen, ekzekutohet **blloku2**.

Nuk ka mundësi të ekzekutohen të dy blloqet përnjëheri - ose njëra ose tjetra.

---

**Detyrë:** Të kërkohet numri i pikëve nga tastiera (numër i plotë), dhe të tregohet nëse është kaluar provimi. Provimi kalohet me 50 ose më shumë pikë.

```text
Jepni piket: 67
Keni kaluar provimin
```

```text
Jepni piket: 32
Nuk keni kaluar provimin
```

**Bonus:** Të lexohen edhe pikët e provimit me gojë, dhe studenti kalon vetëm nëse mesatarja është mbi 50 dhe secili provim i ka mbi 40. Nëse kalimi është me kusht të shfaqet në ekran.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int piket;
  cout << "Jepni piket: ";
  cin  >> piket;
  if (piket >= 50) {
    cout << "Keni kaluar provimin";
  } else {
    cout << "Nuk keni kaluar provimin";
  }

  return 0;
}
```

---

**Detyrë:** Të lexohet nga tastiera një numër i plotë $x$. Të llogaritet dhe të shfaqet vlera $y$ sipas funksionit:

$$
y = \begin{cases}
2x - 3 & \text{kur}\; x \geq 7 \\
x^2 + 1 & \text{kur}\; x < 7
\end{cases}
$$

**Bonus:** Të shtohet rasti kur $x < 4$:

$$
y = \begin{cases}
2x - 3 & \text{kur}\; x \geq 7 \\
x^2 + 1 & \text{kur}\; 4 \leq x < 7 \\
3 \times |x-1| & \text{kur}\; x < 4
\end{cases}
$$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int x, y;
  cout << "Jepni x: ";
  cin  >> x;

  if (x >= 7) {
    y = 2 * x - 3;
  } else {
    y = x * x + 1;
  }

  cout << "y = " << y << endl;
  return 0;
}
```

---

**Detyrë:** Të lexohet nga tastiera një numër i plotë $x$. Të llogaritet vlera absolute e tij.

Definicioni i vlerës absolute:

$$
|x| = \begin{cases}
x & \text{kur}\; x \geq 0 \\
-x & \text{kur}\; x < 0
\end{cases}
$$

**Bonus:** Të llogaritet vlera absolute:

1. Pa përdorur kushtëzime.
2. Pa përdorur kushtëzime e as krahasime.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int x, absx;
  cout << "Jepni x: ";
  cin  >> x;

  if (x >= 0) {
    absx = x;
  } else {
    absx = -x;
  }

  cout << "|x| = " << absx << endl;
  return 0;
}
```

---

Kushtëzimi me shumë degë:

```cpp
if (kushti1) {
  blloku1;
} else if (kushti2) {
  blloku2;
} else if (kushti3) {
  blloku3;
} else {
  blloku4;
}
```

Ekzekutohet blloku i parë i cili përmbush kushtin përkatës. Nëse asnjëri kusht nuk përmbushet ekzekutohet blloku 4.

---

**Detyrë:** Të caktohet dhe të shfaqet nota varësisht nga numri i pikëve sipas tabelës:

Nota|Pikët
-|-
10|90+
9|80-89
8|70-79
7|60-69
6|50-59
5|Përfundi 50

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int piket, nota;
  cout << "Jepni piket: ";
  cin  >> piket;

  if (piket >= 90) {
    nota = 10;
  } else if (piket >= 80) {
    nota = 9;
  } else if (piket >= 70) {
    nota = 8;
  } else if (piket >= 60) {
    nota = 7;
  } else if (piket >= 50) {
    nota = 6;
  } else {
    nota = 5;
  }

  cout << "Nota: " << nota << endl;
  return 0;
}
```

---

**Detyrë:** Të lexohen dy numra të plotë nga tastiera. Të tregohet nëse të dy numrat janë pozitiv, të dytë negativ, të dytë zero, ose janë të përzier.

**Bonus:** Të tregohet nëse numrat janë të dytë çift, të dytë tek, ose të përzier.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a, b;

  cout << "Jepni numrin e pare: ";
  cin  >> a;
  cout << "Jepni numrin e dyte: ";
  cin  >> b;

  if (a > 0 && b > 0) {
    cout << "Te dy numrat jane pozitiv." << endl;
  } else if (a == 0 && b == 0) {
    cout << "Te dy numrat jane zero." << endl;
  } else if (a < 0 && b < 0) {
    cout << "Te dy numrat jane negativ." << endl;
  } else {
    cout << "Numrat jane te perzier." << endl;
  }

  return 0;
}
```

---

## Bllok diagramet

E paraqesin programin në formë vizuele.

---

Figurat i lidhim me shigjeta për ta përshkruar **algoritmin** tonë.

**Algoritëm** - rregullat dhe hapat logjik të një programi.

---

Urdhërat paraqiten me drejtkëndësha:

![](/lendet/gjuhe-programuese/java3/diag1.png) <!-- .element: style="border:none" -->

---

Hyrjet dhe daljet paraqiten me trapezoidët:

![](/lendet/gjuhe-programuese/java3/diag2.png) <!-- .element: style="border:none" -->

---

Kushtëzimet paraqiten me romb:

![](/lendet/gjuhe-programuese/java3/diag3.png) <!-- .element: style="border:none" -->

---

![](/lendet/gjuhe-programuese/java3/diag4.png) <!-- .element: style="border:none" -->

---

**Detyrë:** Të vizatohet bllok diagrami për llogaritjen dhe shfaqjen e shumës në vijim. Parametri $n$ të merret si vlerë hyrëse.

$$
S=\sum_{i=0}^{n}{(2i+3)}
$$

--

![](/lendet/gjuhe-programuese/java3/sum.png) <!-- .element: style="border:none;max-height:540px;" -->

---

## Detyra shtesë

---

**Detyrë:** Të lexohet një numër i plotë, dhe pastaj të shfaqet në formë decimale, heksadecimale, dhe oktale.

--

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
  int numri;
  cout << "Jepni numrin: ";
  cin  >> numri;

  cout << "Decimale: " << setbase(10) << numri << endl
       << "Heksadecimale: " << setbase(16) << numri << endl
       << "Oktale: " << setbase(8) << numri << endl;

  return 0;
}
```

---

**Detyrë:** Të lexohet një karakter nga tastiera. Të tregohet nëse ky karakter është shkronjë e madhe (A-Z), shkronjë e vogël (a-z), apo diçka tjetër.

**Bonus:** Të vizatohet bllok diagrami i këtij programi.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  char karakteri;

  cout << "Shtypni nje karakter: ";
  cin  >> karakteri;

  if (karakteri >= 'A' && karakteri <= 'Z') {
    cout << "Karakteri eshte shkronje e madhe." << endl;
  } else if (karakteri >= 'a' && karakteri <= 'z') {
    cout << "Karakteri eshte shkronje e vogel." << endl;
  } else {
    cout << "Karakteri eshte dicka tjeter." << endl;
  }

  return 0;
}
```

---

**Detyrë:** Të lexohen dy numra të plotë nga tastiera. Të tregohet nëse numrat janë të plotëpjestueshëm ndërmjet veti (nuk ka rëndësi cili me cilin).

```text
Shtypni a: 5
Shtypni b: 10
Numrat jane te plotepjestueshem.
```

```text
Shtypni a: 7
Shtypni b: 2
Numrat nuk jane te plotepjestueshem.
```

**Bonus:** Të vizatohet bllok diagrami i këtij programi.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a, b;

  cout << "Jepni numrin e pare: ";
  cin  >> a;
  cout << "Jepni numrin e dyte: ";
  cin  >> b;

  if (a % b == 0 || b % a == 0) {
    cout << "Numrat jane te plotepjestueshem." << endl;
  } else {
    cout << "Numrat nuk jane te plotepjestueshem." << endl;
  }

  return 0;
}
```