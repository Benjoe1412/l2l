# l2l

## Alapvetések
egyértelmű alapok, hol állunk merre megyünk


- technológiák
dotnetcore

- eszközök használata

- feladat: amit nem kell tervezni

- Továbbfejleszthető legyen

## Vázlat
Megnevezni az alkalmazásokat

- elsődleges cél: egy webalkalmazás (MVC)
- továbbfejlesztés: üzleti logika elérhetőségének biztosítása (MVC)
- továbbfejl: desktop alkalmazás (WPF)
- mobil alkalmazás (Xamarin)
- Webes Single page készítése (Blazor)

## Webalkalmazás 
Oktató webalkalmazás, 
- oktatók tudnak csatlakozni ahol tanfolyamokat tudnak létrehozni 
- tanulók tudnak csatlakozni, hogy elvégezzék a tanfolyamot

fullstack C# fejlesztés

 DB                       Repository                       Service             MVC WebApp
+-----------------+      +-------------------------+      +-----------+       +-----------------------------------------+
|                 |      |                         |      |           |       |                                         |
|                 |      |                         |      |           |       | +---------+  +----------+ +-------+     |
|                 +----->| +-------+               +----->|           +------>| |         |  |          | |       |     |
|                 |      | |       |               |      |           |       | | View    |  |Controller| | View  |     |
|                 |<-----+ |       |               |<-----+           |<------+ |         |  |          | |       |     |
|                 |      | | EF    |               |      |           |       | | Model   |  |          | |       |     |
|                 |      | |       |               |      |           |       | |         |  |          | |       |     |
|                 |      | | Model |               |      |           |       | |         |  |          | |       |     |
|                 |      | |       |               |      |           |       | |         |  |          | |       |     |
|                 |      | |       |               |      |           |       | |         |  |          | |       |     |
|                 |      | +-------+               |      |           |       | +---------+  +----------+ +-------+     |
|                 |      |                         |      |           |       |                                         |
+-----------------+      +-------------------------+      +-----------+       +-----------------------------------------+
Ha az EF modell mellet kiemeljük a szervezési feladatokat (legyen mondjuk *üzleti logika* a neve az olyan szakzsargon-pozitív, vagy **Service**), akkor már van olyan pont, ahol az API be tud kapcsolódni, és lehetőség szerint nem duplikálunk majd a megvalósításnál már eleve tervezett módon kilóméternyi kódokat.

## OOD objektum orientált tervezés

- **Csatolás *(Coupling)*:** ha egy elem függ más elemektől, akkor ezek az elemek csatolásban vannak
- **gyenge *(low)*** ez a csatolás abban az esetben, ha a csatolásban lévő elemek esetén egy változás továbbterjedése megállítható.


Első cél: **gyenge csatolás** elérése.


- **kohézió *(cohesion)*:** egy elem felelősségeinek egymáshoz való kapcsolata
- a kohézió **gyenge (*low*)**, ha az adott elemnek túl sok egymástól független felelőssége van
- a kohézió **erős (*high*)**, ha az adott elem felelősségei erősen összefüggnek és nagyon koncentráltak

Cél: **Erős kohézió** dobozon belül

- költségek
 - Erőforrástól
 - Időtől
 - élettartamtól

## Feladatok, felelősségi körök

### DB
- legyen ef core támogatása
    - adatbázis tervezés és telepítés
- [docker container] támogatás
- kezdetben sqlight, majd kibővítjük mssql-re

- kockázatok
    - teljesítmény
    - relációs adatbázisok


### Repository
- CRUD műveleted elvégzése (**C**reate, **R**ead,**U**pdate, **D**elete)
- Listázás (Szűrés, Sorbarendezés és lapozás)
- offline adatokat szolgáltat
  sosem ad vissza IQueryable példányt
- adatmodell-eket szolgáltat
- LINQ-t csak itt használunk

- Kockázatok

### Service
- transzformáció adatmodell és a viewmodell között (Data mapping)
- Validálás a viewmodell képességeit meghaladóan
- Minden amit eddig nem említettünk

- Kockázatok


### Web UI
                                                              Web Browser
 MVC WebApp                                                   +-------------------+
+-----------------------------------------+                   |                   |
|                                         |                   |                   |
| +---------+  +----------+ +-------+     |                   |                   |
| |         |  |          | |       |     |                   |                   |
| | View    |  |Controller| | View  |     |                   |                   |
| |         |  |          | |       |     +------------------>|                   |
| | Model   |  |          | |       |     |   http/https      |                   | <-------- User
| |         |  |          | |       |     |<------------------+                   |
| |         |  |          | |       |     |                   |                   |
| |         |  |          | |       |     |                   |                   |
| |         |  |          | |       |     |                   |                   |
| +---------+  +----------+ +-------+     |                   |                   |
|                                         |                   +-------------------+
+-----------------------------------------+

- http kérés fogadása és válasz küldése
    MVC keretrendszer
- felhasználó azonosítása
    ASP.NET Core Identity
- jogosultság kezelés
    ASP.NET Core Identity
- bejövő adatok validálása
    MVC ViewModel

- Kockázatok
    - több alkalmazáson át elosztott bejelentkezés és jogosultságkezelés
    Identity Server
## Továbbiak
- docker containeres fejlesztési környezet
- visual studio code