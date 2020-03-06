import sqlite3

class Database:

    def __init__(self,dataa):

        self.con = sqlite3.connect(dataa)
        self.cur = self.con.cursor()
        self.cur.execute('CREATE TABLE IF NOT EXISTS info'
                '(id INTEGER PRIMARY KEY,Name text,Last_name text,Age INTIGER,Id_number INTEGER )')
        self.con.commit()

    def show(self):


        #self.con = sqlite3.connect('book2.db')
        #self.cur = con.cursor()
        self.cur.execute('SELECT * FROM info')
        result = self.cur.fetchall()
        return result
        self.con.commit()

    def insert(self, Name, Last_name, Age, Id_number):


        #self.con = sqlite3.connect('book2.db')
        #self.cur = con.cursor()
        self.cur.execute("INSERT INTO info VALUES (null,?,?,?,?)"
                         ,(Name, Last_name, Age, Id_number))
        self.con.commit()

    def search(self,Name,Last_name,Age,Id_number):


        #con = sqlite3.connect('final.book2.db')
        #cur = con.cursor()
        self.cur.execute('SELECT * FROM info WHERE Name = ?,Last_name = ?,Age = ?,Id_number =?',(Name,Last_name,Age,Id_number))
        reply = self.cur.fetchall()
        return reply
        self.commit()
        #con.close()

    def update(self,id,Name,Last_name,Age,Id_number) :


        #self.con = sqlite3.connect('final.book2.db')
        #self.cur = con.cursor()
        self.cur.execute('UPDATE info SET Name=?,Last_name=?,Age=?,Id_number=? WHERE id=?',(Name,Last_name,Age,Id_number,id))
        self.con.commit()

    def remove(self,id):

        self.con.execute('DELETE FROM info  WHERE id=?',(id))
        self.con.commit()



