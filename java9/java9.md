# Gjuhë Programuese - Java 9

---

## Funksionet

---

Funksioni - një grup urdhërash me një emër të caktuar.

Deri tani kemi përdorur vetëm funksionin **main**.

---

Funksioni është diçka që transformon **hyrjet** në **daljet**.

$$
\begin{array}{rcl}
45° \rightarrow & \boxed{f(x)} & \rightarrow \frac{\sqrt{2}}{2} \\
6 \rightarrow & \boxed{g(x)} & \rightarrow 36 \\
\texttt{'c'} \rightarrow & \boxed{h(x)} & \rightarrow 3
\end{array}
$$

---

Funksioni $y = f(x)$ merr një parametër $x$, e transformon sipas rregullës $f(x)$ dhe kthen një rezultat $y$.

![](/lendet/gjuhe-programuese/java9/funksioni.png) <!-- .element: style="border:none" -->

---

Funksioni ka **domenin** dhe **rangun**.

$$
\begin{array} {ccrcl}
f(x) = x^2 & : & \mathbb{Z} & \rightarrow & \mathbb{Z}^+ \\ \\
g(a,b) = a + b & : & \mathbb{Z} \times \mathbb{Z} & \rightarrow & \mathbb{Z} \\ \\
h(a,b) = \dfrac{a}{b} & : & \mathbb{Z} \times (\mathbb{Z} \setminus \lbrace 0 \rbrace) & \rightarrow & \mathbb{R} \\ \\
\sin(x) & : & \mathbb{R} & \rightarrow & [-1, 1]
\end{array}
$$

---

**Shembull:** Funksioni **katrori** merr një numër të plotë dhe kthen katrorin e tij.

$$
\begin{array}{ccc}
2 & \Rightarrow & 4 \\
3 & \Rightarrow & 9 \\
5 & \Rightarrow & 25 \\
& \vdots & \\
x & \Rightarrow & x^2
\end{array}
$$

---

Funksioni `katrori` i shkruar formalisht:

$$
f(x) = x^2 \quad : \quad \mathbb{Z} \rightarrow \mathbb{Z}
$$

Interpretimi: **merr** një numër $x \in \mathbb{Z}$ dhe **kthe** një numër $x^2 \in \mathbb{Z}$.

---

Funksioni katrori: $f(x) = x^2$ shkruhet në këtë mënyrë:

```cpp
int katrori(int x) {
  return x * x;
}
```

Funksioni `katrori` merr një numër të plotë $x$ dhe kthen (return) një numër plotë.

$$
\overbrace{\texttt{int}}^{\text{tipi i daljes}}\underbrace{\texttt{katrori}}_{\text{emri i funksionit}}\texttt{(}\overbrace{\texttt{int x}}^{\text{tipi i hyrjes}}\texttt{)}\quad\texttt{\{}\quad\dots\quad\texttt{\}}
$$

---

"Thirrja" e funksionit:

```cpp
cout << "f(2) = " << katrori(2) << endl;
cout << "f(5) = " << katrori(5) << endl;
```

Na shfaqet:

```text
f(2) = 4
f(5) = 25
```

---

Kur thirret funksioni, blloku aktual i kodit pauzohet dhe rrjedha e ekzekutimit futet në bllokun e funksionit.

Funksioni mbaron kur ekzekutohet urdhëri `return`, me ç'rast kthehet rezultati dhe ekzekutimi vazhdon në bllokun prind.

---

Funksione kemi hasur në librari të ndryshme, psh:

- math.h: `pow`, `sin`, `sqrt`
- iomanip: `setw`, `setprecision`
- iostream: `system`

---

- Hyrjet e funksionit i quajmë **parametra**.
- Vlerat e dhëna gjatë thirrjes së funksionit i quajmë **argumente**.
- Rezultati i funksionit quhet **vlera e kthyer** (return value).

---

Përshkrimi formal i funksionit:

$$
f(\underbrace{x}_{\text{Parametri x}}) = \underbrace{x^2}_{\text{Vlera që kthehet}}
$$

Thirrja e funksionit:

$$
f(\underbrace{2}_{\text{Argumenti}}) = \underbrace{4}_{\text{Vlera e kthyer}}
$$

---

