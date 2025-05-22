sequenceDiagram
    participant browser
    participant server

    Note right of browser: Käyttäjä kirjoittaa muistiinpanon tekstikenttään ja painaa "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: Palvelin tallentaa uuden muistiinpanon ja ohjaa selaimen takaisin /notes-sivulle
    server-->>browser: HTTP redirect response (302) -> /notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: Selain suorittaa JavaScript-koodin, joka hakee muistiinpanot palvelimelta

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON list of notes including the new one
    deactivate server

    Note right of browser: Selain suorittaa palautetun JSON-datan perusteella muistiinpanojen renderöinnin


