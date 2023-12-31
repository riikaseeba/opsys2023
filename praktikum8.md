# RAID ja andmete varundamine

Käesolevas praktikumis sain ühtteist teada RAID-arhitektuurist, mida töötlesin ka praktikas, ning sain paigaldada oma virtuaalmasinatele ka Nextcloudi. 

Selles praktikumi kulus mul siiani kõige rohkem aega ehk 7h. Mul tekkis probleeme RAID 1 süsteemi käsitlemine Ubuntiga, kui juhenditeksti mõstsin valesti ja jäin ringiratast _snapshot_'idega mässama nii kaua, kuni "kala" välja tuli ja probleemi ära lahendasin.

Kõigi ülesannetega olen saanud edukalt hakkama, mille tõestused leiab ka siit aruandest allpool.

## RAID 1 Windowsiga
_Tehke ekraanipilt mõlemast (nii tervest kui katkisest/(puuduv)) kettast, nii et oleks näha ka teie punktis 3 kettale K: loodud fail ja selle sisu._:

![image](https://github.com/riikaseeba/opsys2023/assets/144622934/07aadcf9-b84c-4753-8cfa-86fcb55926e0)

### RAID 1 Ubuntuga
_Lisage aruandesse ekraanipildid käskude lsblk ja cat /proc/mdstat väljunditest._:

lsblk:
<img width="428" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/c38224a5-fe2b-40a8-a45b-97f7243e83b4">

cat /proc/mdstat:
<img width="280" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/9ae3dab0-f3ed-47ce-a747-24e80c5dcc7c">

_Lisage oma aruandesse jällegi ekraanipildid käskude lsblk ja cat /proc/mdstat väljunditest:_

<img width="364" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/d0b2297b-a8e0-4efa-97ec-51b533ed1004">

## Nextcloudi varundamine Windows 11-s
Tehke ekraanipilt sünkroniseeritud kaustast UT\OS\Operatsioonisüsteemid_2023 ja failist nextcloud_test_<eesnimi>.txt Nextcloudi veebiliideses nii, et näha oleks faili nimi, faili sisu (üleval paremas nurgas) ja jagamine õppejõuga:

<img width="959" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/50bf0c86-e1e3-43ff-a6d8-f2de08b3b8bb">

### Nextcloudi varundamine Ubuntus
Lisage aruandesse ekraanivaade, kus näha faili sisu ja Properties-akna sisu:

<img width="960" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/db0f44a5-7085-48d5-ae79-d4ab87d67983">

## Microsoft OneDrive
Esitage ekraanivaade tõestamaks, et teil on olemas aktiivne OneDrive failide sünkroniseerimine kohaliku arvuti ja pilveandmete vahel. Vaheleht Settings -> Account:
<img width="645" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/d4a3a5c4-b787-49f1-97e9-3bf527c1dfc6">
