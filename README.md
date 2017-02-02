# mongodb-query

## 1. Membuat database akademik
```
use academic
```
## 2. Menampilkan semua collection dan data dalam database
```
show dbs
```
## 3. Membuat atau mengaktifkan database
```
use academic
```
## 4. Membuat collection department
```
db.createCollection("department")
```
## 5. Membuat collection student
```
db.createCollection("student")
```
## 6. melihat struktur collection student
```
var col_list= db.student.findOne();
for (var col in col_list) { print (col) ; }
```
## 7. menginputkan 5  data ke dalam collection department
```
db.department.insert([
  {
    name:"9square",location:"Jakarta"
  },
  {
    name:"wealth",location:"Bandung"
  },
  {
    name:"poins",location:"surabaya"
  },
  {
    name:"square",location:"Kebayoran"
  },
  {
    name:"binus",location:"slipi"
  }])

```
## 8. menginputkan 3 data ke dalam collection student beserta reference ke department.
```
db.student.insert([
{
  studentId: "1",
  name: "rudi",
  address:"makasar",
  department: [
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a02"),
        "$db" : "academic"
    },
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a03"),
        "$db" : "academic"
    }
  ]
},
{
  studentId: "2",
  name: "andy",
  address: "surabaya",
  department: [
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a05"),
        "$db" : "academic"
    }
  ]
},
{
  studentId: "3",
  name: "budi",
  address: "bogor",
  department: [
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a02"),
        "$db" : "academic"
    },
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a06"),
        "$db" : "academic"
    }
  ]
}])
```
## 9. Melihat isi collection student
```
db.student.find({})
```
## 10. Menampilkan key name dan address dalam collectino student
```
db.student.find({}, { name: 1, address: 1})
```
## 11. Menampilkan key studentId, name, dan address dari data student yang mempunyai studentId tertentu.
```
db.student.find({studentId:"1"})
```
## 12. Menampilkan semua data student secara urut berdasarkan name dengan sort() secara ascending maupung descending.
```
/*asc | sort document ascending by studentId */
db.student.find().sort( { studentId: 1 } )
/* desc | sort document descending by studentId */
db.student.find().sort( { studentId: -1 } )
```
## 13. Menampilkan semua data department secara urut berdasarkan name secara scending maupun descending.
```
/* asc | sort document ascending by studentId */
db.department.find().sort( { name: 1 } )
/* desc | sort document descending by studentId */
db.department.find().sort( { name: -1 } )
```
## 14. Mencari data student dengan name
```
db.student.find({ name: "andy" })
```
