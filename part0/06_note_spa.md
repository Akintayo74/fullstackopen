sequenceDiagram
    participant browser
    participant server

    Note right of browser: User creates a note and clicks save

    Note right of browser: Browser executes form event handler

    Note right of browser: Browser calls e.preventDefault() to prevent default handling

    Note right of browser: Event handler creates new note and pushes it to array with notes.push(note)

    Note right of browser: Input field is cleared and Notes list is redrawn with DOM manipulation


    browser ->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of browser: Request contains JSON data type determined via Content-type header
    Note right of browser: Request payload
    server -->>browser: 201 created
    deactivate server

    Note right of browser: No page redirection occurs, user stays on the same page
    Note right of browser: No further HTTP requests is sent