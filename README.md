# Datenschutzerklärung für D-Ticket Wallet

**Stand:** November 2026  
**Verantwortlicher:** Fynn Hicken (<fynn.hicken@gmail.com>)

---

### Kurzfassung
**D-Ticket Wallet funktioniert zu 100 % offline.** Es existieren keine Server, keine Analyse-Tools, kein Tracking und keine Weitergabe von Daten. Ihre Daten verlassen Ihr iPhone zu keinem Zeitpunkt.

---

### 1. Grundsatz der lokalen On-Device-Verarbeitung
Die App „D-Ticket Wallet“ wurde nach den Prinzipien „Privacy by Design“ und „Privacy by Default“ entwickelt:
* **Keine Internetverbindung:** Die Kernfunktionen der App (Bildanalyse, Barcode-Extraktion, Pass-Erstellung und Signierung) benötigen und verwenden keine Netzwerkverbindung.
* **Keine Server:** Wir betreiben keine Backend-Server, Datenbanken oder Cloud-Dienste.
* **Kein Tracking:** Es sind keinerlei Tracking-Bibliotheken, Analysedienste (z. B. Firebase, Google Analytics) oder Werbenetzwerke eingebunden.
* **Keine Registrierung:** Zur Nutzung der App ist kein Benutzerkonto erforderlich.

### 2. Zugriff auf Fotos und Bildverarbeitung
* Der Fotozugriff erfolgt über den sicheren, systemeigenen Bildauswahldialog von iOS (`PhotosPicker`). Die App erhält ausschließlich Zugriff auf das eine Foto, das Sie aktiv auswählen.
* Die optische Erkennung (OCR) und das Dekodieren des Aztec-Barcodes erfolgen ausschließlich im lokalen Arbeitsspeicher Ihres iPhones mithilfe der Apple-Systemframeworks *Vision* und *CoreImage*.
* Das Foto wird nicht dauerhaft in der App gespeichert und unmittelbar nach dem Auslesen aus dem flüchtigen Speicher verworfen.

### 3. Erstellung und Signierung des Apple Wallet Passes
* Die Umwandlung der Ticketdaten in eine Pass-Datei (`.pkpass`) sowie die kryptografische Signierung (PKCS#7 / CMS) erfolgen vollständig auf Ihrem Gerät.
* Die erstellte Pass-Datei wird über die offizielle PassKit-Schnittstelle von Apple direkt in Ihre persönliche Apple Wallet App importiert.

### 4. Rechte der Betroffenen
Da wir keine personenbezogenen Daten auf externen Servern speichern oder verarbeiten, liegen bei uns keine personenbezogenen Daten vor, die eingesehen, berichtigt, gesperrt oder gelöscht werden könnten. Sie haben jederzeit die vollständige Kontrolle über Ihre Daten, indem Sie erstellte Pässe aus Apple Wallet löschen oder die App deinstallieren.
