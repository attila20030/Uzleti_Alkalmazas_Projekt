# EcoTrack & Fleet Manager - Vállalati Karbonlábnyom-követő és Flottakezelő Rendszer

Az **EcoTrack** egy modern, .NET alapú zöldtechnológiai (GreenTech) vállalati szoftver. A rendszer célja, hogy segítse a vállalatokat a kötelező **ESG (Environmental, Social, and Governance) jelentések** elkészítésében, a CO2-kibocsátás nyomon követésében, valamint az elektromos autóflotta és a töltőállomások hatékony koordinálásában.

---

## 🚀 Főbb Funkciók (MVP)

### 📊 Karbonlábnyom-követő Modul (Carbon Footprint Tracker)
* **Adatbeviteli API:** Részlegek és munkatársak által termelt kibocsátások (autós utazások, áramfogyasztás, fűtés, papírfelhasználás) egyszerű rögzítése.
* **Automatikus CO2 Kalkuláció:** A rendszer a háttérben, az aktuális konverziós faktorok alapján azonnal kiszámítja és kg-ban tárolja a CO2-egyenértéket.
* **Aggregált Riportálás:** Végpontok a statisztikák havi/éves és kategóriánkénti (Utazás, Energia, Logisztika) csoportosítására, amely készen áll a grafikonos megjelenítésre.

### 🚗 Zöld Flottakezelő Modul (Green Fleet Management)
* **E-Autó Nyilvántartás:** Elektromos céges járművek és belső töltőállomások adatainak kezelése.
* **Foglalási Rendszer:** Munkatársi időpontfoglalás a szabad gépjárművekre és töltőkre, automatikus ütközésvizsgálattal.

---

## 🛠️ Alkalmazott Technológiák

* **Backend:** .NET 8 / .NET 9 ASP.NET Core Web API
* **Adatbázis-kezelés:** Entity Framework Core (Code-First megközelítés, Migrációk)
* **Adatbázis:** Microsoft SQL Server / PostgreSQL
* **Architektúra:** Rétegelt architektúra (Controllers -> Services -> Repositories -> Data)

---

## 📐 Adatmodell (Entitások)

A rendszer magját az alábbi Entity Framework entitások alkotják:
* `User`: A rendszert használó munkatársak adatai és szerepkörei.
* `EmissionSource`: Különböző kibocsátási típusok (pl. Áram, Benzin) és a hozzájuk tartozó `ConversionFactor`.
* `LogEntry`: A rögzített fogyasztások, a kiszámolt `CalculatedCO2` értékkel és időbélyeggel.
* `Vehicle` & `Booking`: Az elektromos járművek adatai és a hozzájuk kapcsolódó foglalások naptári adatai.

---

## 🏃 Hogyan indítsd el helyileg?

### Előfeltételek
* [.NET SDK (8.0 vagy újabb)](https://microsoft.com)
* [SQL Server] vagy tetszőleges kompatibilis adatbázis-kezelő

### Lépések

1. **Klónozd a repót:**
   ```bash
   git clone https://github.com
   cd ecotrack-fleet-manager
   ```

2. **Adatbázis kapcsolati karakterlánc beállítása:**
   Frissítsd az `appsettings.json` fájlban található `ConnectionStrings` részt a saját helyi adatbázisod elérésével.

3. **Migrációk futtatása (Adatbázis létrehozása):**
   ```bash
   dotnet ef database update
   ```

4. **Az alkalmazás futtatása:**
   ```bash
   dotnet run --project EcoTrack.API
   ```
   Az API elindulása után a Swagger felület alapértelmezetten a `http://localhost:5000/swagger` (vagy a konzolban kiírt HTTPS porton) érhető el.

---

## 🔮 Jövőbeli Tervek (Roadmap)
* **Élő API Integráció:** A fix konverziós faktorok leváltása külső, valós idejű zöld API integrációval (pl. Electricity Maps).
* **Szerepkör alapú jogosultságkezelés:** Külön felület az adatrögzítő alkalmazottaknak és az összesített riportokat elemző ESG Menedzsereknek (ASP.NET Core Identity & JWT).
