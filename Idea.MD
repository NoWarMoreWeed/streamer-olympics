# Streamer Olympics – Projektidee

**Status:** Frühe Konzeptphase  
**Repository:** `streamer-olympics`  
**Ziel:** Eine zentrale, selbst betriebene Webplattform für Streamer-Olympiaden, auf der Vorbereitung, Lobby, Spiele, Punkte, Moderation und Zuschaueransicht zusammenlaufen.

## 1. Vision

Streamer sollen eine komplette Spiele-Olympiade über **eine einzige Webseite** durchführen können. Die Plattform führt den Host durch den Abend, startet die einzelnen Spiele, verwaltet Teams und Punkte und liefert eine saubere Ansicht für OBS.

Die Spiele sollen nach Möglichkeit **direkt in der Plattform laufen** und nicht von öffentlichen Spiele-Webseiten abhängen. Dadurch bleiben Ablauf, Verfügbarkeit und Zugang unter eigener Kontrolle. Bekannte Spiele dienen als Inspiration; eigene Umsetzungen sollen keine fremden Namen, Assets oder Quelltexte kopieren.

## 2. Warum das Projekt?

Öffentliche Spiele-Webseiten werden bei größeren Streams teilweise gestört oder gezielt angegriffen. Eine eigene Plattform soll:

- nur eingeladenen Teilnehmern Zugang geben,
- öffentliche Lobbys und erratbare Raumcodes vermeiden,
- Abhängigkeiten von fremden Diensten reduzieren,
- Spiele und Punktestand auch nach einem Reload zuverlässig erhalten,
- Moderatoren schnelle Korrekturen ermöglichen,
- den Wechsel zwischen vielen Webseiten und Programmen vermeiden.

**Wichtig:** Selbsthosting verhindert DDoS-Angriffe nicht automatisch. Der eigentliche Server darf nicht direkt offengelegt werden. Später werden unter anderem vorgeschalteter DDoS-Schutz, eine verborgene Origin-Adresse, Zugriffsschutz, Rate-Limits und ein sicherer WebSocket-Aufbau benötigt.

## 3. Grundprinzip der Plattform

1. Der Streamer erstellt eine Olympia-Veranstaltung.
2. Er lädt Teilnehmer und optional Moderatoren ein.
3. Teilnehmer treten solo oder als Team bei.
4. Der Host wählt Spiele und deren Reihenfolge aus.
5. Die Reihenfolge ist fest, einmalig gemischt oder wird während des Events ausgelost.
6. Die Webseite führt alle Beteiligten von Spiel zu Spiel.
7. Ergebnisse fließen automatisch oder nach Bestätigung in die Gesamtwertung ein.
8. Ein OBS-Overlay zeigt aktuelles Spiel, Teams, Punkte und Zwischenstand.

## 4. Rollen

### Host / Lobby-Besitzer

Pro Lobby gibt es genau einen steuernden Streamer.

- Veranstaltung vorbereiten und starten
- Teilnehmer und Teams verwalten
- Spiele auswählen
- Glücksrad beziehungsweise Zufallsauswahl bedienen
- Spiele starten, überspringen, später nachholen oder wiederholen
- Ergebnisse bestätigen
- Veranstaltung beenden

### Teilnehmer

Weitere Streamer sind aktive Spieler, aber keine Mit-Administratoren der Lobby.

- Lobby beitreten
- Team und eigenen Status sehen
- am aktuellen Spiel teilnehmen
- eigene geheime Informationen sehen, wenn ein Spiel dies benötigt
- keine Spiele starten oder den Ablauf verändern

### Moderator

- Teilnehmer bei Problemen unterstützen
- Spielinhalte vorbereiten
- Punkte und Ergebnisse erfassen oder korrigieren
- technische Spielzustände kontrolliert zurücksetzen
- Host bei einem Verbindungsabbruch unterstützen

### Plattform-Admin

Nur für Notfälle und systemweite Aufgaben:

- Host einer Lobby neu zuweisen
- kaputte Zustände wiederherstellen
- Audit-Verlauf prüfen
- Veranstaltung hart beenden
- Benutzer und Plattform verwalten

## 5. Spiele der aktuellen Olympia

### 5.1 QuackThing

- genauer Ablauf und Regeln müssen noch dokumentiert werden
- prüfen, ob eine eigene Browser-Version sinnvoll und rechtlich möglich ist

### 5.2 Guess the Price

- Produkt oder Gegenstand mit Bild und optionaler Beschreibung anzeigen
- Spieler beziehungsweise Teams geben verdeckt einen Preis ab
- Punkte nach Nähe zum echten Preis
- mögliche Varianten: Überbieten verboten, Zeitlimit, Kategorien, mehrere Runden

### 5.3 GeoBingo

