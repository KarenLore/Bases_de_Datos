# Trabajo de Aerolinea
Entregado por: Karen Lorena Cristancho Caceres

# Modelo Conceptual
Entidades y Atributos:
1.	Pais
•	id (PK)
•	nombre
2.	Ciudad
•	id (PK)
•	nombre
•	idpais (FK)
3.	Aeropuerto
•	id (PK)
•	nombre
•	idciudad (FK)
4.	Aerolinea
•	id (PK)
•	nombre
5.	Fabricante
•	id (PK)
•	nombre
6.	Estado
•	id (PK)
•	nombre
7.	Modelo
•	id (PK)
•	nombre
•	idfabricante (FK)
8.	Avion
•	nromatricula (PK)
•	capacidad
•	fechafabricacion
•	idestado (FK)
•	modelo
•	idaerolinea (FK)
•	idmodelo (FK)
9.	Trayecto
•	id (PK)
•	fechatrayecto
•	valor
•	ciudadOrigen (FK)
•	ciudadDestino (FK)
10.	Escala
•	id (PK)
•	idtrayecto (FK)
•	idavion (FK)
•	nnrovuelo
•	idaeropuerto (FK)
11.	Gates
•	id (PK)
•	nropuerta
•	idaeropuerto (FK)
12.	Roltripulacion
•	id (PK)
•	nombre
13.	Empleado
•	id (PK)
•	nombre
•	idrol (FK)
•	fechaingreso
•	idaerolinea (FK)
•	idaeropuerto (FK)
14.	Tripulacion
•	idempleado (FK)
•	idescala (FK)
15.	Revision
•	id (PK)
•	fecha
•	idavion (FK)
16.	RevEmpleado
•	idempleado (FK)
•	idrevision (FK)
17.	DetalleRevision
•	idrevision (FK)
•	descripcion
•	fecharev
•	idempleado (FK)
18.	Tipodocumento
•	id (PK)
•	nombre
19.	Clientes
•	id (PK)
•	edad
•	idtipodoc (FK)
20.	Reservaviaje
•	id (PK)
•	fecha
•	idtrayecto (FK)
21.	Tarifasvuelo
•	id (PK)
•	descripcion
•	valor
22.	DetalleReserva
•	id (PK)
•	idcliente (FK)
•	idtarifa (FK)
•	valortarifa
# Relaciones:
•	Un Pais tiene muchas Ciudades.
•	Una Ciudad tiene muchos Aeropuertos.
•	Una Aerolinea tiene muchos Aviones.
•	Un Fabricante tiene muchos Modelos.
•	Un Modelo puede estar asociado a muchos Aviones.
•	Un Trayecto tiene muchas Escalas.
•	Un Empleado puede estar en muchas Tripulaciones.
•	Un Cliente puede tener muchas Reservas.


