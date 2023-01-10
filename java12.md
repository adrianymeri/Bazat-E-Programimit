# Gjuhë Programuese - Java 12

---

## Përsëritje

---

**Detyrë:** Çfarë shfaqet kur ekzekutohet ky kod?

```cpp
#include <iostream>

void f(int a) {
  a = a - 1;
}
int main() {
  int a = 8;
  f(a);
  std::cout << a;
}
```

--

```text
8
```

---

**Detyrë:** Çfarë shfaqet kur ekzekutohet ky kod?

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

--

```text
6
```

---

**Detyrë:** Çfarë shfaqet kur ekzekutohet ky kod?

```cpp
#include <iostream>

int f(int x) {
  return 2 * x;
}
int g(int x) {
  return x + 3;
}
int main() {
  std::cout << f(g(3));
}
```

--

```text
12
```

---

**Detyrë:** Çfarë shfaqet kur ekzekutohet ky kod?

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

--

```text
20
```

---

**Detyrë:** Çfarë shfaqet kur ekzekutohet ky kod?

```cpp
#include <iostream>
#define A 3

int f(int a) {
  a = a + A;
  return A + a;
}
int main() {
  int a = A;
  std::cout << f(a * A);
}
```

--

```text
15
```

---

## Numërimet

Numërim quajmë një bashkësi të vlerave.

---

Marrim ngjyrat e semaforit: kuqe, verdhë, gjelbër.

Në program këtë e paraqitshim duke ia shoqëruar ngjyrës nga një vlerë numerike:

Ngjyra|Kodi
-|-
Kuqe|0
Verdhë|1
Gjelbër|2

---

**Numërim** quajmë tipin që merr vlera nga një bashkësi diskrete.

$$
\text{Ngjyrat}= \lbrace \textit{Kuqe}, \textit{Verdhe}, \textit{Gjelber} \rbrace
$$

Prapa skenave vlerave iu shoqërohen shifra.

---

Numërimet i kemi realizuar përmes `#define`:

```cpp
#define KUQE 0
#define VERDHE 1
#define GJELBER 2

...

int ngjyra = KUQE;
if (ngjyra == GJELBER) {
  ...
}
```

---

Ekziston edhe mundësia me `enum`:

```cpp
enum Ngjyra {
  kuqe,
  verdhe,
  gjelber
};

...

Ngjyra n = kuqe;
if (n == gjelber) {
  ...
}
```

---

Përmes `enum` krijojmë tip të vërtetë, ndërkaq me `#define` bëjmë zëvendësime paraprocesorike.

Kur kemi nevojë ta ruajmë një `Ngjyra`, e deklarojmë variablen e tipit `Ngjyra`:

```cpp
Ngjyra x = kuqe;
```

---

Kompajlleri anëtarëve iu cakton vlera rendore $0, 1, 2, \dots$

Nëse kemi nevojë t'iu japim anëtarëve vlera tjera, i cekim manualisht:

```cpp
enum Ngjyra {
  kuqe = 10,
  verdhe = 20,
  gjelber = 30
};
```

---

Sa e ka vlerën `gjelber` në këtë rast?

```cpp
enum Ngjyra {
  kuqe = 10,
  verdhe = 20,
  gjelber
};
```

---

Kur nuk ceket vlera, anëtari e merr vlerën e ardhshme të lirë pas anëtarit të kaluar.

Kështu që `gjelber = 21`

---

**Shembull:** Rajonet e targave të Kosovës.

```cpp
enum Rajoni {
  Prishtine = 1,
  Mitrovice = 2,
  Peje      = 3,
  Prizren   = 4,
  Ferizaj   = 5,
  Gjilan    = 6,
  Gjakove   = 7
};
```

---

```cpp
void shfaqRajonin(Rajoni r) {
  switch (r) {
    case Prishtine: cout << "Rajoni i Prishtines"; break;
    case Mitrovice: cout << "Rajoni i Mitrovices"; break;
    case Peje:      cout << "Rajoni i Pejes";      break;
    ...
  }
}

...

shfaqRajonin(Peje);
```

---

**Shembull:** Niveli i studimeve:

```cpp
enum NiveliStudimeve {
  Fillore,
  Mesme,
  Bachelor,
  Master,
  Doktorature
};
```

---

**Shembull:** Drejtimet gjeografike:

```cpp
enum Drejtimi {
  Veri,
  VeriLindje,
  Lindje,
  JugLindje,
  Jug,
  JugPerendim,
  Perendim,
  VeriPerendim
};
```

---

**Detyrë:**

