# Trabajo de vtaCiclas
Este proyecto se centra en la gestión de ventas y mantenimiento de bicicletas. Su objetivo es simplificar el proceso de compra y venta, así como garantizar un buen servicio al cliente.

# Modelo Conceptual
## Entidades y Atributos
1. **Clientes**
   - Identificador de cliente (PK)
   - Nombre
   - Apellido
   - Dirección
   - Teléfono
   - Correo Electrónico

2. **Proveedores**
   - ProveedorID (PK)
   - Nombre
   - Dirección
   - Teléfono
   - Correo Electrónico

3. **Bicicletas**
   - Identificación de bicicleta (PK)
   - Modelo
   - Marca
   - Tipo
   - Precio
   - CantidadEnStock
   - ProveedorID (FK)
   - RepuestoID (FK)

4. **Ventas**
   - VentaID (PK)
   - Fecha
   - ID de cliente (FK)
   - Total

5. **DetallesVenta**
   - Identificación de detalle (PK)
   - VentaID (FK)
   - Identificación de bicicleta (FK)
   - Cantidad
   - PrecioUnitario

6. **Compras**
   - CompraID (PK)
   - Fecha
   - ProveedorID (FK)
   - Total

7. **DetallesCompra**
   - DetalleCompraID (PK)
   - CompraID (FK)
   - Identificación de bicicleta (FK)
   - Cantidad
   - PrecioUnitario
   - RepuestoID (FK) 

8. **Repuestos**
   - ID de repuesto (PK)
   - Tipo
   - Marca
   - Precio
   - CantidadEnStock
   - BicicletaID (FK)

9. **Empleados**
   - Identificación de empleado (PK)
   - Nombre
   - Apellido
   - Puesto
   - Teléfono
   - Correo Electrónico

10. **Promociones**
    - ID de promoción (PK)
    - Descripción
    - Descuento
    - FechaInicio
    - FechaFin

11. **Reseñas**
    - ID de reseña (PK)
    - ID de cliente (FK)
    - Identificación de bicicleta (FK)
    - Calificación
    - Comentario
    - Fecha

12. **Mantenimiento**
    - ID de mantenimiento (PK)
    - Identificación de bicicleta (FK)
    - Fecha
    - Tipo de servicio
    - Costo
    - RepuestoID (FK)

## Relaciones
- **Clientes a Ventas**: Un cliente puede realizar muchas ventas (1:N).
- **Ventas a DetallesVenta**: Una venta puede tener muchos detalles (1:N).
- **Bicicletas a DetallesVenta**: Una bicicleta puede estar en muchos detalles de venta (1:N).
- **Proveedores de bicicletas**: Un proveedor puede suministrar muchas bicicletas (1:N).
- **Compras a DetallesCompra**: Una compra puede tener muchos detalles (1:N).
- **Bicicletas a DetallesCompra**: Una bicicleta puede estar en muchos detalles de compra (1:N).
- **Clientes a Reseñas**: Un cliente puede dejar muchas reseñas (1:N).
- **Bicicletas a Reseñas**: Una bicicleta puede tener muchas reseñas (1:N).
- **Bicicletas a Mantenimiento**: Una bicicleta puede tener muchos registros de mantenimiento (1:N).
- **Repuestos - Bicicletas**: Para especificar qué bicicletas usan ciertos repuestos.
- **Repuestos - DetallesCompraRepuestos**: Para registrar compras de repuestos.
- **Repuestos - DetallesMantenimiento**: Para registrar los repuestos usados en el mantenimiento de bicicletas.

---

# Modelo Lógico
## Entidades y Atributos
1. **Cliente**
   - Atributos:
     - ClienteID (Identificador único)
     - Nombre
     - Apellido
     - Dirección
     - Teléfono
     - Correo Electrónico

2. **Proveedor**
   - Atributos:
     - ProveedorID (Identificador único)
     - Nombre
     - Dirección
     - Teléfono
     - Correo Electrónico

3. **Bicicleta**
   - Atributos:
     - BicicletaID (Identificador único)
     - Modelo
     - Marca
     - Tipo
     - Precio
     - Cantidad en stock

4. **Venta**
   - Atributos:
     - VentaID (Identificador único)
     - Fecha
     - Total

5. **Detalle de Venta**
   - Atributos:
     - DetalleID (Identificador único)
     - Cantidad
     - Precio Unitario

