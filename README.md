# Technická specifikace systému pro rezervaci letenek

## Cíl projektu
Cílem je vytvořit dynamickou webovou aplikaci umožňující uživatelům:
- Rezervovat letenky s možností volby destinace, data a času, počtu pasažérů a cestovní třídy.
- Zobrazit trasu letu na mapě.
- Využívat přehlednou historii rezervací (pro přihlášené uživatele).
- Správci systému řešit storna a případné spory.

## Funkcionality

### Nepřihlášený uživatel
1. **Vyhledávání a rezervace letu**:
   - Výběr místa odletu a příletu.
   - Volba data a času odletu.
   - Volba třídy (první nebo druhá).
   - Nastavení počtu letenek (při více než jedné letenky zadávání jmen pasažérů).
   - Zobrazení počasí v místě odletu a příletu podle času letu pomocí OpenWeatherAPI.
2. **Zobrazení výsledků vyhledávání**:
   - Vypisuje se seznam letů odpovídající zadaným filtrům.
   - Pro každý let se zobrazuje:
     - Cena letenky v první a druhé třídě.
     - Cena příručního zavazadla.
     - Cena zavazadla do 20 kg.
3. **Interaktivní mapa**:
   - Body místa odletu a příletu budou propojené vzdušnou čarou.
   - Nad čarou se zobrazí délka letu (v hodinách a minutách) a vzdálenost (v kilometrech).
   - Po najetí myší na bod zobrazení detailů, např. počasí.
4. **Registrace a přihlášení**:
   - Nezbytné pro dokončení nákupu (pokud si nepřihlášený uživatel vybere letenku, musí se registrovat).

### Přihlášený uživatel
- Rozšířené možnosti oproti nepřihlášenému:
  - **Historie rezervací** – uživatel vidí seznam všech zakoupených letenek (včetně detailů).

### Správce systému
- Možnost řešit administrativní úkony:
  - **Storno letenek**
  - **Řešení sporů** a potíží s rezervacemi

## Technologie

### Frontend
- **TypeScript** + **React**
- **Leaflet** pro zobrazení map a tras
- **OpenWeatherAPI** pro zobrazování aktuálního a předpokládaného počasí
- **shadcn/ui** pro rychlou tvorbu uživatelského rozhraní

### Backend
- **.NET (C#)** pro tvorbu REST API

### Databáze
- **SQL Server** pro perzistentní ukládání uživatelských dat, informací o rezervacích, cen zavazadel a administrátorských akcí.

## API Specifikace
- **Vlastní REST API** poskytující:
  - Seznam dostupných letů (místa, časy, ceny, zavazadla).
  - Správu uživatelských účtů a autorizaci.
  - Správu rezervací (vytváření, rušení).
