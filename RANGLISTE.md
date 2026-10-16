# Gemeinsame Rangliste einrichten

Die Rangliste speichert nur Nickname, Punktzahl und Zeitpunkt. Nicknames sind öffentlich sichtbar. Keine echten Namen, E-Mail-Adressen oder anderen persönlichen Daten eintragen.

1. Ein kostenloses Supabase-Projekt erstellen.
2. In Supabase den SQL Editor öffnen und den Inhalt von `leaderboard-schema.sql` ausführen.
3. Unter Project Settings > API die Project URL und den `anon`/publishable key kopieren. Nicht den `service_role`-Key verwenden.
4. Die Werte in `leaderboard-config.js` eintragen:

```js
window.QUIZ_LEADERBOARD_CONFIG = {
  url: "https://DEIN-PROJEKT.supabase.co",
  anonKey: "DEIN_OEFFENTLICHER_ANON_KEY"
};
```

5. `leaderboard-config.js` committen und nach `master` pushen. GitHub Pages veröffentlicht die Rangliste danach automatisch.

Die Datenbank erlaubt öffentlichen Lesezugriff und Einträge mit Nickname und Punktzahl, aber keine Änderungen oder Löschungen. Da das Quiz anonym spielbar ist, kann eine weltweite Rangliste nicht vollständig vor gefälschten Punktzahlen geschützt werden.