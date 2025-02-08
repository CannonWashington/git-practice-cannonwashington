```mermaid
erDiagram

    DECK }o--|{ CARD : contains
    USER ||-- |{ CARD : owns
    USER ||--|{ DECK : owns
    ADMIN ||--|{ CARD : creates
    
    
    CARD {
        string name
        class type
        string rarity
        int attack
        int defense
    }
    DECK {
        class[] CARD
        string name
        
    }
    USER {
        string name
        
    }
    ADMIN {
        string name
        boolean permissions
        
    }
```
```mermaid
flowchart
    A[Start] -->|New User| B[Sign Up]   
    A -->|Existing User| C[Log In]

    B --> D[Dashboard]
    C --> D
    
    
    
    D -->|Cards Button| E[Cards]
    E -->|View Cards| F[My Cards]
    E -->|Add Cards| G[Card Store]
    
    
    D -->|Decks Button| I[Decks]
    I -->|Individual Deck| J[Deck]
    D -->|Create Deck| K[Create Deck]
    
    F -->|Individual Card| H[Card]
    H -->|Add Card to Deck| I
    
    
    C -->|Admin Login| L[Admin]
    L --> D
    L -->|New Card| M[Blank Card]
    M -->|Finish Card| G
```

```mermaid
flowchart
    A[User] --> |Interacts With| B[Front-end]
    B --> |API Calls| C[Backend]
    
    C --> |Stores and Retrieves Data| D[Card Database]
    C --> |Stores and Retrieves Data| E[Deck Database]
    C --> |Handles Authentication| F[Login/Signup Services]
    
    G[Admin] --> |Interacts With| B
    G --> |Interacts With| C
```
| Endpoint                      | Method | Authentication |
|-------------------------------|--------|----------------|
| `/api/cards`                  | GET    | No             |
| `/api/cards:id`               | GET    | No             |
| `/api/cards`                  | POST   | Yes, Admin     |
| `/api/cards/:id`              | PUT    | Yes, Admin     |
| `/api/cards/:id`              | DELETE | Yes, Admin     |
| `/api/decks`                  | GET    | Yes, User      |
| `/api/decks/:id`              | GET    | Yes, User      |
| `/api/decks`                  | POST   | Yes, User      |
| `/api/decks/:id`              | PUT    | Yes, User      |
| `/api/decks/:id`              | DELETE | Yes, User      |
| `/api/authorization/login`    | POST   | No             |
| `/api/authorization/register` | POST   | No             |
| `/api/authorization/logout`   | POST   | Yes, User      |