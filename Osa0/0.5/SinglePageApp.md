sequenceDiagram

    participant browser
    participant server

    Note right of browser: Selain hakee palvelimesta HTML dokumentin, CSS- ja JavaScript-tiedoston ja lataa ne sivustolle. 
    
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
    
    Note right of browser: Selain alkaa suorittamaan JavaScripti koodia, joka hakee JSON-datan ja lataa sen sivustolle. 
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "", "date": "" }, ... ] 
    deactivate server    

    Note right of browser: Selain suorittaa komennon, joka lataa JSON-datan muistiinpanot palvelimeen. Tämän jälkeen sivusto on valmis. 
