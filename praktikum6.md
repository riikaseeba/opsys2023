# Protsessid ja signaalid

Käesolvas praktikumis tutvusin protsessidega lähemalt (protsessi käivitamisest väljundite suunamiseni). 
Praktikumi sooritamiseks kulus seekord aega umbes viis tundi. Kõige keerulisem ülesanne oli viimane, ehk neljas ülesanne. Suurema aja võttis pikemate käsuridade koostamine, aga teemadest viimane, mis selgeks sai, oli sisendi ja väljundi ümbersuunamine.

## Järgnevad ülesannete lahenduste tulemused:

### Ülesanne 1

saatsin SIGCONT-signaali veendumaks, et gedit jälle toimiks:

<img width="795" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/f1879d75-7f64-4838-a11d-0f5ab80845bc">


### Ülesanne 2

SIGHUP signaaliga toimetamine: 

<img width="454" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/c91dbebb-8bc0-4ea5-b002-fc96fb1c831b">


### Ülesanne 3

käsk teksti kujul: 
ps -axu | grep daemon | tr -s " " | cut -d" " -f11-

<img width="660" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/2003e293-bea4-4800-a403-4aa9ce3f41d9">

### Ülesanne 4

käsk teksti kujul: 
ip a | grep -w inet | grep -v 127.0.0.1 | tr -s " " | cut -d" " -f3 | cut -d"/" -f1

<img width="584" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/97dfe36f-6c68-47f4-998f-2d2efdc8846b">
