#IntermediateMango Database Query Results

## Dataset Info
- Database: Employee
- Collection: detail
- Total:  4 Employee
- Fields: _id, name, email, address, verified, gender, age

##  Demonstrate How To Use  $Exist ie Check Whether  Name  Exists In Document Or not and if Name Field Exists In Document Then  Fetches Only Those Records 

**Query:**
```javascript
db.details.find({ name: { $exists: true } })

```

### Output:
```json
[
  {
    "_id": 1,
    "name": "Abhi",
    "email": "Abhi@gmail.com",
    "address": {
      "City": [
        "Mysore",
        "Banaglore"
      ]
    },
    "verified": "false",
    "gender": "M",
    "age": 20
  },
  {
    "_id": 2,
    "name": "Pooja",
    "email": "Pooja@gmail.com",
    "address": {
      "City": [
        "Hubli",
        "Davangere"
      ]
    },
    "verified": "false",
    "gender": "F",
    "age": 18
  },
  {
    "_id": 3,
    "name": "Ryan",
    "email": "Ryan@gmail.com",
    "address": {
      "City": [
        "Mangalore",
        "Udupi"
      ]
    },
    "verified": "false",
    "gender": "M",
    "age": 21
  }
]
```
---

##  Demonstrate How To Use  $Exist Ie Check Whether  Name Does not Exists In Document ,Then  Fetches Only Those Records 

**Query:**
```javascript
db.details.find({ name: { $exists: false } })

```

### Output:
```json
[
  {
    "_id": 4,
    "regno": 210243,
    "gender": "M",
    "verified": "false",
    "age": 16
  }
]
```
---
##  Demonstrate How to use  $Exist To Check Whether  Name  Exists In Document  And  Age >18  

**Query:**
```javascript
db.details.find({
  name: { $exists: true },
  age: { $gt: 18 }
})

```

### Output:
```json
[
  {
    "_id": 1,
    "name": "Abhi",
    "email": "Abhi@gmail.com",
    "address": {
      "City": [
        "Mysore",
        "Banaglore"
      ]
    },
    "verified": "false",
    "gender": "M",
    "age": 20
  },
  {
    "_id": 3,
    "name": "Ryan",
    "email": "Ryan@gmail.com",
    "address": {
      "City": [
        "Mangalore",
        "Udupi"
      ]
    },
    "verified": "false",
    "gender": "M",
    "age": 21
  }
]
```
## Query to Find Documents Where a Nested Field Exists using Exist Operator 

**Query:**
```javascript
db.details.find({ "nestedField.subField": { $exists: true } })

```

### Output:
```json
[]
```
##  Query to find email exists in document ,if exists then  update field verified=true using updateMany 

**Query:**
```javascript
db.details.updateMany(
  { email: { $exists: true } },
  { $set: { verified: true } }
)

```
### Output:
```json
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 3,
  "modifiedCount": 3,
  "upsertedCount": 0
}
```
```

