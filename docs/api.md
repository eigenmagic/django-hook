# API

Both webhooks (`api/webhooks`) and events (`api/events`) are available through RESTful API supporting CRUD operations
following standard conventions.

Use the API console and help for the complete API documentation.

| `http://localhost:8000/api-help/` | `http://localhost:8000/api/` |
| --- | --- |
| ![API Help](screenshots/api-help.png) |  ![API Console](screenshots/api-console.png) |


> NOTE: API endpoint URLs uses the default Django
>[trailing slash is required convention](https://docs.djangoproject.com/en/3.0/ref/settings/#append-slash).
>
>  `http://127.0.0.1:8000/api/webhooks/`: Correct usage
>
>  `http://127.0.0.1:8000/api/webhooks`: Will return `HTTP/1.1 301 Moved Permanently`


```shell script
$ curl  -s http://127.0.0.1:8000/api/webhooks/ | python -m json.tool
{
    "count": 3,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 2,
            "name": "Alerts",
            "url": "http://localhost:8888/alerts",
            "events": [
                1,
                3
            ]
        },
        {
            "id": 3,
            "name": "Auditing",
            "url": "http://localhost:8888/audit",
            "events": [
                3
            ]
        },
        {
            "id": 1,
            "name": "Logging",
            "url": "http://localhost:8888/logging",
            "events": [
                1,
                2,
                3,
                4
            ]
        }
    ]
}
```

```shell script
$ curl  -s http://127.0.0.1:8000/api/events/ | python -m json.tool
{
    "count": 5,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 1,
            "name": "create"
        },
        {
            "id": 3,
            "name": "delete"
        },
        {
            "id": 4,
            "name": "read"
        },
        {
            "id": 10,
            "name": "test"
        },
        {
            "id": 2,
            "name": "update"
        }
    ]
}
