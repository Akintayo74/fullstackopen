sequenceDiagram
    participant browser
    participant server

    Note right of browser: User rights a note and clicks save button

    browser ->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of browser: Form data contains the new note content
    server -->>browser: HTTP 302 Redirect to /notes
    deactivate server

    browser ->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server -->>browser: HTML document
    deactivate server

    browser ->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server -->>browser: CSS stylesheet
    deactivate server

    browser ->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server -->>browser: JavaScript file
    deactivate server

    Note right of browser: The browser starts executing JS code that fetches the JSON from server

    browser ->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server -->>browser: [{ "content": "jealousy, jealousy", "date": "2025-03-30" }, ...]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes