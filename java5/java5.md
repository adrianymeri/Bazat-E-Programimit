# Gjuhë Programuese - Java 5

---

## Përsëritje

---

**Detyrë:** Çfarë do të shtypet kur ekzekutohet ky kod?

```cpp
#include <iostream> 
using namespace std;
int main()
{
  int x=2, y=3, a=3, b=2, g;
  bool s,t;
  if ((3*x+2*y) < (a+3*b)) s=true; else s=false;
  if ((y>(2*x)) && (x<=(2*y))) t=true; else t=false;
  g=(a>(2*b)) ? (3*a+b) : (a+2*b);
  cout<<"s="<<s<<", t="<<t<<", g="<<g<<endl;
  return 0;
}
```

--

```text
s=0, t=0, g=7

```

---

**Detyrë:** Çfarë do të shtypet kur ekzekutohet ky kod?

```cpp
#include <iostream>
#include <iomanip>
using namespace std;
int main()
{
  float x = 2, a = 4, b = 3, g;
  if ((2 * b) > a)
    if (x > (2 * b))
      g = 2 * a + 5 * b - 1;
    else
      g = x + 3;
  else
    g = b + 3 * x;
  cout << "\nRezultati g="
       << setw(5)
       << g
       << "\n";
  return 0;
}
```

--

```text

Rezultati g=    5
```

---

## Unazat

Unaza është koncepti i përsëritjes së bllokut.

---

**Unaza while**

1. Nëse **kushti**, ekzekuto **bllokun**.
2. Kthehu te hapi 1.

```cpp
while (kushti) {
  blloku;
}
```

A po vëreni ngjashmëri?

```cpp
if (kushti) {
  blloku;
}
```

---

<!-- .slide: style="font-size:0.9em;" -->

**`if`** ekzekuton bllokun 1 herë **nëse** vlen **kushti**.

**`while`** ekzekuton bllokun **derisa** vlen **kushti**.

![](/lendet/gjuhe-programuese/java5/while.png) <!-- .element: style="max-height:400px;border:none;" -->

---

**Shembull:** Numërimi nga 1 deri 5:

```cpp
int i = 1;
while (i <= 5) {
  cout << i << endl;
  i++;
}
```

Shfaqet:

```text
1
2
3
4
5
```

---

Duhet pasur kujdes që elementet e kushtit të ndryshojnë brenda bllokut të unazës.

Nëse nuk ndryshojnë, unaza mund të ekzekutohet pafundësisht.

Pse?

---

**Shembull:**

```cpp
int i = 1;
while (i <= 5) {
  cout << i << endl;
  // Kemi harruar ta ndryshojme i.
}
```

`i` gjithmonë ka vlerën 1, dhe programi nuk përfundon asnjëherë.

---

**Detyrë:** Të llogaritet vlera:

$$
z = \sum_{i=1}^{n}{i} + \prod_{i=1}^{n}{i}
$$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int i, n, S, P, z;
  cout << "Shtypni n: ";
  cin  >> n;

  i = 1;
  S = 0;
  P = 1;
  while (i <= n) {
    S += i;
    P *= i;
    i++;
  }
  
  z = S + P;
  cout << "z = " << z << endl;

  return 0;  
}
```

---

Brenda unazës kemi dy urdhëra të cilat mund të kontrollojnë rrjedhën e ekzekutimit.

1. **`continue`** - përsërite ciklin e unazës.
2. **`break`** - dil nga unaza.

---

Shumë shpesh unaza ka këtë formë:

```cpp
int i = 1; /* Inicializimi */
while (i < x) /* Kushti */ {
  blloku; /* Blloku */

  i++; /* Avansimi */
}
```

Për këtë arsye ekziston unaza **`for`**:

```cpp
for (inicializimi; kushti; avansimi) {
  blloku;
}
```

---

**Shembull:** Gjetja e shumës:

```cpp
int S = 0;
int i = 1; // a
while (i <= n) { // b
  S += i; 
  i++; // c
}
```

```cpp
int S = 0;
//   <---a--->  <--b--> <-c->
for (int i = 1; i <= n; i++) {
  S += i;
}
```

Unazat e mësipërme janë ekuivalente.

---

**Detyrë:** Të shkruhet programi i cili shfaq numrat tek nga $1$ deri $n$.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int n;
  cout << "Shtypni n: ";
  cin  >> n;

  for (int i = 1; i <= n; i++) {
    if (i % 2 != 0) {
      cout << i << endl;
    }
  }

  return 0;
}
```

