# Review


# 1. Schema electrică

## General

* [x] Verificare CAD ERC 100% fără erori.
* [x] Denumirile pinilor pentru toate simbolurile din schemă corespund cu datasheet-ul
* [x] Simbolul componentelor este corect ales.
* [x] Denumirile și valorile componentelor sunt conform cerințelor.
* [x] Componentele polarizate sunt specificate clar în schemă.

## Alimentare și regulatoare

* [x] Protecție la suprasarcină și/sau tensiune inversă la intrarea sistemului.
* [x] Protecție la subtensiune/supratensiune configurată corect.
* [x] Protecție TVS la intrarea alimentării (_**USBLC6-2SC6Y**_).
* [x] Toate intrările de alimentare sunt alimentate cu tensiunea corectă.
* [x] Consumul estimat de energie pe fiecare traseu de putere corespunde cu specificațiile regulatorului.

## Decuplare

* [x] Decuplare prezentă pentru toate IC-urile.
* [x] Decuplare de masă prezentă la sursa de alimentare.

## Semnale

* [x] Semnalele au nivel logic corect pentru pinul de intrare.
* [x] Pull-up pe toate ieșirile open-drain.
* [x] TX/RX corect pereche pentru UART, SPI.
* [x] Polaritatea semnalelor de activare (enable) high/low este corectă.

## Pini de inițializare / strap

* [x] Pull-up / pull-down pe toate semnalele care trebuie să aibă o stare definită la pornire.
* [x] Pinii de configurare conectați la netul corespunzător pentru starea dorită.
* [ ] Conector JTAG/ICSP prevăzut pentru dispozitivul programabil. (Schema nu prevede o asemenea conexiune dedicată)

## Depanare / posibilitate de rework

* [x] Asigură puncte multiple de masă.
* [x] Masă dedicată în apropiere de punctele de test analogice.
* [x] Puncte de test pe toate traseele de putere.
* [x] Puncte de test pe semnalele de interes care pot necesita sondare în timpul punerii în funcțiune sau depanării.


# 2. Board

## General

* [x] DRC pentru layout aprobat 100%. (cu 2 erori acceptate conform specificațiilor proiectului)
* [x] Traseele nu conțin unghiuri drepte.
* [x] Dimensiunile de contur și forma plăcii corespund cerințelor proiectului (inclusiv decupaj în zona antena ESP32C6)
* [x] Componentele principale amplasate conform documentației.

## Decuplare

* [x] Condensatorii de decuplare cât mai aproape posibil de pinii de alimentare.

## Footprints

* [x] Confirmă disponibilitatea componentelor în pachetul selectat.
* [x] Confirmă că componentele (mai ales conectorii și regulatoarele) pot susține curentul dorit în pachetul ales.
* [x] Verifică dacă simbolul schematic corespunde cu pachetul ales.
* [x] Confirmă că diagrama de pini este pentru partea superioară vs inferioară a componentului.
* [x] Modele 3D obținute și verificate.
* [x] Deschideri în soldermask pe toate pad-urile

## Semnale de mare viteză

* [x] Distanță suficientă față de potențiale interferențe.
* [x] Trasee de lungime potrivită dacă este necesar.
* [x] Minimizează trecerile peste întreruperi sau schimbări de straturi; folosește condensatori sau via-uri de legătură dacă nu se poate evita.
* [x] Adaugă vias-uri de legătură către planul de masă în pad-urile mari din stratul superior pentru a evita rezonanțele.

## Alimentare

* [x] Minim de întreruperi în plane cauzate de vias-uri.
* [x] Lățime suficientă pentru trasee pentru curentul necesar.


## Mecanic

* [x] Confirmă că toți conectorii către alte sisteme respectă standardele mecanice (orientare, poziție cheie etc.).
* [x] LED-uri, butoane și alte elemente UI pe partea externă a plăcii.
* [x] Spațiu liber în jurul IC-urilor mari pentru disiparea căldurii.
* [-] Confirmă dimensiunile PCB-ului și poziția/diametrul găurilor de montare cu proiectul carcasei sau rack-ului. (Vezi issue #1)
* [-] Plan de masă pe top și bottom. (Vezi issue #2) 
* [x] Componentele nu se suprapun fizic.
* [x] Spațiu liber în jurul punctelor de test pentru accesul sondelor.


## Solder mask

* [x] Confirmă geometria pad-urilor SMD.
* [x] Distanță adecvată în jurul pad-urilor.

## Silkscreen

* [x] Dimensiunea textului în limitele producătorului.
* [-] Textul nu se suprapune cu găuri sau pad-uri de componente. (Vezi issue #3)
* [x] Textul eliminat complet sau mutat în afara zonelor aglomerate cu componente/via-uri.
* [-] Punctele de test etichetate dacă spațiul permite. (Vezi issue #4)


## Producție CAM

* [x] Export fișierele Gerber, cpl.


# 3. Readme

* [-] Diagrama block cu toate componentele și cum sunt ele conectate. (Vezi issue #5)
* [x] Bill Of Materials.
* [x] Descrierea în detaliu a funcționalității hardware.
* [x] Descrierea în detaliu a funcționalității pinilor ESP32-C6.
* [x] Imagini cu randări ale PCB-ului.
