# Failiõigused Linuxis

Käesolevas praktikumis sain ülevaate Unixi failiõigustest ning lahendasin hulgalisest ülesandeid seoses failiõigustega seotud atribuutidest, probleemidest ja võimalustest. Praktikum sooritamine võttis aega natuke vähem, kui 6h. Aega kulus info otsimisele ja sügavuti aru saamisele. 5.4 kuni 5.6 ülesanded olid pisut kergemad, teistele kulus rohkem aega.

Allpool on näha iga ülesande tulemus.


**Ülesanne 5-1:** 

**a)**  Unixi omanikul on vaja kausta /tmp/kaust lugemisõigust(r), et lugeda kataloogi sisu. 
     Selleks et faili lugeda kataloogist on omanikul vaja ka faili minufail.txt enda lugemisõigust (r).

**b)**   Unixi omanikul on vaja kausta /tmp/kaust kirjutamisõigust (w), et faili kustutada.
     Selleks, et faili minufail.txt kustutada, peab olema omanikul faili kirjutamisõigus (w).


**Ülesanne 5-2:** 

Käsuga chmod a=x skriptifail annab kõigile õiguse faili käivitada, kuid sellest ei piisa edukaks käivitamiseks. Selleks, et selle faili sisu samuti ekraani näha on vaja lisaks käivitusõigusele ka lugemisõigust (+rx).


**Ülesanne 5-3:** 

Omanimeline grupp aitab Unix-põhises operatsioonisüsteemis hallata ja kontrollida kasutajate juurdepääsu failidele ning soodustada koostööd ja turvalisust. See on osa süsteemi õiguste ja turvamudelist ning aitab tõhusalt hallata ressursside jagamist.


**Ülesanne 5-4:**

Kasutajal endal ja grupil "majasisene" peaks olema lugemisõigus. (-r--r-----)
(Aga kui kasutada käsku sudo cat uusfail.txt, siis on lugemisõigust vaja ainult kasutajal. (-r--------))

<img width="442" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/2c44a37f-8ade-459c-95e9-fe851329bbfa">


**Ülesanne 5-5:**

Setuid õigus võimaldab piiratud juurdepääsusid süsteemiressurssidele, et saaks käivitada programmi kasutajaõigustega, mis erinevad programmi omaniku tegelikest õigustest.

<img width="339" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/34925ad2-0beb-4e5c-8271-ea3064dd1372">


**Ülesanne 5-6:** 

Setuid ja setgid failid on ohtlikud, kuna need võivad anda volitamata kasutajale juurdepääsu failile/kataloogile mõne teise kasutaja nimel oleva programmi käitamiseks.,


**Ülesanne 5-7:**

Pilt, kus peeter ise proovib eemaldada faili, mis tal ka õnnestub:
<img width="243" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/77397ddd-9d33-4628-9626-52e848b3e7f9">

Tavakasutaja (minu enda nimeline), ei õnnestu:
<img width="287" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/9d8d65f8-0e09-429d-8d22-1e3db6d877de">


Opetaja, õnnestub:
<img width="284" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/9d3833ae-b6db-4a38-86d8-9a5aae03c6b5">


**Ülesanne 5-8:**

<img width="297" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/41fd7fe4-abeb-4d82-a622-d8080f77a904">


**Ülesanne 5-9:**

**a)** chattr +i parameetritega faili sisu ei saa keegi kirjutada ega kustutada. See atribuut takistab faili sisu muutmist ja kustutamist, muutes faili "kirjutuskaitstud".

**b)** kõigepealt: **sudo chattr -i testfail-2**
siis: **rm testfail-2**
