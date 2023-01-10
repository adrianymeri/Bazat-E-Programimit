# Paradigmat programuese

---

Kur kompleksiteti i problemeve rritet, bëhet më i vështirë shkrimi dhe menaxhimi i programeve të cilat merren me ato probleme.

---

**Paradigmë programuese** e quajmë filozofinë e shkruarjes së programeve.

---

**Paradigma imperative**

Programuesi jep urdhërat se çfarë duhet bërë gjatë ekzekutimit të programit.

Urdhërat diktojnë rrjedhën e ekzekutimit dhe ndryshimin e gjendjes hap pas hapi.

---

**Gjuha e asamblerit**

Formë imperative e shkrimit të programeve në nivel të makinës.

Programuesi ia jep hapat e ekzekutimit procesorit, si psh. `add`, `jump`, `compare` etj.

Nuk ekziston struktura e blloqeve, kushtëzimeve, ose unazave. Urdhërat vetëm ndryshojnë gjendjen ose bëjnë kërcime të ekzekutimit.

---

**Programimi i strukturuar**

Formë imperative e shkrimit të programeve, ku urdhërat grupohen në nivel të **blloqeve**.

Kjo formë programimi është aplikuar gjatë kësaj lënde.

Bazohet në: blloqe, kushtëzime, unaza, switch, etj.

---

**Programimi procedural**

Formë imperative e programimit të strukturuar, ku programi ndahet në blloqe të njohura si **procedura**.

**Shembull:** Programi i një loje kompjuterike:

```cpp
int main() {
  inicializoFushen();
  luajLojen();
  shfaqPiket();
  return 0; // fund
}
```

---

**Programimi funksional**

Filozofi e programimit që bazohet në funksione.

Bazohet në: transformimin e të dhënave, kompozimin e funksioneve, jo-ndryshueshmërinë, largimin e efekteve anësore.

Gjuhë të tilla: Haskell, Scala, ML, F#, JavaScript

---

**Programimi i orientuar në objekte**

Filozofi programimi që bazohet në struktura të dhënave dhe sjellje të tyre.

Gjërat e jetës reale pasqyrohen në objekte. Objekti mban të dhëna si dhe funksionalitet.

Bazohet në: klasa, enkapsulim, trashëgimi, polimorfizëm, abstraksione.

Gjuhë të tilla: Java, C++, C#, JavaScript

---

## Llojet e gjuhëve programuese

---

Gjuha programuese mund të jetë:

- **E kompajlluar** - një program tjetër e merr kodin dhe e kthen në urdhëra të makinës, psh. C++.
- **E interpretuar** - një program tjetër e merr kodin dhe e ekzekuton aty për aty, psh. JavaScript.
- **JIT (Just In Time) kompajlluar** - programi kompajllohet në një gjuhë të ndërmjetshme. Kjo gjuhë kompajllohet në urdhëra të makinës kur ekzekutohet programi (aty për aty), psh Java, C#.

---

Gjuha programuese mund të jetë:

- **Me tipe statike** - tipi i variablave dihet paraprakisht (psh. `int x`) - C++, Java, C#, etj.
- **Me tipe dinamike** - tipi i variablave dihet vetëm kur ekzekutohet programi - JavaScript, Python, PHP, Ruby, etj.

---

Gjuha programuese mund të jetë:

- **Me tipe "të forta"** - tipet e të dhënave nuk ndryshohen pa urdhëra ose transformime eksplicite - Java, C#, F#, Python, etj.
- **Me tipe "të dobëta"** - tipet e të dhënave ndryshohen sipas situatës, psh. `"5" == 5` jep `true` - JavaScript, C (në një nivel), etj.

---

Memoria e programit mund të jetë:

- **E menaxhuar** - gjatë ekzekutimit dikush kujdesët që memorien e pashfrytëzuar ta lirojë (garbage collection).
- **E pamenaxhuar** - programuesi vet duhet të kujdesët që memorien e pashfrytëzuar ta lirojë.

---

## Llojet e programeve

---

Disa lloje arkitekturash të programit:

- Model-View-Controller
- Model-View-ViewModel
- Model-View-Update
- Model-View-Presenter

---

Programet shfrytëzohen për shumë qëllime:

- Web serverë - shërbejnë HTTP kërkesa.
- Web klientë - aplikacione në shfletues.
- Aplikacionet desktop - ndërfaqe GUI.
- Aplikacione mobile - GUI në pajisje mobile.
- Programet console - kryejnë punë të ndryshme.
- Programet në mikrokontrollerë dhe sisteme operative.

---

**Web serveri** është një program që vazhdimisht shërben kërkesa për klientët.

Disa teknologji për web serverë:

- PHP
- ASP.NET
- Ruby on Rails
- Node.js

Zakonisht njihet si back-end programim.

---

**Klient aplikacioni** është një aplikacion që ekzekutohet në shfletues dhe komunikon me web serverin.

Zakonisht shkruhen në JavaScript dhe njihet si front-end programim.

Disa teknologji për klient aplikacione:

- HTML, CSS, JavaScript
- jQuery, React, Vue, Angular

Për më shumë rreth web lexoni [këtu](https://github.com/kamranahmedse/developer-roadmap).

---

**Desktop aplikacionet** janë programe që ekzekutohen në kompjuterët lokal. Ata ofrojnë një ndërfaqe për interaksion me shfrytëzuesin.

Disa teknologji për desktop aplikacione:

- C# me WPF, UWP, ose WinForms
- Java me JavaFX, Swing, etj.
- Node.js me Electron
- C++ me Qt

---

**Aplikacionet mobile** janë programet e shkruara për pajisje mobile - kryesoret Android dhe iOS.

Disa teknologji për ueb aplikacione:

- Android me Java, Kotlin, Scala
- iOS me Swift, Objective-C
- Ndër-platformë me React Native, Flutter, Xamarin, etj.
