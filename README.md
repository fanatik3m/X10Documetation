
# RESTful API documentation for x10game


## Telegram profiles
#### Listing telegram profiles

<details>
 <summary><code>GET</code> <code>api/v1/telegram_profiles/</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | -|  -| --   | -  |


##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `[{"telegram_id": integer, "first_name": string, "last_name": string, "username": string, "phone_number": string, "avatar": string}]`                                |
>| `400x`         | `application/json`                | `{"detail": string}`                                                                                      |

</details>

------------------------------------------------------------------------------------------

#### Getting telegram profile by id

<details>
 <summary><code>GET</code>  <code>api/v1/telegram_profiles/</code> <code><b>{id}/</b></code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer   | id of telegram profile  |


##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"telegram_id": integer, "first_name": string, "last_name": string, "username": string, "phone_number": string, "avatar": string}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                   |

</details>

------------------------------------------------------------------------------------------

#### Updating telegram profiles

<details>
 <summary><code>PUT</code>  <code>api/v1/telegram_profiles/</code> <code><b>{id}/</b></code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer   | id of telegram profile  |
> | first_name|  request_body| string   | first name of telegram profile  |
> | last_name|  request_body| string   | last name of telegram profile  |
> |phone_number| request_body| string  | phone number of telegram profile
> | avatar|  request_body| string   | avatar of telegram profile  |


##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"telegram_id": integer, "first_name": string, "last_name": string, "username": string, "phone_number": string, "avatar": string}`                                |
>| `400x`         | `application/json`                | `{"detail": string}`                                                               |

</details>

------------------------------------------------------------------------------------------
## Meetings
#### Listing meetings

<details>
 <summary><code>GET</code>  <code>api/v1/meetings/</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | -|  -| -| -|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"count": integer, "next": string, "previous": string, "results": [{"id": integer, "photo": string, "name_field": string, "type_field": string, "date_time": data, "city": string, "place": string, "description": string, "expired": boolean, "organizer": integer, "winner": integer}]}`                                |
>| `400x`         | `application/json`                | `{"detail": string}`                                                                   |

</details>

------------------------------------------------------------------------------------------

#### Getting meeting by id

<details>
 <summary><code>GET</code>  <code>api/v1/meetings/</code> <code><b>{id}/</b></code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer| id of meeting|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `IF GAME {"game": {"id": integer, "photo": string, "name_field": string, "type_field": string, "date_time": data, "city": string, "place": string, "description": string, "expired": boolean, "organizer": integer, "winner": integer}, "available": boolean} ELSE "id": integer, "photo": string, "name_field": string, "type_field": string, "date_time": data, "city": string, "place": string, "description": string, "expired": boolean, "organizer": integer, "winner": integer}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                    |

</details>

------------------------------------------------------------------------------------------

#### Searching meetings

<details>
 <summary><code>GET</code>  <code>api/v1/meetings/search/</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | query|  query string| string| whatever user types in search field|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `[{"id": integer, "photo": string, "name_field": string, "type_field": string, "date_time": data, "city": string, "place": string, "description": string, "expired": boolean, "organizer": integer, "winner": integer}]`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                 |

</details>

------------------------------------------------------------------------------------------

#### Getting meeting invite link by id

<details>
 <summary><code>GET</code>  <code>api/v1/meetings/</code> <code><b>{id}/</b></code> <code>invite_link/</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer| id of meeting|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"invite_link": string, "qr_code": "string"}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                               |

</details>

------------------------------------------------------------------------------------------

#### Listing games with pagination

<details>
 <summary><code>GET</code>  <code>api/v1/meetings/games/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | page|  query string| integer| page to list |



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `[{"string": {"id": integer, "photo": string, "name_field": string, "type_field": string, "date_time": data, "city": string, "place": string, "description": string, "expired": boolean, "organizer": integer, "winner": integer}, "available": boolean}]`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                    |

</details>

------------------------------------------------------------------------------------------

#### Listing events with pagination

<details>
 <summary><code>GET</code>  <code>api/v1/meetings/events/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | page|  query string| integer| page to list|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"id": integer, "photo": string, "name_field": string, "type_field": string, "date_time": data, "city": string, "place": string, "description": string, "expired": boolean, "organizer": integer, "winner": integer}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                |

