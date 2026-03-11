# ShareCabin Lite - Modular Challenge (Software Architecture)
This repository presents the proposed software architecture for ShareCabin Lite, a system designed to manage reservations and shared access to leisure properties such as cabins or cottages. The system enables users belonging to different families or groups to coordinate property usage through a shared reservation system while enforcing clear governance rules and access control.

## In Scope, Out of Scope & Future Scope

### In Scope:
- User registration and authentication
- Users belonging to multiple families/groups
- Creation and management of families
- Inviting and managing family members
- Family roles for managing membership and responsibilities
- Creation and management of properties
- Assigning ownership and co-ownership of properties to families
- Granting and revoking property access for families
- Creating reservations for entire properties using time ranges
- Modifying and cancelling reservations
- Preventing overlapping reservations for the same property
- Ensuring only authorised families can reserve properties
- Basic reporting (number of reservations and total reserved time grouped by property and family)
- Email notifications about reservations

### Out of Scope
The following features are intentionally excluded from ShareCabin Lite:
- Payments, billing, or cost settlement between members
- External authentication providers (SSO, OAuth, social login)
- Mobile applications
- Legal property registry integration
- Advanced fairness or scheduling optimisation algorithms


### Future Change Scenarios
The system is designed with future evolution and extensibility in mind. The architecture anticipates the addition of new features such as reservable sub-resources within properties (e.g., sauna, boat, or separate buildings), bookkeeping and cost balancing between families, maintenance task management, and configurable reservation policies. To support such evolution, the architecture emphasises modular separation of responsibilities and clearly defined boundaries between domain concepts.

## Domain Model and Ubiquitous Language
To avoid ambiguity and ensure consistent understanding, we have defined a set of domain terms. These terms form the ubiquitous language used throughout the architecture and documentation.


### Ubiquitous Language 
| Term | Description |
|------|-------------|
| User | A person with an individual account authenticated using email and password. A user may belong to multiple families. |
| Family / Group | A stable group of users who share responsibilities and access rights to properties. Families act as the primary authority unit in the system. |
| Membership | A relationship between a user and a family. Each membership defines the user’s role and permissions within that family. |
| Role | A permission level assigned to a user within a family (e.g., administrator or member). Each family must have at least one administrator. |
| Property | A shared resource such as a cabin or cottage that can be reserved. A property must have at least one owner family and may be shared with other families. |
| Ownership | A relationship where a family has administrative control over a property. Owner families can grant or revoke access to other families. |
| Access Right | Permission granted to a family allowing its members to reserve a property. Access is managed by the owner's family. |
| Reservation | A booking of a property for a specific time range. Reservations are created by users on behalf of their family and cannot overlap for the same property. |
| Report | Aggregated information about property usage, such as the number of reservations and total reserved time, grouped by family and property. |


## Bounded Contexts and Domain Decomposition
Based on the domain relationships, domain roles, and invariants defined in Section 2, the system is decomposed into bounded contexts that separate responsibilities according to ownership of rules and data. 

<p align="center">
  <img src="./Diagrams/Current Bounded Context.jpg" alt="System Architecture" width="500"/>
  <br>
  <em>Diagram: Bounded Context (Current Scope)</em>
</p>