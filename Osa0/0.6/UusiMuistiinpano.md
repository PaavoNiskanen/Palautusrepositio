sequenceDiagram

    participant browser
    participant server

    Note right of browser: Käyttäjä kirjoittaa muistiinpanon tekstikenttään ja painaa "Save"
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
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
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server    

    Note right of browser: Selain suorittaa palautetun JSON-datan perusteella muistiinpanojen renderöinnin
