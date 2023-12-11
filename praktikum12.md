# Skriptimine Linuxis
Käesolev praktikum annab ülevaate käsurea skriptide loomisest Linuxis.

## Ajaarvamine
* 9:00 - 10:30
* 11:00 - 12:30
* 


## Sisu
* Skriptide loomine ja käivitamine
  * päise lisamine - #!/bin/sh
  * Silumisvahendina on kasulik lipp -x: näiteks sh -x skriptinimi.sh või esimesel real #!/bin/sh -x
* Muutujad ja käsurea parameetrid
  * Kasutades ülakomasid (') teksti ümber, ei asendata seal sees muutujate väärtusi, (") kasutades aga mõjub.
  * skrpiti käivitamine argumendiga: ./esimene.sh "Juku Mets"
* Interaktiivne sisend
  * küsida kasutaja käest täiendavat informatsiooni (näiteks failinime), saab kasutada read-käsku
* Juhtvood
  * IF-ELSE: NB! Pööra tähelepanu nurksulgude ees ja järel tühikute kasutamisele!
  * While: While-tsükli sisu korratakse seni, kuni tingimus on tõene
  * For: nimekirja või listi läbi vaatamiseks, NB! Kui tegemist on teksti sisaldavate muutujatega, siis on soovitav muutuja kasutamisel ümbritseda see jutumärkidega nii: echo "$i"
* Funktsioonid
  * 
* Skriptimine ja AI

### Ülesanne 3
#!/bin/sh

echo "Sisesta oma nimi:"

read nimi

echo "Sisesta oma eriala:"

read eriala

echo "Sisesta oma martiklinumber"

read martiklinumber

echo "Tere, $nimi!"

echo "$nimi õpib erialal $eriala."

echo "Tema martiklinumber on $martiklinumber"

<img width="246" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/ce4223dc-1426-41d2-b2ff-906a906b101c">


### Ülesanne 4
#!/bin/bash



read -p "Sisesta algne laiend: " laiend1

read -p "Sisesta uus laiend: " laiend2



for fail in $(ls); do

  if [ "${fail##*.}" = "${laiend1:1}" ]; then

    uus_nimi="${fail/$laiend1/$laiend2}"

    mv "$fail" "$uus_nimi"

  fi

done

echo "Kõik $laiend1 failid on ümber nimetatud laiendiks $laiend2."

<img width="273" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/14aadb1a-8d56-454b-8a29-679d53f620ea">
