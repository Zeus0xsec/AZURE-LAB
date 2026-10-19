# ☁️ Azure & Entra ID Security Lab

[![PL](https://img.shields.io/badge/Język-Polski-red.svg)](README_PL.md)
[![EN](https://img.shields.io/badge/Language-English-blue.svg)](README.md)

## 📌 O Projekcie
Konfiguracja i wdrożenie chmurowego środowiska tożsamości opartego na **Microsoft Azure** oraz **Microsoft Entra ID** (dawniej Azure AD). Projekt skupia się na zarządzaniu tożsamością i dostępem (IAM), kontroli wydatków w chmurze, weryfikacji uprawnień (RBAC / Least Privilege) oraz analizie logów bezpieczeństwa pod kątem zadań Helpdesk L1 i Junior SOC.

## 🛠️ Wykorzystane Technologie
- **Dostawca chmury:** Microsoft Azure
- **Zarządzanie tożsamością:** Microsoft Entra ID (Entra Admin Center)
- **Bezpieczeństwo:** Azure RBAC, Zasada Least Privilege, Dzienniki logowania (Sign-in Logs)
- **Zarządzanie kosztami:** Azure Cost Management & Budgets

---

## 🏛️ Architektura: Lokalne AD DS vs. Chmurowe Entra ID

| Cecha / Technologia | 🏢 Lokalnie (Active Directory DS) | ☁️ Chmura (Microsoft Entra ID) |
| :--- | :--- | :--- |
| **Główne zastosowanie** | Zarządzanie sprzętem i tożsamością w sieci LAN. | Tożsamość w chmurze, dostęp do M365 i aplikacji SaaS. |
| **Główny serwer** | Kontroler Domeny (DC). | Usługa w pełni zarządzana przez Microsoft. |
| **Protokoły logowania** | Kerberos, NTLM. | OAuth 2.0, SAML 2.0, OpenID Connect. |
| **Struktura** | Jednostki Organizacyjne (OU), Drzewa i Las. | Płaska struktura oparta na Grupach Bezpieczeństwa. |
| **Zarządzanie stacjami**| Polityki GPO (Group Policy Objects). | Microsoft Intune (MDM / MAM). |
| **Przykład użycia** | Logowanie się do komputera stacjonarnego w biurze. | Logowanie z MFA do poczty Outlook w przeglądarce. |

---

## 🚀 Zrealizowane Zadania i Dowody (Screenshots)

### 1. Zarządzanie Kosztami (Azure Cost Management)
Skonfigurowano sztywny budżet środowiska testowego, zapobiegając niekontrolowanym opłatom po wyczerpaniu darmowych środków.
- **Kwota budżetu:** 10.00 USD
- **Alert:** Automatyczne powiadomienie e-mail po przekroczeniu 80% limitu (8.00 USD).

<img width="1000" alt="Konfiguracja Budżetu Azure" src="budget.png" />

---

### 2. Zarządzanie Tożsamością i Grupami w Entra ID
- Utworzono 5 kont użytkowników z wymuszona zmianą hasła przy pierwszym logowaniu.
- Utworzono grupy zabezpieczeń (`IT-Helpdesk`, `Sprzedaz`) do zarządzania dostępem.
- Przeprowadzono testowe logowanie na portalu `myaccount.microsoft.com`.

<img width="1000" alt="Udane pierwsze logowanie użytkownika" src="uzytkownik.jpg" />

---

### 3. Zasada Najmniejszych Uprawnień (Least Privilege)
Przetestowano granice uprawnień ról administracyjnych w celu ochrony przed nieuprawnionym podniesieniem uprawnień (*Privilege Escalation*).
- **Przypisana rola:** `Administrator pomocy technicznej` (`Helpdesk Administrator`) dla użytkownika `Jan Kowalski`.
- **Test 1 (Reset hasła):** **SUKCES** — Użytkownik pomyślnie zresetował hasło zwykłemu pracownikowi (`Adam Drabina`).
- **Test 2 (Modyfikacja ról):** **BLOKADA** — Opcja edycji i dodawania ról została zablokowana przez system z powodu braku uprawnień.

<img width="1000" alt="Przypisanie roli Helpdesk Administrator" src="przypisanie roli.png" />
<img width="1000" alt="Pomyślny reset hasła przez L1" src="resethaslazkontauzytkownika.png" />
<img width="1000" alt="Brak uprawnień do zmiany ról" src="brakuprawnien.png" />

---

### 4. Analiza Incydentów: Sign-in Logs (Chmurowy odpowiednik Event ID 4625)
Wygenerowano i przeanalizowano zdarzenia nieudanych logowań w dziennikach Entra ID.
- **Typ zdarzenia:** Nieudane logowanie (`Niepowodzenie` / `Failure`).
- **Konto:** `admin.jan@--------.onmicrosoft.com`
- **Kod błędu logowania:** `50126` (*Błędne poświadczenia / nieprawidłowe hasło*).
- **Adres IP i lokalizacja:** `46.205.197.181` (Huba, Małopolskie, PL).
- **Aplikacja:** `My Profile` przez przeglądarkę Windows 10.
- **Triaż SOC L1:** Wykryto 2 nieudane próby wprowadzenia hasła z domowego IP użytkownika. Brak oznak masowego ataku typu Password Spraying lub Brute Force. Zgłoszenie zamknięte jako błąd własny użytkownika.

<img width="1000" alt="Dzienniki logowania w Entra ID" src="logowaniefailed.png" />
<img width="1000" alt="Szczegóły błędu 50126" src="szczegolydzialan.png" />

---

## 🔮 Kolejne Kroki
Kolejny etap projektu to budowa **Środowiska Hybrydowego** — połączenie tego laba chmurowego z lokalnym kontrolerem domeny Windows Server Active Directory (AD DS) przy użyciu narzędzia **Entra Connect / Cloud Sync**.
