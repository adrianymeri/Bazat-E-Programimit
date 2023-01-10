# Tipi 'void'

---

Funksioni kemi thënë është një transformim nga **hyrja** në **daljen**.

$$
\begin{array}{rcl}
45° \rightarrow & \boxed{f(x)} & \rightarrow \frac{\sqrt{2}}{2} \\
6 \rightarrow & \boxed{g(x)} & \rightarrow 36 \\
\texttt{'c'} \rightarrow & \boxed{h(x)} & \rightarrow 3
\end{array}
$$

---

**Shembull:** Funksioni katrori $f(x) = x^2$ merr vlerën $x$ (int) dhe kthen katrorin e saj (përsëri int):

```cpp
int katrori(int x) {
  return x * x;
}

int main() {
  int y = katrori(2);
  cout << "y = " << y;
  return 0;
}
```

---

Përmes funksioneve krijojmë blloqe kodi të ripërdorshme.

Çdo herë që na nevojitet katrori i një numri, e përdorim të gatshëm funksionin `katrori`.

```cpp
int a = katrori(2);
int b = katrori(5);
int c = katrori(13);
```

---

Jo gjithmonë na nevojitet krijimi i funksionit për të transformuar të dhëna dhe për të marrë rezultate.

Ndonjëherë nuk ka intereson rezultati, por vetëm na duhet ta kryejmë një punë.

---

**Shembull:** Funksioni `shfaqPiket(p)` e merr numrin e pikëve dhe e shfaq në ekran:

```cpp
??? shfaqPiket(int piket) {
  cout << "Studenti ka arritur " 
       << piket
       << " pike ne provim."
       << endl;
  return ???;
}
```

Çfarë rezultati ka ky funksion? Çfarë tipi dhe çfarë vlere duhet të kthejë ky operacion?

---

Përgjigja: Funksioni nuk kthen **asgjë**. Qëllimi i funksionit është të kryejë punë, e jo të bëjë llogaritje:

```cpp
int main() {
  shfaqPiket(25);
  shfaqPiket(60);
  shfaqPiket(100);
}
```

Rezultati në ekran:

```text
Studenti ka arritur 25 pike ne provim.
Studenti ka arritur 60 pike ne provim.
Studenti ka arritur 100 pike ne provim.
```

---

Kur funksioni ka për qëllim kryerjen e një pune e cila nuk kthen ndonjë rezultat të dobishëm, atëherë themi se funksioni nuk kthen asgjë.

"Asgjë"-ja në programim quhet **void** (vrimë) - mungesë tipi.

```cpp
void shfaqPiket(int piket) {
  cout << "Studenti ka arritur " 
       << piket
       << " pike ne provim."
       << endl;
  return; // nuk po kthejmë asgjë
}
```

---

Kur funksioni nuk kthen asgjë, atëherë ai përdorët vetëm si urdhër, e jo si **shprehje**.

**Rikujtim:** Gjithçka që ka tip dhe vlerë quhet **shprehje**.

**void** nuk paska as tip e as vlerë, prandaj nuk është shprehje!

```cpp
int x = shfaqPiket(73); // gabim: shfaqPiket nuk kthen rezultat!
cout << shfaqPiket(25); // gabim: shfaqPiket nuk kthen rezultat!
```

---

Kur tipi i kthimit është `void`, nuk është i obligueshëm urdhëri `return` në fund të funksionit, pasi që nënkuptohet:

```cpp
void pershendeteBoten() {
  cout << "Pershendetje Bote!";
  return;
}
```

Kodi i mësipërm thjeshtohet në:

```cpp
void pershendeteBoten() {
  cout << "Pershendetje Bote!";
}
```
