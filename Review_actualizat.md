# Review


# 1. Schema electrică

## General

* ✅ Verificare CAD ERC 100% fără erori.
* ✅ Denumirile pinilor pentru toate simbolurile din schemă corespund cu datasheet-ul
* ✅ Simbolul componentelor este corect ales.
* ✅ Denumirile și valorile componentelor sunt conform cerințelor.
* ✅ Componentele polarizate sunt specificate clar în schemă.

## Alimentare și regulatoare

* ✅ Protecție la suprasarcină și/sau tensiune inversă la intrarea sistemului.
* ✅ Protecție la subtensiune/supratensiune configurată corect.
* ✅ Protecție TVS la intrarea alimentării (_**USBLC6-2SC6Y**_).
* ✅ Toate intrările de alimentare sunt alimentate cu tensiunea corectă.
* ✅ Consumul estimat de energie pe fiecare traseu de putere corespunde cu specificațiile regulatorului.

## Decuplare

* ✅ Decuplare prezentă pentru toate IC-urile.
* ✅ Decuplare de masă prezentă la sursa de alimentare.

## Semnale

* ✅ Semnalele au nivel logic corect pentru pinul de intrare.
* ✅ Pull-up pe toate ieșirile open-drain.
* ✅ TX/RX corect pereche pentru UART, SPI.
* ✅ Polaritatea semnalelor de activare (enable) high/low este corectă.

## Pini de inițializare / strap

* ✅ Pull-up / pull-down pe toate semnalele care trebuie să aibă o stare definită la pornire.
* ✅ Pinii de configurare conectați la netul corespunzător pentru starea dorită.
* ❌ Conector JTAG/ICSP prevăzut pentru dispozitivul programabil. (Schema nu prevede o asemenea conexiune dedicată)

## Depanare / posibilitate de rework

* ✅ Asigură puncte multiple de masă.
* ✅ Masă dedicată în apropiere de punctele de test analogice.
* ✅ Puncte de test pe toate traseele de putere.
* ✅ Puncte de test pe semnalele de interes care pot necesita sondare în timpul punerii în funcțiune sau depanării.


# 2. Board

## General

* ✅ DRC pentru layout aprobat 100%. (cu 2 erori acceptate conform specificațiilor proiectului)
* ✅ Traseele nu conțin unghiuri drepte.
* ✅ Dimensiunile de contur și forma plăcii corespund cerințelor proiectului (inclusiv decupaj în zona antena ESP32C6)
* ✅ Componentele principale amplasate conform documentației.

## Decuplare

* ✅ Condensatorii de decuplare cât mai aproape posibil de pinii de alimentare.

## Footprints

* ✅ Confirmă disponibilitatea componentelor în pachetul selectat.
* ✅ Confirmă că componentele (mai ales conectorii și regulatoarele) pot susține curentul dorit în pachetul ales.
* ✅ Verifică dacă simbolul schematic corespunde cu pachetul ales.
* ✅ Confirmă că diagrama de pini este pentru partea superioară vs inferioară a componentului.
* ✅ Modele 3D obținute și verificate.
* ✅ Deschideri în soldermask pe toate pad-urile

## Semnale de mare viteză

* ✅ Distanță suficientă față de potențiale interferențe.
* ✅ Trasee de lungime potrivită dacă este necesar.
* ✅ Minimizează trecerile peste întreruperi sau schimbări de straturi; folosește condensatori sau via-uri de legătură dacă nu se poate evita.
* ✅ Adaugă vias-uri de legătură către planul de masă în pad-urile mari din stratul superior pentru a evita rezonanțele.

## Alimentare

* ✅ Minim de întreruperi în plane cauzate de vias-uri.
* ✅ Lățime suficientă pentru trasee pentru curentul necesar.


## Mecanic

* ✅ Confirmă că toți conectorii către alte sisteme respectă standardele mecanice (orientare, poziție cheie etc.).
* ✅ LED-uri, butoane și alte elemente UI pe partea externă a plăcii.
* ✅ Spațiu liber în jurul IC-urilor mari pentru disiparea căldurii.
* ⏳ Confirmă dimensiunile PCB-ului și poziția/diametrul găurilor de montare cu proiectul carcasei sau rack-ului. (Vezi issue #1)
* ⏳ Plan de masă pe top și bottom. (Vezi issue #2) 
* ✅ Componentele nu se suprapun fizic.
* ✅ Spațiu liber în jurul punctelor de test pentru accesul sondelor.


## Solder mask

* ✅ Confirmă geometria pad-urilor SMD.
* ✅ Distanță adecvată în jurul pad-urilor.

## Silkscreen

* ✅ Dimensiunea textului în limitele producătorului.
* ⏳ Textul nu se suprapune cu găuri sau pad-uri de componente. (Vezi issue #3)
* ✅ Textul eliminat complet sau mutat în afara zonelor aglomerate cu componente/via-uri.
* ⏳ Punctele de test etichetate dacă spațiul permite. (Vezi issue #4)


## Producție CAM

* ✅ Export fișierele Gerber, cpl.


# 3. Readme

* ⏳ Diagrama block cu toate componentele și cum sunt ele conectate. (Vezi issue #5)
* ✅ Bill Of Materials.
* ✅ Descrierea în detaliu a funcționalității hardware.
* ✅ Descrierea în detaliu a funcționalității pinilor ESP32-C6.
* ✅ Imagini cu randări ale PCB-ului.
