erDiagram

    ROLLID {
        TINYINT id PK
        VARCHAR nimi
    }

    KASUTAJAD {
        INT id PK
        VARCHAR eesnimi
        VARCHAR perenimi
        CHAR isikukood
        VARCHAR email
        VARCHAR parooli_hash
        TINYINT rolli_id FK
        TIMESTAMP loodud
    }

    TRENNID {
        INT id PK
        VARCHAR nimetus
        DATE kuupäev
        TIME algusaeg
        SMALLINT kestus_minutites
        SMALLINT max_osalejaid
        INT loodud_kasutaja FK
        TIMESTAMP loodud
    }

    REGISTREERIMISED {
        INT id PK
        INT kasutaja_id FK
        INT trenni_id FK
        TIMESTAMP loodud
    }

    ROLLID ||--o{ KASUTAJAD : "omab"
    KASUTAJAD ||--o{ TRENNID : "loob"
    KASUTAJAD ||--o{ REGISTREERIMISED : "registreerib"
    TRENNID ||--o{ REGISTREERIMISED : "sisaldab"
