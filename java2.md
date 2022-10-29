# Gjuhë Programuese - Java 2

---

## Përsëritje

1. Çfarë është programi?
2. Çfarë është gjuha programuese?

--

1. Programi - varg urdhërash që ekzekutohen nga kompjuteri.
2. Gjuha programuese - sintaksa dhe rregullat për shkruarjen e programeve.

---

Çfarë është **main**?

--

**main** është pika hyrëse e programit.

```cpp
int main() {
  return 0;
}
```

---

Çfarë quajmë **bllok të kodit** dhe si shënohet?

--

**Bllok të kodit** e quajmë vargun e urdhërave të mbështjellur me kllapa gjarpërore.

```cpp
{
  urdher;
  urdher;
  urdher;
}
```

---

Të shpjegohet ky program:

```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "Pershendetje" << endl;
  return 0;
}
```

---

**Detyrë:** Të krijohet një projekt i ri dhe të shkruhet programi i cili shfaq këtë tekst në ekran:

```text
Përshëndetje!

Po mësojmë gjuhën programuese "C++".
```

**Ndihmesë:** karakteri `ë` shkruhet `\x89`

```cpp
"\x89"
```

--

```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "P\x89rsh\x89ndetje!" 
       << endl
       << endl
       << "Po m\x89sojm\x89 gjuh\x89n programuese \"C++\".";
  return 0;
}
```

---

## Tipet dhe Variablat

---

**Rikujtim:** Kompjuteri të dhënat i ruan në formë binare - vargje të njësheve dhe zerove.

- Biti (bit) - shifra 0 ose 1.
- Bajti (byte) - vargu i 8 bitave.

--

**Shembull:** Numri $25$ në formë binare shkruhet:

$$
25_{10}=00011001_2
$$

---

Kemi disa lloje të të dhënave:

1. Tipet numerike.
2. Tipi i vërtetësisë - boolean.
3. Tipet tekstuale - karakteret dhe stringjet.
4. Tipet komplekse.

---

## Tipet numerike

Ndahen në dy kategori kryesore:

1. Numrat e plotë - **integer**
2. Numrat me presje - **floating-point**

---

<!-- .slide: style="font-size: 0.6em" -->

Numrat e plotë (integer) **me shenjë**:

Tipi|Madhësia|Vlerat
---|---|---:
`char`|1 bajt|`-128` deri `127`
`short int`|2 bajt|`-32768` deri `32767`
`int`|4 bajt|`-2147483648` deri `2147483647`
`long int`|4 bajt|`-2147483648` deri `2147483647`
`long long int`|8 bajt|`-9223372036854775808` deri `9223372036854775807`

---

<!-- .slide: style="font-size: 0.6em" -->

Numrat e plotë (integer) **pa shenjë**:

Tipi|Madhësia|Vlerat
---|---|---:
`unsigned char`|1 bajt|`0` deri `255`
`unsigned short int`|2 bajt|`0` deri `65535`
`unsigned int`|4 bajt|`0` deri `4294967295`
`unsigned long int`|4 bajt|`0` deri `4294967295`
`unsigned long long int`|8 bajt|`0` deri `18446744073709551615`

---

Numrat me presje - floating-point

Tipi|Madhësia|Preciziteti
---|---|---:
`float`|4 bajt|7 shifra
`double`|8 bajt|15-16 shifra
`long double`|16 bajt|28-29 shifra

---

Shpesh përdorën këto terme:

- Single-precision - për **float**.
- Double-precision - për **double**.

---

## Tipi i vërtetësisë

