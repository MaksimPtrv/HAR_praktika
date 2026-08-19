# Human Activity Recognition — praktikandi klassifikatsiooniülesanne

Selles kaustas on mõõduka raskusastmega masinõppeülesanne UCI **Human Activity Recognition Using Smartphones** andmestikuga. Eesmärk on ennustada ühe 2,56-sekundilise akna põhjal inimese tegevust kuue klassi vahel.

Tehisaru kasutamine on soovituslik, kuid code-review ajal on vaja osata selgitada enda lahendust.

## Kausta sisu

- `PRAKTIKAULESANNE.md` — praktikandile antav ülesanne ja hindamisrubriik.
- `student/HAR_praktikandi_mall.ipynb` — soovitusliku struktuuriga töömall.
- `requirements.txt` — minimaalsed Pythoni sõltuvused.

Näidislahendus kasutab valmis 561 tunnusega andmetabeleid (`X_train.txt` ja `X_test.txt`). Kaust `Inertial Signals` jääb selle ülesande põhiosast välja, sest raw-signaalide süvaõpe muudaks töö ebavajalikult keeruliseks.