Raste të veçanta të funksioneve janë ato që nuk marrin asnjë vlerë ose nuk kthejnë asnjë vlerë.

Në këtë rast funksioni nuk është transformim i të dhënave, por është një sekuencë e urdhërave me qëllim të kryerjes së ndonjë pune.

Këto sekuenca njihen si **nënprograme**, **procedura**, ose **subrutina**. 

---

Mungesa e tipit pranues ose kthyes quhet **void**.

Void ka kuptimin e "vrimës" - mungon tipi.

```cpp
void pershendeteBoten(void) {
  cout << "Pershendetje Bote!";
}
```

Funksioni i mësipërm as nuk merr vlera e as nuk kthen vlera. Procedurat përdoren vetëm për të ekzekutuar "efektet anësore".

---

Përmes funksioneve krijojmë "komanda" të cilat mund t'i ripërdorim.

---

**Shembull:** Procedura `pause`:

```cpp
#include <iostream>
using namespace std;

void pause() {
  cout << "Press enter to continue . . . ";
  cin.sync();
  cin.ignore();
}

int main() {
  cout << "Pershendetje" << endl;
  pause(); // Thirrja e pause.
  return 0;
}
```

---

**Shembull:** Funksioni `shuma(n)`:

$$
\textit{shuma}(n) = \sum_{i=1}^{n}{i}
$$

```cpp
int shuma(int n) {
  int S = 0;
  for (int i = 1; i <= n; i++) {
    S += i;
  }
  return S;
}

int main() {
  cout << "Shuma nga 1 deri 5: " << shuma(5) << endl;
  return 0;
}
```

---

Funksioni ka **deklarimin** dhe **definimin**.

- Deklarimi na njofton për emrin dhe natyrën e funksionit.
- Definimi e përshkruan trupin e funksionit.

---

Në C++ është rregulla që gjatë thirrjes funksioni **duhet** të jetë i deklaruar dhe **mund** të jetë i definuar.

```cpp
int shuma(int n); // Deklarimi

int main() {
  cout << shuma(5) << endl;
  return 0;
}

int shuma(int n) { // Definimi
  int S = 0;
  for (int i = 1; i <= n; i++) {
    S += i;
  }
  return S;
}
```

---

**Detyrë:** Të shkruhet funksioni `faktorieli(n)` dhe të thirret me vlerat $3, 4, 5$:

$$
\textit{faktorieli}(n) = n!
$$

--

```cpp
#include <iostream>
using namespace std;

int faktorieli(int n) {
  int f = 1;
  for (int i = 1; i <= n; i++) {
    f = f * i;
  }

  return f;
}

int main() {
  cout << "3! = " << faktorieli(3) << endl;
  cout << "4! = " << faktorieli(4) << endl;
  cout << "5! = " << faktorieli(5) << endl;
  return 0;
}
```

---

**Detyrë:** Të shkruhet funksioni `kaKaluar(p)` i cili merr numrin e pikëve $p$ (`int`) dhe kthen nëse kalohet provimi me ato pikë ($p \geq 50$).

**Ndihmesë:** Tipi i kthimit duhet të jetë `bool`.

--

```cpp
#include <iostream>
using namespace std;

bool kaKaluar(int p) {
  if (p >= 50) {
    return true;
  } else {
    return false;
  }
}

int main() {
  if (kaKaluar(60)) {
    cout << "Studenti 1 kalon." << endl;
  } else {
    cout << "Studenti 1 nuk kalon." << endl;
  }
  
  if (kaKaluar(35)) {
    cout << "Studenti 2 kalon." << endl;
  } else {
    cout << "Studenti 2 nuk kalon." << endl;
  }

  return 0;
}
```

---

**Detyrë:** Të shkruhet procedura `lexoDheMbledh()` e cila lexon dy numra nga tastiera dhe kthen shumën e tyre.

--

```cpp
#include <iostream>
using namespace std;

int lexoDheMbledh() {
  int a, b;
  cin >> a;
  cin >> b;
  return a + b;
}

int main() {
  int shuma = lexoDheMbledh();
  cout << "Shuma: " << shuma << endl;
  return 0;
}
```

---

Funksioni quhet "i pastër" (pure) nëse nuk shkakton efekte anësore.

