# StrategyGame

🧩 Задание: Създаване на база данни за стратегическа игра с Entity Framework
🧩 Допълнение: Реализирайте MVC (Model-View-Controller) приложение с потребителски интерфейс по желание, което да работи със създадената БД. Внедрете функционалност, която сметнете за необходима. Използвайте добрите практики при писане на програмен код. 
🎯 Цел:

Да се моделира релационна база данни за стратегическа игра, в която играчите изграждат сгради, управляват ресурси, създават единици и водят битки. Използвай Entity Framework Core за създаване на моделите и миграциите.
📋 Таблици (15 общо)
1. Players

    Id (PK)

    Username

    Email

    CreatedAt

2. Factions

    Id (PK)

    Name

    Description

3. PlayerFactions

    Id (PK)

    PlayerId (FK → Players)

    FactionId (FK → Factions)

    StartDate

    Един играч може да играе с различни фракции в различни сесии.

4. Buildings

    Id (PK)

    Name

    Description

    BuildTime (в секунди)

    FactionId (FK → Factions)

5. PlayerBuildings

    Id (PK)

    PlayerId (FK → Players)

    BuildingId (FK → Buildings)

    Level

    BuiltAt

6. Units

    Id (PK)

    Name

    AttackPower

    DefensePower

    TrainingTime

    FactionId (FK → Factions)

7. PlayerUnits

    Id (PK)

    PlayerId (FK → Players)

    UnitId (FK → Units)

    Quantity

8. Resources

    Id (PK)

    Name

    Description

9. PlayerResources

    Id (PK)

    PlayerId (FK → Players)

    ResourceId (FK → Resources)

    Amount

10. Battles

    Id (PK)

    AttackerId (FK → Players)

    DefenderId (FK → Players)

    StartedAt

    EndedAt

    Result (enum: AttackerWin, DefenderWin, Draw)

11. BattleUnits

    Id (PK)

    BattleId (FK → Battles)

    UnitId (FK → Units)

    PlayerId (FK → Players)

    Quantity

12. Maps

    Id (PK)

    Name

    SizeX

    SizeY

    Description

13. PlayerLocations

    Id (PK)

    PlayerId (FK → Players)

    MapId (FK → Maps)

    X

    Y

14. Technologies

    Id (PK)

    Name

    Description

    ResearchTime

15. PlayerTechnologies

    Id (PK)

    PlayerId (FK → Players)

    TechnologyId (FK → Technologies)

    IsResearched

    ResearchedAt

📦 Примерни начални данни (JSON)

{
  "Factions": [
    { "Id": 1, "Name": "Humans", "Description": "Balanced race with strong economy." },
    { "Id": 2, "Name": "Orcs", "Description": "Strong melee units, weak defenses." }
  ],
  "Buildings": [
    { "Id": 1, "Name": "Barracks", "Description": "Trains infantry.", "BuildTime": 60, "FactionId": 1 },
    { "Id": 2, "Name": "Farm", "Description": "Produces food.", "BuildTime": 30, "FactionId": 1 }
  ],
  "Units": [
    { "Id": 1, "Name": "Swordsman", "AttackPower": 10, "DefensePower": 5, "TrainingTime": 45, "FactionId": 1 },
    { "Id": 2, "Name": "Archer", "AttackPower": 7, "DefensePower": 3, "TrainingTime": 30, "FactionId": 1 }
  ],
  "Resources": [
    { "Id": 1, "Name": "Gold", "Description": "Used for building and training." },
    { "Id": 2, "Name": "Food", "Description": "Required for units to survive." }
  ],
  "Technologies": [
    { "Id": 1, "Name": "Advanced Metallurgy", "Description": "Increases attack by 10%", "ResearchTime": 120 },
    { "Id": 2, "Name": "Efficient Farming", "Description": "Increases food production by 20%", "ResearchTime": 90 }
  ],
  "Maps": [
    { "Id": 1, "Name": "Valley of Kings", "SizeX": 100, "SizeY": 100, "Description": "A balanced map with hills and forests." }
  ]
}

📌 Задание към студента:

    Изгради всички модели и релации с помощта на Entity Framework Core.

    Създай начална миграция и запълни базата с примерните данни от JSON.

    Добави примерна заявка, която:

        Извежда всички играчи с техните ресурси.

        Показва резултат от последните 5 битки.

        Извежда всички сгради и единици, достъпни за фракция "Humans".