1. Të deklarohet numërimi `Muaji` i cili ka vlerat $\text{janar} = 1, \text{shkurt} = 2, \dots$
2. Të deklarohet numërimi `Stina` e cila ka vlerat $\text{pranvere}, \text{vere}, \text{vjeshte}, \text{dimer}$
3. Të shkruhet funksioni `merrStinen` i cili pranon një `Muaji` dhe kthen `Stina` e atij muajit.
4. Të shkruhet funksioni `shfaqStinen` i cili pranon një `Stina` dhe e shfaq në ekran. 
5. Të thirren funksionet me $m=\text{prill}$

--

```cpp
#include <iostream>
using namespace std;

enum muaji
{
  janar = 1,
  shkurt,
  mars,
  prill,
  maj,
  qershor,
  korrik,
  gusht,
  shtator,
  tetor,
  nentor,
  dhjetor
};

enum stina
{
  pranvere,
  vjeshte,
  vere,
  dimer
};

stina merrStinen(muaji m)
{
  switch (m)
  {
  case dhjetor:
  case janar:
  case shkurt:
    return dimer;
  case mars:
  case prill:
  case maj:
    return pranvere;
  case qershor:
  case korrik:
  case gusht:
    return vere;
  default:
    return vjeshte;
  }
}

void shfaqStinen(stina s)
{
  switch (s)
  {
  case pranvere:
    cout << "Stina e pranveres" << endl;
    break;
  case vere:
    cout << "Stina e veres" << endl;
    break;
  case vjeshte:
    cout << "Stina e vjeshtes" << endl;
    break;
  case dimer:
    cout << "Stina e dimrit" << endl;
    break;
  }
}

int main()
{
  Muaji m = Prill;
  Stina s = merrStinen(m);
  shfaqStinen(s);
  return 0;
}
```

---

## Strukturat

Struktura është një grupim logjik i variablave.

---

Supozojmë që duhet ta plotësojmë një formular:

Fusha|Vlera
-|-
Emri|Filan
Mbiemri|Fisteku
Mosha|22
Jeni student?|Po

---

Këto fusha paraqesin grupimin logjik për të dhënat personale të një `Personi`.

---

Secila fushë e këtij grupimi ka një tip të të dhënave:

Fusha|Tipi
-|-
Emri|string
Mbiemri|string
Mosha|int
Jeni student?|bool

---

Në C++ ky grup i të dhënave modelohet kështu:

```cpp
struct Personi {
  string Emri;
  string Mbiemri;
  int Mosha;
  bool Student;
};
```

---

Kur kemi nevojë të ruajmë të dhënat e një `Personi`, e deklarojmë një variabël të këtij tipi:

```cpp
Personi p;
p.Emri = "Filan";
p.Mbiemri = "Fisteku";
p.Mosha = 22;
p.Student = true;
```

---

Ekziston një formë e shkurtë për inicializimin e strukturës:

```cpp
Personi p = {
  "Filan",
  "Fisteku",
  22,
  true
}
```

---

Strukturat përdorën kur kemi nevojë ta dërgojmë ose ta kthejmë një grup logjik të të dhënave në vend se vetëm një tip të thjeshtë (int, bool, etj.).

---

**Shembull:** Struktura `Data` është grupim logjik i `Viti`, `Muaji`, `Dita`:

```cpp
struct Data {
  int Dita;
  int Muaji;
  int Viti;
};

int main() {
  Data pavaresise = { 17, 2, 2008 };
}
```

---

Kur themi `Data d` nuk bëhet për ndonjë tip të thjeshtë si psh. `int` ose `double`, por për grupimin e tre numrave të plotë (`Dita`, `Muaji`, `Viti`):

Dita|Muaji|Viti
:-:|:-:|:-:
17|02|2008

---

Funksionet mund t'i përdorin tipet tona:

```cpp
Data sot() {
  Data d = { ... };
  return d;
}

void shtyp(Data d) {
  cout << d.Dita << "/" << d.Muaji << "/" << d.Viti;
}

int main() {
  shtyp(sot());
}
```

---

**Detyrë:** Të deklarohet struktura `Rezultati` me fushat `PiketShkrim`, `PiketGoje`. Të deklarohet një variabël e këtij tipi dhe të mbushet nga tastiera. Pastaj të tregohet a kalohet provimi me ato pikë.

--

```cpp
#include <iostream>
using namespace std;

struct Rezultati
{
  int PiketMeShkrim;
  int PiketMeGoje;
};

int main()
{
  Rezultati r;
  cout << "Shtypni piket me shkrim: ";
  cin >> r.PiketMeShkrim;
  cout << "Shtypni piket me goje: ";
  cin >> r.PiketMeGoje;

  if (r.PiketMeShkrim >= 50 && r.PiketMeGoje >= 50)
  {
    cout << "Kalon";
  }
  else
  {
    cout << "Nuk kalon";
  }

  return 0;
}
```

---

**Detyrë:** Të deklarohet struktura `Rezultati` sikur në detyrën e kaluar, por secili hap i kërkuar nga detyra të realizohet me nga një funksion.

