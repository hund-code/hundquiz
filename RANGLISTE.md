# Gemeinsame Rangliste einrichten

Die Rangliste speichert nur Nickname, Punktzahl und Zeitpunkt. Nicknames sind öffentlich sichtbar. Keine echten Namen, E-Mail-Adressen oder anderen persönlichen Daten eintragen.

1. Ein kostenloses Supabase-Projekt erstellen.
2. Unter Authentication die E-Mail-Anmeldung aktiviert lassen. E-Mail-Bestätigung kann eingeschaltet bleiben.
3. Im SQL Editor den Inhalt von `leaderboard-schema.sql` ausführen.
4. Unter Project Settings > API die Project URL und den `anon`/publishable key kopieren. Niemals den `service_role`-Key in die Website eintragen.
5. Die Werte in `leaderboard-config.js` eintragen:

```js
window.QUIZ_LEADERBOARD_CONFIG = {
  url: "https://DEIN-PROJEKT.supabase.co",
  anonKey: "DEIN_OEFFENTLICHER_ANON_KEY"
};
```

6. `leaderboard-config.js`, `index.html` und `leaderboard-schema.sql` committen und nach `master` pushen. GitHub Pages veröffentlicht die Änderungen automatisch.

Der Knopf oben rechts öffnet Registrierung und Anmeldung. Nach der Anmeldung wird die Punktzahl mit der Nutzer-ID gespeichert; die Top 10 mit Nickname und Punktzahl sind öffentlich lesbar. Jeder angemeldete Nutzer kann nur neue eigene Einträge hinzufügen, keine Einträge ändern oder löschen.

Supabase bestätigt neue Konten je nach Projekteinstellung per E-Mail. Die öffentliche Rangliste prüft nicht serverseitig, ob eine Punktzahl ehrlich erspielt wurde; das wäre für einen manipulationssicheren Wettbewerb zusätzlich nötig.