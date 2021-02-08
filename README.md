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

1) **user_id** - id of user on your side
2) **project_id** - id of project on our side
3) **type_id** - id of type on our side
4) **key** - unique key of happened event (we will expect it from you on receive event request)

# 2) Receive Event

**POST** https://app-push.mailfire.io/api/v1/client-app-push/event <br>
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

1) **API_KEY** - we are providing it to you
2) **key** - unique key of happened event (we send it to you on the event requesting)
3) **data** - object that contains info required for push (user data/links/etc.)

#Send Push (without Event)

**POST** https://app-push.mailfire.io/api/v1/client-app-push <br>
header:
```Authorization: API_KEY```<br>
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
5) **data** - object that contains info required for push (user data/links/etc.)
