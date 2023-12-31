# Azure VM ja WSL

Käesoleva praktikumi teemaks oli Azure keskkonna näitel pilvetehnoloogiate katsetamine. 
Täpsemalt Windows 11 virtuaalmasina loomine, sellega ühendumine ja sinna peale WSL-i (Windows SubSystem for Linux) installimine.
Praktikumi läbimiseks kulus aega natuke rohkem kui viis tundi.
Sassi läksid algul perenimi ja eesnimi ning praktikumi vahepeal tekkis suur segadus selle kohta, mis virtuaalmasinas, millisel käsureal peab ülesannet parasjagu lahendama. Muidu enamus tööst kujunes hästi. Ülesannete lahendused leiab siit aruandest.


## Konspekt (bing)
1. Mis on **Azure Subscription**?
   *  Azure’i tellimus on loogiline konteiner, mida kasutatakse Azure’i ressursside, nagu virtuaalmasinad (VM-id), andmebaasid jne, pakkumiseks1.
     Iga Azure’i ressurss on seotud ainult ühe tellimusega2.
     Kui loote Azure’i ressursi, näiteks VM-i, määratlete, millise tellimusega see seotud on1.

3. Mis on **Azure Resource**?
   *  Azure’i ressurss on Azure’i poolt hallatav üksus.
     Virtuaalmasinad, virtuaalsed võrgud ja salvestuskontod on kõik Azure’i ressursside näited1.
     Kui loote uue ressursi, loote tegelikult Azure’i teenuse2.

5. Mis on **Azure Resource Group**?
   *  Azure’i ressursside rühm on loogiline konteiner, mis hoiab seotud ressursse Azure’i lahenduse jaoks.
     Ressursside rühm võib sisaldada kõiki lahenduse ressursse või ainult neid ressursse, mida soovite rühmana hallata3.
     Otsustate, kuidas soovite ressursse ressursside rühmadele jaotada, lähtudes sellest, mis teie organisatsiooni jaoks kõige mõttekam on3.

### Ülesanne 1: _Tehke Azure virtuaalmasina ülevaateaknast Essentials ekraanivaade_

![image](https://github.com/riikaseeba/opsys2023/assets/144622934/b2209857-8ea2-49a8-a8f4-d04791ec91b7)

### Ülesanne 2: Tehke Azure virtuaalmasina ülevaateaknast Properties ekraanivaade

<img width="771" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/68b3cff3-7814-4997-a574-4b0293c53b56">
<img width="702" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/1d6554c9-b267-46da-b188-0b85502d8bad">

### Ülesanne 3:_Minge Settings -> System -> About ning tehke ekraanivaade kogu RDP aknast_

  *  Juhtus nii, et perenimi-admin on minul eesnimega.
![image](https://github.com/riikaseeba/opsys2023/assets/144622934/3454f1cb-a48c-4831-a889-cc2429b5d674)

### Ülesanne 4: _Avage powershell abil ühendus enda Azure pilvearvuti ja tehke ekraanivaade kogu powershelli aknast_

<img width="611" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/f4bc0b74-cf63-4e1c-a199-eeee1eb6490d">

### Ülesann 5: _Esitage ekraanivaade, kus te enda isikliku arvuti käsurealt sisestate käsu: ssh -J perenimi-admin@perenimi2023.northeurope.cloudapp.azure.com eesnimi@WSL-IP-Address_

![image](https://github.com/riikaseeba/opsys2023/assets/144622934/425792ca-ca4a-4316-9dc3-d883acfa2868)

### Ülesanne 6

WSL:
![image](https://github.com/riikaseeba/opsys2023/assets/144622934/d8599592-342c-4589-a893-1a9b6fbf785b)