6. **Compra**
   - Atributos:
     - CompraID (Identificador único)
     - Fecha
     - Total

7. **Detalle de compra**
   - Atributos:
     - DetalleCompraID (Identificador único)
     - Cantidad
     - Precio Unitario

8. **Repuesto**
   - Atributos:
     - RepuestoID (Identificador único)
     - Tipo
     - Marca
     - Precio
     - Cantidad en stock

9. **Empleado**
   - Atributos:
     - EmpleadoID (Identificador único)
     - Nombre
     - Apellido
     - Puesto
     - Teléfono
     - Correo Electrónico

10. **Promoción**
    - Atributos:
      - PromocionID (Identificador único)
      - Descripción
      - Descuento
      - Fecha de inicio
      - Fecha de fin

11. **Reseña**
    - Atributos:
      - ReseñaID (Identificador único)
      - Calificación
      - Comentario
      - Fecha

12. **Mantenimiento**
    - Atributos:
      - MantenimientoID (Identificador único)
      - Tipo de servicio
      - Costo
      - Fecha

## Relaciones
- **Cliente realiza Venta**: Un cliente puede realizar muchas ventas (1:N).
- **Venta tiene Detalle de Venta**: Una venta puede tener muchos detalles (1:N).
- **Bicicleta está en Detalle de Venta**: Una bicicleta puede estar en muchos detalles de venta (1:N).
- **Proveedor suministra bicicletas**: Un proveedor puede suministrar muchas bicicletas (1:N).
- **Compra tiene Detalle de Compra**: Una compra puede tener muchos detalles (1:N).
- **Bicicleta está en Detalle de Compra**: Una bicicleta puede estar en muchos detalles de compra (1:N).
- **Cliente deja Reseña**: Un cliente puede dejar muchas reseñas (1:N).
- **Bicicleta tiene Reseña**: Una bicicleta puede tener muchas reseñas (1:N).
- **Bicicleta tiene Mantenimiento**: Una bicicleta puede tener muchos registros de mantenimiento (1:N).
- **Repuestos - Bicicletas**: Para especificar qué bicicletas usan ciertos repuestos.
- **Repuestos - DetallesCompraRepuestos**: Para registrar compras de repuestos.
- **Repuestos - DetallesMantenimiento**: Para registrar los repuestos usados en el mantenimiento de bicicletas.
  
---

# MODELO FISICO

```sql
CREATE TABLE Clientes (
ClienteID INT PRIMARY KEY AUTO_INCREMENT,
Nombre VARCHAR(50) NOT NULL,
Apellido VARCHAR(50) NOT NULL,
Direccion VARCHAR(100),
Telefono VARCHAR(15),
CorreoElectronico VARCHAR(100) UNIQUE
);
```

```sql
CREATE TABLE Proveedores (
ProveedorID INT PRIMARY KEY AUTO_INCREMENT,
Nombre VARCHAR(50) NOT NULL,
Direccion VARCHAR(100),
Telefono VARCHAR(15),
CorreoElectronico VARCHAR(100) UNIQUE
);
```

```sql
CREATE TABLE Bicicletas (
BicicletaID INT PRIMARY KEY AUTO_INCREMENT,
Modelo VARCHAR(50) NOT NULL,
Marca VARCHAR(50) NOT NULL,
Tipo VARCHAR(30),
Precio DECIMAL(10, 2) NOT NULL,
CantidadEnStock INT NOT NULL,
ProveedorID INT,
FOREIGN KEY (ProveedorID) REFERENCES Proveedores(ProveedorID)
);
```

```sql
CREATE TABLE Ventas (
VentaID INT PRIMARY KEY AUTO_INCREMENT,
Fecha DATETIME NOT NULL,
ClienteID INT,
Total DECIMAL(10, 2) NOT NULL,
FOREIGN KEY (ClienteID) REFERENCES Clientes(ClienteID)
);
```

```sql
CREATE TABLE DetallesVenta (
DetalleID INT PRIMARY KEY AUTO_INCREMENT,
VentaID INT,
BicicletaID INT,
Cantidad INT NOT NULL,
PrecioUnitario DECIMAL(10, 2) NOT NULL,
FOREIGN KEY (VentaID) REFERENCES Ventas(VentaID),
FOREIGN KEY (BicicletaID) REFERENCES Bicicletas(BicicletaID)
);
```

