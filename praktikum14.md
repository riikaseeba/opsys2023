# Azure VM ja WSL

Käesoleva praktikumi teemaks oli Azure keskkonna näitel pilvetehnoloogiate katsetamine. 
Täpsemalt Windows 11 virtuaalmasina loomine, sellega ühendumine ja sinna peale WSL-i (Windows SubSystem for Linux) installimine.


## Konspekt
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
