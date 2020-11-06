## Replace single qoute to double qoutes using git bash
```sed "s/'/\"/g" file.json > output.json```

# Python -> Json to database
```python
import pymysql, os, json, pprint

# read JSON file which is in the next parent folder
# file = "MyAll.json00"
# f = open(file, 'r')
# s = f.read().strip()
# json_obj = json.loads((eval(s)))



file = "MyS04.json"
json_data=open(file).read()
json_obj = json.loads(json_data)


# do validation and checks before insert
def validate_string(val):
   if val != None:
        if type(val) is int:
            #for x in val:
            #   print(x)
            return str(val).encode('utf-8')
        else:
            return val


# connect to MySQL
con = pymysql.connect(host = 'localhost',user = 'root',passwd = '',db = 'tlg')
cursor = con.cursor()


# parse json data to SQL insert
for i, item in enumerate(json_obj):
    id = validate_string(item.get("id", None))
    username = validate_string(item.get("username", None))
    phone = validate_string(item.get("phone", None))

    cursor.execute("INSERT INTO user (tlg_id, username, phone) VALUES (%s,	%s,	%s)", (id,	username,	phone))
con.commit()
con.close()
```
