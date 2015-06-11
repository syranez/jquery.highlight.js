# jquery.highlight.js

Based on highlight v5 http://johannburkard.de/blog/programming/javascript/highlight-javascript-text-higlighting-jquery-plugin.html

## Fixes

In Chrome wird der Buchstabe "ß" bei einem "ß".toUpperCase() zu "SS". Somit hat das großgeschriebene Wort ein Zeichen mehr als das Ausgangswort:

    var f = "Fußball";
    if (f.length !== f.toUpperCase().length) {
        PANIC
    }

Weil jquery.highlight.js ein splitText mit der Länge des großgeschriebenen Wortes macht, aber den DOM-Node selber unverändert lässt, schägt splitText mit einer Exception fehl.

Der Fix ist die Originalänge des Wortes für splitText zu verwenden.
