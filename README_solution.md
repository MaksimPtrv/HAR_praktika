# HAR Praktika — lahenduse README

## Käivitamine
1. Paigalda sõltuvused: `pip install -r requirements.txt`
2. Ava notebook: `student/HAR_praktikandi_mall.ipynb`
3. Setup-lahtris määra `DATA_DIR` — tee `UCI HAR Dataset` kausta
4. Käivita kogu notebook algusest lõpuni: Restart Kernel & Run All
   (kontrollitud ka käsuga `jupyter nbconvert --to notebook --execute --inplace student/HAR_praktikandi_mall.ipynb`, mis läbis veatult)

## Keskkond
- Python: 3.14.3
- Sõltuvused: vaata `requirements.txt`

## Seed
SEED = 42 (kasutusel läbivalt: `random`, `numpy`, `StratifiedGroupKFold`, `DummyClassifier`, `LogisticRegression`)

## Valideerimine
5-fold `StratifiedGroupKFold`, grupeeritud `subject_train` järgi. Kontrollitud, et üheski foldis train- ja validation-subjektid ei kattu (overlap=0 kõigis foldides).

## Peamised tulemused

**Baseline (DummyClassifier, subjektipõhine CV):**
macro-F1 = 0.169 ± 0.010

**Mudel (LogisticRegression + StandardScaler pipeline, subjektipõhine CV):**
macro-F1 = 0.935 ± 0.038

**Testkomplekt (lõplik, üks kord pärast mudelivalikut):**
- macro-F1 = 0.9544
- weighted-F1 = 0.9545
- accuracy = 0.9545

## Vigade analüüs
Suurim segamini aetud klassipaar: `SITTING` → `STANDING` (12% tegelikest SITTING juhtudest), vastupidises suunas `STANDING` → `SITTING` (3%). Mõlemad on staatilised olekud, mille eristamine sõltub peenest kehaasendi infost, mitte selgest liikumisdünaamikast — seetõttu on need lineaarsele mudelile raskemad eristada kui kõndimisklassid.