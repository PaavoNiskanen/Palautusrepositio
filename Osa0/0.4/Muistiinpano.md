sequenceDiagram

    participant browser
    participant server

    Note right of browser: Käyttäjä kirjoittaa muistiinpanon tekstikenttään ja painaa "Save"-painiketta

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    
    Note right of server: Palvelin tallentaa uuden muistiinpanon ja ohjaa selaimen takaisin /notes-sivulle
    
    server-->>browser: HTTP kertoo vastauksen -> /notes
    deactivate server

    Note right of server: Selain päivittää muut sivuston osat

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML dokumentti
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS-tiedosto
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript-tiedosto
    deactivate server

    Note right of browser: Selain suorittaa JavaScript-koodin, joka hakee  muistiinpanot.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON lista päivittyy, jolloin uusi muistiinpano lisätään JSON-dataan 
    deactivate server

    Note right of browser: Selain suorittaa palautetun JSON-datan perusteella muistiinpanojen renderöinnin

Käyttäjä siis kirjoittaa muistiinpanon (action="exampleapp/new_note") ja selain tekee POST-pyynnön. Palvelin vastaanottaa pyynnön ja käsittelee uuden muistiinpanon. Sen jälkeen selain hakee HTML-, CSS- ja JavaScript-tiedostot uudestaan GET:in avulla. JavaScript hakee JSON-datan ja selain päivittyy uusien tietojen perusteella.
