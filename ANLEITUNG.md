# Fristen-Wächter – Zugangsdaten bei Abos (Web 2026-11-25a)

## Was neu ist
- Beim Anlegen eines Abos: aufklappbarer Bereich „🔑 Zugangsdaten speichern (optional)“
  mit Login, Passwort und Login-Seite.
- An jeder Abo-Karte: Button „🔑 Zugangsdaten“ (bzw. „Zugang hinzufügen“). Dort kannst du
  die Daten ansehen, das Passwort einblenden und kopieren, die Login-Seite öffnen,
  die Daten bearbeiten oder entfernen.
- Das Passwort ist verdeckt. Eingeblendet verschwindet es nach 30 Sekunden wieder.
  Kopierte Passwörter werden nach 60 Sekunden aus der Zwischenablage gelöscht,
  solange die App offen ist. Geht die App in den Hintergrund, schließt sich der Dialog.

## So funktioniert die Verschlüsselung
- AES-GCM mit 256 Bit. Der Schlüssel wird beim ersten Speichern auf dem Gerät erzeugt
  und als nicht exportierbarer Schlüssel in der App-Datenbank (IndexedDB) abgelegt.
  Er kann nicht ausgelesen oder kopiert werden. Ver- und entschlüsseln kann nur die App selbst.
- In den gespeicherten Einträgen steht nur der verschlüsselte Text.
- Backup ohne Passwort: Zugangsdaten werden weggelassen (Hinweis im Export-Dialog).
- Backup mit Passwort: Zugangsdaten sind enthalten, geschützt durch das Backup-Passwort.
  Beim Wiederherstellen werden sie sofort mit dem Schlüssel des neuen Geräts verschlüsselt.
- Werden die App-Daten gelöscht oder die App neu installiert, ist der Schlüssel weg.
  Die App meldet das und bittet um Neueingabe. Deshalb: verschlüsseltes Backup machen.

## Was es nicht schützt
- Wer dein entsperrtes Handy mit geöffneter App in der Hand hat, kann die Daten ansehen.
  Eine zusätzliche Sperre per Face ID / Fingerabdruck wäre der nächste Schritt.
- Android: Die App läuft als Web-App unter echoreachai.github.io. Alle Seiten unter
  dieser Adresse teilen sich denselben Speicher, auch andere Repos von dir auf GitHub Pages
  (z. B. eine Staging-Version). Dort nur eigenen, vertrauenswürdigen Code veröffentlichen.

## Übernehmen
1. Staging: index.html, app.js, styles.css, sw.js, ios-web/index.html, ios-web/app.js,
   ios-web/styles.css kopieren und testen.
2. Live-Repo: dieselben Dateien. Android bekommt das Update ohne neues App-Paket.
3. iOS: neuer Build über Codemagic. Ist Version 1.3 schon eingereicht oder live,
   in codemagic.yaml APP_VERSION auf "1.4" setzen (und MARKETING_VERSION in project.pbxproj).
