# Gjuhë Programuese - Java 10

---

## Funksionet (vazhdim)

---

**Rikujtim:** Funksioni është një bllok i parametrizuar i urdhërave i cili mund të kthejë vlerë.

```cpp
int mbledh(int a, int b) {
  return a + b;
}
```

$$
\text{mbledh}(a \in \mathbb{Z} , b \in \mathbb{Z}) = (a + b) \in \mathbb{Z}
$$

---

Variablat hyrëse i quajmë **parametra**, ndërsa vlerat konkrete gjatë thirrjes së funksionit i quajmë **argumente**.

```cpp
// mbledh merr parametrat a dhe b
int mbledh(int a, int b) {
  return a + b;
}

...
// mbledh eshte thirrur me argumentet 2 dhe 3
mbledh(2, 3);
```

---

**Variablat lokale**

Gjatë kryerjes së llogaritjeve brenda funksionit mund të përdorim variabla, psh. `int S = 0`.

Këto variabla shihen vetëm nga blloku aktual i funksionit, prandaj quhen **variabla lokale**.

---

**Shembull:**

```cpp
int shuma(int n) {
  int S = 0; // variabel lokale
  for (int i = 1; i <= n; i++) {
    S += i;
  }

  return S;
}

int main() {
  cout << S; // gabim!
  return 0;
}
```

---

**Detyrë:** Çfarë shfaqet kur ekzekutohet ky kod?

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

--

```text
-2
```

---

**Variablat globale**

Variablat që shihen nga të gjitha funksionet quhen **variabla globale**.

**Shembull:** `cout` është variabël globale që i referohet daljes standarde.

---

**Shembull:**

```cpp
int S = 0;

void rritShumen(int v) {
  S += v;
}

int main() {
  rritShumen(4);
  cout << S << endl; // shfaqet 4
  rritShumen(3);
  cout << S << endl; // shfaqet 7
  return 0;
}
```

---

Variablat globale janë të rrezikshme pasi që gjithkush ka qasje që t'i ndryshojë.

Ndryshimi i papritur i ndonjë variable mund të shkaktojë defekte në program.

---

**Detyrë:** Të llogaritet shprehja e mëposhtme duke definuar dhe përdorur funksionin `shuma`.

$$
S = \sum_{i=3}^{8}{i} + \sum_{i=2}^{6}{i}
$$

--

```cpp
#include <iostream>
using namespace std;

int shuma(int a, int b) {
  int S = 0;
  for (int i = a; i <= b; i++) {
    S += i;
  }

  return S;
}

int main() {
  int S = shuma(3, 8) + shuma(2, 6);
  cout << "S = " << S << endl;
  return 0;
}
```

---

**Detyrë:** Të krijohet libraria `funksionet.h` e cila ofron funksionet `shuma(v,n)`, `mesatarja(v,n)`, `max(v,n)`, dhe `min(v,n)`.

Nga fajlli `main.cpp` të thirren këto funksione me vektorin $v=\lbrace 4, 2, 6, 7, 1 \rbrace$

--

`funksionet.h`:

```cpp
int shuma(int v[], int n);
double mesatarja(int v[], int n);
int max(int v[], int n);
int min(int v[], int n);
```

--

`funksionet.cpp`:

```cpp
int shuma(int v[], int n) {
  int s = 0;
  for (int i = 0; i < n; i++) {
    s += v[i];
  }

  return s;
}

double mesatarja(int v[], int n) {
  return (double)shuma(v, n) / n;
}

int max(int v[], int n) {
  int m = v[0];
  for (int i = 1; i < n; i++) {
    if (v[i] > m) {
      m = v[i];
    }
  }

  return m;
}

int min(int v[], int n) {
  int m = v[0];
  for (int i = 1; i < n; i++) {
    if (v[i] < m) {
      m = v[i];
    }
  }

  return m;
}
```

--

`main.cpp`:

```cpp
#include <iostream>
#include "funksionet.h"
using namespace std;

int main() {
  const int n = 6;
  int v[n] = { 4, 2, 6, 7, 1 };
  cout << "Shuma: " << shuma(v, n) << endl;
  cout << "Mesatarja: " << mesatarja(v, n) << endl;
  cout << "Maksimumi: " << max(v, n) << endl;
  cout << "Minimumi: " << min(v, n) << endl;
  return 0;
}
```