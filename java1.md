## Bazat e Programimit - Java 1

Adrian Ymeri

adrian.ymeri@uni-pr.edu


---

### Kompjuteri

Pajisje e cila kryen punë të dobishme.

- Procesori - kryen punë
- Memoria - mban në mend
- Hyrja/Dalja - komunikon me botën

---

### Programi

Një varg urdhërash që ekzekutohen (ndjeken) nga kompjuteri.

- Word, Excel, PowerPoint
- Google Chrome, Mozilla Firefox
- Visual Studio
- Me mijëra tjera...

---

Programet shkruhen përmes **gjuhës programuese**.

Gjuha programuese është urë lidhëse mes programerit dhe kompjuterit.

Sikur gjuhët e njerëzve, gjuhët programuese i kanë rregullat dhe karakteristikat e veta.

---

### Kompajlleri

Kompajlleri është program i cili përkthen gjuhën programuese në gjuhë të makinës.

Gjuha e makinës është varg i njësheve dhe zerove.

---

Secili program ka:

1. Pikën e nisjes **main**
2. Hyrjen dhe daljen standarde*

*(standard input / standard output)

---

**main** paraqet pikën nga e cila fillon ekzekutimi i urdhërave.

Programi përfundon kur ekzekutohen të gjithë urdhërat që gjenden në **main**.

---

Kur përfundon ekzekutimi i **main**, programi kthen një numër për ta treguar statusin e gabimit - error code

- Vlera **0** tregon që nuk ka pasur gabim
- Vlerat **tjera** tregojnë që ka pasur gabim

Shumicën e rasteve do ta vendosni statusin **0**.

---

Si duket main në gjuhën programuese C++?

```cpp
int main() {
  return 0;
}
```

Ky program nuk bën asgjë. Vetëm ekzekutohet dhe tregon që është ekzekutuar me sukses.

---

Anatomia e programit

$$
\texttt{int main()}\;\lbrace\;\textit{blloku}\;\rbrace
$$

**Bllok** quhet një varg i urdhërave.

---

Në C++ blloku i urdhërave mbështjellet në kllapa gjarpërore.

```cpp
{
  urdher;
  urdher;
  urdher;
  return 0;
}
```

Urdhërat brenda bllokut ndahen me pikëpresje.

Hapësirat dhe rreshtat e rinj nuk kanë rëndësi. Ato përdorën për ta bërë kodin më të lexueshëm.

---

$$
\overbrace{\color{red}{\texttt{int}}}^{\text{tipi i bllokut}}\texttt{ main() { ... }}
$$


**int** - Shkurtesë për **integer** (shqip: numër i plotë)

Tregon që main (programi) kthen një numër të plotë - **error code**.

---

$$
\texttt{int }\overbrace{\color{red}{\texttt{main}}}^{\text{emri i bllokut}}\texttt{() { ... }}
$$

Blloku hyrës gjithmonë duhet ta ketë emrin "main".

Në të ardhmën do të krijojmë edhe blloqe tjera - funksione. Për fillim do të merremi vetëm me **main**.

---

$$
\texttt{int main}\overbrace{\color{red}{\texttt{()}}}^{\text{parametrat}}\texttt{ { ... }}
$$

Në kllapa futen parametrat, por për main nuk na nevojiten. Prandaj lihen të zbrazëta.

Do të shpjegohen më vonë më detajisht.

---

```cpp
int main() {
  return 0;
}
```

Urdhëri `return 0;` ka kuptimin "kthe zero" - programi i ekzekutuar nuk ka gabim.

Me kohën do të mësojmë urdhëra tjerë.

---

**Komenti** na lejon të shkruajmë shpjegime ose shënime tjera në kod.

```cpp
int main() {
  // Rreshti në vijim kthen statusin 0
  return 0;
}
```

Kompajllerit nuk i intereson për komente - ato injorohen.

---

Komentet shkruhen në dy mënyra.

Mënyra e parë është me `//`

```cpp
int main() {
  return 0; // Ky tekst injorohet nga kompajlleri
  // Edhe ky tekst injorohet
}
```

Kur vendoset sekuenca `//`, gjithçka pas saj në atë rresht injorohet.

---

Mënyra e dytë për komente

```cpp
int main() {
  /* Ky koment shtrihet
  në disa rreshta. */
  return 0;  
}
```

Komenti vendoset brenda sekuencës `/* ... */`.

Kjo mënyrë e lejon komentin të shtrihet në disa rreshta.