---

**Unaza do while**

E ngjashme me unazën `while`, me dallimin që kushti vlerësohet në fund.

```cpp
do {
  blloku;
} while (kushti);
```

---

Blloku është i garantuar të ekzekutohet së paku një herë.

![](/lendet/gjuhe-programuese/java5/dowhile.png) <!-- .element: style="max-height:400px;border:none;" -->

---

**while** vs. **do while**:

![](https://i.redd.it/6wksqjmmyw321.jpg)  <!-- .element: style="max-height:400px;border:none;" -->

---

<!-- .slide: style="font-size:0.9em" -->

**Detyrë:** Të shkruhet programi dhe të tregohet dalja për $a=1,\; b=10,\; c=3$.

![](/lendet/gjuhe-programuese/java5/detyra1.png) <!-- .element: style="max-height:480px;border:none;" -->

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a, b, c;
  cout << "a=";
  cin >> a;
  cout << "b=";
  cin >> b;
  cout << "c=";
  cin >> c;
  int s = 0;
  int i = a;
  do {
    s = s + i;
    i = i + c;
    cout << "i=" << i
         << ", s=" << s
         << endl;
  } while (i <= b);
  return 0;
}
```

--

Dalja për $a=1,\; b=10,\; c=3$:

```text
i=4, s=1
i=7, s=5
i=10, s=12
i=13, s=22
```

---

<!-- .slide: style="font-size:0.7em" -->

**Detyrë:** Të kryhen veprimet e kërkuara në vijim në lidhje me kodin e dhënë.

1. Të tregohet se çka do të shtypet në ekran pas ekzekutimit të kodit.
2. Sa herë do të testohet kushti: `if (i % 3 == 0)` në kodin e dhënë?
3. Kodi i dhënë të rishkruhet duke përdorur unazën while.

```cpp
#include <iostream>
using namespace std;

int main()
{
  int a = 2, b = 12;
  double c = 0;
  for (int i = a; i <= b; i = i + 2)
    if (i % 3 == 0)
      continue;
    else
      c = c - i;
  cout << "c=";
  cout.width(5);
  cout.fill('x');
  cout << c << endl;
  return 0;
}
```

--

1) Rezultati në ekran.

```text
c=xx-24

```

--

2) Kushti do të testohet 6 herë.

--

3) Me unazën `while`:

```cpp
#include <iostream>
using namespace std;

int main()
{
  int a = 2, b = 12;
  double c = 0;
  int i = a;
  while (i <= b) {
    if (i % 3 == 0) {
      i = i + 2;
      continue;
    } else {
      c = c - i;
      i = i + 2;
    }
  }

  cout << "c=";
  cout.width(5);
  cout.fill('x');
  cout << c << endl;
  return 0;
}
```

---

**Unazat brenda unazave**

Ndonjëherë kërkohet që brenda një cikli të unazës të ekzekutohet ndonjë unazë tjetër.

```cpp
for (int i = 1; i <= 10; i++) {
  for (int j = 1; j <= 10; j++) {
    cout << "i=" << i << ", j=" << j << endl;
  }
}
```

Sa rreshta shfaqen në ekran?

---

## Detyra shtesë

---

**Detyrë:** Të llogaritet shuma:

$$
S = \sum_{\begin{array}{c}i=1\\i=\textit{tek},\;i\neq 5\end{array}}^{n}{(2i^2+5)}
$$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int n;
  cout << "n=";
  cin >> n;

  int S = 0;
  for (int i = 1; i <= n; i++) {
    if (i % 2 == 0 || i == 5) {
      continue;
    }

    S += 2 * i * i + 5;
  }

  cout << "S=" << S << endl;
  return 0;
}
```

---

**Detyrë:** Të shfaqet kjo figurë përmes unazave:

```text
*
**
***
****
*****
****
***
**
*
```