# Modelo Lógico
1.	Tablas y Columnas:
## Pais
•	id VARCHAR(5) PRIMARY KEY
•	nombre VARCHAR(30)
## Ciudad
•	id VARCHAR(5) PRIMARY KEY
•	nombre VARCHAR(30)
•	idpais VARCHAR(5) (FK) REFERENCES Pais(id)
## Aeropuerto
•	id VARCHAR(5) PRIMARY KEY
•	nombre VARCHAR(50)
•	idciudad VARCHAR(5) (FK) REFERENCES Ciudad(id)
## Aerolinea
•	id INT AUTO_INCREMENT PRIMARY KEY
•	nombre VARCHAR(30)
## Fabricante
•	id INT AUTO_INCREMENT PRIMARY KEY
•	nombre VARCHAR(40)
## Estado
•	id INT AUTO_INCREMENT PRIMARY KEY
•	nombre VARCHAR(30)
## Modelo
•	id INT AUTO_INCREMENT PRIMARY KEY
•	nombre VARCHAR(30)
•	idfabricante INT (FK) REFERENCES Fabricante(id)
## Avion
•	nromatricula VARCHAR(30) UNIQUE PRIMARY KEY
•	capacidad INT
•	fechafabricacion DATE
•	idestado INT (FK) REFERENCES Estado(id)
•	modelo VARCHAR(30)
•	idaerolinea INT (FK) REFERENCES Aerolinea(id)
•	idmodelo INT (FK) REFERENCES Modelo(id)
## Trayecto
•	id INT AUTO_INCREMENT PRIMARY KEY
•	fechatrayecto DATE
•	valor DOUBLE
•	ciudadOrigen VARCHAR(5) (FK) REFERENCES Ciudad(id)
•	ciudadDestino VARCHAR(5) (FK) REFERENCES Ciudad(id)
## Escala
•	id INT AUTO_INCREMENT PRIMARY KEY
•	idtrayecto INT (FK) REFERENCES Trayecto(id)
•	idavion VARCHAR(30) (FK) REFERENCES Avion(nromatricula)
•	nnrovuelo INT
•	idaeropuerto VARCHAR(5) (FK) REFERENCES Aeropuerto(id)
## Gates
•	id INT PRIMARY KEY
•	nropuerta INT
•	idaeropuerto VARCHAR(5) (FK) REFERENCES Aeropuerto(id)
•	Roltripulacion
•	id INT PRIMARY KEY
•	nombre VARCHAR(30)
## Empleado
•	id INT PRIMARY KEY
•	nombre VARCHAR(50)
•	idrol INT (FK) REFERENCES Roltripulacion(id)
•	fechaingreso DATE
•	idaerolinea INT (FK) REFERENCES Aerolinea(id)
•	idaeropuerto VARCHAR(5) (FK) REFERENCES Aeropuerto(id)
## Tripulacion
•	idempleado INT (FK) REFERENCES Empleado(id)
•	idescala INT (FK) REFERENCES Escala(id)
•	Revision
•	id INT PRIMARY KEY
•	fecha DATE
•	idavion VARCHAR(30) (FK) REFERENCES Avion(nromatricula)
## RevEmpleado
•	idempleado INT (FK) REFERENCES Empleado(id)
•	idrevision INT (FK) REFERENCES Revision(id)
•	DetalleRevision
•	idrevision INT (FK) REFERENCES Revision(id)
•	descripcion TEXT
•	fecharev DATE
•	idempleado INT (FK) REFERENCES Empleado(id)
## Tipodocumento
•	id INT AUTO_INCREMENT PRIMARY KEY
•	nombre VARCHAR(30)
## Clientes
•	id VARCHAR(20) PRIMARY KEY
•	edad INT
•	idtipodoc INT (FK) REFERENCES Tipodocumento(id)
## Reservaviaje
•	id INT AUTO_INCREMENT PRIMARY KEY
•	fecha DATE
•	idtrayecto INT (FK) REFERENCES Trayecto(id)
## Tarifasvuelo
•	id INT PRIMARY KEY
•	descripcion VARCHAR(50)
•	valor DOUBLE
## DetalleReserva
•	id INT AUTO_INCREMENT PRIMARY KEY
•	idcliente VARCHAR(20) (FK) REFERENCES Clientes(id)
•	idtarifa INT (FK) REFERENCES Tarifasvuelo(id)
•	valortarifa DOUBLE