---

### Hyrja dhe dalja standarde

Më herët u cek që programi ka **hyrjen** dhe **daljen** standarde.

**Hyrja** mundëson leximin e informacionit.

**Dalja** mundëson shkruarjen e informacionit.

Anglisht: **standard input** dhe **standard output**.

---

Në C++, hyrja dhe dalja standarde gjenden në librarinë **iostream**.

$$
\overbrace{\texttt{i}}^{\text{input}}
\underbrace{\texttt{o}}_{\text{output}}
\texttt{stream}
$$

**stream** ka kuptimin e rrjedhës - burimi i informacionit ose rrjedha e informacionit.

---

Hyrja standarde është objekti `std::cin`

Dalja standarde është objekti `std::cout`

- std - standard
- cin - character input
- cout - character output

---

Nga `std::cin` lexohet me operatorin `>>`

```cpp
std::cin >> x;
```

Kjo ka kuptimin

$$
\textit{standard input}\xrightarrow{lexo} x
$$

Merr nga standard input dhe vendose në $x$.

---

Në `std::cout` shkruhet me operatorin `<<`

```cpp
std::cout << "Pershendetje";
```

Kjo ka kuptimin

$$
\textit{standard output}\xleftarrow{shkruaj}\text{"Pershendetje"}
$$

Shkruaj tekstin "Pershendetje" në standard output.

---

Shembulli i plotë

```cpp
#include <iostream>

int main() {
  std::cout << "Pershendetje";
  return 0;
}
```

Pas ekzekutimit, në dritare shfaqet

```text
Pershendetje
```

---

Rreshti `#include <iostream>` ka kuptimin:

Përfshije librarinë `iostream`, pasi që programi im ka nevojë të shkruajë ose të lexojë nga hyrja/dalja.

```cpp
#include <iostream>

int main() {
  std::cout << "Pershendetje";
  return 0;
}
```

---

```cpp
#include <iostream>

int main() {
  std::cout << "Pershendetje";
  return 0;
}
```

Programi i sipërm mund të shënohet si më poshtë

```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "Pershendetje";
  return 0;
}
```

---

`using namespace std;` e largon nevojën e shkruarjes së parashtesës `std::` çdo herë që dëshirojmë të komunikojmë me `cin` ose `cout`.

---

```cpp
#include <iostream>

int main() {
  std::cout << "Pershendetje!\n";
  std::cout << "Mire se vini.";
  return 0;
}
```

Në ekran shfaqet:

```text
Pershendetje!
Mire se vini.
```

---

```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "Pershendetje!\n";
  cout << "Mire se vini.";
  return 0;
}
```

Në ekran shfaqet:

```text
Pershendetje!
Mire se vini.
```

---

Teksti në shembujt e kaluar u fut në thonjëza.

```cpp
"Pershendetje"
```

Kjo është e nevojshme për ta dalluar urdhërin nga teksti i zakonshëm.

---

Në tekst që shkruhet në kod, nuk kemi mundësi të vendosim rresht të ri duke shtypur enter.

Për të treguar që në tekst gjendet rreshti i ri, përdoret karakteri special `\n`, ku `n` e ka kuptimin "newline".

```cpp
cout << "Pershendetje!\nMire se vini.";
```

Në ekran shfaqet:

```text
Pershendetje!
Mire se vini.
```

---

Ekzistojnë disa karaketere tjera speciale. Karakteret që fillojnë me `\` kanë kuptim të veçantë.

Karakteri|Kuptimi
-|-
`\n`|Rresht i ri
`\t`|Tab
`\'`|Thonjëza e njëfishtë
`\"`|Thonjëza e dyfishtë
`\\`|Vetë karakteri \\

Dhe tjera...

---

Shembull

```cpp
// Importo librarine iostream
#include <iostream>
using namespace std;

// Pika hyrese e programit
int main() {
  cout << "Rreshti i pare" << "\n" << "Rreshti i dyte";
  return 0;
}
```

Rezultati në ekran

```text
Rreshti i pare
Rreshti i dyte
```

Siç po shihet më lartë, mund të lidhen operatorët `<<` njëri pas tjetrit.

---

### Tipet e të dhënave

Ekzistojnë disa lloje të të dhënave. Kryesoret:

Emri|Përshkrimi|Shembuj
---|---|---
int|Numër i plotë|$-2,\,0,\,3,\,15$
float|Numër me presje|$-1.2,\,0.0,\,3.5$
char|Karakter i vetëm|$\texttt{'a'},\,\texttt{'b'},\,\texttt{'\n'}$
string|Varg i karaktereve (tekst)|$\texttt{"Pershendetje"}$
bool|Vlerë e vërtetësisë|$\texttt{true},\,\texttt{false}$

---

# Ushtrime

---

## Instalimi i Visual Studio

1. Vizitojmë faqen [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
2. Te `Visual Studio IDE`, e zgjedhim `Community 2017`.
3. Klikojmë butonin dhe presim deri të shkarkohet.
4. Ndjekim hapat e instalimit, dhe sigurohemi që kemi zgjedhur opsionin `Desktop development with C++` gjatë instalimit.

---

<!-- .slide: style="font-size:0.6em;" -->

## Krijimi i projektit

1. Hapim Visual Studio.
2. Shkojmë te `File > New > Project`.
3. Te lista e gjuhëve, kërkojmë gjuhën `Visual C++`.
4. Te lloji i projektit, e kërkojmë njërën nga këto:
   - Për Visual Studio 2017, e zgjedhim `Windows Desktop Wizard`.
   - Për versione më të vjetra, e zgjedhim `Win32 Project`.
5. E vendosim emrin e projektit, psh. `Ushtrimi1`.
6. Te lokacioni i projektit, e zgjedhim dosjen ku dëshirojmë ta ruajmë projektin. Këtë e bëjmë duke shtypur butonin `Browse...`.
7. E shtypim `OK`.
8. Na shfaqet dritarja për të konfiguruar projektin.
    - E zgjedhim opsionin `Empty Project`
    - Tek `Application type` e zgjedhim `Console Application`
9. Shtypim `OK`.

---

<!-- .slide: style="font-size:0.6em;" -->

## Krijimi i fajllit burimor

1. Pasi ta kemi hapur projektin, në anën e djathtë e shohim `Solution Explorer`.
    - Nëse nuk e shohim, shkojmë te `View > Solution Explorer` për ta shfaqur.
2. Te projekti ynë, i shohim katër dosje. Dosjen `Source Files` e hapim me tastin e djathtë, dhe shkojmë te `Add > New Item...`.
3. Na hapet menyja për krijimin e fajllave. E zgjedhim `C++ File (.cpp)`, dhe ia lëmë emrin sipas dëshirës, psh `programi.cpp`. E shtypim `Add`.
4. Te dosja `Source Files` na shfaqet fajlli i sapo-krijuar. E klikojmë dy herë dhe na shfaqet editori.

---

## Programi fillestar

Në editor, shkruajmë këtë kod:

```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "Pershendetje" << endl;
  return 0;
}
```

Pas ekzekutimit shfaqet:

```text
Pershendetje
Press any key to continue...
```

---

<!-- .slide: style="font-size:0.6em;" -->

## Ekzekutimi i programit

1. Shkojmë te `Debug > Start Without Debugging`.
    - Këtë veprim mund ta bëjmë edhe duke shtypur `Ctrl+F5`.
2. Nëse kodi është në rregull, programi kompajllohet dhe shfaqet dritarja e aplikacionit.
3. Nëse kemi gabime, na del një njoftim që programi nuk ka mundur të kompajllohet. E shtypim `No` për t'u kthyer te editori.
4. Rikthehemi te editori dhe korigjojmë gabimet.
    - Dritarja `Error List` na ndihmon në gjetjen e gabimeve. Gabimet mund t'i klikojmë dy herë me tastin e majtë për të na dërguar te rreshti i kodit tek i cili gjendet problemi.
5. Pasi t'i kemi korigjuar gabimet, kthehemi te hapi 1.

---

## Mbyllja e projektit

1. Shkojmë te `File > Close Solution`.
    - Nëse kemi ndryshime të paruajtura, na pyet nëse dëshirojmë t'i ruajmë para se ta mbyllim projektin.

---

## Rihapja e projektit

1. Shkojmë te `File > Open > Project/Solution`.
2. E kërkojmë shtegun e projektit tonë.
3. Brenda dosjes së projektit, e zgjedhim `.sln` fajllin i cili mban emrin e projektit.
4. Shtypim `Open` dhe na hapet projekti. 

---

## Resurse online

- [cplusplus.com](http://www.cplusplus.com/doc/tutorial/) - Materiale mësimore për gjuhën C++.
- [cpp.sh](http://cpp.sh/) - Testo programe të C++ në ueb.
