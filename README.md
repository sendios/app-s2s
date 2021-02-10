#**Event Flow**

# 1) Request Event <br>

**POST** YOUR_API_URL <br>
body:

```json
{
  "user_id": <integer>,
  "project_id": <integer>,
  "type_id": <integer>,
  "key": <string>
}
```

description:

1) **user_id** - external id of user
2) **project_id** - internal id of project, we provide it to you
3) **type_id** - internal id of type, we provide it to you
4) **key** - unique key of happened event (we are expecting it from you on receiving event request)

# 2) Receive Event

**POST** https://app-push.sendios.io/api/v1/client/event <br>

header:
```Authorization: API_KEY```<br>

body:

```json
{
  "key": <string>,
  "data": <object>
}
```

description:

1) **API_KEY** - we provide it to you
2) **key** - unique key of happened event (we send it to you on the event requesting)
3) **data** - object that contains info required for push <br>
example:

```json
{
  "project_title": <string>,
  "users": [
    {
      "name" : <string>,
      "age" : <int>
    }
  ]
}
```

# Send Push (without Event)

**POST** https://app-push.sendios.io/api/v1/client/push <br>

header: ```Authorization: API_KEY```<br>

body:

```json
{
  "user_id": <int>,
  "project_id": <int>,
  "type_id": <int>,
  "data": <object>,
}
```

description:

1) **API_KEY** - we are providing it to you
2) **user_id** - id of user on your side
3) **project_id** - id of project on our side
4) **type_id** - id of type on our side
5) **data** - object that contains info required for push <br>
example:

```json
{
  "project_title": <string>,
  "users": [
    {
      "name" : <string>,
      "age" : <int>
    }
  ]
}
```
