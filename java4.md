# Gjuhë Programuese - Java 4

---

## Përsëritje

1. Çfarë janë **shprehjet e vërtetësisë**?
2. Çfarë mundësojnë **kushtëzimet**?
3. Çfarë janë **bllok diagramet**?

--

1. Çdo shprehje që ka përgjigjen **po** ose **jo** është **shprehje e vërtetësisë**.
2. **Kushtëzimet** mundësojnë ekzekutimin e blloqeve të kodit vetëm nëse plotësohen kushtet e caktuara.
3. **Bllok diagramet** janë paraqitje vizuele e **algoritmit** të programit.

---

## Shprehjet e kushtëzuara, switch, goto

---

**Operatori ternar (`?`)**

Shpesh kemi kushtëzimin me dy degëzime si në vijim:

```cpp
if (kushti) {
  y = shprehja1;
} else {
  y = shprehja2;
}
```

Këtë mund ta thjeshtojmë në:

```cpp
y = kushti ? shprehja1 : shprehja2;
```

---

Urdhëri:

```cpp
y = kushti ? shprehja1 : shprehja2
```

interpretohet kështu:

$$
y = \begin{cases}
shprehja1 & \text{nëse}\; \textit{kushti} \\
shprehja2 & \text{nëse jo}
\end{cases}
$$

---

Nga definicioni i vlerës absolute:

$$
|x| = \begin{cases}
x & \text{kur}\; x \geq 0 \\
-x & \text{kur}\; x < 0
\end{cases}
$$

Në kod shkruhet kështu:

```cpp
vlera_absolute = (x >= 0 ? x : -x);
```

---

**`(a > b ? a : b)`** është shprehje.

Pse?

---

**`(a ? b : c)`** është **shprehje** e cila mund të përdoret kudo që kemi **RValue**.

Jep vlerën ose **`b`** ose **`c`**, varësisht a vlen kushti **`a`**.

```cpp
cout << (piket >= 50 ? "Keni kaluar" : "Nuk keni kaluar");

vlera_absolute = (x >= 0 ? x : -x);
```

---

**Shembull:** Gjetja e vlerës maksimale.

```cpp
int a, b, max;
cin >> a;
cin >> b;
max = a > b ? a : b;
cout << "Maksimumi është: " << max;
```

---

**Detyrë:** Të lexohen dy numra nga tastiera. Të shfaqet numri më i madh nga këta dy.

**Bonus:** Të gjendet maksimumi i 3 numrave.

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

  cout << "Maksimumi eshte: "
       << (a > b ? a : b)
       << endl;

  return 0;
}
```

---

**Detyrë:** Të lexohet një numër i plotë nga tastiera, dhe të tregohet nëse ai numër është çift apo tek.

```text
Shtypni numrin: 7
Keni shtypur numer tek.
```

**Bonus:** Të lexohen 5 numra të plotë dhe të gjendet shuma e numrave tek dhe çift.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int numri;

  cout << "Shtypni numrin: ";
  cin  >> numri;

  cout << "Keni shtypur numer "
       << (numri % 2 == 0 ? "cift" : "tek")
       << "." << endl;

  return 0;
}
```

---

**Detyrë:** Të lexohet nga tastiera një numër i plotë $x$. Të llogaritet dhe të shfaqet vlera $y$ sipas funksionit:

