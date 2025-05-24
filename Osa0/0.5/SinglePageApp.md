
sequenceDiagram

    participant Käyttäjä
    participant Selain
    participant Palvelin
    participant JavaScript
    participant DOM

    Käyttäjä->>Selain: Siirry osoitteeseen /spa
    Selain->>Palvelin: HTTP GET /spa
    Palvelin-->>Selain: HTML-tiedosto (SPA-runko)
    Selain->>Palvelin: GET app.js ja muut resurssit
    Palvelin-->>Selain: JavaScript, CSS, ym.
    Selain->>JavaScript: Aja JavaScript
    JavaScript->>Palvelin: GET /notes (API-kutsu)
    Palvelin-->>JavaScript: JSON-data (muistiinpanot)
    JavaScript->>DOM: Päivitä näkymä muistiinpanoilla
