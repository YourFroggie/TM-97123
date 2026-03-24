# 🛡️ RAPORT ANALIZY WYCIEKÓW (SECRETS)
**Student:** [Dariusz]  
**Indeks:** [97123]  
**Data raportu:** [24-03-2026]  

---

## 🛑 1. Trzy najbardziej groźne znaleziska (High Risk)
*Poniższe elementy wymagają natychmiastowej zmiany w kodzie źródłowym:*

1. **[URL_Endpoint] -> `http://www.example.com/lala/foobar@example.com`**
   - *Naruszenie PII / Hardcoded Credentials:* Ekspozycja adresu e-mail w ścieżce URL sugeruje wyciek danych osobowych (PII) lub pozostawienie w kodzie twardo zakodowanych poświadczeń testowych.
2. **[Potential_Secret] -> `password`**
   - *Hardcoded Secrets:* Obecność tego klucza w plikach konfiguracyjnych (np. strings.xml) stwarza wysokie ryzyko pozostawienia przez dewelopera domyślnych haseł dostępowych do baz danych lub zewnętrznych usług.
3. **[Potential_Secret] -> `reset_password_warning`**
   - *Zagrożenie Logiki Biznesowej::*  Wskazuje na prawdopodobieństwo implementacji mechanizmów resetowania hasła po stronie klienta (Client-side). Może to umożliwić atakującemu manipulację i ominięcie procesu weryfikacji.

## 🟢 2. Trzy znaleziska typu "False Positive" (Low/No Risk)
*Poniższe elementy zostały błędnie sklasyfikowane jako zagrożenie:*

1. **[URL_Endpoint] -> `http://www.google.com`**
   - *Uzasadnienie:* Standardowy adres wykorzystywany powszechnie do sprawdzania statusu łączności internetowej (Connectivity Check).
2. **[API_Key_Format] -> `table_layout_1_triple_star`**
   - *Uzasadnienie:* Ciąg znaków dopasowany przez wyrażenie regularne dla kluczy API, będący w rzeczywistości jedynie identyfikatorem elementu interfejsu (UI Layout ID).
3. **[API_Key_Format] -> `abc_font_family_display_3_material`**
   - *Uzasadnienie:* Zasób systemowy frameworka Android (nazwa czcionki powiązana z biblioteką Material Design). Brak wartości kryptograficznej.

---

## 🎓 Wnioski końcowe
Automatyczne skanowanie RegEx jest skuteczne, ale wymaga **manualnej weryfikacji inżyniera**, ponieważ skrypt nie rozumie kontekstu biznesowego aplikacji.