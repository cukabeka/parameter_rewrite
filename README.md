Parameter Rewrite
========================

Dieses AddOn ermöglicht dir eigene Parameter-Trenner festzulegen.

Die URL:

> https://example.org/?foo=bar

wird zum Beispiel mit dem Trenner "++" zu:

> https://example.org/++/foo/bar

Settingspage
------------
Die Settingspage integriert sich als Tab-Reiter innerhalb des AddOns <a href="/redaxo/index.php?page=yrewrite/parameter_rewrite">yRewrite</a>.
Innerhalb der Settingspage kann der Parameter-Trenner festgelegt wexrden.

Installation
------------
Hinweis: dies ist kein Plugin!

* Release herunterladen und entpacken.
* Ordner umbenennen in `parameter_rewrite`.
* In den Addons-Ordner legen: `/redaxo/src/addons`.

Oder den REDAXO-Installer / ZIP-Upload AddOn nutzen!

Voraussetzungen
------------

* yrewrite AddOn

SEO-Optimierung & Best Practices
-------------------------------

**Empfohlener Parameter-Trenner:**
- Alternativ: `-p-` als sichtbaren Trenner
- Spezialzeichen wie `++`, `~`, `_` oder `--` vermeiden (siehe SEO-OPTIMIERUNG.md)

## Empfohlene Parameter-Trenner

**Beispiel-URL ohne Trenner:**
```
https://example.org/foo/bar/
```

**Beispiel-URL mit Trenner:**
```
https://example.org/-p-/foo/bar/
```

### praktikable Trenner (semantisch neutral, stören keine Rewrite-Regeln):
- `-p-`
- `-x-`
- `-param-`
- `-data-`
- `-info-`
- `-extra-`
- `-sec-`
- `-block-`
- `-mod-`
- `-custom-`

**Nicht empfohlen:**
- `++`, `--`, `_`, `~`, `.`, `/`, `|`, `:`, `;`, `,` (können zu Encoding-, SEO- oder Rewrite-Problemen führen)

*Unterstrich _ (Underscore)*

- SEO-Probleme: Google und andere Suchmaschinen interpretieren _ als Wortverbinder, nicht als Trenner. Das heißt, foo_bar wird als ein Wort gelesen, nicht als zwei.
- Encoding-Probleme: Im URL-Kontext ist _ zwar zulässig, aber:
- Manche CMS, Frameworks oder Routing-Libraries nutzen _ als Platzhalter für Variablen oder Methoden (z.B. foo_bar als Funktionsname).
- In manchen Regex-basierten Rewrite-Regeln kann _ zu Konflikten führen, wenn es als Teil eines Musters verwendet wird.
- Bei Copy-Paste aus Office-Programmen kann _ als Unicode-Zeichen (＿) oder als HTML-Entity (&#95;) kodiert werden, was zu Problemen bei der URL-Weitergabe führen kann.
Praxis: _ ist technisch meist erlaubt, aber für SEO und semantische Trennung ungeeignet. Encoding-Probleme entstehen vor allem bei Copy-Paste, Unicode-Mischung oder strengen Routing-Regeln

* Tilde ~ (Tilde)*

- Encoding-Probleme: Die Tilde ist im ASCII-Zeichensatz ein reserviertes Zeichen, aber laut RFC 3986 für URLs eigentlich zulässig. Dennoch:
Manche ältere Webserver, Proxies oder Security-Filter behandeln ~ als Sonderzeichen (z.B. für User-Home-Verzeichnisse wie /~user/).
- In manchen Rewrite-Regeln (z.B. Apache .htaccess) kann ~ als regulärer Ausdruck interpretiert werden.
- In E-Mail-Clients, CMS-Plugins oder bei Copy-Paste aus Word/Excel kann die Tilde in Unicode (˜) oder als HTML-Entity (&#126;) kodiert werden, was zu Problemen bei der URL-Weitergabe oder -Verarbeitung führen kann.
- Manche Webanwendungen wandeln die Tilde in %7E um, was zu doppelter Kodierung führen kann.
Praxis: In modernen Browsern und Servern ist ~ meist unproblematisch, aber in Legacy-Umgebungen oder bei strengen Rewrite-Regeln kann es zu Fehlern kommen.

**SEO Best Practices:**
- URLs sollten sprechend und semantisch sein, z.B. `/foo/bar/`
- Keine unnötigen Sonderzeichen oder Parameter in der URL
- Canonical URLs und robots.txt beachten
- Nur relevante URLs in die Sitemap aufnehmen

**Optimierungen ab November 2025:**
- Fehlerkorrektur bei REQUEST_URI
- Validierung der Parameter-Keys
- Sichere Behandlung von Query-Strings
- Verbesserte Robustheit und Code-Qualität

**Weitere Hinweise:**
- Nach Änderungen: URLs und Weiterleitungen testen!

---
Stand: November 2025
Getestet mit: PHP 8.x, REDAXO 5.x
