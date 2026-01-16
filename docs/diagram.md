# Diagram przepływu



```mermaid
graph TD
    Start((START)) --> Login[Logowanie]
    Login --> Dashboard[Ekran Główny]

    %% Wybór ścieżki
    Dashboard -->|Wybór A| SingleBook[Szybka rezerwacja]
    Dashboard -->|Wybór B| Planner[Kreator Planu]

    %% Ścieżka Kreatora
    Planner --> Step1[Wybór wydarzenia nr 1]
    Step1 --> Suggest[System sugeruje lokale obok]
    
    Suggest --> Step2[Wybór wydarzenia nr 2]
    Step2 --> CheckTime{Czy zdążysz?}
    
    CheckTime -->|Nie| Error[Komunikat: Za mało czasu]
    Error --> Step2
    
    CheckTime -->|Tak| Timeline[Oś czasu]
    
    Timeline --> Decision{Koniec?}
    Decision -->|Nie| Suggest
    Decision -->|Tak| Summary[Podsumowanie]

    %% Finalizacja
    SingleBook --> Summary
    Summary --> Payment[Płatność]
    Payment --> Ticket[Bilety QR]
    Ticket --> End((KONIEC))