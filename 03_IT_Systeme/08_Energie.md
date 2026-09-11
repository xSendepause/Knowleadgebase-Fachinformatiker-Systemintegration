# Stromkosten berechen

## Formel zur Berechnung der Stromkosten
## Stromkosten berechnen

Die Stromkosten hängen von der **Leistung**, der **Betriebsdauer** und dem **Strompreis** ab.

### Formel

Stromkosten = (Watt / 1000) × Stunden × Tage × Preis (€/kWh)

### Beispiel

Ein Gerät mit **300 W** läuft **8 Stunden pro Tag** an **200 Tagen im Jahr**.
Der Strompreis beträgt **0,40 €/kWh**.

**1. Leistung in kW umrechnen:**

300 W / 1000 = 0,3 kW

**2. Energieverbrauch berechnen:**

0,3 kW × 8 h × 200 Tage = 480 kWh

**3. Stromkosten berechnen:**

480 kWh × 0,40 €/kWh = 192 €

**Ergebnis: 192 € Stromkosten pro Jahr.**

> **Merke:**
> - 1 kW = 1000 W
> - Leistung (kW) × Zeit (h) = Energie (kWh)
> - Energie (kWh) × Strompreis (€/kWh) = Stromkosten (€)
> - Watt bei der Berechnung zuerst in Kilowatt umrechnen.

---

## Wirkungsgrad berechnen

Der **Wirkungsgrad (η)** gibt an, wie effizient ein Gerät die aufgenommene Energie bzw. Leistung in nutzbare Energie bzw. Leistung umwandelt.

### Formel

η = Nutzleistung / Eingangsleistung

Als Prozentwert:

η = (Nutzleistung / Eingangsleistung) × 100 %

### Beispiel

Ein Netzteil nimmt **500 W** aus dem Stromnetz auf und gibt davon **450 W** als nutzbare Leistung an den Computer weiter.

- Eingangsleistung: **500 W**
- Nutzleistung: **450 W**

η = 450 W / 500 W = 0,9 = 90 %

Das Netzteil hat also einen **Wirkungsgrad von 90 %**.

### Verlustleistung

Die Leistung, die nicht genutzt werden kann, wird hauptsächlich als **Wärme** abgegeben.

Verlustleistung = Eingangsleistung - Nutzleistung

Im Beispiel:

500 W - 450 W = 50 W

Das Netzteil verliert also **50 W** als Verlustleistung.

### Formel umstellen

Ist der Wirkungsgrad und die Nutzleistung bekannt, kann die benötigte Eingangsleistung berechnet werden:

Eingangsleistung = Nutzleistung / η

**Beispiel:**

Ein Gerät benötigt **400 W Nutzleistung** und das Netzteil hat einen Wirkungsgrad von **80 % (0,8)**.

400 W / 0,8 = 500 W

Das Netzteil muss also **500 W aus dem Stromnetz aufnehmen**.

### Zusammenhang

| Wirkungsgrad | Nutzleistung bei 500 W Eingangsleistung | Verlustleistung |
|---|---:|---:|
| **80 %** | 400 W | 100 W |
| **90 %** | 450 W | 50 W |
| **95 %** | 475 W | 25 W |

> **Merke:**
> - Je höher der Wirkungsgrad, desto geringer sind die Verluste.
> - Ein Wirkungsgrad von **90 %** bedeutet: 90 % werden genutzt, 10 % gehen als Verlustleistung verloren.
> - Der Wirkungsgrad liegt zwischen **0 und 1** bzw. **0 % und 100 %**.
> - **η (Eta)** ist das Formelzeichen für den Wirkungsgrad.

---

## USV-Arten (Unterbrechungsfreie Stromversorgung)


| USV-Art | Abkürzung | Funktionsweise / Eigenschaften | Schutz | Typischer Einsatz |
|---|---|---|---|---|
| **Offline-USV** | **VFD** | Im Normalbetrieb werden die Geräte direkt aus dem Stromnetz versorgt. Erst bei einem Stromausfall schaltet die USV auf den Akku um. Dabei entsteht eine **kurze Umschaltzeit**. | Grundschutz bei Stromausfall | PCs, kleine Arbeitsplätze, einfache Geräte |
| **Line-Interactive-USV** | **VI** | Kann **Spannungsschwankungen automatisch ausgleichen**, ohne sofort den Akku zu verwenden. Bei einem Stromausfall wird auf den Akku umgeschaltet. Es gibt eine **kurze Umschaltzeit**. | Schutz vor Stromausfall sowie Unter- und Überspannung | Server, NAS, Switches und andere Netzwerkgeräte |
| **Online-USV** | **VFI** | Die angeschlossenen Geräte werden **dauerhaft über den Wechselrichter versorgt**. Der Eingangsstrom wird von **AC in DC und anschließend wieder von DC in AC** umgewandelt (Doppelwandlung). Bei einem Stromausfall entsteht **keine Umschaltzeit**. | Sehr hoher Schutz vor Stromausfällen und Störungen der Netzspannung | Rechenzentren, kritische Server und andere wichtige IT-Systeme |

### Einfach merken

- **Offline (VFD)** → Günstig und einfacher Schutz
- **Line-Interactive (VI)** → Zusätzlich automatische Spannungsregelung
- **Online (VFI)** → Höchster Schutz, keine Umschaltzeit

### Bedeutung der Abkürzungen

- **VFD – Voltage and Frequency Dependent from Mains Supply**
  - Standby- bzw. **Offline-USV**
  - Spannung und Frequenz sind vom Stromnetz abhängig.
  - Bei Stromausfall erfolgt die Umschaltung auf den Akku.
<img width="375" height="239" alt="image" src="https://github.com/user-attachments/assets/7fd3aecc-186e-477e-9f85-0f0126f951bf" />




- **VI – Voltage Independent from Mains Supply**
  - **Line-Interactive-USV** bzw. netzinteraktive USV
  - Die Spannung wird von der USV geregelt.
  - Die Frequenz bleibt vom Stromnetz abhängig.
<img width="375" height="222" alt="image" src="https://github.com/user-attachments/assets/669e67ed-21ef-4bfa-86d4-998516f962be" />


- **VFI – Voltage and Frequency Independent from Mains Supply**
  - **Online-USV / Doppelwandler-USV**
  - Spannung und Frequenz sind vom Stromnetz unabhängig.
  - Permanente Doppelwandlung (AC → DC → AC).
  - Keine Umschaltzeit bei Stromausfall.
<img width="375" height="217" alt="image" src="https://github.com/user-attachments/assets/b124cdcf-615e-4b3e-953f-fafeaba8dbc9" />


### Funktionsweise vereinfacht

**Offline-USV:**

Stromnetz → Verbraucher  
Bei Stromausfall → Akku → Wechselrichter → Verbraucher

**Line-Interactive-USV:**

Stromnetz → Spannungsregelung → Verbraucher  
Bei Stromausfall → Akku → Wechselrichter → Verbraucher

**Online-USV:**

Stromnetz → AC/DC-Wandler → DC → Wechselrichter → Verbraucher  
                         ↕
                       Akku

Die **Online-USV** versorgt den Verbraucher somit ständig über den Wechselrichter. Deshalb muss bei einem Stromausfall nicht erst auf den Wechselrichter umgeschaltet werden.