- Solo- und Teammodus
- zentral in die Plattform eingebunden
- Orte, Aufgaben und Fortschritt pro Team verwalten
- Ergebnis automatisch an die Gesamtwertung übergeben
- bestehendes GeoBingo kann technisch als getrenntes Modul beziehungsweise eigener Dienst bleiben, soll sich für Benutzer aber wie ein Teil der Plattform anfühlen

### 5.4 Fragen-Antwort-Spiel

- Frage mit vier Antworten: A, B, C und D
- Einzel- oder Teamantwort
- verdeckte Antworten bis zum Ablauf des Timers
- Punkte für richtige und optional schnelle Antworten
- Fragenpakete über einen einfachen Import vorbereiten

### 5.5 Imposter-Wortspiel

Beispiel mit vier Spielern:

- drei Spieler erhalten dasselbe geheime Wort
- ein Spieler ist der Imposter und kennt das Wort nicht
- alle geben nacheinander Hinweise
- anschließend Abstimmung über den Imposter
- Punkte für richtiges Erkennen beziehungsweise erfolgreiches Täuschen
- Spielerzahl und Anzahl der Imposter später konfigurierbar

### 5.6 Snake Arena

- vier Spieler gleichzeitig gegeneinander
- Browser-Multiplayer in einer gemeinsamen Arena
- Kollisionen, Ausscheiden und Platzierung werden automatisch erkannt
- mögliche Formate: einzelne Runde, Best-of-X oder Punkte nach Platzierung

### 5.7 Zeichen- und Ratespiel

Eigene, integrierte Variante nach dem Grundprinzip bekannter Zeichen-Ratespiele:

- ein Spieler zeichnet einen Begriff
- die anderen raten im Chat
- richtige Antworten und Geschwindigkeit geben Punkte
- Wortlisten können vorbereitet und importiert werden
- keine Abhängigkeit von einer öffentlichen Skribbl.io-Lobby

### 5.8 Multiplayer-Minigolf

Eigene browserbasierte Minigolf-Variante als langfristiges Spielmodul:

- mehrere Spieler auf einem Kurs
- Schläge und Platzierung automatisch erfassen
- kurze, streamtaugliche Kurse
- zunächst kein Anspruch, den vollständigen Umfang von Golf With Your Friends nachzubauen

### 5.9 Russisches-Roulette-Spiel

Eigene fiktionale Browser-Variante, inspiriert von dem gespielten Steam-Spiel:

- rundenbasiertes Risiko- und Bluffspiel
- Regeln und verwendetes Steam-Spiel noch genau identifizieren
- eigener Name, eigene Gestaltung und eigenständige Mechaniken
- keine Übernahme geschützter Assets oder Marken

### 5.10 Wortbombe / Wortkette

Beispiel:

- die Bombe zeigt `FE`
- ein Spieler ergänzt zu einem gültigen Wort, zum Beispiel `Affe`
- daraus entsteht die nächste Buchstabenfolge, beispielsweise `AF`
- der nächste Spieler muss rechtzeitig ein neues gültiges Wort finden
- bei Ablauf der Zeit explodiert die Bombe und der Spieler verliert ein Leben oder erhält Minuspunkte

Noch zu klären:

- wie genau die nächste Buchstabenfolge aus dem vorherigen Wort entsteht,
- welches Wörterbuch gilt,
- ob Beugungen, Namen und Wiederholungen erlaubt sind.

### 5.11 Karten-Ablegespiel

Eigene Browser-Umsetzung eines schnellen farb- und zahlenbasierten Ablegespiels:

- private Handkarten pro Spieler
- Zugreihenfolge und erlaubte Karten serverseitig prüfen
- Aktionskarten, Ziehstapel und Siegbedingung
- eigener Name und eigene Gestaltung statt Verwendung der Marke UNO

## 6. Gemeinsame Spielmodul-Schnittstelle

Jedes integrierte Spiel sollte dem Hub dieselben Grundinformationen liefern können:

- Spielstatus: vorbereitet, bereit, läuft, pausiert, beendet oder abgebrochen
- Teilnehmer und Teams
- aktueller Durchgang
- Rohresultat des Spiels
- daraus berechnete Olympia-Punkte
- Gewinner beziehungsweise Platzierung
- Wiederholung oder Neustart
- Verbindungsstatus der Spieler

Dadurch kann der Hub neue Spiele aufnehmen, ohne den gesamten Veranstaltungsablauf neu zu bauen.

## 7. Punkte und Nachvollziehbarkeit

- Rohresultate eines Spiels und Olympia-Punkte getrennt speichern
- Gesamtwertung aus einzelnen Punktebuchungen berechnen
- Änderungen nicht heimlich überschreiben
- Korrekturen als nachvollziehbare Gegenbuchung oder neue Version speichern
- Undo für die letzte Aktion anbieten
- bei Wiederholung auswählen: neue Runde hinzufügen oder altes Ergebnis ersetzen
- Gleichstände und manuelle Bonus-/Strafpunkte unterstützen

