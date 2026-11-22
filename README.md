import sqlite3

connection = sqlite3.connect('FruitBasket.sl3')
cur = connection.cursor()

cur.execute('CREATE TABLE IF NOT EXISTS Fruits (name TEXT, color TEXT);')
cur.execute('INSERT INTO Fruits (name, color) VALUES ("Яблуко", "Червоне")')
cur.execute('INSERT INTO Fruits (name, color) VALUES ("Банан", "Жовтий")')
cur.execute('INSERT INTO Fruits (name, color) VALUES ("Апельсин", "Помаранчевий")')
connection.commit()

cur.execute('UPDATE Fruits SET color="Зелене" WHERE name="Яблуко";')
connection.commit()

cur.execute('SELECT * FROM Fruits WHERE color="Жовтий";')
print(cur.fetchall())

cur.execute('SELECT * FROM Fruits;')
print(cur.fetchall())

connection.close()
