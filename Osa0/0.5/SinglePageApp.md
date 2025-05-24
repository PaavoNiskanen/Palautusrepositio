
sequenceDiagram

    participant browser
    participant server
    
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
    
    Note right of browser: Palvelin alkaa suorittamaan JavaScripti koodia, joka JSON-datan selaimesta
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "", "date": "" }, ... ]
    deactivate server    

    Note right of browser: Palvelin suorittaa komennon, joka lataa JSON-datan muistiinpanot selaimeen
