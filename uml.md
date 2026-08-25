classDiagram
    direction LR

    %% 1. Association (Loose Relationship)
    class Person {
        -String name
        +bookRoom(Hotel h) void
    }
    class Hotel {
        -String hotelName
    }
    %% Straight line for Association
    Person "0..*" --> "0..*" Hotel : Association

    %% 2. Aggregation (Weak Has-a Relationship)
    class Airliner {
        -ArrayList~CrewMember~ crew
        +add(CrewMember c) void
    }
    class CrewMember {
        -String name
        -String role
    }
    %% Empty diamond for Aggregation
    Airliner o-- "0..*" CrewMember : Aggregation

    %% 3. Composition (Strong Has-a Relationship)
    class House {
        -Room room
        +House()
    }
    class Room {
        -int roomNo
    }
    %% Filled diamond for Composition
    House *-- "1..*" Room : Composition
