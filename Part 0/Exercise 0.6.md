# Exercise 0.6

```mermaid
sequenceDiagram
    participant U as User
    participant B as Browser
    participant S as Server
    
    U->>B: 1. Writes note content
    U->>B: 2. Clicks on "Save"
    
    Note over B: JS calls e.preventDefault to stop page reload
    
    B->>B: 3. Creates note object and updates local list 
    B->>U: 4. Renders the list again
    
    B->>S: 5. POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate S
    S->>S: 6. Saves note in DB
    

    S-->>B: 7. Status 201 Created
    deactivate S
