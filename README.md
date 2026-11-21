# Streamflix webOS (inoffizieller Port)

Eigenständige, **private inoffizielle** webOS-Umsetzung der Streamflix-Idee für LG-Fernseher.
Dies ist **keine offizielle App** des Projekts "Streamflix Reborn" und wird von dessen
Maintainer:innen weder autorisiert noch unterstützt.

Die Provider- und Extractor-Logik wurde aus dem Apache-2.0-lizenzierten Projekt
[Streamflix Reborn](https://git.gay/streamflix-reborn2/streamflix) von Kotlin nach
JavaScript portiert. Lizenztext und Namensnennung: siehe `LICENSE` und `NOTICE`.

## Status

Entwicklungskandidat. Auf Desktop-Chrome durchgespielt (Start, Suche, Detail,
Film-/Episodenwiedergabe über MEGAKino, Pluto TV DE). **Auf einem echten TV noch
nicht getestet** — Luna-Service, webOS-Chromium-Wiedergabe und Fernbedienungstasten
sind ungeprüft.

Eingebaute Quellen: MEGAKino, Pluto TV DE (legal, kostenlos). Nicht eingebaut:
KellerKino (Cloudflare-Schutzseite), AniWorld (DDoS-Guard), KinoGer / FilmPalast /
HDFilme / SerienStream (CUII-gelistet). Keine Umgehung von Schutzmaßnahmen, kein
`webSecurity:false`.

## Installation (nur Dev Mode)

1. `.ipk` aus dem neuesten Release herunterladen.
2. Auf dem TV: Developer-Mode-App → Dev Mode ON (Session aktiv halten).
3. Mit dem [webOS Dev Manager](https://github.com/webosbrew/dev-manager-desktop)
   (oder `ares-install`): Apps → Install → die `.ipk` auswählen.
4. Updates ersetzen die App über dieselbe App-ID — vorher nicht deinstallieren.

## Aufbau

- `app/` — Web-App (10-foot-UI, D-Pad, hls.js-Player, Poster-Umschalter im Info-Tab)
- `service/` — Luna-JS-Service (HTTP-Abruf + lokaler Medienproxy auf 127.0.0.1)
- `shared/` — gemeinsamer Fetch-/Proxy-Kern
- `dev/` — Desktop-Testharness (`node dev/dev-server.js`, dann http://127.0.0.1:8300/)
- `src/` — portierte Kotlin-Originalquellen (Referenz, Apache-2.0)

Paketieren mit [@webos-tools/cli](https://www.npmjs.com/package/@webos-tools/cli):
`ares-package app service -o dist`

Der vollständige Quellstand liegt jedem Release zusätzlich als
`*-source.tar.gz`-Asset bei.
