```mermaid
erDiagram
    CARD }|--o{ DECK : within
    DECK }o--|{ CARD : contains
    USER ||--|{ CARD : owns
    USER ||--|{ DECK : owns
    
    
```