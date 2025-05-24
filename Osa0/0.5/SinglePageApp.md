
sequenceDiagram

    participant Käyttäjä
    participant Selain
    participant Palvelin
    participant JavaScript
    participant DOM

    Käyttäjä->>Selain: Siirry osoitteeseen https://studies.cs.helsinki.fi/exampleapp/spa
    Selain->>Palvelin: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa (Single-page application)
    Palvelin-->>Selain: HTML-tiedosto 
    Selain->>Palvelin: GET https://studies.cs.helsinki.fi/exampleapp/spa.js ja https://studies.cs.helsinki.fi/exampleapp/main.css
    Palvelin-->>Selain: Palauttaa JavaScript ja CSS
    Selain->>JavaScript: Suorita Javascripti 
    JavaScript->>Palvelin: GET notes (etsii kaikki muistiinpanot JSON-datasta)
    Palvelin-->>JavaScript: JSON-data (muistiinpanot)
    JavaScript->>DOM: Päivitä näkymä muistiinpanoilla
    
Selain pyytää ja lataa ensin HTML-sivun /spa. Sen jälkeen haetaan ja ajetaan JavaScripti. Sitten se tekee erillisen kutsun, joka hakee muistiinpanot JSON-datasta. Käyttöliittymä (DOM) päivittyy JavaScriptin avulla ilman uudelleenlatausta.
