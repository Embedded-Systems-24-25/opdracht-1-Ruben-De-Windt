
# Node-RED Project – Opdracht 1

## 📋 Beschrijving

Dit Node-RED project demonstreert een eenvoudige IoT-toepassing waarin een LED aangestuurd wordt via MQTT en data wordt opgeslagen en opgevraagd uit een MySQL-database.

Functionaliteiten:
- 🟢 Aansturen van een LED via een dashboard-switch
- 📥 Verzenden en ontvangen van berichten via MQTT
- 🗃️ Opslaan van acties in een MySQL database
- 📅 Filteren van logdata via een date picker
- 📊 Weergeven van logdata in een dashboard-tabel

## ⚙️ Benodigdheden

- Node-RED
- MQTT Broker (bijv. Mosquitto)
- MySQL server met database `globe_bank`
- Raspberry Pi met GPIO ondersteuning (voor de LED)

## 🛠️ Installatie & Setup

1. **Clone deze repository**:
    ```bash
    git clone <https://github.com/Embedded-Systems-24-25/opdracht-1-Ruben-De-Windt.git>
    cd opdracht1
    ```

2. **Importeer de flow in Node-RED**:
    - Open de Node-RED editor (`http://localhost:1880`)
    - Klik rechtsboven op het menu → Import → Upload `opdracht1.json`

3. **MySQL database setup**:
    - Maak een database `globe_bank`
    - Maak een tabel:
      ```sql
      CREATE TABLE log_events (
        id INT AUTO_INCREMENT PRIMARY KEY,
        event_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        action VARCHAR(255)
      );
      ```

4. **MQTT setup**:
    - Zorg dat een broker draait op `192.168.137.1` of pas dit aan in de flow.

## 🧩 Belangrijke nodes

| Node | Beschrijving |
|------|--------------|
| `mqtt in` | Ontvangt berichten via topic `opdracht1rubendewindt` |
| `rbe` | Filtert dubbele waarden uit |
| `ui_switch` | Zet een LED aan of uit via GPIO |
| `function` | Bouwt SQL-queries om acties op te slaan |
| `mysql` | Verstuurd gegevens naar de MySQL database |
| `ui_table` | Toont logdata in een dashboard |
| `ui_date_picker` | Laat de gebruiker een datum kiezen om logs op te vragen |

## 📸 Dashboardvoorbeeld

- Switch: LED aan/uit
- Date Picker: Selecteer een datum om loggegevens op te halen
- Tabel: Toont de logs van de geselecteerde datum

## ✍️ Auteur

Ruben de Windt
