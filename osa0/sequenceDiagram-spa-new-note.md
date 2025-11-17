sequenceDiagram
    participant browser
    participant server

    Note right of browser: Käyttäjä kirjoittaa uuden muistiinpanon<br/>tekstikenttään ja painaa "tallenna"-nappia.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server

    Note left of server: Palvelin vastaanottaa uuden muistiinpanon<br/>sisällön HTTP-pyynnön rungossa (body).<br/>Palvelin lisää muistiinpanon olemassa olevaan<br/>tietorakenteeseen (esim. listaan tai tiedostoon).

    server-->>browser: HTTP 201 Created (palauttaa uuden muistiinpanon JSON-muodossa)
    deactivate server

    Note right of browser: Selain suorittaa tapahtumankäsittelijän,<br/>joka päivittää muistiinpanolistan.<br/>Uusi muistiinpano lisätään näkymään<br/>ilman sivun uudelleenlatausta.