Gjerësia maksimale e figurës të lexohet nga tastiera.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int n;
  cout << "n=";
  cin >> n;

  for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= i; j++) {
      cout << "*";
    }

    cout << endl;
  }

  for (int i = n - 1; i >= 1; i--) {
    for (int j = 1; j <= i; j++) {
      cout << "*";
    }

    cout << endl;
  }

  return 0;
}
```

---

**Detyrë:** Të shfaqen 20 numrat e parë të serisë Fibonacci.

$$
1, 1, 2, 3, 5, 8, 13, 21, 34, ...
$$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a = 0;
  int b = 1;
  cout << a << endl
       << b << endl;

  for (int i = 0; i < 18; i++) {
    int c = a + b;
    a = b;
    b = c;
    cout << c << endl;
  }

  return 0;
}
```

---

**Detyrë:** Të llogaritet vlera $y$:

$$
y = 5x - 2 \prod_{\begin{array}{c}k=2\\k=\textit{cift}\end{array}}^{n}{(k+x)} + 3 \sum_{\begin{array}{c}i=1\\i=\textit{tek}\end{array}}^{m+n}{(2i+n)}
$$

$m,\;n,\;x$ janë hyrje nga tastiera.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int m, n, x, y;
  cout << "m=";
  cin >> m;
  cout << "n=";
  cin >> n;
  cout << "x=";
  cin >> x;

  int P = 1;
  int S = 0;

  for (int k = 2; k <= n; k += 2) {
    P *= k + x;
  }

  for (int i = 1; i <= m + n; i += 2) {
    S += 2 * i + n;
  }

  y = 5 * x - 2 * P + 3 * S;
  cout << "y=" << y << endl;

  return 0;
}
```

---

**Detyrë:** Të lexohet një numër i plotë nga tastiera. Të tregohet nëse ky numër është numër i thjeshtë.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int n;
  cout << "n=";
  cin >> n;

  bool nr_thjeshte = true;
  for (int i = 2; i < n; i++) {
    if (n % i == 0) {
      nr_thjeshte = false;
      break;
    }
  }

  if (nr_thjeshte) {
    cout << "n eshte numer i thjeshte" << endl;
  } else {
    cout << "n nuk eshte numer i thjeshte" << endl;
  }

  return 0;
}
```

---

**Detyrë:**

1. Të lexohen vazhdimisht numra nga tastiera.
2. Programi ndalon kur japim numër negativ.
3. Pas ndalimit të shfaqet shuma e numrave çift dhe shuma e numrave tek të lexuar.

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int shuma_cift = 0;
  int shuma_tek = 0;
  while (true) {
    int n;
    cin >> n;
    if (n < 0) {
      break;
    }

    if (n % 2 == 0) {
      shuma_cift += n;
    } else {
      shuma_tek += n;
    }
  }

  cout << "Shuma e nr cift: " << shuma_cift << endl
       << "Shuma e nr tek: " << shuma_tek << endl;
  return 0;
}
```

---

<!-- .slide: style="font-size:0.8em;" -->

**Detyrë:** Të zhvillohet një lojë e thjeshtë.

1. Loja gjeneron një numër sekret në intervalin $[1,100]$.
2. Shfrytëzuesi jep numër nga tastiera.
3. Nëse është më i madh se numri sekret, të shfaqet "Më i vogël".
4. Nëse është më i vogël se numri sekret, të shfaqet "Më i madh".
5. Nëse është sa numri sekret, të shfaqet "Keni fituar" dhe të tregohet numri i hapave.

**Ndihmesë:** Numri i rastit gjenerohet me kodin:

```cpp
#include <stdlib.h>
#include <time.h>
...
srand(time(0));
int nr_sekret = rand() % 100 + 1;
```

--

```cpp
#include <iostream>
#include <stdlib.h>
#include <time.h>
using namespace std;

int main() {
  srand(time(0));
  int nr_sekret = rand() % 100 + 1;

  int provat = 0;
  while (true)  { 
    provat++;

    int n;
    cout << "Jepni n: ";
    cin >> n;
    if (n == nr_sekret) {
      break;
    } else if (n > nr_sekret) {
      cout << "Me i vogel" << endl;
    } else {
      cout << "Me i madh" << endl;
    }
  }

  cout << "E qelluat numrin me "
       << provat << " prova." << endl;
  return 0;
}
```