</details>

------------------------------------------------------------------------------------------
## Paricipants profiles
#### Listing participants profiles 

<details>
 <summary><code>GET</code>  <code>api/v1/participants_profiles/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | -|  -| -| -|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"count": integer, "next": string, "previous": string, "results": [{"telegram_id": integer, "events_visited": integer, "games_visited": integer, "meetings_visited": integer, "wins": integer, "earned_coins": integer, "companies_bought": integer, "cards": array of integer}]}`                                |
>| `400x`         | `application/json`                | `{"detail": string}`                                                                       |

</details>

------------------------------------------------------------------------------------------

#### Getting participant profile by id

<details>
 <summary><code>GET</code>  <code>api/v1/participants_profiles/</code> <code><b>{id/}</b></code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer| id of participant profiles|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"telegram_id": integer, "events_visited": integer, "games_visited": integer, "meetings_visited": integer, "wins": integer, "earned_coins": integer, "companies_bought": integer, "cards": array of integer}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                  |

</details>

------------------------------------------------------------------------------------------

#### Searching participants profiles

<details>
 <summary><code>GET</code>  <code>api/v1/participants_profiles/search/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | query|  query string| string| whatever user types in search field|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"telegram_id": integer, "skills": string}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                           |

</details>

------------------------------------------------------------------------------------------

#### Listing participants profiles rating

<details>
 <summary><code>GET</code>  <code>api/v1/participants_profiles/rating/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | page|  query string| integer| page to list|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"name": {"telegram_id": integer, "events_visited": integer, "games_visited": integer, "meetings_visited": integer, "wins": integer, "earned_coins": integer, "companies_bought": integer, "cards": array of integer}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                      |

</details>

------------------------------------------------------------------------------------------

## Regular profiles
#### Listing regular profiles

<details>
 <summary><code>GET</code>  <code>api/v1/regular_profiles/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | -|  -| -| -|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `[{"telegram_id": integer, "name_field": string, "biography": string, "needs": string, "skills": string, "avatar": string, "contacts": json, "contacts_allowed": array of integer}]`                                |
>| `400x`         | `application/json`                | `{"detail": string}`          

</details>

------------------------------------------------------------------------------------------

#### Geeting regular profile by id

<details>
 <summary><code>GET</code>  <code>api/v1/regular_profiles/</code> <code><b>{id}/</b></code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer| telegram id of regular profile|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"regular_profile": {"telegram_id": integer, "name_field": string, "biography": string, "needs": string, "skills": string, "avatar": string, "contacts": json, "contacts_allowed": array of integer}, "contacts_allowed": boolean}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                    |

</details>

------------------------------------------------------------------------------------------

#### Geeting regular profile's contacts by id

<details>
 <summary><code>GET</code>  <code>/api/v1/regular_profiles/</code> <code><b>{id}/</b></code> <code>contacts/</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer| telegram id of regular profile|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"key": string}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`          

</details>

------------------------------------------------------------------------------------------

#### Updating regular profile by id

<details>
 <summary><code>PUT</code>  <code>api/v1/regular_profiles/</code> <code><b>{id}/</b></code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer| telegram id of regular profile|
> | name_field|  request body| string| name of regular profile|
> | biography|  request body| string| biography of regular profile|
> | needs|  request body| string| needs of regular profile|
> | skills|  request body| string| skills of regular profile|
> | avatar|  request body| string| avatar of regular profile|
> | contacts|  request body| json| contacts of regular profile|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"telegram_id": integer, "name_field": string, "biography": string, "needs": string, "skills": string, "avatar": string, "contacts": json, "contacts_allowed": array of integer}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                                                                                  

</details>

------------------------------------------------------------------------------------------

## Session-based Auth
#### Authorize user throug telegram webapp

<details>
 <summary><code>POST</code>  <code>auth/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | init_data|  request body| string| special data which can be got from javascript code when entering webapp|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"telegram_id": integer}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                            |
> | `401`         | `application/json`         | {"detail": "Не удалось авторизовать пользователя"}                                                                |

</details>

------------------------------------------------------------------------------------------