## 8. Host-Dashboard

Während des Streams soll der Host möglichst wenig nachdenken müssen.

Immer sichtbar:

- aktuelles Spiel
- eine große, eindeutige Hauptaktion
- nächster erwarteter Schritt
- Teilnehmer- und Verbindungsstatus
- Gesamtpunktestand
- nächste Spiele
- letzte Aktion und Undo

Typische Aktionen:

- Starten
- Ergebnis bestätigen
- Pausieren
- Für später überspringen
- Wiederholen
- Nächstes Spiel auslosen
- Olympia beenden

## 9. Zuschauer- und OBS-Ansicht

- transparente Browser-Source für OBS
- aktuelles Spiel und Runde
- Teilnehmer beziehungsweise Teams
- Gesamtpunktestand
- Gewinneranimation und Zwischenstände
- keine geheimen Spielerinformationen
- Overlay darf keine Steuerfunktionen besitzen
- verschiedene Layouts für 16:9, Hochformat und kompakte Einblendungen später möglich

## 10. Inhalte und Vorbereitung

Für Quizfragen, Wörter, Produkte und andere Spielinhalte:

- manuelle Eingabe
- wiederverwendbare Inhaltspakete
- einfacher Listenimport: ein Eintrag pro Zeile
- CSV-Import für Fragen mit A/B/C/D und richtiger Antwort
- Vorschau vor dem Import
- Duplikate und fehlerhafte Zeilen anzeigen
- Inhalte vor dem Stream als „bereit“ markieren

## 11. Sicherheits- und Betriebsanforderungen

- keine öffentlichen, frei durchsuchbaren Lobbys
- starke, nicht erratbare Einladungslinks oder eingeloggte Konten
- Lobby-Zugriff widerrufbar
- serverseitige Rollen- und Rechteprüfung
- serverseitige Prüfung aller Spielzüge
- Rate-Limits für Login, Lobby-Beitritt, Chat und Spielaktionen
- Origin-Server nicht direkt im DNS oder Client-Code offenlegen
- vorgeschalteter DDoS-Schutz beziehungsweise geeigneter Tunnel/Proxy
- WebSocket-Verbindungen authentifizieren und begrenzen
- automatische Wiederverbindung ohne Verlust des Spielzustands
- Audit-Log für administrative und punktverändernde Aktionen
- Backups für Veranstaltungen, Inhalte und Ergebnisse

## 12. Sinnvoller MVP

Nicht alle Spiele gleichzeitig bauen. Zuerst muss der gemeinsame Olympia-Ablauf funktionieren.

### Phase 1 – Hub

- Konten und Einladungen
- Lobby mit Host, Teilnehmern, Teams und Mods
- feste oder zufällige Spielreihenfolge
- Host-Dashboard
- manuelle Ergebnisse und Gesamtwertung
- Undo und Korrekturen
- einfache OBS-Ansicht

### Phase 2 – erste integrierte Spiele

Je ein repräsentatives Modul:

1. A/B/C/D-Quiz
2. Imposter-Wortspiel
3. Wortbombe
4. Guess the Price

Damit werden Echtzeitantworten, geheime Informationen, Timer, Inhaltsimporte und automatische Punkte abgedeckt.

### Phase 3 – komplexe Echtzeitspiele

- Snake Arena
- Zeichen- und Ratespiel
- Karten-Ablegespiel
- GeoBingo-Anbindung

### Phase 4 – aufwendige Spielwelten

- Multiplayer-Minigolf
- Roulette-/Risiko-Spiel
- weitere Olympia-Spiele

## 13. Offene Fragen

- Wie genau funktioniert QuackThing?
- Wie heißt das gespielte russische-Roulette-Spiel auf Steam und welche Regeln davon sind wichtig?
- Wie wird beim Wortbomben-Spiel die nächste Buchstabenfolge bestimmt?
- Werden Punkte nur nach Platzierung oder je Spiel individuell vergeben?
- Wie viele Spieler und Teams sollen eine Lobby maximal unterstützen?
- Spielen alle Teilnehmer am PC oder teilweise am Smartphone?
- Benötigt jede Person ein eigenes Konto oder reicht ein einmaliger Einladungslink?
- Soll ein Moderator bei Bedarf die Host-Steuerung vollständig übernehmen können?
- Welche Spiele müssen für die erste echte Olympia zwingend fertig sein?

## 14. Leitlinie

Die Plattform ist kein loses Menü mit Minispielen. Sie ist ein **geführtes Live-Event-System**, das Vorbereitung, Durchführung, Wiederherstellung, Wertung und Übertragung zuverlässig zusammenhält.
