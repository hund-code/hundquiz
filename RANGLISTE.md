# Gemeinsame Rangliste einrichten

Die Rangliste speichert nur Nickname, Punktzahl und Zeitpunkt. Nicknames sind öffentlich sichtbar. Keine echten Namen, E-Mail-Adressen oder anderen persönlichen Daten eintragen.

1. Ein kostenloses Supabase-Projekt erstellen.
2. Im SQL Editor den Inhalt von `leaderboard-schema.sql` ausführen.
3. Unter Project Settings > API die Project URL und den `anon`/publishable key kopieren. Niemals den `service_role`-Key in die Website eintragen.
4. Die Werte in `leaderboard-config.js` eintragen:

```js
window.QUIZ_LEADERBOARD_CONFIG = {
  url: "https://DEIN-PROJEKT.supabase.co",
  anonKey: "DEIN_OEFFENTLICHER_ANON_KEY"
};
```

5. `leaderboard-config.js`, `index.html` und `leaderboard-schema.sql` committen und nach `master` pushen. GitHub Pages veröffentlicht die Änderungen automatisch.

Es gibt keine Konten. Jeder Nickname darf nur einmal verwendet werden; Groß- und Kleinschreibung zählt dabei nicht. Nickname und Punktzahl erscheinen öffentlich in der Top 10. Anonyme Spieler können Punktzahlen hinzufügen und ändern, aber keine Einträge löschen.

Der Fortschritt der unbegrenzt vielen Stufen wird lokal im Browser gespeichert und nicht zwischen Geräten synchronisiert. Die Fragen wiederholen sich nach den ersten 100 Fragen.

Beim Laden der lokalen Rangliste werden vorhandene Einträge namens Lumpi aus diesem Browser entfernt und nicht angezeigt. Der Name kann weiterhin neu verwendet werden. Der zuletzt gewählte Nickname wird lokal gespeichert und beim nächsten Besuch vorausgefüllt.

Wenn du die Online-Rangliste schon eingerichtet hast, führe `leaderboard-schema.sql` erneut aus. Das Schema verhindert doppelte Nicknames auch dann, wenn sie sich nur durch Groß- und Kleinschreibung unterscheiden, und erlaubt Gesamtpunktzahlen über 100. Falls es bereits doppelte Nicknames in der Datenbank gibt, muessen diese vor dem Anlegen des eindeutigen Indexes bereinigt werden.

Wenn die doppelten Einträge in Supabase stehen, führe zuerst `leaderboard-remove-lumpi.sql` einmal aus. Danach `leaderboard-schema.sql` ausführen, damit keine doppelten Nicknames mehr gespeichert werden können. Das Löschskript entfernt alle bisherigen Schreibweisen von `Lumpi`.
