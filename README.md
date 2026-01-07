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

---

## 🔄 Adaptivni algoritam

Adaptivni algoritam u realnom vremenu upoređuje dužine redova vozila.  
Ako razlika između redova pređe definisani prag, zeleno svjetlo se produžava u opterećenijem pravcu, uz poštovanje minimalnog i maksimalnog trajanja faze.

Na ovaj način se:
- smanjuje prosječno vrijeme čekanja
- izbjegava dugotrajno zagušenje
- postiže bolja ravnoteža protoka saobraćaja

---

## ✅ Zaključci

- Adaptivni semafori značajno smanjuju prosječno vrijeme čekanja
- Sistem se bolje prilagođava promjenama u intenzitetu saobraćaja
- Jednostavan adaptivni algoritam nadmašuje fiksno upravljanje semaforima

---

## 🛠️ Korištene tehnologije
- **NetLogo**
- Agentsko modeliranje (ABM)

---

## 🎓 Informacije o predmetu
**Predmet:** Modeliranje i simulacije  
**Tip projekta:** Agentska simulacija  
**Alat:** NetLogo  

---

## 📷 Preporučene slike (za izvještaj ili prezentaciju)

1. Početno stanje simulacije (setup)
2. Fiksni režim rada (adaptive OFF)
3. Adaptivni režim rada (adaptive ON)
4. Graf prosječnog vremena čekanja
5. Graf dužine redova
6. Detalj raskrsnice (trake, boje, zelenilo)
7. Pregled korisničkog interfejsa
