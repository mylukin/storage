打开任意节点，执行集群初始化

```js
rs.initiate({
    "_id": "rs0",
    "members": [
        {
            "_id": 0,
            "host": "localhost:27017",
            "priority": 10
        },
        {
            "_id": 1,
            "host": "localhost:27018",
            "priority": 5
        },
        {
            "_id": 2,
            "host": "localhost:27019",
            "arbiterOnly": true
        },
    ]
})
```
