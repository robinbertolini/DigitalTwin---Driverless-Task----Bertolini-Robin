# 🏎️ Formula Student Driverless Simulation - E-Agle Task

Questo repository contiene lo sviluppo di un simulatore per un veicolo a guida autonoma realizzato in **Unreal Engine 5.7**. Il progetto si focalizza sulla creazione di un ambiente dinamico, sulla fisica accurata del veicolo e sulla simulazione della percezione sensoriale tramite LiDAR e Camera.

## 📌 Stato dell'Implementazione

### 🟢 Level 1: Racetrack & Environment
* **Track:** Realizzato un circuito personalizzato basato su *Spline Meshes*, garantendo estrema flessibilità nel design del percorso.
* **Markers (Coni):** Il circuito è delimitato da semplici coni arancioni.
* **Nota Tecnica:** Il Blueprint contiene la logica per lo spawning dinamico e procedurale dei coni lungo la spline. 
    * *Nota sulla valutazione:* Sebbene la logica sia presente nel grafo di BluePrint, a causa di problemi, si è optato per un posizionamento manuale dei marker per garantire la navigabilità immediata del tracciato per la consegna.
* **Materials:** Implementazione di materiali personalizzati simili per colore, lucidità ed altri parametri ad asfalto, terreno non-asfalto (fuoripista) e segnaletica (muri di confine e coni).

### 🟢 Level 2: Physics-Based Vehicle Model
* **Engine:** Utilizzo del sistema **Racing Car Vehicle** didefault di Unreal Engine per una simulazione fisica avanzata e per semplicità di implementazione.
* **Dynamics:** Il veicolo simula correttamente il comportamento di sospensioni, attrito degli pneumatici e coppia motore.
* **Control:** * **User:** Supporto alla guida manuale tramite tastiera per test rapidi.
    * **Code-ready:** Il Blueprint è strutturato per l'integrazione con sistemi autonomi; gli input di sterzo e accelerazione sono mappati su variabili specifiche (`AI_Steer`, `AI_Throttle`) predisposte per essere pilotate da algoritmi di controllo esterni.

### 🟢 Level 3: Perception Sensors (Core Task)
* **LiDAR Simulation:** * Implementata tramite *multi-raycasting* (Line Traces) a 360°.
    * **Logica di rilevamento:** Le linee di debug cambiano colore dinamicamente: sono **Rosse** in assenza di ostacoli e diventano **Verdi** istantaneamente al rilevamento con un cono o un ostacolo, simulando il feedback di un sensore di prossimità reale.
* **Virtual Camera:** * Camera frontale (~posizione targa anteriore) montata sul veicolo con parametri RGB e orientamento corretti.
    * **Decisione Tecnica:** Il feed è acquisito tramite `Scene Capture 2D`. È stato scelto di non renderizzarlo nell'HUD finale per ottimizzare le prestazioni e mantenere pulita l'interfaccia durante il testing del LiDAR.

---

## 🛠️ Setup & Instructions

### Prerequisiti
* **Unreal Engine:** 4.5 o superiore.
* **.NET SDK 8.0:** Raccomandato per la piena compatibilità con il build system.

### 📊 Analisi Tecnica
Il progetto dimostra solide competenze nel:

Gestire Blueprint complessi, inclusa la logica procedurale e i sistemi di fallback per la stabilità delle demo.

Implementare sensori attivi capaci di interagire in tempo reale con l'ambiente (LiDAR reattivo).

Utilizzo di grafo Blueprint per controllo action-driven e di componenti.

### 📂 Struttura del Progetto

**/Config:** *File di configurazione auto-generati da UnReal Engine*

**/Content:** *Tutti i vari files, blueprint, materials, textures, vehicles, road-spline, road-segment*

**Altre Cartelle:** *File di Cache di UnReal Engine*
