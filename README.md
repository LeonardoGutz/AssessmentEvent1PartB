# AssessmentEvent1PartB
Revisar la version de Node instalada en tu equipo cmd / node -v

Crear la Base de datos Nodelogin.db

CREATE TABLE users (ID	INTEGER NOT NULL UNIQUE,User TEXT NOT NULL,Password TEXT NOT NULL,Email	TEXT,PRIMARY KEY("ID" AUTOINCREMENT));
INSERT INTO users VALUES (NULL,'DiegoAlcocer','123abc','dalcocer@esn.edu.mx');
INSERT INTO users VALUES (NULL,'SantiagoAllande','123abd','sallande@esn.edu.mx');
INSERT INTO users VALUES (NULL,'EmilioAquino','123abe','eaquino@esn.edu.mx');

npm init -y
npm install sqlite3

Creamos Main.js

const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database('Nodelogin', (err) => {
    if (err) {
      return console.error(err.message);
    }
    console.log('Congratulations you have connected with the database Nodelogin');
  });

  db.close((err) => {
    if (err) {
      return console.error(err.message);
    }
    console.log('Close the connections to the Nodelogin database');
  });
  
  en la terminal ejecutamos la consulta mediante el codigo node Main.js

Creamos CodeConnection.js

const sqlite3 = require('sqlite3').verbose();

// open database in memory
let Nodelogin = new sqlite3.Database(':memory:', (err) => {
  if (err) {
    return console.error(err.message);
  }
  console.log('Connecting to the database create using SQLite');
});

// close the database connection
Nodelogin.close((err) => {
  if (err) {
    return console.error(err.message);
  }
  console.log('Closing Nodelogin connection.');
});

en la terminal ejecutamos la consulta mediante el codigo node CodeConnection.js

Creamos la consulta CodeQueryALL.js

const sqlite3 = require('sqlite3').verbose();

// open the database
let AlumnosESN = new sqlite3.Database('AlumnosESN.db');

let sql = `SELECT * FROM user`;

AlumnosESN.all(sql, [], (err, rows) => {
  if (err) {
    throw err;
  }
  rows.forEach((row) => {
    console.log(row.ID,row.User,row.Password,row.Email);
  });
});

// close the database connection
AlumnosESN.close();

en la terminal ejecutamos la consulta mediante el codigo CodeQueryALL.js

Creamos la consulta CodeQueryGET.js

const sqlite3 = require('sqlite3').verbose();

// open the database
let Nodelogin = new sqlite3.Database('Nodelogin.db');

let sql = `SELECT ID,user FROM user WHERE ID = ?`;
let ID =3;

Nodelogin.get(sql, [ID], (err, row) => {
  if (err) {
    return console.error(err.message);
  }
  return row
   ? console.log(row.ID,row.User)
    : console.log('The user with $ {ID} cannot be found');
});

// close the database connection
Nodelogin.close();

en la terminal ejecutamos la consulta mediante el codigo CodeQueryGET.js