# Relaciones 
1.	Pais
•	Relación: Un Pais tiene muchas Ciudades.
•	Cardinalidad: 1 a N
2.	Ciudad
•	Relación: Una Ciudad pertenece a un Pais.
•	Cardinalidad: N a 1
•	Relación: Una Ciudad tiene muchos Aeropuertos.
•	Cardinalidad: 1 a N
3.	Aeropuerto
•	Relación: Un Aeropuerto pertenece a una Ciudad.
•	Cardinalidad: N a 1
4.	Aerolinea
•	Relación: Una Aerolinea tiene muchos Aviones.
•	Cardinalidad: 1 a N
5.	Fabricante
•	Relación: Un Fabricante tiene muchos Modelos.
•	Cardinalidad: 1 a N
6.	Modelo
•	Relación: Un Modelo pertenece a un Fabricante.
•	Cardinalidad: N a 1
•	Relación: Un Modelo puede estar asociado a muchos Aviones.
•	Cardinalidad: 1 a N
7.	Avion
•	Relación: Un Avion pertenece a una Aerolinea.
•	Cardinalidad: N a 1
•	Relación: Un Avion tiene un Estado.
•	Cardinalidad: N a 1
•	Relación: Un Avion tiene un Modelo.
•	Cardinalidad: N a 1
8.	Trayecto
•	Relación: Un Trayecto tiene muchas Escalas.
•	Cardinalidad: 1 a N
•	Relación: Un Trayecto tiene un ciudadOrigen y un ciudadDestino.
•	Cardinalidad: N a 1 (para ambas relaciones con Ciudad)
9.	Escala
•	Relación: Una Escala pertenece a un Trayecto.
•	Cardinalidad: N a 1
•	Relación: Una Escala tiene un Avion.
•	Cardinalidad: N a 1
•	Relación: Una Escala tiene un Aeropuerto.
•	Cardinalidad: N a 1
10.	Gates
•	Relación: Un Gate pertenece a un Aeropuerto.
•	Cardinalidad: N a 1
11.	Roltripulacion
•	Relación: Un Roltripulacion puede ser asignado a muchos Empleados.
•	Cardinalidad: 1 a N
12.	Empleado
•	Relación: Un Empleado tiene un Roltripulacion.
•	Cardinalidad: N a 1
•	Relación: Un Empleado puede pertenecer a una Aerolinea.
•	Cardinalidad: N a 1
•	Relación: Un Empleado puede trabajar en un Aeropuerto.
•	Cardinalidad: N a 1
•	Relación: Un Empleado puede estar en muchas Tripulaciones.
•	Cardinalidad: 1 a N
13.	Tripulacion
•	Relación: Una Tripulacion está formada por un Empleado.
•	Cardinalidad: N a 1
•	Relación: Una Tripulacion está asociada a una Escala.
•	Cardinalidad: N a 1
14.	Revision
•	Relación: Una Revision está asociada a un Avion.
•	Cardinalidad: N a 1
15.	RevEmpleado
•	Relación: Un RevEmpleado está asociado a un Empleado y a una Revision.
•	Cardinalidad: N a 1 (para ambas relaciones)
16.	DetalleRevision
•	Relación: Un DetalleRevision está asociado a una Revision

# Modelo Físico
CREATE TABLE Pais (
    ->   id VARCHAR(5) PRIMARY KEY,
    ->   nombre VARCHAR(30)
    -> );

CREATE TABLE Ciudad (
    ->   id VARCHAR(5) PRIMARY KEY,
    ->   nombre VARCHAR(30),
    ->   idpais VARCHAR(5),
    ->   FOREIGN KEY (idpais) REFERENCES Pais(id)
    -> );

CREATE TABLE Aeropuerto (
    ->   id VARCHAR(5) PRIMARY KEY,
    ->   nombre VARCHAR(50),
    ->   idciudad VARCHAR(5),
    ->   FOREIGN KEY (idciudad) REFERENCES Ciudad(id)
    -> );

CREATE TABLE Aerolinea (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   nombre VARCHAR(30)
    -> );

CREATE TABLE Fabricante (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   nombre VARCHAR(40)
    -> );

CREATE TABLE Estado (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   nombre VARCHAR(30)
    -> );

CREATE TABLE Modelo (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   nombre VARCHAR(30),
    ->   idfabricante INT,
    ->   FOREIGN KEY (idfabricante) REFERENCES Fabricante(id)
    -> );

CREATE TABLE Avion (
    ->   nromatricula VARCHAR(30) UNIQUE,
    ->   capacidad INT,
    ->   fechafabricacion DATE,
    ->   idestado INT,
    ->   modelo VARCHAR(30),
    ->   idaerolinea INT,
    ->   idmodelo INT,
    ->   PRIMARY KEY (nromatricula),
    ->   FOREIGN KEY (idestado) REFERENCES Estado(id),
    ->   FOREIGN KEY (idaerolinea) REFERENCES Aerolinea(id),
    ->   FOREIGN KEY (idmodelo) REFERENCES Modelo(id)
    -> );

