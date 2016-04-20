#Working with CRUD using SQLAlcemy


###READ
* How to print a single column value of a queried document/row
```
var document_1=session.query(collection_name).first()
print document_1.column_name
```

* How to print a column of all records in a collection
```
var all_records = session.query(collection_name).all()
for record in all_records:
	print record.column_name
```

###READ
1. Find entry (i.e., filter_by() )
2. Reset Values
3. Add the variable to session (i.e., session.add(obj_to_change))
4. Commit the session to the database (i.e., session.commit() )

e.g., Update Rebecca's address in the Database
Two collections:
1. Employee collection: a. name, b.id
2. Address collection: a. street, b. zip, c. employee_id

Code:
```
#query rebecca document from Employee collection
rebecca= session.query(Employee).filter_by(name="Rebecca Allen").one()

#query the corresponding address using rebeccas's id
RebeccasAddress = session.query(Address).filter_by(employee_id = rebecca.id).one()

RebeccasAddress.street = "Richmond Ct"
RebeccasAddress.zip = "01189"

#Add updated document to session
session.add(RebeccasAddress)
#commit update in this session
session.commit()
```