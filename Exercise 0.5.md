sequenceDiagram
    participant U as User
    participant B as Browser
    participant S as Server

    U->>B: 1. Acces the URL 
    
    B->>S: 2. GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate S
    
    S->>B: 3. Status 200 OK (Sends initial html)
    deactivate S
    
    Note over B: The HTML file references the main JS file
    
    B->>S: 4. GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate S
    
    S->>B: 5. Status 200 OK (Sends JS code)
    deactivate S

    Note over B: JS starts running
    
    B->>S: 6. GET https://studies.cs.helsinki.fi/exampleapp/data.json (Asks for notes data)
    activate S
    
    S->>S: 7. Retrieve notes from DB
    S-->>B: 8. Status 200 OK (send notes as JSON)
    deactivate S
    
    B->>U: 9. Shows the page with the notes