# Exercise 0.4

```mermaid
sequenceDiagram
    participant U as User
    participant B as Browser
    participant S as Server
    
    U->>B: 1. Write the note content
    U->>B: 2. Click on "Save" or hit Enter
    
    B->>S: 3. POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate S
    S->>S: 3.1. Save the new note to the database
    S->>B: 4. Status 302 Found (Redirect to /notes URL)
    deactivate S

    Note over B, S: The browser automatically follows the redirect

    B->>S: 5. GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate S
    S->>S: 6. Retrieves ALL notes (including the new one)
    S-->>B: 7. Status 200 OK (Sends the updated HTML page)
    deactivate S

    B->>U: 8. Displays the reloaded page with the new note added to the list
