# Review


# Listă de verificare pentru revizuirea schemei electrice

## General

* [ ] Verificare CAD ERC complet curată (100%). Dacă există erori false din cauza particularităților software-ului, fiecare excepție trebuie inspectată și aprobată ca fiind invalidă.
* [ ] Verifică numerele pinilor pentru toate simbolurile din schemă în raport cu datasheet-ul sau documentația interfeței externe (dacă nu a fost deja testată pe placă).
* [ ] Simbolul schematic se potrivește cu pachetul componentului ales.
* [ ] Pad-urile termice sunt conectate la șina corectă de alimentare (nu întotdeauna la masă/GND).
* [ ] Interfețele de depanare nu sunt dezactivate în modul sleep.
* [ ] Verifică pinajul tuturor cablurilor către alte plăci din sistem (direct vs oglindit).

## Componente pasive

* [ ] Specifică tensiunea putere / toleranța componentelor conform cerințelor.
* [ ] Condensatorii ceramici sunt devalorizati corespunzător pentru curba C/V.
* [ ] Componentele polarizate sunt specificate clar în schemă dacă se folosesc condensatori electrolitici etc.

## Alimentare

### Intrare alimentare sistem

* [ ] Protecție la suprasarcină și/sau tensiune inversă la intrarea sistemului.
* [ ] Protecție TVS la intrarea alimentării.
* [ ] Verifică capacitatea totală de intrare și adaugă limitator de curent de pornire dacă este necesar.

### Regulatoare

* [ ] Protecție la subtensiune/supratensiune configurată corect, dacă este utilizată.
* [ ] Verifică consumul estimat de energie pe fiecare șină în raport cu specificațiile regulatorului.
* [ ] Rezistoare de măsurare a curentului sunt plasate după condensatorii de ieșire ai regulatorului, nu în bucla de comutație.
* [ ] Folosește detecție la distanță (remote sense) pe șine de tensiune joasă sau curent mare.
* [ ] Regulatoarele liniare și IC-urile de referință de tensiune sunt stabile cu ESR-ul condensatorului de ieșire ales.
* [ ] Confirmă secvențierea șinelor de alimentare conform datasheet-urilor dispozitivelor.

### Decuplare

* [ ] Decuplare prezentă pentru toate IC-urile.
* [ ] Decuplarea respectă sau depășește recomandările producătorului dacă sunt specificate.
* [ ] Decuplare de masă prezentă la sursa de alimentare.

### General

* [ ] Toate intrările de alimentare sunt alimentate cu tensiunea corectă.
* [ ] Verifică semiconductorii discreți de mare putere și pasivele să facă față sarcinii așteptate.
* [ ] Șinele analogice sunt filtrate / izolate de circuitele digitale, după caz.

### Erate

* [ ] Citește fișele de erate (dacă sunt disponibile) pentru toate dispozitivele principale.
* [ ] STM32: nu folosi pinul JTRST ca I/O.

## Semnale

### Digital

* [ ] Semnalele au nivel logic corect pentru pinul de intrare.
* [ ] Pull-up pe toate ieșirile open-drain.
* [ ] Pull-down pe toate ieșirile PECL.
* [ ] Terminare pe toate semnalele de mare viteză.
* [ ] Condensatori de cuplare AC pe transceivere gigabit.
* [ ] TX/RX corect pereche pentru UART, SPI, MGT, etc.
* [ ] Polaritatea / împerecherea corectă pentru perechile diferențiale.
* [ ] Polaritatea semnalelor de activare (enable) high/low este corectă.
* [ ] Respectă regulile de grupare I/O pe FPGA-uri etc.
* [ ] Dacă se folosesc convertori de nivel auto-senzoriali, asigură-te că receptorul intenționat nu are pull-up/down activ.

### Analog

* [ ] Constanta de timp RC pentru atenuatoare este rezonabilă raportat la frecvența de eșantionare ADC.
* [ ] Verifică răspunsul în frecvență al componentelor RF pe întreg domeniul de funcționare. Nu presupune că un amplificator „1–100 MHz” are același câștig pe toată banda.
* [ ] Verifică polaritatea feedback-ului pentru amplificatoarele operaționale.

### Ceasuri

* [ ] Toți oscilatorii respectă cerințele de jitter / toleranță de frecvență. Ai grijă specială la oscilatoarele MEMS — tind să aibă jitter mai mare.
* [ ] Condensatori de sarcină corecți pentru cristalele discrete.
* [ ] Cristalele sunt folosite doar dacă IC-ul are driver de cristal integrat.
* [ ] Respectă regulile pentru intrările capabile de ceas pentru FPGA-uri:
    * [ ] FPGAs Xilinx: ceasurile single-ended folosesc partea \_P a perechilor diferențiale.
    * [ ] Dacă este posibil, creează un design dummy cu toate ceasurile și semnalele cheie și verifică dacă se sintetizează corect (P&R).