Ka vetëm dy vlera - **saktë**/**pasaktë**, **po**/**jo**, **1**/**0**.

Tipi|Madhësia|Vlerat
---|---|---
bool|1 bajt|`true` ose `false`

---

## Tipet tekstuale

Emri|Madhësia
---|---
char|1 bajt
char16_t|2 bajt
char32_t|4 bajt
string|Pacaktuar

---

**String** paraqet vargun e karaktereve deri te karakteri terminues `\0`

0  |1  |2  |3  |4
:-:|:-:|:-:|:-:|:-:
`'D'`|`'i'`|`'t'`|`'a'`|`'\0'`

---

## Tipet komplekse

1. Strukturat dhe klasat e librarisë standarde.
2. Tipet që i definojmë vet (në të ardhmen).

---

Prej gjithë këtyre tipeve, më së shpeshti do të përdorim:

- **int** - kur na nevojitet numër i plotë.
- **double** - kur na nevojitet numër me presje.
- **bool** - kur duhet ta ruajmë ndonjë fakt.

---

## Variablat

Përmes variablave "mbajmë në mend".

Variabla ka **tipin** dhe **emrin**.

```cpp
<tipi> <emri> [= <vlera fillestare>];
```

---

Variablat i kemi të njohura nga shkencat tjera:

$$
F = ma
$$

$$
v = \frac{s}{t}
$$

$$
y = 2x + 3
$$

---

Deklarimi i variablave:

```cpp
int variabla;
```

Nëse dëshirojmë ta inicializojmë me vlerë fillestare:

```cpp
int variabla = 42;
```

Programi "rezervon" hapësirë për ta ruajtur këtë të dhënë.

---

**Shembull:**

**`nr_studenteve`** është numër i plotë (**`int`**), dhe paraqet numrin e studentëve prezent në sallë.

```cpp
int nr_studenteve = 14;

cout << nr_studenteve; // Çfarë na shfaqet?
```

---

Variablave ia lëmë emrin sipas dëshirës, me kushtin që nuk është fjalë kyçe e gjuhës programuese, psh. `int`, `float`, etj.

```cpp
int mosha;
double nota_mesatare;
bool eshte_student;
string emri;
```

---

Kur kemi disa variabla, mund t'i deklarojmë në një urdhër të vetëm:

```cpp
int a, b, c;
double x, y;
```

---

Variablat mund t'i lexojmë nga tastiera:

```cpp
int a, b;

cout << "Shtypni vleren a: ";
cin  >> a; // Lexojmë nga standard input.
cout << "Shtypni vleren b: ";
cin  >> b; // Lexojmë nga standard input.
cout << "Keni shtypur a=" << a << " dhe b=" << b << endl;
```

Programi "mban në mend" numrat $a$ dhe $b$.

---

**Detyrë:** Të shkruhet programi i cili lexon 3 numra të plotë dhe pastaj i shfaq ata.

```text
Jepni vleren a: 15
Jepni vleren b: -2
Jepni vleren c: 3

Keni shtypur vlerat:
a = 15
b = -2
c = 3
```

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a, b, c;

  cout << "Jepni vleren a: ";
  cin  >> a;
  cout << "Jepni vleren b: ";
  cin  >> b;
  cout << "Jepni vleren c: ";
  cin  >> c;

  cout << endl << "Keni shtypur vlerat:" << endl;
  
  cout << "a = " << a << endl
       << "b = " << b << endl
       << "c = " << c << endl;

  return 0;
}
```

---

## Shprehjet

Gjithçka që ka vlerë dhe tip quhet **shprehje**.

```cpp
15      // Shprehje e tipit int.
x + 1.5 // Shprehje e tipit double.
"Tung"  // Shprehje e tipit char[] (string).
true    // Shprehje e tipit bool.
```

Ky definicion na duhet në vazhdim.

---

## Operatorët

Përmes operatorëve kryejmë llogaritje të ndryshme.

---

**Operatori i shoqërimit (assignment)**

Llogarit shprehjen nga ana **e djathtë** dhe e vendos në shprehjen e anës **së majtë**.

```cpp
int a, b;
a = 25; // Vendos 25 (ana e djathtë) në a (ana e majtë)
b = a;  // Vendos a (ana e djathtë) në b (ana e majtë)
```

Shënohet me simbolin **`=`** (baraz)

---

Shprehja e anës së majtë dhe e anës së djathtë duhet ta kenë tipin e njejtë.

```cpp
int a;
a = 25;     // Ok.
a = "Tung"; // Nuk ka kuptim.
```

---

Disa shprehje nuk mund të vendosën në anën e majtë:

```cpp
2 = 1 + 5 // Nuk ka kuptim!
```

- **LValue** - shprehjet të cilat mund të paraqiten në anën e majtë - zakonisht variablat.
- **RValue** - shprehjet që mund të paraqiten në anën e djathtë - shprehjet matematikore, variablat që kanë vlerë, rezultatet e funksioneve, etj.

---

Analizojeni kodin në vijim:

```cpp
int a;
a = 3;
cout << a << endl;
a = a + 1;
cout << a << endl;
```

Na shfaqet:

```text
3
4
```

Pse?

---

```cpp
a = 3;
a = a + 1;
// a == 4
```

$$
\underbrace{a}_{\text{Ana e majtë}} \leftarrow \underbrace{a + 1}_{\text{Ana e djathtë}}
$$

Llogaritet shprehja e djathtë:

$$
\begin{array}{rl}
a &\leftarrow \overbrace{a}^{3} + 1 \\
a &\leftarrow 3 + 1 \\
a &\leftarrow 4
\end{array}
$$

---

**Shembull**: Është dhënë vlera $a=21$, ndërsa vlera $b$ duhet të jepet nga tastiera. Të llogaritet vlera $c=a+b$ dhe të shfaqet në ekran.

```cpp
#include <iostream>
using namespace std;

int main() {
  int a = 21;
  int b;
  int c;

  cin >> b; // Vlera b lexohet nga tastiera.
  c = a + b;

  cout << "Vlera e a+b eshte: " << c << endl;
  return 0;
}
```

---

## Operatorët aritmetikor

```cpp
double a = 10.0;
double b = 4.0;
```

Veprimi|Operatori|Shprehja|Rezultati
-|:-:|:-:|--:
Mbledhja|`+`|`a + b`|`14.0`
Zbritja|`-`|`a - b`|`6.0`
Shumëzimi|`*`|`a * b`|`40.0`
Pjesëtimi|`/`|`a / b`|`2.5`
Modulimi|`%`|`a % b`|`2.0`

---

Shumëzimi dhe pjesëtimi kanë përparësi ndaj mbledhjes dhe zbritjes.

```cpp
int a = 2 + 2 * 2;
cout << a;
```

Na shfaqet:

```text
6
```

---

Përmes kllapave mund të caktojmë përparësi tjetër të operatorëve.

```cpp
int a = (2 + 2) * 2;
cout << a;
```

Na shfaqet:

```text
8
```

---

**Detyrë:** Të shkruhet programi i cili lexon 3 numra me presje dhe llogaritë mesatarën e tyre.

```text
Jepni vleren a: 3.2
Jepni vleren b: 6
Jepni vleren c: 1.3

Vlera mesatare: 3.5
```

--

```cpp
#include <iostream>
using namespace std;

int main() {
  double a, b, c, m;

  cout << "Jepni vleren a: ";
  cin  >> a;
  cout << "Jepni vleren b: ";
  cin  >> b;
  cout << "Jepni vleren c: ";
  cin  >> c;
  cout << endl;
  
  m = (a + b + c) / 3.0;
  cout << "Vlera mesatare: " << m << endl;

  return 0;
}
```

---

**Detyrë:** Të lexohen nga tastiera brinjët e drejtkëndëshit, pastaj të llogariten perimetri dhe sipërfaqja (në variabla), dhe të shfaqen në ekran.

```text
Jepni brinjen a: 5
Jepni brinjen b: 3
Perimetri i drejtkendeshit: 16
Siperfaqja e drejtkendeshit: 15
```

**Kujtesë:** $\;S=ab,\; P=2(a+b)$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a, b, S, P;
  
  cout << "Jepni brinjen a: ";
  cin  >> a;
  cout << "Jepni brinjen b: ";
  cin  >> b;

  P = 2 * (a + b);
  S = a * b;
  
  cout << "Perimetri i drejtkendeshit: " << P << endl;
  cout << "Siperfaqja e drejtkendeshit: " << S << endl;

  return 0;
}
```

---

## Funksionet matematikore

Kur e përfshijmë headerin `<math.h>`, na mundësohet thirrja e funksioneve matematikore sikur:

Funskioni|Emri|Shembull|Interpretimi
-|-|-|:-:
Rrënja katrore|`sqrt`|`sqrt(16)`|$\sqrt{16}$
Ngritja në fuqi|`pow`|`pow(2, 4)`|$2^4$
Sinusi|`sin`|`sin(0)`|$\sin{(0_\text{rad})}$
Kosinusi|`cos`|`cos(3.14)`|$\cos{(\pi_\text{rad})}$

Dhe tjera...

---

**Detyrë:** Janë dhënë vlerat reale $a=2.0,\;b=3.5,\;c=1.2$.

Të llogariten shprehjet:

$$
\begin{array}{rlcr}
1) & a + 2c - \frac{7}{9}b & \Rightarrow & 1.67 \\
2) & a + 2(1.1 + b) - c & \Rightarrow & 10 \\
3) & b^a - 2c & \Rightarrow & 9.85  \\
4) & \sqrt{\frac{a^2 + b^2}{c + 1}} & \Rightarrow & 2.71 \\
\end{array}
$$

--

```cpp
#include <iostream>
#include <math.h>
using namespace std;

int main() {
  double a = 2.0;
  double b = 3.5;
  double c = 1.2;

  cout << a + 2 * c - 7.0 / 9.0 * b << endl;
  cout << a + 2 * (1.1 + b) - c << endl;
  cout << pow(b, a) - 2 * c << endl;
  cout << sqrt((pow(a, 2) + pow(b, 2)) / (c + 1)) << endl;

  return 0;
}
```

---

## Konstantet

Ndonjëherë vlera e variables është fikse dhe nuk ndryshon asnjëherë.

Këto quhen konstante dhe shkruhen duke ia shtuar fjalën `const` përpara deklarimit të variablës:

```cpp
const double pi = 3.14;
const int a = 4;
```

---

**Detyrë:** Të gjendet sipërfaqja dhe perimetri i rrethit, nëse rrezja $r$ jepet nga tastiera. Vlera e PI ($\pi$) të deklarohet si konstante.

```text
Jepni vleren e rrezes: 3
Perimetri i rrethit: 18.84
Siperfaqja e rrethit: 28.26
```

**Kujtesë:** $\;P=2\pi r,\; S=\pi r^2,\;\pi\approx 3.14$

--

```cpp
#include <iostream>
#include <math.h>
using namespace std;

int main() {
  const double pi = 3.14;
  double r, P, S;

  cout << "Jepni vleren e rrezes: ";
  cin >> r;

  P = 2 * pi * r;
  S = pi * pow(r, 2);

  cout << "Perimetri i rrethit: " << P << endl;
  cout << "Siperfaqja e rrethit: " << S << endl;

  return 0;
}
```

---

## Operatorët shkurtesë

Shpesh kemi nevojë ta zmadhojmë ose zvogëlojmë një variabël për një vlerë të caktuar.

---

Shkurtesa|Kuptimi
:-:|:-:
`a += x`|`a = a + x`
`a -= x`|`a = a - x`
`a *= x`|`a = a * x`
`a /= x`|`a = a / x`
`a %= x`|`a = a % x`

---

**Shembull**

```cpp
int a = 7;
int b = 2;
a += b; // Rrite a per b.
b -= 1; // Zvogeloje b per 1.
cout << "Vlera e a: " << a << endl;
cout << "Vlera e b: " << b << endl;
```

Shfaqet:

```text
Vlera e a: 9
Vlera e b: 1
```

---

Shkurtesat për inkrement dhe dekrement.

Shkurtesa|Kuptimi
:-:|:-
`a++`|Ktheje `a`, pastaj rrite për `1`.
`++a`|Rrite `a` për `1`, pastaj ktheje.
`a--`|Ktheje `a`, pastaj zvogëloje për `1`.
`--a`|Zvogëloje `a` për `1`, pastaj ktheje.

---

**Shembulli 1: `a++`**

```cpp
int a = 5;
cout << "Para inkrementimit: " << a << endl;
cout << "Gjate inkrementimit: " << a++ << endl;
cout << "Pas inkrementimit: " << a << endl;
```

Shfaqet:

```text
Para inkrementimit: 5
Gjate inkrementimit: 5
Pas inkrementimit: 6
```

---

**Shembulli 2: `++a`**

```cpp
int a = 5;
cout << "Para inkrementimit: " << a << endl;
cout << "Gjate inkrementimit: " << ++a << endl;
cout << "Pas inkrementimit: " << a << endl;
```

Shfaqet:

```text
Para inkrementimit: 5
Gjate inkrementimit: 6
Pas inkrementimit: 6
```

---

**Detyrë:** Të deklarohet variabla $shuma=0$, dhe të lexohen pesë numrat e ardhshëm nga tastiera. Secili numër i lexuar t'i shtohet shumës.

```text
Jepni numer: 3
Jepni numer: 1
Jepni numer: 2
Jepni numer: 7
Jepni numer: 4
Totali: 17
```

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int shuma = 0;
  int numri;

  cout << "Jepni numer: ";
  cin >> numri;
  shuma += numri;

  cout << "Jepni numer: ";
  cin >> numri;
  shuma += numri;

  cout << "Jepni numer: ";
  cin >> numri;
  shuma += numri;

  cout << "Jepni numer: ";
  cin >> numri;
  shuma += numri;

  cout << "Jepni numer: ";
  cin >> numri;
  shuma += numri;

  cout << "Totali: " << shuma << endl;

  return 0;
}
```

---

## Detyra shtesë

---

**Detyrë:** Të lexohen numrat e plotë $a$ dhe $b$ nga tastiera, dhe pastaj t'iu ndërrohen vlerat mes veti.

```text
Shtypni a: 10
Shtypni b: 3
Para nderrimit:
a = 10, b = 3
Pas nderrimit:
a = 3, b = 10
```

--

```cpp
#include <iostream>
using namespace std;

int main() {
  int a, b, temp;

  cout << "Shtypni a: ";
  cin  >> a;
  cout << "Shtypni b: ";
  cin  >> b;

  cout << "Para nderrimit:"
       << "a = " << a 
       << ", b = " << b << endl;

  temp = a;
  a = b;
  b = temp;

  cout << "Pas nderrimit:"
       << "a = " << a 
       << ", b = " << b << endl;

  return 0;
}
```

---

**Detyrë:** Të llogaritet hipotenuza e trekëndëshit nëse katetet $a$ dhe $b$ jepen nga tastiera.

```text
Shtypni a: 4
Shtypni b: 3
Hipotenuza e trekendeshit me katetet a=4 dhe b=3 eshte c=5.
```

**Kujtesë:** $\;c=\sqrt{a^2+b^2}$

--

```cpp
#include <iostream>
#include <math.h>
using namespace std;

int main() {
  double a, b, c;

  cout << "Shtypni a: ";
  cin  >> a;
  cout << "Shtypni b: ";
  cin  >> b;

  c = sqrt(pow(a, 2) + pow(b, 2));

  cout << "Hipotenuza e trekendeshit me katetet a="
       << a << " dhe b=" << b << " eshte c=" << c << endl;

  return 0;
}
```

---

**Detyrë:** Të shkruhet programi që bën konvertimin nga Celsius në Fahrenheit. Vlera në Celsius lexohet nga tastiera.

```text
Te jepet vlera ne Celsius: 25
Vlera ne Fahrenheit: 77
```

**Kujtesë:** $\;F=\frac{9}{5}C + 32$

--

```cpp
#include <iostream>
using namespace std;

int main() {
  double celsius, fahrenheit;

  cout << "Te jepet vlera ne Celsius: ";
  cin  >> celsius;

  fahrenheit = 9.0 / 5.0 * celsius + 32.0;
  cout << "Vlera ne Fahrenheit: " << fahrenheit << endl;

  return 0;
}
```

---

**Detyrë:** Të shkruhet nga një program për secilën formulë më poshtë.

$$
F = ma \tag{1}
$$

$$
v = \frac{s}{t} \tag{2}
$$

$$
E = mc^2 \tag{3}
$$

$$
y = -5\times\sqrt{2x^2 + 3} \tag{4}
$$

--

**(1)**

```cpp
#include <iostream>
using namespace std;

int main() {
  double F, m, a;

  cout << "Jepni m: ";
  cin  >> m;
  cout << "Jepni a: ";
  cin  >> a;

  F = m * a;
  cout << "F = " << F << endl;

  return 0;
}
```

--

**(2)**

```cpp
#include <iostream>
using namespace std;

int main() {
  double v, s, t;

  cout << "Jepni s: ";
  cin  >> s;
  cout << "Jepni t: ";
  cin  >> t;

  v = s / t;
  cout << "v = " << v << endl;

  return 0;
}
```

--

**(3)**

```cpp
#include <iostream>
#include <math.h>
using namespace std;

int main() {
  const double c = 3e8;
  double E, m;

  cout << "Jepni m: ";
  cin  >> m;

  E = m * pow(c, 2);
  cout << "E = " << E << endl;

  return 0;
}
```

--

**(4)**

```cpp
#include <iostream>
#include <math.h>
using namespace std;

int main() {
  double x, y;

  cout << "Jepni x: ";
  cin  >> x;

  y = -5 * sqrt(2 * pow(x, 2) + 3);
  cout << "y = " << y << endl;

  return 0;
}
```