$$
y = \begin{cases}
-4x + 3 & \text{kur}\; x \leq 3 \\
x - 5 & \text{kur}\; x > 3
\end{cases}
$$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int x, y;
  cout << "Shtypni x: ";
  cin  >> x;
  y = x <= 3 ? -4 * x + 3 : x - 5;
  cout << "y = " << y << endl;
  return 0;
}
```

---

## Urdhëri switch

E krahason një shprehje me një listë të vlerave.

---

```cpp
switch (vlera) {
  case 1:
    blloku1;
    break;
  case 2:
    blloku2;
    break;
  default:
    blloku3;
    break;
}
```

1. Kur `vlera == 1` ekzekutohet `blloku1`.
2. Kur `vlera == 2` ekzekutohet `blloku2`.
3. Në rastet tjera ekzekutohet `blloku3`.

---

Kodet në vazhdim janë ekuivalente:

```cpp
switch (vlera) {
  case 1:
    blloku1;
    break;
  case 2:
    blloku2;
    break;
  default:
    blloku3;
    break;
}
```

```cpp
if (vlera == 1) {
  blloku1;
} else if (vlera == 2) {
  blloku2;
} else {
  blloku3;
}
```

---

![](https://www.tutorialspoint.com/cprogramming/images/switch_statement.jpg) <!-- .element: style="border:none" -->

---

<!-- .slide: style="font-size:0.7em;" -->

**Shembull:**

```cpp
switch (nota) {
  case 5:
    cout << "Shkelqyeshem.";
    break;
  case 4:
    cout << "Shume mire.";
    break;
  case 3:
    cout << "Mire.";
    break;
  case 2:
    cout << "Mjaftueshem.";
    break;
  case 1:
    cout << "Dobet.";
    break;
  default:
    cout << "Nuk ka kuptim.";
    break;
}
```

---

Rastet mund të bashkohen:

```cpp
switch (dita) {
  case 1:
  case 2:
  case 3:
  case 4:
  case 5:
    cout << "Dite pune";
    break;
  case 6:
  case 7:
    cout << "Dite pushimi";
    break;
}
```

---

**Detyrë:** Të lexohen dy numra dhe një karakter. Varësisht nga karakteri, të llogaritet:

Karakteri|Shprehja
---|---
`+`|`a + b`
`-`|`a - b`
`*`|`a * b`
`/`|`a / b`
`%`|`a % b`

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a, b, c;
  char v;

  cout << "Jepni a: ";
  cin  >> a;
  cout << "Jepni veprimin: ";
  cin  >> v;
  cout << "Jepni b: ";
  cin  >> b;

  switch (v) {
    case '+':
      c = a + b;
      break;
    case '-':
      c = a - b;
      break;
    case '*':
      c = a * b;
      break;
    case '/':
      c = a / b;
      break;
    case '%':
      c = a % b;
      break;
    default:
      cout << "Karakter jo-valid.";
      return 1; // Mbyllim programin me gabim.
  }

  cout << "Rezultati: " << c << endl;
  return 0;
}
```

---

**Detyrë:** Të lexohet një numër i plotë. Të shfaqet muaji i vitit që ka atë numër.

```text
Jepni numrin e muajit: 3
Numri 3 i korrespondon muajit mars.
```

--

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
  int n;
  string muaji;

  cout << "Jepni numrin e muajit: ";
  cin  >> n;

  switch (n) {
    case 1:
      muaji = "janar";
      break;
    case 2:
      muaji = "shkurt";
      break;
    case 3:
      muaji = "mars";
      break;
    case 4:
      muaji = "prill";
      break;
    case 5:
      muaji = "maj";
      break;
    case 6:
      muaji = "qershor";
      break;
    case 7:
      muaji = "korrik";
      break;
    case 8:
      muaji = "gusht";
      break;
    case 9:
      muaji = "shtator";
      break;
    case 10:
      muaji = "tetor";
      break;
    case 11:
      muaji = "nentor";
      break;
    case 12:
      muaji = "dhjetor";
      break;
    default:
      cout << "Keni shtypur numer jo-valid.";
      return 1;
  }

  cout << "Numri " << n
       << " i korrespondon muajit " << muaji
       << "." << endl;
  return 0;
}
```

---

## Urdhëri goto

Bën kërcim të pa-kushtëzuar të ekzekutimit.

Na mundëson përsëritjen e kodit - unazat.

---

**Labela:** Vendos pozitë ku mund të kërcejmë.

```cpp
int i = 0, S = 0, n;
cin >> n;

mbledhja:
S = S + i;
i = i + 1;

if (i <= n) {
  goto mbledhja;
}

cout << "Shuma S=" << S << endl;
```

---

**Detyrë:** Të llogaritet vlera:

$$
S = \sum_{i=1}^{n}{i}
$$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int i, S, n;
  cout << "Shtyp n: ";
  cin  >> n;

  i = 1;
  S = 0;

  mbledhja:
  S += i;
  i++;

  if (i <= n) {
    goto mbledhja;
  }

  cout << "S = " << S << endl;
  return 0;
}
```

---

**Detyrë:** Të llogaritet vlera:

$$
P = n! = \prod_{i=1}^{n}{i}
$$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int i, P, n;
  cout << "Shtyp n: ";
  cin  >> n;

  i = 1;
  P = 1;

  shumezimi:
  P *= i;
  i++;

  if (i <= n) {
    goto shumezimi;
  }

  cout << "P = " << P << endl;
  return 0;
}
```

---

## Detyra shtesë

---

**Detyrë:**

1. Të lexohet numri i pikëve $p$ nga tastiera.
2. Nëse `cin.eof() == true` të mbyllet programi.
3. Të shqyrtohet vlera e $p$:
    - Nëse $p<0$ të mbyllet programi.
    - Nëse $p\geq 50$ të shfaqet "Kalon provimin."
    - Nëse $p<50$ të shfaqet "Nuk kalon provimin.".
4. Kthehu te hapi 1.

**Bonus:** Të shfaqet nota varësisht nga pikët.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int p;

  lexo:
  cin >> p;
  if (!cin.eof() && p > 0) {
    cout << (p >= 50 ? "Kalon provimin." : "Nuk kalon provimin.") 
         << endl;
    goto lexo;
  }

  return 0;
}
```
