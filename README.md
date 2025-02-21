# Project

Ende: 27.3.2025, 8:00

Erstellen Sie eine Web Anwendung nach dem [Clean Architecture Muster](https://github.com/amantinband/clean-architecture/blob/main/src/CleanArchitecture.Application/Reminders/Queries/GetReminder/GetReminderQueryHandler.cs). 
Achten Sie dabei wenn möglich auf die Verwendung moderner Programmierparadigmen

IMPORTANT: 
- **Every week at least one Commit/Push.**
- Use Aspire, Postgres, ...
- Use the [CQRS pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs). 


## Domain modelling
Modellierung und dem Mapping eines OO-Models in eine relationale Datenbank.

**Start with Plant UML. (UK Notation)!**


## What should be included:
- Entities, at least 5.
- Inheritance.
- Different relationships (One to many, Inheritance, One to one?, ...)
- Enums 
- Value Objects
- Rich Types
- DB Constraints (not null, …)
- Generate test data with Bogus.
- Configuring a property as a concurrency token. Optimistic locking.
- ...
 
## Persistence Layer

- Work with services.
- Work with Repositories.

## Web (RESTful API)

- Use validation.
- Use simple Authentication + Authorization
- Implement a meaningful exception handling.
- Add pagination logic to your endpoints.
- Add query and path parameters.
- Use DTOs (with GUIDs -> no IDs in DTOs) and Commands.
- Use the correct HTTP Status Codes.
- Add query and path parameters.
- Write more complex business logic.

### Beispiel einer Servicedokumentation, die Resourcen eines OrderManagers:

| Ressource   |      URI      |  URI	Methode(n) |
|----------|:--------------|:------|
| Alle Bestellungen |  /orders | GET, POST |
| Einzelne Bestellung |	/orders/{id} |	GET, PUT, POST
| Stornierte Bestellungen |	/orders?state=cancelled |	GET
| Ausgelieferte Bestellungen |	/orders?state=shipped |	GET
|…		| |

Die Stornierungen wird hier als eigene Ressource abgebildet.

| Ressource   |      URI      |  URI	Methode(n) |
|----------|:--------------|:------|
| Stornierungen |	/cancellations/	| GET, POST
| Einzelne Stornierung |	/cancellations/{id}	| GET

Für die Benutzeroberfläche ist es sinnvoll einzelne Bestellpositionen zu bearbeiten, daher gibt es noch:

| Ressource   |      URI      |  URI	Methode(n) |
|----------|:--------------|:------|
| Bestellpositionen einer Bestellung |	/orders/{id}/items	| GET, POST
| Einzelne Bestellposition |	/orders/{id}/items/{itemId}	| GET, PUT, DELETE

Bauen Sie auch PATCH-Methoden in ihren REST API ein.

### PATCH request

The PUT and PATCH methods are used to update an existing resource. The difference between them is that PUT replaces the entire resource, while PATCH specifies only the changes, see: [MS Documentation](https://learn.microsoft.com/en-us/aspnet/core/web-api/jsonpatch).


## Testing

- XUnit Test (Domain, ...)
- Verwenden Sie bei einigen Test auch Mocking.
- Persistencetests, funktionieren die Queries?
- Siehe dazu auch: [Datenbanktests](https://learn.microsoft.com/en-us/ef/core/testing/choosing-a-testing-strategy), speziell auch Tests, die, die [DB ändern](https://learn.microsoft.com/en-us/ef/core/testing/testing-with-the-database#tests-which-modify-data).
- Tests der Web API (Endpoint Tests mit WebApplicationFactory). 
- Integrationstests.
  
  
