sequenceDiagram
    
    participant browser
    participant server

    Note right of browser: Käyttäjä kirjoittaa muistiinpanon tekstikenttään ja painaa "Save"
    
    browser->>server: https://studies.cs.helsinki.fi/exampleapp/notes_form
    activate server
    Note right of server: Palvelin tallentaa uuden muistiinpanon ja ohjaa selaimen takaisin /notes-sivulle
    server-->>browser: HTTP vastaus -> /notes
    deactivate server

    Note right of browser: Selain uudelleen lataa HTML dokumentin, CSS- ja JavaScript-tiedoston. 

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML dokumentti
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS-tiedosto
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JavaScripti-tiedosto
    deactivate server
    
    Note right of browser: Selain suorittaa JavaScript-koodin, joka hakee muistiinpanot palvelimelta
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "", "date": "2025-5-24" }, ... ]
    deactivate server    

    Note right of browser: Selain suorittaa palautetun JSON-datan perusteella muistiinpanojen renderöinnin
