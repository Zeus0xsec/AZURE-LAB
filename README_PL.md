# Azure & Entra ID Security Lab

[![PL](https://img.shields.io/badge/Język-Polski-red.svg)](README_PL.md)
[![EN](https://img.shields.io/badge/Language-English-blue.svg)](README.md)

## O Projekcie
Konfiguracja i wdrożenie chmurowego środowiska tożsamości opartego na **Microsoft Azure** oraz **Microsoft Entra ID** (dawniej Azure AD). Projekt skupia się na zarządzaniu tożsamością i dostępem (IAM), kontroli wydatków w chmurze, weryfikacji uprawnień (RBAC / Least Privilege) oraz analizie logów bezpieczeństwa pod kątem zadań Helpdesk L1 i Junior SOC.

## 🛠️ Wykorzystane Technologie
- **Dostawca chmury:** Microsoft Azure
- **Zarządzanie tożsamością:** Microsoft Entra ID (Entra Admin Center)
- **Bezpieczeństwo:** Azure RBAC, Zasada Least Privilege, Dzienniki logowania (Sign-in Logs)
- **Zarządzanie kosztami:** Azure Cost Management & Budgets

---

## Architektura: Lokalne AD DS vs. Chmurowe Entra ID

| Cecha / Technologia | 🏢 Lokalnie (Active Directory DS) | ☁️ Chmura (Microsoft Entra ID) |
| :--- | :--- | :--- |
| **Główne zastosowanie** | Zarządzanie sprzętem i tożsamością w sieci LAN. | Tożsamość w chmurze, dostęp do M365 i aplikacji SaaS. |
| **Główny serwer** | Kontroler Domeny (DC). | Usługa w pełni zarządzana przez Microsoft. |
| **Protokoły logowania** | Kerberos, NTLM. | OAuth 2.0, SAML 2.0, OpenID Connect. |
| **Struktura** | Jednostki Organizacyjne (OU), Drzewa i Las. | Płaska struktura oparta na Grupach Bezpieczeństwa. |
| **Zarządzanie stacjami**| Polityki GPO (Group Policy Objects). | Microsoft Intune (MDM / MAM). |
| **Przykład użycia** | Logowanie się do komputera stacjonarnego w biurze. | Logowanie z MFA do poczty Outlook w przeglądarce. |

---

## Zrealizowane Zadania i Dowody (Screenshots)

### 1. Zarządzanie Kosztami (Azure Cost Management)
Skonfigurowano sztywny budżet środowiska testowego, zapobiegając niekontrolowanym opłatom po wyczerpaniu darmowych środków.
- **Kwota budżetu:** 10.00 USD
- **Alert:** Automatyczne powiadomienie e-mail po przekroczeniu 80% limitu (8.00 USD).

<img width="3436" height="1305" alt="budzety" src="https://github.com/user-attachments/assets/dce3372f-fa39-47a7-adf2-904de1671d6e" />

---

### 2. Zarządzanie Tożsamością i Grupami w Entra ID
- Utworzono 5 kont użytkowników z wymuszona zmianą hasła przy pierwszym logowaniu.
- Utworzono grupy zabezpieczeń (`IT-Helpdesk`, `Sprzedaz`) do zarządzania dostępem.
- Przeprowadzono testowe logowanie na portalu `myaccount.microsoft.com`.

<img width="3435" height="1304" alt="uzytkownicy" src="https://github.com/user-attachments/assets/0ec8ad9a-be0e-4e5e-a764-8f59c378a638" />

---

### 3. Zasada Najmniejszych Uprawnień (Least Privilege)
Przetestowano granice uprawnień ról administracyjnych w celu ochrony przed nieuprawnionym podniesieniem uprawnień (*Privilege Escalation*).
- **Przypisana rola:** `Administrator pomocy technicznej` (`Helpdesk Administrator`) dla użytkownika `Jan Kowalski`.
- **Test 1 (Reset hasła):** **SUKCES** — Użytkownik pomyślnie zresetował hasło zwykłemu pracownikowi (`Adam Drabina`).
- **Test 2 (Modyfikacja ról):** **BLOKADA** — Opcja edycji i dodawania ról została zablokowana przez system z powodu braku uprawnień.

<img width="3439" height="1308" alt="przypisanie roli" src="https://github.com/user-attachments/assets/1f38c475-56ee-4f69-a8d0-dcb2d8531b7c" />
<img width="3433" height="1308" alt="resethaslazkontauzytkownika" src="https://github.com/user-attachments/assets/58121f6b-81b5-441e-bb9b-db42df53977b" />
<img width="3436" height="1310" alt="brakuprawnien" src="https://github.com/user-attachments/assets/b07195d8-f210-4db8-93ba-ddcebf0f600e" />

---

### 4. Analiza Incydentów: Sign-in Logs (Chmurowy odpowiednik Event ID 4625)
Wygenerowano i przeanalizowano zdarzenia nieudanych logowań w dziennikach Entra ID.
- **Typ zdarzenia:** Nieudane logowanie (`Niepowodzenie` / `Failure`).
- **Konto:** `admin.jan@--------.onmicrosoft.com`
- **Kod błędu logowania:** `50126` (*Błędne poświadczenia / nieprawidłowe hasło*).
- **Adres IP i lokalizacja:** `46.205.197.181` (Huba, Małopolskie, PL).
- **Aplikacja:** `My Profile` przez przeglądarkę Windows 10.
- **Triaż SOC L1:** Wykryto 2 nieudane próby wprowadzenia hasła z domowego IP użytkownika. Brak oznak masowego ataku typu Password Spraying lub Brute Force. Zgłoszenie zamknięte jako błąd własny użytkownika.

<img width="3436" height="1307" alt="logowaniefailed" src="https://github.com/user-attachments/assets/91e6e3fe-e188-4b6b-b998-f301c46d532a" />
<img width="833" height="1186" alt="szczegolydzialan" src="https://github.com/user-attachments/assets/ee8364d8-e742-4205-9967-ab74977520e0" />

---

## Kolejne Kroki
Kolejny etap projektu to budowa **Środowiska Hybrydowego** — połączenie tego laba chmurowego z lokalnym kontrolerem domeny Windows Server Active Directory (AD DS) przy użyciu narzędzia **Entra Connect / Cloud Sync**.
