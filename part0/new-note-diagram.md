sequenceDiagram
    participant user
    participant server

    user->>server: user go to> https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>user: HTML document
    deactivate server

    user->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>user: the css file
    deactivate server

    user->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>user: the JavaScript file
    deactivate server

    Note right of user: The user starts executing the JavaScript code that fetches the JSON from the server

    user->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>user: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of user: The user executes the callback function that renders the notes and shows it a form

    user->>server: User types "New Note" on the form and click on "Save" button
    activate server

    server-->>user: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    user->>server: POST https://studies.cs.helsinki.fi/exampleapp/main.css a new JSON file with the new note data.
    activate server

    user->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>user: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of user: Finaly server returns JSON data with the new note added