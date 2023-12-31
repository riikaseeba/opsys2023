# Skriptimine Linuxis
Käesolev praktikum andis ülevaate käsurea skriptide loomisest Linuxis. 

Praktikumi sooritamine sujus ilma suuremate probleemideta. Praktikumi sooritajal kulus aega ligi neli tundi.
Lahenduste vastused leiab siit aruandest allpool.

Head hindamist praktikumi juhendajale!

## Sisu kordamiseks
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
  * Tihtiesinevaid tegevusi skriptides on mõistlik kirjeldada funktsioonina, mida saab hiljem mitmeid kordi välja kutsuda.
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
    read -p "Sisesta algne laiend (näiteks .txt): " laiend1
    read -p "Sisesta uus laiend (näiteks .csv): " laiend2
    for fail in *$laiend1; do
      if [ "${fail##*.}" = "${laiend1:1}" ]; then
        uus_nimi="${fail/$laiend1/$laiend2}"
        mv "$fail" "$uus_nimi"
      fi
    done
    echo "Kõik $laiend1 failid on ümber nimetatud laiendiks $laiend2."

<img width="372" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/0473d421-923e-4732-9386-5bd88ba0b136">

### Ülesanne 5

    #!/bin/bash
    protsessi_nimi=$1
    IFS=$'\n'
    for line in $(ps -A | grep "$protsessi_nimi"); do
            pid=$(echo " ""$line" | tr -s ' ' | cut -d ' ' -f2)
            nimi=$(echo " ""$line" | tr -s ' ' | cut -d ' ' -f5)
            echo "$nimi: $pid"
    done

<img width="261" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/2ed1beec-6670-4fc6-8faf-94b648c0b810">

### Ülesanne 6

    #!/bin/bash
    astendame () {
            vastus=$1
            for ((i=1; i<$2; i++)); do
                    vastus=$((vastus * $1))
            done
            echo  $vastus
    }
    vastus=$(astendame 9 5)
    echo $vastus

<img width="372" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/ac49fa4c-c980-445c-b8d3-ec510829a324">

### Ülesanne 7

* minu küsimus:
  * <img width="953" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/b4b75eb6-bba7-490e-9aa3-e1704749257b">
* microsoft bing vastus:
  * <img width="958" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/0355c51b-75cc-459f-9cc2-0520d1096442">

