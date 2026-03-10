## Минимальный контракт для MVP  

### Auth  
#### POST /api/auth/register  
##### Request:
* email
* password

##### Response:
* user: { id, email }

#### POST /api/auth/login
##### Request:
* email
* password

##### Response:
* user: { id, email }

#### POST /api/auth/logout
##### Response:
* ok: true

### Tree
#### GET /api/tree
##### Response:  
* tree: { id, title, rootPersonId }

#### PATCH /api/tree
##### Request (любое из):
* title
* rootPersonId

##### Response:
* tree

### Persons
#### GET /api/persons
##### Response:
* persons: Person[]

#### POST /api/persons
##### Request:
* firstName
* lastName
* gender?
* birthYear?
* fatherId?
* motherId?

##### Response:
* person

#### PATCH /api/persons/:id
##### Request:
* любые поля Person (кроме id, treeId)

##### Response:
* person

#### DELETE /api/persons/:id
##### Response:
* ok: true

### Relation
#### GET /api/relation/:personId
##### Query:
* rootId (если не используешь tree.rootPersonId)

##### Response:
* relationLabel: string

---
#### Зачем он нужен:

Это фиксирует, какие эндпоинты существуют и какие данные они принимают/возвращают.
Без этого ты начнёшь дергать API “как получится”, и фронт/бэк будут расходить