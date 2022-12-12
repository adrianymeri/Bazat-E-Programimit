# Gjuhë Programuese - Java 7

---

## Përsëritje

---

**Detyrë:** Të gjendet shuma e numrave çift nga $2$ deri në $n$.

--

Mënyra e parë:

```cpp
#include <iostream>
using namespace std;

int main()
{
  int n;
  cout << "n=";
  cin >> n;

  int S = 0;
  for (int i = 2; i <= n; i += 2) {
    S += i;
  }

  cout << "S=" << S << endl;
  return 0;
}
```

--

Mënyra e dytë:

```cpp
#include <iostream>
using namespace std;

int main()
{
  int n;
  cout << "n=";
  cin >> n;

  int S = 0;
  for (int i = 2; i <= n; i ++) {
    if (i % 2 == 0) {
      S += i;
    }
  }

  cout << "S=" << S << endl;
  return 0;
}
```

---

Te shkruhet programi i cili:

1. E deklaron një varg 5 anëtaresh të tipit numër i plotë.
2. E mbush këtë varg me vlera nga tastiera.
3. E llogarit mesataren e elementeve.
4. E gjen elementin maksimal dhe minimal.

--

```cpp
#include <iostream>
using namespace std;

int main()
{
  const int n = 5;

  // 1. Deklarimi i vargut.
  int v[n];

  // 2. Leximi nga tastiera.
  for (int i = 0; i < n; i++)
  {
    cout << "Shtypni elementin V["
         << i + 1 << "]: ";
    cin >> v[i];
  }

  // 3. Mesatarja
  int s = 0;
  for (int i = 0; i < n; i++)
  {
    s += v[i]; // llogarisim shumen
  }

  double mes = (double)s / n;
  cout << "Mesatarja: " << mes << endl;

  // 4. Max dhe min

  // min
  int min = v[0];
  for (int i = 0; i < n; i++)
  {
    if (v[i] < min) {
      min = v[i];
    }
  }

  cout << "Minimumi: " << min << endl;

  // max
  int max = v[0];
  for (int i = 0; i < n; i++)
  {
    if (v[i] > max) {
      max = v[i];
    }
  }

  cout << "Maksimumi: " << max << endl;

  return 0;
}
```

---

Të lexohen 7 numra nga tastiera

1. Numrat guxojnë te jenë ndërmjet 1 dhe 30.
2. Te numërohen numrat e thjeshtë në këtë varg.
3. Të numërohen sa elemente janë mbi mesatare.
