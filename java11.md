# Gjuhë Programuese - Java 11

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

Funksioni ka **domenin** dhe **rangun**.

- Domeni - cilat vlera i pranon funksioni?
- Rangu - çfare vlera kthen funksioni?

---

Funksioni në C++ nuk identifikohet vetëm nga **emri** por edhe nga **domeni**.

$$
\text{max}(a \in \mathbb{Z}, b \in \mathbb{Z}) \in \mathbb{Z}
$$

dhe:

$$
\text{max}(a \in \mathbb{Z}, b \in \mathbb{Z}, c \in \mathbb{Z}) \in \mathbb{Z}
$$

janë të ndryshme, edhe pse kanë emër të njejtë.

---

Konkretisht, kodi i mëposhtëm kompajllohet pa gabime.

```cpp
int max(int a, int b) {
  return a > b ? a : b;
}

int max(int a, int b, int c) {
  int max = a > b ? a : b;
  return max > c ? max : c;
}
```

Kjo lejohet sepse funksionet kanë domen të ndryshëm, edhe pse emri është i njejti.

---

Gjatë thirrjes së funksioneve të mbingarkuara, kompajlleri e identifikon funksionin e duhur duke shikuar **tipet** dhe **numrin** e argumenteve.

Mbingarkimet janë të dobishme kur kemi një bashkësi të veprimeve të ngjashme.

---

Shembull:

```cpp
double shuma(double a, double b) {
  return a + b;
}

int shuma(int a, int b) {
  return a + b;
}
```

Natyra e funksioneve `shuma` e llogaritë shumën e numrave `a` dhe `b`.

---

**Kujdes!** Funksioni nuk guxon të mbingarkohet vetëm përmes tipit kthyes:

```cpp
int shuma(int a, int b);
double shuma(int a, int b); // Gabim!
```

**Rikujtim:** Funksioni identifikohet nga **emri** dhe **parametrat** (domeni).

---

**Detyrë:** Të krijohet natyra e funksioneve `shuma`, ku funksionet marrin 2, 3, dhe 4 parametra të `int`.

E njejta të përsëritet edhe për tipin `double`.

--

```cpp
#include <iostream>
using namespace std;

int shuma(int a, int b) {
  return a + b;
}

int shuma(int a, int b, int c) {
  return a + b + c;
}

int shuma(int a, int b, int c, int d) {
  return a + b + c + d;
}

double shuma(double a, double b) {
  return a + b;
}

double shuma(double a, double b, double c) {
  return a + b + c;
}

double shuma(double a, double b, double c, double d) {
  return a + b + c + d;
}

int main() {
  int s2, s3, s4;

  s2 = shuma(3, 5);
  cout << "Shuma e dy numrave:" << s2 << endl;

  s3 = shuma(7, 12, 1);
  cout << "Shuma e tre numrave:" << s3 << endl;

  s4 = shuma(6, 1, 3, 5);
  cout << "Shuma e kater numrave:" << s4 << endl;

  return 0;
}
```

---

**Detyrë:** Të krijohet funksioni diskret dhe kontinual `f(x)` për shprehjen në vijim:

$$
f(x) = \dfrac{2x}{3}
$$

Të thirret ky funksion me vlerat `5` dhe `5.0` dhe të shfaqen rezultatet.

--

```cpp
#include <iostream>
using namespace std;

int f(int x) {
  return 2 * x / 3;
}

double f(double x) {
  return 2.0 * x / 3.0;
}

int main() {
  cout << f(5) << endl;
  cout << f(5.0) << endl;
  return 0;
}
```

---

**Direktivat paraprocesorike**

Rreshtat që fillojnë me `#` njihen si urdhëra paraprocesorik.

---

Urdhërat paraprocesorik ekzekutohen para se të fillojë kompajllimi i programit.

Një urdhër i thjeshtë është `#DEFINE` i cili zëvendëson tekstin me diçka tjetër - sikur find and replace në programet tekstuale.

---

**Shembull:**

```cpp
#define PI 3.14

...

cout << 2 * PI
```

Kudo që shihet `PI` zëvendësohet me 3.14

---

**Detyrë:** Të shkruhet funksionet `siperfaqja` dhe `perimetri` të cilat pranojnë vlerën e rrezës `r` dhe kthejnë sipërfaqen dhe perimetrin e rrethit. Vlera PI të definohet përmes `#define`.

--

```cpp
#include <iostream>
using namespace std;

#define PI 3.1415

double siperfaqja(double r) {
  return PI * r * r;
}

double perimetri(double r) {
  return 2 * PI * r;
}

int main() {
  double r;
  cout << "Jepni r: ";
  cin >> r;
  cout << "Siperfaqja: " << siperfaqja(r) << endl;
  cout << "Perimetri: " << perimetri(r) << endl;
  return 0;
}
```

---

Definimet shpesh përdoren për t'iu shoqëruar emra vlerave konstante numerike, psh PI.

Përveç kësaj, definimet janë të përshtatshme për t'i dhënë kuptim numrave sipas nevojave tona.

---

**Shembull:** Definimi i ngjyrave të semaforit:

```cpp
#define KUQE 0
#define VERDHE 1
#define GJELBER 2

void statusi(int ngjyra) {
  switch (ngjyra) {
    case KUQE:    cout << "Stop.";        break;
    case VERDHE:  cout << "Gati.";        break;
    case GJELBER: cout << "Nisu.";        break;
    default:      cout << "S'ka kuptim."; break;
  }
}
```

---

Më e kapshme është të themi `KUQE`, `VERDHE`, `GJELBER` sesa `0`, `1`,` 2`.

Gjithashtu zvogëlohet shanca për gabime.

---

Me këtë filozofi punojnë shkronjat dhe simbolet në kompjuter.

Shkronjës `A` i shoqërohet numri `65`, shkronjës `B` i shoqërohet numri `66`, etj...

---

Zëvendësimet përmes `#define` mund të jenë edhe parametrike. Këto njihen si macro, dhe zakonisht nuk preferohet përdorimi i tyre.

```cpp
#define max(a, b) (a > b ? a : b)

...

cout << max(2, 3);
```

Edhe pse thirrja e macros duket si funksion i zakonshëm, ajo në realitet zëvendësohet para kompajllimit me trupin e makros.

---

**Detyrë:** Të shkruhet macro `abs(x)` e cila zëvendësohet me shprehjen për vlerën absolute të x.

--

```cpp
#include <iostream>
using namespace std;

#define abs(x) ((x >= 0) ? (x) : -(x))

int main() {
  cout << abs(2 - 3);
  return 0;
}
```

---

## Detyra shtesë

---

Të shkruhen funksionet e mbingarkuara `shuma`. Funksioni i parë merr një varg ndërsa i dyti merr një matricë. Të dy funksionet kthejnë shumën e strukturës së dërguar.

--

```cpp
#include <iostream>
using namespace std;

#define N 4

int shuma(int v[], int m)
{
  int s = 0;
  for (int i = 0; i < m; i++)
  {
    s += v[i];
  }

  return s;
}

int shuma(int M[][N], int m)
{
  int s = 0;
  for (int i = 0; i < m; i++)
  {
    for (int j = 0; j < N; j++)
    {
      s += M[i][j];
    }
  }

  return s;
}

int main()
{
  int v[4] = { 1, 3, 2, 6 };
  cout << "Shuma e vektorit: "
       << shuma(v, 4 /* nr elementeve */)
       << endl;

  int M[3][N] = {
    { 3, 2, 7, 5 },
    { 5, 4, 3, 1 },
    { 3, 6, 2, 1 }
  };

  cout << "Shuma e matrices: " 
       << shuma(M, 3 /* nr rreshtave */)
       << endl;
  return 0;
}
```

---

Të shkruhet programi i cili definon të gjitha ditët e javës si konstante, dhe përmes një funksioni të bëhet switch vlera e ditës dhe shfaqet dita përkatëse.

--

```cpp
#include <iostream>
using namespace std;

#define DIELE 0
#define HENE 1
#define MARTE 2
#define MERKURE 3
#define ENJTE 4
#define PREMTE 5
#define SHTUNE 6

void shfaqDiten(int nr) {
  switch (nr) {
    case HENE:
      cout << "E hene";
      break;
    case MARTE:
      cout << "E marte";
      break;
    case MERKURE:
      cout << "E merkure";
      break;
    case ENJTE:
      cout << "E enjte";
      break;
    case PREMTE:
      cout << "E premte";
      break;
    case SHTUNE:
      cout << "E shtune";
      break;
    case DIELE:
      cout << "E diel";
      break;
    default:
      cout << "Gabim";
      break;
  }
}

int main() {
  int r;
  cout << "Jepni numrin e dites: ";
  cin >> r;
  shfaqDiten(r);
}
```

---

Të shkruhet funksioni i cili llogarit shprehjen:

$$
f(n,x) = \begin{cases}
\sum_{i=1}^{n}{i} \quad & x \geq 0 \\
\prod_{i=1}^{n}{i} \quad & x < 0
\end{cases}
$$

--

```cpp
#include <iostream>
using namespace std;

int f(int n, int x)
{
  int s = 0;
  int p = 1;

  for (int i = 1; i <= n; i++)
  {
    s = s + i;
    p = p * i;
  }

  if (x >= 0)
  {
    return s;
  }
  else
  {
    return p;
  }
}

int main()
{
  int n, x;
  cout << "Shtypni n: ";
  cin >> n;
  cout << "Shtypni x: ";
  cin >> x;
  cout << "f(n,x) = " << f(n, x);
  return 0;
}
```

---

Të shkruhen funksioni i cili llogarit produktin skalar të dy vargjeve.

--

```cpp
#include <iostream>
using namespace std;

int produktiSkalar(int a[], int b[], int n)
{
  int s = 0;
  for (int i = 0; i < n; i++)
  {
    s = s + a[i] * b[i];
  }

  return s;
}

int main()
{
  const int n = 5;
  int a[n] = {1, 0, 1, 4, 7};
  int b[n] = {34, 7, 7, 5, 1};
  cout << produktiSkalar(a, b, n) << endl;
  return 0;
}
```