CREATE TABLE Trayecto (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   fechatrayecto DATE,
    ->   valor DOUBLE,
    ->   ciudadOrigen VARCHAR(5),
    ->   ciudadDestino VARCHAR(5),
    ->   FOREIGN KEY (ciudadOrigen) REFERENCES Ciudad(id),
    ->   FOREIGN KEY (ciudadDestino) REFERENCES Ciudad(id)
    -> );

CREATE TABLE Escala (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   idtrayecto INT,
    ->   idavion VARCHAR(30),
    ->   nnrovuelo INT,
    ->   idaeropuerto VARCHAR(5),
    ->   FOREIGN KEY (idtrayecto) REFERENCES Trayecto(id),
    ->   FOREIGN KEY (idavion) REFERENCES Avion(nromatricula),
    ->   FOREIGN KEY (idaeropuerto) REFERENCES Aeropuerto(id)
    -> );

CREATE TABLE Gates (
    ->   id INT PRIMARY KEY,
    ->   nropuerta INT,
    ->   idaeropuerto VARCHAR(5),
    ->   FOREIGN KEY (idaeropuerto) REFERENCES Aeropuerto(id)
    -> );

CREATE TABLE Roltripulacion (
    ->   id INT PRIMARY KEY,
    ->   nombre VARCHAR(30)
    -> );

CREATE TABLE Empleado (
    ->   id INT PRIMARY KEY,
    ->   nombre VARCHAR(50),
    ->   idrol INT,
    ->   fechaingreso DATE,
    ->   idaerolinea INT,
    ->   idaeropuerto VARCHAR(5),
    ->   FOREIGN KEY (idrol) REFERENCES Roltripulacion(id),
    ->   FOREIGN KEY (idaerolinea) REFERENCES Aerolinea(id),
    ->   FOREIGN KEY (idaeropuerto) REFERENCES Aeropuerto(id)
    -> );



CREATE TABLE Tripulacion (
    ->   idempleado INT,
    ->   idescala INT,
    ->   FOREIGN KEY (idempleado) REFERENCES Empleado(id),
    ->   FOREIGN KEY (idescala) REFERENCES Escala(id)
    -> );

CREATE TABLE Revision (
    ->   id INT PRIMARY KEY,
    ->   fecha DATE,
    ->   idavion VARCHAR(30),
    ->   FOREIGN KEY (idavion) REFERENCES Avion(nromatricula)
    -> );

CREATE TABLE RevEmpleado (
    ->   idempleado INT,
    ->   idrevision INT,
    ->   FOREIGN KEY (idempleado) REFERENCES Empleado(id),
    ->   FOREIGN KEY (idrevision) REFERENCES Revision(id)
    -> );

CREATE TABLE DetalleRevision (
    ->   idrevision INT,
    ->   descripcion TEXT,
    ->   fecharev DATE,
    ->   idempleado INT,
    ->   FOREIGN KEY (idrevision) REFERENCES Revision(id),
    ->   FOREIGN KEY (idempleado) REFERENCES Empleado(id)
    -> );
CREATE TABLE Tipodocumento (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   nombre VARCHAR(30)
    -> );

CREATE TABLE Clientes (
    ->   id VARCHAR(20) PRIMARY KEY,
    ->   edad INT,
    ->   idtipodoc INT,
    ->   FOREIGN KEY (idtipodoc) REFERENCES Tipodocumento(id)
    -> );

CREATE TABLE Reservaviaje (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   fecha DATE,
    ->   idtrayecto INT,
    ->   FOREIGN KEY (idtrayecto) REFERENCES Trayecto(id)
    -> );

CREATE TABLE Tarifasvuelo (
    ->   id INT PRIMARY KEY,
    ->   descripcion VARCHAR(50),
    ->   valor DOUBLE
    -> );

CREATE TABLE DetalleReserva (
    ->   id INT AUTO_INCREMENT PRIMARY KEY,
    ->   idcliente VARCHAR(20),
    ->   idtarifa INT,
    ->   valor tarifa DOUBLE,
    ->   FOREIGN KEY (idcliente) REFERENCES Clientes(id),
    ->   FOREIGN KEY (idtarifa) REFERENCES Tarifasvuelo(id)
    -> );

### Imagen
![alt text](image.png)