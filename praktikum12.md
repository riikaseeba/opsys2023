# Skriptimine Linuxis
Käesolev praktikum annab ülevaate käsurea skriptide loomisest Linuxis.

## Ajaarvamine
* 9:00 -10:30


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

### Ülesanne 4
#!/bin/bash

kaust=$1

algne_laiend=$2

uus_laiend=$3

for fail in "$kaust"/*"$algne_laiend"

do

    if [ -f "$fail" ]

    then

        uus_nimi=$(basename "$fail" "$algne_laiend")"$uus_laiend"

        mv "$fail" "$kaust"/"$uus_nimi"

        echo "Fail $fail nimetati ümber $uus_nimi failiks."

    fi

done
