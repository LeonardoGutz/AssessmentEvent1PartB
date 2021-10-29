# AssessmentEvent1PartB
Revisar la version de Node instalada en tu equipo cmd / node -v

Crear la Base de datos Nodelogin.db

CREATE TABLE users (ID	INTEGER NOT NULL UNIQUE,User TEXT NOT NULL,Password TEXT NOT NULL,Email	TEXT,PRIMARY KEY("ID" AUTOINCREMENT));
INSERT INTO users VALUES (NULL,'DiegoAlcocer','123abc','dalcocer@esn.edu.mx');
INSERT INTO users VALUES (NULL,'SantiagoAllande','123abd','sallande@esn.edu.mx');
INSERT INTO users VALUES (NULL,'EmilioAquino','123abe','eaquino@esn.edu.mx');


CREATE TABLE users(ID INTEGER PRIMARY KEY AUTOINCREMENT,nombre TEXT NOT NULL,correo TEXT NOT NULL);

CREATE TABLE pacientes(cedula TEXT PRIMARY KEY,nombre TEXT NOT NULL,correo TEXT NOT NULL);


CREATE TABLE citas(num INTEGER PRIMARY KEY AUTOINCREMENT, medico TEXT NOT NULL, paciente TEXT NOT NULL, precio INT NOT NULL,
FOREIGN KEY (medico) REFERENCES medicos (cedula),FOREIGN KEY (paciente) REFERENCES pacientes (cedula));


INSERT INTO medicos VALUES ('123456','Alfredo Aboumrad','5510111213');
INSERT INTO medicos VALUES ('123457','Diego Aguilar','5510111214');
INSERT INTO medicos VALUES ('123458','Kayla Alcalde','5510111215');
INSERT INTO pacientes VALUES ('123471','Sofia Ugarte','sofiau@mail.com');
INSERT INTO pacientes VALUES ('123472','Miranda Uribe','mirandau@mail.com');



INSERT INTO citas VALUES (NULL,'123456','123471',1700);
INSERT INTO citas VALUES (NULL,'123457','123472',2200);
INSERT INTO citas VALUES (NULL,'123456','123472',2300);


SELECT citas.num,citas.medico,medicos.nombre,medicos.telefono,citas.paciente,pacientes.nombre,pacientes.correo,citas.precio
FROM citas,medicos,pacientes
WHERE citas.medico=medicos.cedula
AND citas.paciente=pacientes.cedula;
