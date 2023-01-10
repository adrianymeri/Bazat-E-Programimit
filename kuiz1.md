---
noslides: true
---

# Kuiz në C++

---

Si quhet pika hyrëse e programit? <input class="fill" data-answer="main" />

---

Si quhet tipi i numrit të plotë? <input class="fill" data-answer="int" />

---

Si quhet tipi i numrit me presje? <input class="fill" data-answer="double" />

---

Si quhet tipi i vërtetësisë? <input class="fill" data-answer="bool" />

---

Çfarë na mundësojnë variablat?

1. Transformimin e të dhënave.          <!-- [li]: class=choice; -->
2. Ruajtjen e përkohshme të të dhënave. <!-- [li]: class=choice correct; -->
3. Ruajtjen e përhershme të të dhënave. <!-- [li]: class=choice; -->
4. Shfaqjen në ekran.                   <!-- [li]: class=choice; -->

---

Çfarë shfaqet kur të ekzekutohet kodi në vijim? <input class="fill" data-answer="-10" />

```cpp
int x = 13;
int b = 6 % 2 + 3;
cout << (x > b ? b - x : x + b + 1);
```

---

Çfarë shfaqet kur të ekzekutohet kodi në vijim? <input class="fill" data-answer="jo" />

```cpp
int piket = 55 - 1;
piket -= 15 + 3;
if (piket > 50 || piket == 50) {
  cout << "po";
} else {
  cout << "jo";
}
```

---

Çfarë shfaqet kur të ekzekutohet kodi në vijim? <input class="fill" data-answer="-2" />

```cpp
int x = 5 / 2 + 1;
switch (x) {
  case 2:  cout << "-1"; break;
  case 3:  cout << "-2"; break;
  case 4:  cout << "-3"; break;
  default: cout << "-4"; break;
}
```

---

Çfarë shfaqet kur të ekzekutohet kodi në vijim? <input class="fill" data-answer="7" />

```cpp
const int n = 5;
int v[n] = { 3, 4, 1, -2, 4 };
int c = 2;
for (int i = 0; i < n; i++) {
  c += v[i] - 1;
}

cout << c;
```

---

Çfarë është funksioni?

1. Ruajtja e përkohshme e të dhënave. <!-- [li]: class=choice; -->
2. Transformimi i të dhënave.         <!-- [li]: class=choice correct; -->
3. Krahasimi i dy vlerave.            <!-- [li]: class=choice; -->
4. Dalja standarde e programit.       <!-- [li]: class=choice; -->

---

Çfarë shfaqet kur të ekzekutohet kodi në vijim? <input class="fill" data-answer="8" />

```cpp
#include <iostream>
#define VLERA 3

int f(int x) {
  if (x > VLERA + 2) {
    return x - VLERA;
  } else {
    return (VLERA - 1) * x;
  }
}

int main() {
  std::cout << "Rezultati = " << f(f(7));
  return 0;
}
```

---

Çfarë shfaqet kur të ekzekutohet kodi në vijim? <input class="fill" data-answer="21" />

```cpp
#include <iostream>

struct drejtkendeshi {
  int a;
  int b;
};

int katrori(int x) {
  return x * x;
}

drejtkendeshi ngritNeKatror(drejtkendeshi d) {
  return { katrori(d.a), katrori(d.b) };
}

int main() {
  drejtkendeshi d1 = { 5, 4 };
  drejtkendeshi d2 = ngritNeKatror(d1);
  std::cout << d2.a - d1.b;
  return 0;
}
```

---

Çfarë quajmë mbingarkim të funksionit?

1. Thirrjen e funksionit me shumë argumente. <!-- [li]: class=choice; -->
2. Kthimin e disa vlerave nga funksioni.     <!-- [li]: class=choice; -->
3. Disa funksione me të njejtin emër.        <!-- [li]: class=choice correct; -->
4. Kthimi i numrit me presje nga funksioni.  <!-- [li]: class=choice; -->

---

Kush konsiderohet faktor gjatë mbingarkimit të funksioneve?

1. Tipi kthyes.                   <!-- [li]: class=choice; -->
2. Vetëm numri i parametrave.     <!-- [li]: class=choice; -->
3. Vetëm lloji i parametrave.     <!-- [li]: class=choice; -->
4. Numri dhe lloji i parametrave. <!-- [li]: class=choice correct; -->

---

Cili është tipi kthyes për thirrjen e mbingarkimit `f(2)` në vijim? <input class="fill" data-answer="double" />

```cpp
bool f(int a, int b) {
  return a > b;
}

double f(int x) {
  return x + 2.5;
}

int f(double x) {
  return (int)x;
}
```

---

Çfarë shfaqet kur të ekzekutohet kodi në vijim? <input class="fill" data-answer="2500" />

```cpp
#include <iostream>

enum njesia { m, cm, mm };

double konverto(double metrat, njesia n) {
  switch (n) {
    case m:  return metrat;
    case cm: return metrat * 100.0;
    case mm: return metrat * 1000.0;
    default: return metrat;
  }
}

int main() {
  std::cout << konverto(2.5, mm);
  return 0;
}
```
