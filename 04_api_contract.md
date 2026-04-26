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

#### Users (Пользователи которые регистрируются в приложении и строят древо)
###### GET /api/me
##### Response:
* 

##### Request:
* id
* email
* first_name
* last_name

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
Authorization: Bearer <token>
##### Response:
* persons: Person[]

#### POST /api/persons
Authorization: Bearer <token>
##### Request:
* first_name
* last_name
* gender
* birth_year
* birth_month
* birth_day
* is_alive
* death_year
* death_month
* death_day
* father_id
* mother_id

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