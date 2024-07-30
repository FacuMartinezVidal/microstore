# Sistema de Gestión de Tienda en Línea con Microservicios

Este proyecto implementa un sistema de tienda en línea utilizando una arquitectura de microservicios. Cada microservicio es responsable de una función específica del negocio y puede ser desarrollado, desplegado y escalado de forma independiente.

## Estructura del Proyecto

El sistema está compuesto por los siguientes microservicios:

1. Servicio de Catálogo de Productos
2. Servicio de Carrito de Compras
3. Servicio de Gestión de Usuarios
4. Servicio de Procesamiento de Pedidos
5. Servicio de Pagos
6. Servicio de Notificaciones
7. Servicio de Reseñas y Calificaciones

## Detalles de los Microservicios

### 1. Servicio de Catálogo de Productos

**Base de datos:** MongoDB (NoSQL)

**Estructura de datos:**
```json
{
  "id": "String",
  "nombre": "String",
  "descripcion": "String",
  "precio": "Number",
  "categoria": "String",
  "stock": "Number",
  "imagenes": ["String"]
}
```

### 2. Servicio de Carrito de Compras

**Base de datos:** Redis (Clave-valor)

**Estructura de datos:**
```json
{
  "id": "String",
  "usuarioId": "String",
  "productos": [
    {
      "productoId": "String",
      "cantidad": "Number",
      "precioUnitario": "Number"
    }
  ],
  "total": "Number"
}
```

### 3. Servicio de Gestión de Usuarios

**Base de datos:** PostgreSQL (Relacional)

**Estructura de datos:**
```sql
CREATE TABLE usuarios (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  nombre VARCHAR(100),
  apellido VARCHAR(100),
  direccion TEXT,
  fecha_registro TIMESTAMP
);
```

### 4. Servicio de Procesamiento de Pedidos

**Base de datos:** MySQL (Relacional)

**Estructura de datos:**
```sql
CREATE TABLE pedidos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  usuario_id INT,
  fecha_pedido TIMESTAMP,
  estado ENUM('pendiente', 'procesando', 'enviado', 'entregado'),
  total DECIMAL(10, 2)
);

CREATE TABLE items_pedido (
  id INT AUTO_INCREMENT PRIMARY KEY,
  pedido_id INT,
  producto_id VARCHAR(255),
  cantidad INT,
  precio_unitario DECIMAL(10, 2)
);
```

### 5. Servicio de Pagos

**Base de datos:** PostgreSQL (Relacional)

**Estructura de datos:**
```sql
CREATE TABLE transacciones (
  id SERIAL PRIMARY KEY,
  pedido_id INT,
  monto DECIMAL(10, 2),
  estado VARCHAR(50),
  metodo_pago VARCHAR(50),
  fecha_transaccion TIMESTAMP
);
```

### 6. Servicio de Notificaciones

**Base de datos:** MongoDB (NoSQL)

**Estructura de datos:**
```json
{
  "id": "String",
  "usuario_id": "String",
  "tipo": "String",
  "contenido": "String",
  "fecha_envio": "Date",
  "estado": "String"
}
```

### 7. Servicio de Reseñas y Calificaciones

**Base de datos:** MongoDB (NoSQL)

**Estructura de datos:**
```json
{
  "id": "String",
  "producto_id": "String",
  "usuario_id": "String",
  "calificacion": "Number",
  "comentario": "String",
  "fecha": "Date"
}
```

## Tecnologías Utilizadas

- **Lenguajes de programación:** A definir (e.g., Java, Python, Node.js)
- **Frameworks:** A definir (e.g., Spring Boot, Django, Express)
- **Bases de datos:** MongoDB, Redis, PostgreSQL, MySQL
- **Comunicación entre servicios:** REST APIs, gRPC, o mensajería asíncrona (a definir)

## Despliegue

Cada microservicio se despliega de forma independiente. Se recomienda el uso de contenedores Docker y orquestación con Kubernetes para facilitar el despliegue y la escalabilidad.

## Próximos Pasos

1. Definir las tecnologías específicas para cada microservicio
2. Implementar los servicios
3. Establecer la comunicación entre servicios
4. Configurar el despliegue y la infraestructura
5. Implementar pruebas unitarias e integración
6. Configurar CI/CD

## Contribuir

[Instrucciones para contribuir al proyecto]

## Licencia

[Información sobre la licencia del proyecto]