#### Get current user

<details>
 <summary><code>GET</code>  <code>auth/</code> </summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | -|  -| -| -|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"user": {"telegram_id": integer, "first_name": string, "last_name": string, "username": string, "phone_number": string, "avatar": string}}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                            |


</details>

------------------------------------------------------------------------------------------
## Others
#### Change participant's stats

<details>
 <summary><code>PUT</code>  <code>api/v1/stats/praticipants_profiles/</code> <code><b>{participant_id}/</b></code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | participant_id|  path| integer| id of participant profile|
> | game_id|  query| integer| id of cerain game|
> | win|  request_body| bool| if participant won the game|
> | earned_coins|  request_body| integer| how many coins did participant earn during the game|
> | companies_bought|  request_body| integer| how many companies did participant buy during the game|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"participant": {"telegram_id": integer, "events_visited": integer, "games_visited": integer, "meetings_visited": integer, "wins": integer, "earned_coins": integer, "companies_bought": integer, "cards": array of integer}}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                            |

</details>

------------------------------------------------------------------------------------------

#### Change organizer's stats

<details>
 <summary><code>PUT</code>  <code>api/v1/stats/organizers_profiles/</code> <code><b>{id}/</b></code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | organizer_id|  path| integer| id of organizer|
> | engager_score|  request body| integer (1 - 10)| score on how good did organizer interest participants during the game|
> | organizer_score|  request body| integer (1 - 10)| score on how good did organizer organize the game|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"organizer": {"telegram_id": integer, "master_index": decimal, "engager_index": decimal, "organizer_index": decimal, "events_organized": integer, "games_organized": integer, "meetings_organized": integer}}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                            |

</details>

------------------------------------------------------------------------------------------

#### List game's info differently for any role of game

<details>
 <summary><code>GET</code>  <code>api/v1/games/participants_profiles/</code> <code><b>{id}/</b></code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | id|  path| integer| id of the game|



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | if game expired `{"organizer": {"telegram_id": integer, "master_index": decimal, "engager_index": decimal, "organizer_index": decimal, "events_organized": integer, "games_organized": integer, "meetings_organized": integer}, "winner_personal_data": {"telegram_id": integer, "first_name": string, "last_name": string, "username": string, "phone_number": string, "avatar": string}, "winner": {"telegram_id": integer, "events_visited": integer, "games_visited": integer, "meetings_visited": integer, "wins": integer, "earned_coins": integer, "companies_bought": integer, "cards": array of integer}, "participants": [{"telegram_id": integer, "events_visited": integer, "games_visited": integer, "meetings_visited": integer, "wins": integer, "earned_coins": integer, "companies_bought": integer, "cards": array of integer}]}`                                |
>  | `200`         | `application/json`        | if game not expired and user is organizer`{"participants": [{"telegram_id": integer, "events_visited": integer, "games_visited": integer, "meetings_visited": integer, "wins": integer, "earned_coins": integer, "companies_bought": integer, "cards": array of integer}]}`                                |
>   | `200`         | `application/json`        |if game not expired and user is participant `{"organizer_personal_data": {"telegram_id": integer, "first_name": string, "last_name": string, "username": string, "phone_number": string, "avatar": string}, "organizer": {"telegram_id": integer, "master_index": decimal, "engager_index": decimal, "organizer_index": decimal, "events_organized": integer, "games_organized": integer, "meetings_organized": integer}}`                                |
> | `400`         | `application/json`                | `{"code":"400","message":"Bad Request"}`                            |

</details>

------------------------------------------------------------------------------------------

#### Finish game by organizer

<details>
 <summary><code>PUT</code>  <code>api/v1/games/praticipants_profiles/</code> <code><b>{game_id}/</b></code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | game_id|  path| integer| id of certain game|
> | participant_id|  request body| integer| winner of the game|




##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | `{"game": {"id": integer, "photo": string, "name_field": string, "type_field": string, "date_time": data, "city": string, "place": string, "description": string, "expired": boolean, "organizer": integer, "winner": integer}}`                                |
> | `400x`         | `application/json`                | `{"detail": string}`                            |

</details>

------------------------------------------------------------------------------------------