- Funksione të pastra: `faktorieli(n)`, `shuma(n)`, `kaKaluar(p)`.
- `lexoDheMbledh()` është i papastër pasi që lexon nga `cin`.
- `pershendeteBoten()` është i papastër pasi që shfaq në `cout`.

Funksionet e pastra gjithmonë marrin parametra dhe kthejnë vlera.

---

Funksionet mund të thirrin funksione tjera.

Nëse funksioni e thirrë vetveten ai njihet si funksion **rekursiv**.

---

**Shembull:** Funksioni rekursiv fibonacci:

$$
f(n) =
\begin{cases}
0 \; & \text{kur} \; n = 0 \\
1 \; & \text{kur} \; n = 1 \\
f(n-1) + f(n-2) \; & \text{kur} \; n > 1
\end{cases}
$$

---

**Detyrë:** Të shkruhet funksioni `max(a,b)` i cili merr dy numra dhe kthen numrin më të madh nga këta.

--

```cpp
#include <iostream>
using namespace std;

int max(int a, int b) {
  return a > b ? a : b;
}

int main() {
  cout << "max(3,5) = " << max(3,5) << endl;
  return 0;
}
```

---

**Detyrë:** Të shkruhet funksioni `clamp(v,min,max)` i cili e kufizon vlerën $v$ në intervalin $[\textit{min},\textit{max}]$.

--

```cpp
#include <iostream>
using namespace std;

double clamp(double v, double min, double max) {
  if (v < min) {
    return min;
  }

  if (v > max) {
    return max;
  }

  return v;
}

int main() {
  double v;
  cout << "Shtypni v (nga 1 deri 100): ";
  cin >> v;
  // Nese v eshte jashte 1-100 merret kufiri me i afert.
  cout << clamp(v, 1.0, 100.0);
  return 0;
}
```

---

**Detyrë:** Të shkruhet funksioni `f(n,x)` sipas formulës:

$$
f(n,x) = x + \sum_{i=1}^{n}{(3i + 2)}
$$

--

```cpp
#include <iostream>
using namespace std;

int f(int n, int x) {
  int s = 0;
  for (int i = 1; i <= n; i++) {
    s += 3 * i + 2;
  }

  return x + s;
}

int main() {
  int n, x;
  cout << "Shtypni n: ";
  cin >> n;
  cout << "Shtypni x: ";
  cin >> x;
  int s = f(n, x);
  cout << "s = " << s;
  return 0;
}
```

---

**Detyrë:** Të shkruhet funksionet `eshteCift(x)` dhe `eshteTek(x)` qe tregojnë nëse $x$ është çift/tek.

--

```cpp
#include <iostream>
using namespace std;

bool eshteCift(int nr) {
  return nr % 2 == 0;
}

bool eshteTek(int nr) {
  // E kthen te kunderten e eshteCift-it.
  // (kur nuk eshte cift atehere eshte tek)
  return !eshteCift(nr);
}

int main() {
  int nr;
  cout << "Shtypni numrin: ";
  cin >> nr;

  if (eshteCift(nr)) {
    cout << "Numri i dhene eshte cift." << endl;
  }

  if (eshteTek(nr)) {
    cout << "Numri i dhene eshte tek." << endl;
  }

  return 0;
}
```

---

**Detyrë:** Të shkruhet funksioni `f(a,b,c,x)` sipas formulës:

$$
f(a,b,c,x) = ax^2 + bx + c
$$

--

```cpp
#include <iostream>
using namespace std;

double f(double a, double b, double c, double x) {
  return a * x * x + b * x + c;
}

int main() {
  cout << "y = " << f(2.0, 1.5, 3.2, 6.1);
  return 0;
}
```

---

**Detyrë:** Të shkruhet funksioni fibonacci përmes rekursionit.

--

```cpp
#include <iostream>
using namespace std;

int fibonacci(int n) {
  if (n == 0) {
    return 0;
  } else if (n == 1) {
    return 1;
  } else {
    return fibonacci(n - 1) + fibonacci(n - 2);
  }
}

int main() {
  cout << "15 vlerat e para te serise fibonacci:" << endl;
  for (int i = 0; i <= 14; i++) {
    cout << fibonacci(i) << endl;
  }

  return 0;
}
```