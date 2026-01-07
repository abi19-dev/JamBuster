# 🚦 JamBuster: Adaptivna simulacija saobraćajnih semafora

## 📌 Opis projekta

Ovaj projekat predstavlja **agentsku simulaciju saobraćajne raskrsnice sa adaptivnim semaforima**, razvijenu u alatu **NetLogo** u okviru predmeta *Modeliranje i simulacije*.

Cilj simulacije je uporediti **klasično (fiksno) upravljanje semaforima** sa **adaptivnim pristupom**, gdje se trajanje zelenog svjetla dinamički prilagođava na osnovu trenutnog stanja saobraćaja (dužine redova vozila).

---

## 🧠 Pristup modeliranju

Model je zasnovan na **agentskom modeliranju (Agent-Based Modeling – ABM)**.  
Pojedinačna vozila su modelirana kao autonomni agenti koji se kreću kroz sistem i reaguju na saobraćajnu signalizaciju i druge agente.

---

## 👥 Agenti u modelu

### 🚗 Vozila (turtles)
Vozila su glavni agenti u simulaciji.

**Osobine:**
- smjer kretanja (Sjever, Jug, Istok, Zapad)
- vrijeme čekanja
- brzina kretanja
- traka kretanja

**Ponašanje:**
- kretanje po definisanim trakama
- zaustavljanje na crveno svjetlo
- izbjegavanje sudara
- akumulacija vremena čekanja
- napuštanje sistema po dolasku na ivicu mape

---

### 🚦 Semafor (centralni kontrolni agent)
Semafor je modeliran kao **centralni adaptivni kontrolni agent**.

**Uloga:**
- upravlja fazama saobraćaja (Sjever–Jug / Istok–Zapad)
- mjeri dužinu redova vozila
- prilagođava trajanje zelenog svjetla
- balansira protok saobraćaja

---

### 🟩 Okolina (patches)
Patch-evi predstavljaju statičnu okolinu:
- ceste i trake
- stop-linije
- saobraćajne oznake
- travnate površine i drveće

Patch-evi ne donose odluke, ali direktno utiču na ponašanje agenata.

---

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1031c61d-91ba-4ab9-aa3c-a69b8b46c289" />

## 🎛️ Kontrole (Slideri i prekidači)

| Kontrola | Opis |
|--------|------|
| `spawn-rate` | Broj vozila koja ulaze u sistem po jednom ticku |
| `speed` | Brzina kretanja vozila |
| `phase-length` | Trajanje zelene faze (fiksni režim) |
| `min-green` | Minimalno trajanje zelene faze (adaptivni režim) |
| `max-green` | Maksimalno trajanje zelene faze |
| `queue-threshold` | Prag osjetljivosti adaptivnog algoritma |
| `adaptive?` | Uključuje / isključuje adaptivni režim |

<img width="450" height="662" alt="image" src="https://github.com/user-attachments/assets/d275ce93-c798-45c3-a9d8-d90cd81ae1db" />

---

## 📊 Izlazni podaci i mjerenja

### Monitori
- **avg-wait** – prosječno vrijeme čekanja vozila
- **cars** – broj vozila trenutno u sistemu
- **ns-queue** – dužina reda u smjeru sjever–jug
- **ew-queue** – dužina reda u smjeru istok–zapad

### Grafovi
- **Average wait** – promjena prosječnog vremena čekanja kroz vrijeme
- **Queues** – poređenje dužina redova u oba smjera

<img width="698" height="526" alt="image" src="https://github.com/user-attachments/assets/6a5c9fe0-4422-4672-a714-1ece327089d3" />
<img width="696" height="517" alt="image" src="https://github.com/user-attachments/assets/19a284f5-5c78-4cb8-ab0c-0aed82542c48" />

---

## 🔄 Adaptivni algoritam

Adaptivni algoritam u realnom vremenu upoređuje dužine redova vozila.  
Ako razlika između redova pređe definisani prag, zeleno svjetlo se produžava u opterećenijem pravcu, uz poštovanje minimalnog i maksimalnog trajanja faze.

Na ovaj način se:
- smanjuje prosječno vrijeme čekanja
- izbjegava dugotrajno zagušenje
- postiže bolja ravnoteža protoka saobraćaja

---

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/00b5eab0-7db7-47e6-9123-4f8a8f340218" />


## ✅ Zaključci

- Adaptivni semafori značajno smanjuju prosječno vrijeme čekanja
- Sistem se bolje prilagođava promjenama u intenzitetu saobraćaja
- Jednostavan adaptivni algoritam nadmašuje fiksno upravljanje semaforima
