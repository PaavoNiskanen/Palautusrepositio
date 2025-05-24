sequenceDiagram

    participant browser
    participant server

    Note right of browser: Käyttäjä kirjoittaa muistiinpanon tekstikenttään ja painaa "Save"

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML-tiedosto
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS-tiedosto
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript-tiedosto
    deactivate server

    Note right of browser: Selain suorittaa JavaScript-koodin, joka hakee  muistiinpanot palvelimelta

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON lista päivittyy, jolloin uusi muistiinpano lisätään JSON-dataan 
    deactivate server

    Note right of browser: Selain suorittaa palautetun JSON-datan perusteella muistiinpanojen renderöinnin

Käyttäjä siis kirjoittaa muistiinpanon (action="exampleapp/new_note") ja selain tekee POST-pyynnön. Palvelin vastaanottaa pyynnön GET:illä ja käsittelee uuden muistiinpanon. Sen jälkeen selain hakee HTML-, CSS- ja JavaScript-tiedostot uudestaan. JavaScript hakee JSON-datan ja selain päivittyy uusien tietojen perusteella.
