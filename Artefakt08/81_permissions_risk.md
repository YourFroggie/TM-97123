# 🛡️ AUDYT BEZPIECZEŃSTWA: MANIFEST SCANNER
**Status:** Wykonano automatyczną ekstrakcję ryzyka.

### 📝 1. Zawartość RiskyPermission.xml
Zidentyfikowano następujące wpisy krytyczne:
- **Debuggable:** Ustawiony na true (⚠️ RYZYKO KRYTYCZNE – aplikacja jest otwarta na debugowanie i podatna na inżynierię wsteczną w czasie rzeczywistym).
- **Permissions:** Wykryto dostęp do zasobów sieciowych `(android.permission.INTERNET)` oraz odczytu/zapisu pamięci zewnętrznej.

### 🧠 2. Interpretacja Inżynierska
Z perspektywy bezpieczeństwa aplikacji (AppSec), najpoważniejszą luką jest pozostawiona flaga debuggable="true". Umożliwia ona potencjalnemu intruzowi wykorzystanie protokołu JDWP (Java Debug Wire Protocol) poprzez komendę adb jdwp. W efekcie osoba niepowołana może podpiąć się pod aktywne procesy, śledzić zmienne, a nawet modyfikować logikę biznesową aplikacji.

### 🛠️ 3. Akcja korygująca
Należy zaimplementować skrypt walidacyjny, który będzie parsował manifest przed etapem kompilacji i automatycznie przerywał proces budowania `(fail build), jeśli wykryje flagę debuggable="true"` dla wariantu produkcyjnego `(Release)`.

####  Raport wykonanay przez:
**Podpis:** Dariusz 97123
**Data:**  24-03-2026
 