--

```cpp
#include <iostream>
using namespace std;

struct Rezultati
{
  int PiketMeShkrim;
  int PiketMeGoje;
};

Rezultati lexo()
{
  Rezultati r;
  cout << "Shtypni piket me shkrim: ";
  cin >> r.PiketMeShkrim;
  cout << "Shtypni piket me goje: ";
  cin >> r.PiketMeGoje;
  return r;
}

bool kalues(Rezultati r)
{
  if (r.PiketMeShkrim >= 50 && r.PiketMeGoje >= 50)
  {
    return true;
  }
  else
  {
    return false;
  }
}

int main()
{
  Rezultati r = lexo();
  if (kalues(r))
  {
    cout << "Kalon";
  }
  else
  {
    cout << "Nuk kalon";
  }

  return 0;
}
```

---

**Detyrë:** Të deklarohet struktura `NumerKompleks` me fushat `a` dhe `b` si dhe funksionet `mbledh`, `zbrit`, `shumezo`, `rrezja`, `kendi`.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/af/Complex_number_illustration.svg/223px-Complex_number_illustration.svg.png)  <!-- .element: style="border:none" -->

--

```cpp
#include <iostream>
#include <math.h>
using namespace std;

struct NumerKompleks
{
  double a;
  double b;
};

NumerKompleks mbledh(NumerKompleks nr1, NumerKompleks nr2)
{
  return {nr1.a + nr2.a, nr1.b + nr2.b};
}

NumerKompleks zbrit(NumerKompleks nr1, NumerKompleks nr2)
{
  return {nr1.a - nr2.a, nr1.b - nr2.b};
}

NumerKompleks shumezo(NumerKompleks nr1, NumerKompleks nr2)
{
  return {
      nr1.a * nr2.a - nr1.b * nr2.b,
      nr1.a * nr2.b + nr2.a * nr1.b};
}

double rrezja(NumerKompleks nr)
{
  return sqrt(pow(nr.a, 2) + pow(nr.b, 2));
}

double kendi(NumerKompleks nr)
{
  return atan(nr.b / nr.a);
}

void shfaq(NumerKompleks nr)
{
  cout << nr.a << " + j" << nr.b << endl;
}

int main()
{
  NumerKompleks x = {2, 3};
  NumerKompleks y = {4, 5};
  NumerKompleks rez = mbledh(x, y);
  shfaq(rez);
}
```

---

**Detyrë:** Të deklarohet struktura `Data`. 

1. Të shkruhet funksioni `konstrukto(viti, muaji, dita)` i cili krijon datën nga parametrat e dhënë.
2. Të shkruhet funksioni `shtyp(d)` i cili shfaq datën.
3. Të shkruhen funksionet `dita(d)`, `muaji(d)` dhe `viti(d)` të cilat nxerrin shënimet nga data.
4. Të krijohet data me vlerat e sotit dhe të thirren funksionet e krijuara.

--

```cpp
#include <iostream>
#include <math.h>
using namespace std;

struct Data {
  int dita;
  int muaji;
  int viti;
};

Data krijo(int d, int m, int v) {
  Data rez = { d, m, v };
  return rez;
}

void shfaq(Data d) {
  cout << d.dita << "/" << d.muaji << "/" << d.viti << endl;
}

int dita(Data d) {
  return d.dita;
}

int muaji(Data d) {
  return d.muaji;
}

int viti(Data d) {
  return d.viti;
}

int main() {
  Data sot = { 27, 12, 2018 };
  shfaq(sot);
  cout << "Dita: " << dita(sot) << endl;
  cout << "Muaji: " << muaji(sot) << endl;
  cout << "Viti: " << viti(sot) << endl;
}
```

---

Me numërime dhe struktura mund të modelojmë objektet e jetës reale.

```cpp
#include <iostream>
using namespace std;

enum Marka
{
  Opel,
  Mercedes,
  BMW,
  Audi,
  Volkswagen,
  Nissan
};

enum Ngjyra
{
  Zeze,
  Bardhe,
  Kuqe,
  Kalter,
  Gjelber,
  Hirte
};

enum Transmisioni
{
  Manual,
  Automatik
};

struct Vetura
{
  Marka marka;
  Ngjyra ngjyra;
  int vitiProdhimit;
  Transmisioni transmisioni;
};

int main()
{
  Vetura v1 = {
      Opel,
      Gjelber,
      2005,
      Manual};

  Vetura v2 = {
      Mercedes,
      Zeze,
      2010,
      Automatik};

  return 0;
}
```

---

Ndonjëherë kemi:

1. Një strukturë të të dhënave.
2. Një funksion `konstrukto` që krijon atë strukturë.
3. Funksione tjera që veprojnë mbi atë strukturë.

Bashkësia e këtyre tri elementeve quhet **klasë**.