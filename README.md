# 🚗 Plaq - Real-Time ANPR Parking Validator

> Transformă orice smartphone într-un scanner auto profesional. Fără poze, fără butoane, doar feedback vizual instantaneu prin Edge AI.

## 📌 Despre Proiect
**Plaq** este o aplicație mobilă inovatoare care simplifică procesul de verificare a parcărilor plătite. În loc de echipamente hardware scumpe (camere ANPR pe mașini) sau de introducerea manuală a datelor, Plaq folosește vederea computerizată în timp real pentru a citi plăcuțele de înmatriculare din mers.

Interfața comunică exclusiv prin feedback vizual ambiental: marginea ecranului se face **Verde** dacă parcarea este plătită și **Roșie** dacă abonamentul este inexistent sau expirat.

## ✨ Funcționalități Principale
* **Zero Clicuri:** Aplicația procesează fluxul video live. Nu necesită apăsarea unui buton de declanșare.
* **Edge AI (Procesare Locală):** Folosește Google ML Kit Text Recognition v2 pentru a citi textul direct pe dispozitiv (30 FPS), protejând intimitatea și asigurând o viteză fulgerătoare.
* **Filtrare Inteligentă:** Un algoritm Regex personalizat separă instantaneu numerele de înmatriculare valide de restul textului de pe stradă (reclame, numere de telefon).
* **Protecție Anti-Spam (Debounce):** O memorie temporară inteligentă previne suprasolicitarea serverului, asigurându-se că o mașină este verificată o singură dată pe sesiune, chiar dacă este scanată de zeci de ori pe secundă.
* **UI Minimalist:** Interfața nu distrage utilizatorul, permițându-i să fie atent la stradă.

## 🛠️ Stack Tehnologic
* **Frontend:** React Native, TypeScript/JavaScript
* **Cameră & Procesare Cadre:** `react-native-vision-camera`
* **Optical Character Recognition (OCR):** Google ML Kit (Text Recognition v2)
* **Backend:** Node.js (Express) - *pentru verificarea bazei de date*
* **Bază de Date:** [Adaugă aici MongoDB sau PostgreSQL]

## 🧠 Cum funcționează (Arhitectura)
1. **Captura Live:** Camera extrage cadre video la 30 FPS.
2. **Extragerea Textului:** ML Kit citește tot textul din cadru în milisecunde.
3. **Filtrarea (Regex):** Identificăm formatul specific (ex: `CJ 12 ABC` sau `B 100 XYZ`).
4. **Verificarea (API Call):** Dacă numărul e nou, facem o cerere HTTP către serverul backend.
5. **Feedback Vizual:** Actualizăm "state-ul" aplicației și schimbăm culoarea conturului ecranului (`Verde` / `Roșu`).

## 🚀 Instalare și Rulare
Pentru a rula aplicația local pe mașina ta, urmează acești pași:

### Cerințe preliminare
* Node.js instalat
* React Native mediul de dezvoltare configurat (Android Studio / Xcode)

### Pași
1. Clonează acest repository:
   ```bash
   git clone [https://github.com/username-ul-tau/plaq.git](https://github.com/username-ul-tau/plaq.git)
