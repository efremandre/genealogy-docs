## Минимальный контракт для MVP

### Health
#### GET /health
##### Response:
* plain text `Ok. Version 1.0.0`

### Auth
#### POST /api/auth/register
##### Request:
* email: string
* password: string

##### Response:
* user: { id: number, email: string }

#### POST /api/auth/login
##### Request:
* email: string
* password: string

##### Response:
* user: { id: number, email: string }
* token: string

### Current user
> Эти эндпоинты защищены. Передавайте заголовок `Authorization: Bearer <token>`.

#### GET /api/me
##### Response:
* user: {
  * id: number
  * email: string
  * firstName: string | null
  * lastName: string | null
  * createdAt: string (ISO timestamp)
  * updatedAt: string | null
  }

#### PATCH /api/me
##### Request:
* firstName?: string
* lastName?: string

##### Response:
* user: {
  * id: number
  * email: string
  * firstName: string | null
  * lastName: string | null
  * createdAt: string (ISO timestamp)
  * updatedAt: string | null
  }

### Tree
> Этот эндпоинт защищён. Передавайте заголовок `Authorization: Bearer <token>`.

#### GET /api/tree
##### Response:
* tree: {
  * id: number
  * name: string
  * rootPersonId: number | null
  }

### Persons
> Все следующие эндпоинты защищены. Передавайте заголовок `Authorization: Bearer <token>`.

#### GET /api/persons
##### Response:
* persons: Person[]

#### GET /api/person/{id}
##### Response:
* person: Person

#### POST /api/persons
##### Request:
* firstName: string
* lastName: string
* maidenName?: string
* middleName?: string
* gender?: string
* birthYear?: number
* birthMonth?: number
* birthDay?: number
* isAlive?: boolean
* deathYear?: number
* deathMonth?: number
* deathDay?: number
* fatherId?: number
* motherId?: number

##### Response:
* person: Person

#### PATCH /api/persons/{id}
##### Request:
* firstName?: string
* lastName?: string
* maidenName?: string
* middleName?: string
* gender?: string
* birthYear?: number
* birthMonth?: number
* birthDay?: number
* isAlive?: boolean
* deathYear?: number
* deathMonth?: number
* deathDay?: number
* fatherId?: number
* motherId?: number

##### Response:
* person: Person

#### DELETE /api/persons/{id}
##### Response:
* ok: true

### Person object
* id: number
* firstName: string
* lastName: string
* maidenName?: string
* middleName?: string
* gender?: string
* birthYear?: number
* birthMonth?: number
* birthDay?: number
* isAlive: boolean
* deathYear?: number
* deathMonth?: number
* deathDay?: number
* fatherId?: number
* motherId?: number

---
#### Зачем он нужен:

Это фиксирует, какие эндпоинты существуют и какие данные они принимают/возвращают.
Без этого ты начнёшь дергать API “как получится”, и фронт/бэк будут расходить.