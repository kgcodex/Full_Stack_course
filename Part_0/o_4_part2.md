# Part 0 0.4: User submit the new note using form
Diagram is continued..  
Its a HTTP POST request with status code 302. Its a URL redirect.  
Browser do a new HTTP GET request to the address --notes.  
This causes three more HTTP requests.

```mermaid
sequenceDiagram
    participant browser
    participant server
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->browser: URL Redirect
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

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    Note right of browser: New note is added to data.json on the server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ..,{"content":"new note","date":2023-12-27"} ]
    deactivate server

'''    
