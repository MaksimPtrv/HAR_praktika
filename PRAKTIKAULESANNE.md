# Praktikaülesanne: nutitelefoniandmetest tegevuse klassifitseerimine

## Taust

30 vabatahtlikku sooritasid kuut tegevust, kandes vöökohal kiirendusmõõturi ja güroskoobiga telefoni. Sensorandmed jagati 2,56-sekundilisteks osaliselt kattuvateks akendeks. Iga akna kohta on arvutatud 561 aja- ja sagedusdomeeni tunnust.

Klassid on:

1. `WALKING`
2. `WALKING_UPSTAIRS`
3. `WALKING_DOWNSTAIRS`
4. `SITTING`
5. `STANDING`
6. `LAYING`

Üks rida tähendab üht sensoriakent, mitte üksikut sensori mõõtmist. Sama inimese ja järjestikuste akende vaatlused on omavahel seotud.

## Eesmärk

Treeni klassifikatsioonimudel, mis ennustab kuuest tegevusest õige klassi. Põhitulemus on **macro-F1**. Näita lisaks weighted-F1 ja accuracy, kuid põhjenda, miks valisid põhimõõdikuks macro- või weighted-F1.

Ülesanne ei eelda süvaõpet ega `Inertial Signals` toorandmete kasutamist. Kasuta valmis 561 tunnusega `X_train.txt` ja `X_test.txt` faile.

## Ülesanded

### 1. Andmete laadimine ja kontroll

- Laadi treening- ja testtunnused, sihtmärgid ning subjektide ID-d.
- Lisa tunnustele `features.txt` põhjal veerunimed. Arvesta, et osa nimesid kordub.
- Kontrolli kujusid, puuduvaid väärtusi, klassijaotust ja seda, et kõigil ridadel on sihtmärk ning subjekt.
- Selgita lühidalt, mida üks andmerida esindab.

### 2. Valideerimisplaan

- Hoia ametlik testkomplekt lõpliku hinnangu jaoks puutumata.
- Tee mudelivalik ainult treeningandmetel.
- Kasuta valideerimisel `subject_train.txt` subjektigruppe, näiteks `StratifiedGroupKFold` või `GroupKFold` abil.
- Tõesta kontrolliga, et ühegi foldi treening- ja valideerimisosas ei ole sama subjekti.
- Selgita, miks tavaline juhuslik ridade split oleks 50% kattuvate akende tõttu riskantne.

### 3. Baasmudel

- Treeni vähemalt üks lihtne võrdlusmudel, näiteks `DummyClassifier`.
- Raporteeri selle macro-F1. Baasmudel näitab, kas pärismudel õpib midagi sisulist.

### 4. Klassifikatsioonimudel

- Vali vähemalt üks mõistlik klassifitseerija, näiteks logistiline regressioon, lineaarne SVM, RBF-SVM või random forest.
- Pane eeltöötlus ja mudel ühte scikit-learn `Pipeline`-i.
- Põhjenda:
  - kas ja miks skaleerid tunnuseid;
  - miks valitud mudel sobib;
  - miks feature engineering või feature selection on vajalik või miks valmis tunnustest piisab;
  - miks valitud F1-variant sobib klassijaotusega.
- Ulatuslik hüperparameetrite otsing ei ole nõutud. Piisab ühest mudelist ja kuni mõnest läbimõeldud seadistusest.

### 5. Mudeli võrdlemine ja valik

- Hinda mudelit subjektipõhise ristvalideerimisega.
- Näita foldide macro-F1 väärtusi, keskmist ja standardhälvet.
- Võrdle tulemust baasmudeliga.
- Vali lõplik mudel valideerimistulemuse, mitte testtulemuse põhjal.

### 6. Lõplik testimine

- Treeni valitud pipeline kõigil treeningandmetel.
- Ennusta ametlik testkomplekt ainult üks kord pärast mudelivalikut.
- Raporteeri vähemalt macro-F1, weighted-F1, accuracy ja klassipõhine classification report.

### 7. Vigade analüüs

- Visualiseeri normaliseeritud confusion matrix.
- Nimeta vähemalt kaks klassipaari, mida mudel kõige rohkem segamini ajab.
- Paku vähemalt kaks realistlikku järgmist sammu mudeli või eksperimendi parandamiseks.

## Esitatavad failid

1. Käivitatud Jupyter Notebook koos väljundite, jooniste ja põhjendustega.
2. Lühike `README.md`, milles on:
   - käivitamise juhis;
   - kasutatud Pythoni versioon ja sõltuvused;
   - seed;
   - peamine valideerimis- ja testtulemus.
3. Vajaduse korral eraldi abifailid. Andmestikku ennast ei ole vaja esitada.

Notebook peab töötama algusest lõpuni ilma käsitsi muutujaid vahepeal muutmata.

