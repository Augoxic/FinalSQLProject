# FinalSQLProject
import mysql.connector

mydb = mysql.connector.connect(
    host="localhost",
    user="root",
    password="$$Augoxic12-"
)

print(mydb)

__ CONNECTION COMPLETED ( Will added the relevant code instead of mysql.connect host, user and password.


mycursor = mydb.cursor()
mycursor.execute("SHOW DATABASES")

for x in mycursor:
    print(x)

__ IGNORED DROP TABLE COMMAND FOR NOW SINCE DROP TABLE WILL DELETED ALL TABLES OR ONLY TABLE REVELANT TO THE PROJECT WITH DATA

mycursor = mydb.cursor()

mycursor.execute("SHOW TABLES")

for x in mycursor:
    print(x)
___ STEP 15
INSERTING DATA INTO Pet table
*INSERTS DATA
mycursor = mydb.cursor()

sql = "INSERT INTO pet ( name, owner, species, sex, birth, death)
val = [
    ('Fluffy', 'Harold', 'cat', 'f', '1993-02-04', None),
    ('Claws', 'Gwen', 'cat', 'm', '1993-02-04', None),
    ('Buffy', 'Harold', 'dog', 'f', '1993-02-04', None),
    ('Fang', 'Benny', 'dog', 'm', '1993-02-04', None),
    ('Bowser', 'Diane', 'dog', 'm', '1993-02-04', '1995-07-29'),
    ('Chirpy', 'Gwen', 'bird', 'f', '1993-02-04', None),
    ('Whistler', 'Gwen', 'cat', None, '1993-02-04', None),
    ('Slim', 'Benny', 'snake', 'm', '1993-02-04', None)
]


mycursor.executemany(sql, val)

mydb.commit()

print(mycursor.rowcount, "was inserted. ")
__step 18 SHOWING FEMALE DOGS

mycursor = mydb.cursor()

sql = "SELECT * FROM pet WHERE sex ='f'"

mycursor.execute(sql)

myresult = mycursor.fetchall()

for x in myresult:
   print(x)

__ GETS THE BIRTH OF THE PETS 


mycursor = mydb.cursor()

mycursor.execute("SELECT name, birth FROM pet")

myresult = mycursor.fetchall()

for x in myresult:
   print(x)

___ HOW MANY EACH PETS EACH OWNER HAS

mycursor = mydb.cursor()

sql = "SELECT owner, COUNT(*) FROM pet GROUP by owner"

mycursor.execute(sql)

myresult - mycursor.fetchall()

for x in myresult:
  print(x)

__NAME, BIRTH, MONTH ( BIRTH) STEP 25

mysql> SELECT name, birth, MONTH(birth) FROM pet;
