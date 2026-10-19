# Cloud Identity, Entra ID & Access Management

[![PL](https://img.shields.io/badge/Język-Polski-red.svg)](#README_PL.md)
[![EN](https://img.shields.io/badge/Language-English-blue.svg)](#README.md)

---

## Wersja Polska (PL)

### O Projekcie
Rozszerzenie lokalnego środowiska Active Directory o chmurę Microsoft Azure. Skonfigurowano zarządzanie tożsamością (IAM), monitorowanie kosztów oraz analizę logów logowania pod kątem operacji Helpdesk L1 oraz Junior SOC.

### Wykorzystane Technologie
- Microsoft Azure (Cost Management)
- Microsoft Entra ID (dawniej Azure AD)
- Entra Admin Center
- Azure RBAC / Entra ID Roles

### Zrealizowane Zadania i Dowody (Screenshots)

#### 1. Azure Cost Management & Budgeting
Utworzono dedykowany budżet dla laboratorium w celu kontroli wydatków (zapobieganie przekroczeniu darmowych środków). Skonfigurowano powiadomienia e-mail po przekroczeniu 80% limitu.
<img width="1714" height="1389" alt="Azure Cost Management" src="TUTAJ_LINK_DO_ZDJECIA_BUDZETU" />

#### 2. Zarządzanie tożsamością w chmurze (Entra ID Users & Groups)
Utworzono chmurowe konta użytkowników i wymuszono zmianę hasła przy pierwszym logowaniu. Wdrożono płaską strukturę uprawnień opartą na grupach zabezpieczeń (`IT-Helpdesk`, `Sprzedaz`). Zmiany zweryfikowano udanym logowaniem na portalu *myaccount.microsoft.com*.
<img width="1714" height="1389" alt="Entra ID Users" src="TUTAJ_LINK_DO_ZDJECIA_UZYTKOWNIKOW" />

#### 3. Zasada najmniejszych uprawnień (Least Privilege) w Entra ID
- **Użytkownik testowy:** Jan Kowalski (rola: `Helpdesk Administrator`).
- **Test 1 (Reset hasła):** SUKCES – Jan Kowalski z powodzeniem zresetował hasło zwykłemu użytkownikowi.
- **Test 2 (Nadawanie ról):** BLOKADA – Jan Kowalski nie mógł dodać ani zmienić ról innemu użytkownikowi (przycisk dodawania ról zablokowany).
- **Wniosek:** Dostęp został ograniczony wyłącznie do zadań operacyjnych L1 bez ryzyka podniesienia uprawnień (*Privilege Escalation*).
<img width="1714" height="1389" alt="RBAC Access Denied" src="TUTAJ_LINK_DO_ZDJECIA_BRAKU_UPRAWNIEN" />

#### 4. Analiza incydentu w Entra ID Sign-in Logs (Chmurowy odpowiednik Event ID 4625)
- **Zdarzenie:** Nieudana próba logowania do portalu.
- **Użytkownik:** `admin.jan@--------.onmicrosoft.com`
- **Kod błędu:** `50126` (Invalid credentials / Błędne hasło)
- **Źródłowy IP:** `46.205.197.181` (Huba, Małopolskie, PL)
- **Klient:** Windows 10, Przeglądarka Web -> Aplikacja My Profile
- **Wniosek L1:** Wykryto 2 próby wprowadzenia niepoprawnego hasła z domowego IP użytkownika. Brak symptomów ataku typu Password Spraying lub Brute Force z wielu geolokalizacji. Zgłoszenie zamknięte jako błąd własny użytkownika.
<img width="1714" height="1389" alt="Entra ID Sign-in Logs" src="TUTAJ_LINK_DO_ZDJECIA_LOGOW_50126" />

---