### Pini de inițializare / strap

* [ ] Pull-up / pull-down pe toate semnalele care trebuie să aibă o stare definită la pornire.
* [ ] Pinii de configurare conectați la șina corectă pentru starea dorită.
* [ ] Conector JTAG/ICSP prevăzut pentru toate dispozitivele programabile.
* [ ] Flash de configurare/boot prevăzut pentru toate FPGA-urile sau MPUs fără memorie flash internă.
* [ ] Rezistoarele de referință au valoarea și șina de referință corectă.

### Protecție interfețe externe

* [ ] Ieșirile de alimentare (USB etc) sunt limitate în curent.
* [ ] Protecție ESD pe liniile de date care ies din placă.

### Depanare / posibilitate de rework

* [ ] Folosește rezistențe de 0 ohmi în loc de conexiuni directe pentru pini de strap, dacă este posibil.
* [ ] Asigură puncte multiple de masă pentru sondele de osciloscop.
* [ ] Masă dedicată în apropiere de punctele de test analogice.
* [ ] Puncte de test pe toate șinele de alimentare.
* [ ] Puncte de test pe semnalele de interes care pot necesita sondare în timpul punerii în funcțiune sau depanării.

## Termic

* [ ] Estimări de putere pentru toate IC-urile mari / de mare putere.
* [ ] Calcul termic pentru toate IC-urile mari / de mare putere.
* [ ] Specifică radiatoare (heatsinks) acolo unde este necesar.








# Listă de verificare pentru revizuirea layout-ului

## General

* [ ] [Revizuirea schemei](schematic-checklist.md) completă și aprobată, inclusiv schimbările de pini făcute în timpul layout-ului.
* [ ] DRC pentru layout curat 100%.

## Decuplare

* [ ] Condensatorii de decuplare cât mai aproape posibil de pinii de alimentare.
* [ ] Montare cu inductanță scăzută pentru decuplare (preferabil ViP dacă este disponibil, altfel via-uri în formă de „[]8”).

## DFM / Îmbunătățirea randamentului

* [ ] Toate regulile de design respectă capabilitățile producătorului.
* [ ] Minimizează utilizarea via-urilor/traseelor care se apropie de limitele de fabricație.
* [ ] Impedanță controlată specificată în notele pentru fabricație, dacă este cazul.
* [ ] Confirmă că calculele de impedanță includ soldermask-ul sau că masca a fost îndepărtată de pe traseele RF.
* [ ] Stackup-ul verificat cu producătorul și specificat în notele pentru fabricație.
* [ ] Tipul de finisare al plăcii specificat în notele pentru fabricație.
* [ ] Dacă se face panotare, adaugă indicatori de locație pentru detectarea problemelor locale la reflow.
* [ ] (recomandat) Marcatori de număr de strat pentru a asigura asamblarea corectă.
* [ ] Fiduciale prezente (pe ambele părți ale plăcii) dacă se dorește asamblare automată.
* [ ] Modelul de fiduciale este asimetric pentru a detecta plăci rotite sau întoarse.
* [ ] Respectă distanța dintre soldermask și cupru pe fiduciale.
* [ ] Panotarea specificată dacă este necesară.

## Empreinte (footprints)

* [ ] Confirmă disponibilitatea componentelor în pachetul selectat.
* [ ] Confirmă că componentele (mai ales conectorii și regulatoarele) pot susține curentul dorit în pachetul ales.
* [ ] Verifică dacă simbolul schematic corespunde cu pachetul ales.
* [ ] Confirmă că diagrama de pini este pentru partea superioară vs inferioară a componentului.
* [ ] Conectori FPC: Verifică dacă sunt pentru acces de sus sau de jos și validează pinajul.
* [ ] (recomandat) Printează PCB-ul 1:1 pe hârtie și compară cu componentele fizice.
* [ ] Modele 3D obținute (dacă sunt disponibile) și verificate față de empreinte.
* [ ] Deschideri în soldermask pe toate pad-urile SMT și PTH.

## Perechi diferențiale

* [ ] Rutate diferențial.
* [ ] Skew potrivit între trasee.
* [ ] Distanță corectă față de traseele necuplate.

## Semnale de mare viteză

* [ ] Distanță suficientă față de potențiali agresori.
* [ ] Potrivire de lungime dacă este necesar.
* [ ] Minimizează trecerile peste întreruperi sau schimbări de straturi; folosește condensatori sau via-uri de legătură dacă nu se poate evita.
* [ ] Confirmă că producătorul poate aduce cuprul până la marginea PCB-ului pentru conectori tip edge-launch.
* [ ] Verifică lățimea pad-urilor pe conectori și adaugă decupaje în plane dacă este necesar pentru a evita discontinuități de impedanță.
* [ ] Adaugă via-uri de legătură către planul de masă în pad-urile mari din stratul superior (ex. SMA) pentru a evita rezonanțele.

## Alimentare

* [ ] Minim de întreruperi în plane cauzate de anti-pad-uri pentru via-uri.
* [ ] Lățime suficientă pentru plane/trasee pentru curentul necesar.

## Analog sensibil

* [ ] Inele de protecție / cuști EMI prevăzute dacă este necesar.
* [ ] Separat fizic de surse de zgomot precum surse în comutație de curent mare.
* [ ] Ia în considerare efectul de microfon la MLCC-uri dacă sunt aproape de surse sonore puternice.

## Mecanic

* [ ] Confirmă că toți conectorii către alte sisteme respectă standardele mecanice (orientare, poziție cheie etc.).
* [ ] LED-uri, butoane și alte elemente UI pe partea externă a plăcii.
* [ ] Zone de excludere în jurul perimetrului PCB-ului, ghidaje de card, puncte de rupere pentru panotare etc. respectate.
* [ ] Componentele sensibile la stres (MLCC) sunt suficient de departe de V-score sau mouse-bites și sunt orientate pentru a reduce stresul la îndoire.
* [ ] Spațiu liber în jurul IC-urilor mari pentru radiatoare / ventilatoare dacă este necesar.
* [ ] Spațiu liber în jurul conectorilor detașabili pentru mufele de conectare.
* [ ] Spațiu liber în jurul găurilor de montare pentru șuruburi.
* [ ] Zone de excludere în plane pentru conectori ecranați, magnetici etc.
* [ ] Confirmă dimensiunile PCB-ului și poziția/diametrul găurilor de montare cu proiectul carcasei sau rack-ului.
* [ ] Verifică conexiunea/izolarea găurilor de montare.
* [ ] Componentele nu se suprapun fizic.
* [ ] Spațiu liber în jurul punctelor de test pentru accesul sondelor.
* [ ] Poziția găurilor de montare respectă regulile de proiectare ale carcasei (zonele de îndoire / sudură sunt respectate).

## Termic

* [ ] Relief-uri termice utilizate pentru conexiuni la plane (cu excepția cazurilor în care via-ul este folosit pentru disipare termică).
* [ ] Conexiuni solide la plane dacă se face disipare termică.
* [ ] Asigură echilibru termic pe componentele SMT pentru a reduce riscul de ridicare (tombstoning).

## Pastă de lipit

* [ ] Nu există via-uri fără capac pe pad-uri (cu excepția QFN-urilor de putere mică, unde se acceptă un grad mic de goluri).
* [ ] Pastă de lipit segmentată pentru QFN-uri.
* [ ] Pad-urile mici au 100% acoperire, pad-urile mari sunt reduse pentru a evita excesul de lipitură.
* [ ] Fără deschideri de pastă pe conectorii de margine sau punctele de test.

## Masca de lipire

* [ ] Confirmă geometria pad-urilor SMD vs NSMD.
* [ ] Distanță adecvată în jurul pad-urilor (tipic 50 µm).

## Serigrafie

* [ ] Dimensiunea textului în limitele producătorului.
* [ ] Textul nu se suprapune cu găuri sau pad-uri de componente.
* [ ] Textul eliminat complet sau mutat în afara zonelor aglomerate cu componente/via-uri.
* [ ] Marcaje de trasabilitate (revizie, dată, nume etc.) prezente.
* [ ] Căsuță de serigrafie pentru scriere / lipire număr de serie.
* [ ] Textul este oglindit corect pe stratul inferior.
* [ ] Punctele de test etichetate dacă spațiul permite.

## Specific pentru flex

* [ ] Componentele orientate pentru a reduce forțele de îndoire.
* [ ] Teardrop-uri la toate conexiunile fir-la-pad.

## Producție CAM

* [ ] Specific pentru KiCAD: rulează din nou DRC și actualizează zonele înainte de exportul fișierelor CAM pentru rezultate corecte.
* [ ] Exportă fișierele Gerber/drill simultan pentru consistență.
* [ ] Verificare vizuală a fișierelor CAM finale pentru a detecta eventuale aliniamente greșite.