```sql
CREATE TABLE Compras (
CompraID INT PRIMARY KEY AUTO_INCREMENT,
Fecha DATETIME NOT NULL,
ProveedorID INT,
Total DECIMAL(10, 2) NOT NULL,
FOREIGN KEY (ProveedorID) REFERENCES Proveedores(ProveedorID)
);
```

```sql
CREATE TABLE DetallesCompra (
DetalleCompraID INT PRIMARY KEY AUTO_INCREMENT,
CompraID INT,
BicicletaID INT,
Cantidad INT NOT NULL,
PrecioUnitario DECIMAL(10, 2) NOT NULL,
FOREIGN KEY (CompraID) REFERENCES Compras(CompraID),
FOREIGN KEY (BicicletaID) REFERENCES Bicicletas(BicicletaID)
);
```

```sql
CREATE TABLE Repuestos (
RepuestoID INT PRIMARY KEY AUTO_INCREMENT,
Tipo VARCHAR(50),
Marca VARCHAR(50),
Precio DECIMAL(10, 2) NOT NULL,
CantidadEnStock INT NOT NULL
);
```

```sql
CREATE TABLE Empleados (
EmpleadoID INT PRIMARY KEY AUTO_INCREMENT,
Nombre VARCHAR(50) NOT NULL,
Apellido VARCHAR(50) NOT NULL,
Puesto VARCHAR(50),
Telefono VARCHAR(15),
CorreoElectronico VARCHAR(100) UNIQUE
);
```

```sql
CREATE TABLE Promociones (
PromocionID INT PRIMARY KEY AUTO_INCREMENT,
Descripcion VARCHAR(100),
Descuento DECIMAL(5, 2),
FechaInicio DATETIME,
FechaFin DATETIME,
BicicletaID INT,
FOREIGN KEY (BicicletaID) REFERENCES Bicicletas(BicicletaID)
);
```

```sql
CREATE TABLE Reseñas (
ReseñaID INT PRIMARY KEY AUTO_INCREMENT,
ClienteID INT,
BicicletaID INT,
Calificacion INT CHECK (Calificacion BETWEEN 1 AND 5),
Comentario TEXT,
Fecha DATETIME NOT NULL,
FOREIGN KEY (ClienteID) REFERENCES Clientes(ClienteID),
FOREIGN KEY (BicicletaID) REFERENCES Bicicletas(BicicletaID)
);
```

```sql
CREATE TABLE Mantenimiento (
MantenimientoID INT PRIMARY KEY AUTO_INCREMENT,
BicicletaID INT,
Fecha DATETIME NOT NULL,
TipoServicio VARCHAR(100) NOT NULL,
Costo DECIMAL(10, 2) NOT NULL,
EmpleadoID INT,
FOREIGN KEY (BicicletaID) REFERENCES Bicicletas(BicicletaID),
FOREIGN KEY (EmpleadoID) REFERENCES Empleados(EmpleadoID)
);
```

# Inserción de datos

```sql
INSERT INTO Clientes (Nombre, Apellido, Direccion, Telefono, CorreoElectronico)
VALUES 
('Juan', 'Pérez', 'Calle Falsa 123', '5551234567', 'juan.perez@example.com'),
('Ana', 'López', 'Avenida Siempre Viva 456', '5557654321', 'ana.lopez@example.com');
```

```sql
INSERT INTO Proveedores (Nombre, Direccion, Telefono, CorreoElectronico)
VALUES 
('Proveedor A', 'Calle del Comercio 1', '5551122334', 'contacto@proveedora.com'),
('Proveedor B', 'Avenida de la Industria 2', '5554433221', 'contacto@proveedorb.com');
```

```sql
INSERT INTO Bicicletas (Modelo, Marca, Tipo, Precio, CantidadEnStock, ProveedorID)
VALUES 
('Mountain 200', 'BiciPro', 'Montaña', 450.00, 10, 1),
('City Rider', 'Urbike', 'Ciudad', 300.00, 20, 2);
```

```sql
INSERT INTO Ventas (Fecha, ClienteID, Total)
VALUES 
('2024-10-01 10:30:00', 1, 450.00),
('2024-10-02 14:45:00', 2, 600.00);
```

```sql
INSERT INTO DetallesVenta (VentaID, BicicletaID, Cantidad, PrecioUnitario)
VALUES 
(1, 1, 1, 450.00), 
(2, 2, 2, 300.00);
```

