## Aggregate pipelines in mongodb


 `$match` , `$count` etc are operator in mongo
*  count active users - 
```mongo
[
  {
    $match: {
      isActive: true,
    },
  },
  { $count: "activeUsers" },
]
```

- get average age 
```
[
  {
    $group: {
      _id: null,
      averageAge: {
        $avg: "$age"
      }
    }
  }
]
```
- * group null will grouph them in one document and then we can apply accumulation

* list the top 2 favouriteFruit
```
[
  {
    $group: {
      _id: "$favoriteFruit",
      count: {
        $sum: 1,
      },
    },
  },
  {
    $sort: {
      count: -1,
    },
  },
  {
    $limit: 2,
  },
]
```
* find total number of males and females
```
[
  {
    $group: {
      _id: "$gender",
      
    
    count:{
    $sum:1
    }
    }
  }
]
```

