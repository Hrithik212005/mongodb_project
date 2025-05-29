# BasicMango Database Query Results

## Dataset Info
- Database: student
- Collection: details
- Total: 3 students
- Fields: _id, name, grade, score

##  Query To Update Age =26 Whoose Name Is  Manasa 

**Query:**
```javascript
db.score.updateOne({name:"Manasa"},{$set:{age:36}})
```

### Output:
```json
{
 "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}
```

---

##  Query To  Increment Age By 1  Whose Name Is  Chandrasekar   

### Query:
```javascript
db.score.updateOne({ name: "Chandrasekar" },{ $inc: { age: 6 } })
```

### Output:
```json
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}
```


---

##   Demonstrate Example of Upsert in MongoDB 

### Query:
```javascript
db.score.updateOne({ name: "Anjali" },{ $set: { age: 25, grades: [] } },{ upsert: true })
```

### Output:
```json
{
  "acknowledged": true,
  "insertedId": {
    "$oid": "6837117411443bc75ec3564a"
  },
  "matchedCount": 0,
  "modifiedCount": 0,
  "upsertedCount": 1
}
```

---

##   Query Update Maths Score to 95 Using $[Elem] And Array Filters Of Student Name Deepak

### Query:
```javascript
db.score.updateOne(
  { name: "Deepak" },
  { $set: { "grades.$[elem].score": 99 } },
  { arrayFilters: [ { "elem.grade": "Maths" } ] }
)
```

### Output:
```json
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}
```