```sql
INSERT INTO Compras (Fecha, ProveedorID, Total)
VALUES 
('2024-10-03 09:00:00', 1, 900.00),
('2024-10-04 11:00:00', 2, 600.00);
```

```sql
INSERT INTO DetallesCompra (CompraID, BicicletaID, Cantidad, PrecioUnitario)
VALUES 
(1, 1, 5, 180.00), 
(2, 2, 10, 60.00);
```

```sql
INSERT INTO Repuestos (Tipo, Marca, Precio, CantidadEnStock)
VALUES 
('Llantas', 'BiciPro', 25.00, 50),
('Cadena', 'Urbike', 15.00, 30);
```

```sql
INSERT INTO Empleados (Nombre, Apellido, Puesto, Telefono, CorreoElectronico)
VALUES 
('Carlos', 'Gómez', 'Mecánico', '5559876543', 'carlos.gomez@example.com'),
('Laura', 'Martínez', 'Vendedora', '5556549873', 'laura.martinez@example.com');
```

```sql
INSERT INTO Promociones (Descripcion, Descuento, FechaInicio, FechaFin, BicicletaID)
VALUES 
('Descuento de verano', 15.00, '2024-06-01', '2024-08-31', 1),
('Promoción de fin de año', 20.00, '2024-12-01', '2024-12-31', 2);
```

```sql
INSERT INTO Reseñas (ClienteID, BicicletaID, Calificacion, Comentario, Fecha)
VALUES 
(1, 1, 5, 'Excelente bicicleta, muy resistente y cómoda.', '2024-10-01'),
(2, 2, 4, 'Buena calidad, aunque esperaba más accesorios.', '2024-10-02');
```

```sql
INSERT INTO Mantenimiento (BicicletaID, Fecha, TipoServicio, Costo, EmpleadoID)
VALUES 
(1, '2024-10-05 08:30:00', 'Cambio de llantas', 50.00, 1),
(2, '2024-10-06 09:00:00', 'Ajuste de frenos', 30.00, 2);
```

![cicla](https://github.com/user-attachments/assets/a414d75c-8e56-4351-8155-f1645a366b74)


### Consultas

```sql
- Stock disponible de bicicletas
SELECT Modelo, Marca, CantidadEnStock FROM Bicicletas WHERE CantidadEnStock > 0;
```
![image](https://github.com/user-attachments/assets/edaa3f61-7496-4c88-9938-13ae639c2693)

```sql
- Total de ventas por cliente
SELECT Clientes.Nombre, Clientes.Apellido, SUM(Ventas.Total) AS TotalVentas
FROM Ventas
JOIN Clientes ON Ventas.ClienteID = Clientes.ClienteID
GROUP BY Clientes.ClienteID;
```
![image](https://github.com/user-attachments/assets/9b653325-e778-498a-b630-ee34d06de55f)

```sql
- Modelo de bicicleta más vendido
SELECT Bicicletas.Modelo, SUM(DetallesVenta.Cantidad) AS TotalVendidas
FROM DetallesVenta
JOIN Bicicletas ON DetallesVenta.BicicletaID = Bicicletas.BicicletaID
GROUP BY Bicicletas.Modelo
ORDER BY TotalVendidas DESC
LIMIT 1;
```
![image](https://github.com/user-attachments/assets/b3e78550-342b-4c76-b376-8eb1a60a5ee1)

```sql
- Optimización y Rendimiento
CREATE INDEX idx_bicicletas_modelo ON Bicicletas(Modelo);
CREATE INDEX idx_clientes_nombre ON Clientes(Nombre);
```

```sql
- Integridad y Consistencia de Datos
DELIMITER //

CREATE TRIGGER check_stock
BEFORE INSERT ON DetallesVenta
FOR EACH ROW
BEGIN
    DECLARE stock_actual INT;
    
    - Se obtiene la cantidad en stock de la bicicleta que se está vendiendo
    SELECT CantidadEnStock INTO stock_actual 
    FROM Bicicletas 
    WHERE BicicletaID = NEW.BicicletaID;

    - Se verifica si la cantidad solicitada supera el stock disponible
    IF NEW.Cantidad > stock_actual THEN
        SIGNAL SQLSTATE '45000' 
        SET MESSAGE_TEXT = 'Stock insuficiente para esta venta';
    END IF;
END//

DELIMITER ;
```

- Entregado por: Karen Lorena Cristancho Caceres
