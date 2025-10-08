# 📘 Documentación del Modelo Entidad–Relación

## Entidades y Atributos

### 1. **Vivero**
Representa el conjunto físico donde se gestionan las plantas y productos.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador único del vivero | Numérico (entero positivo) | 1 |
| `Geolocalización` | Coordenadas o dirección del vivero | Texto / Coordenadas GPS | “-32.9468, -60.6393” |

---

### 2. **Zona**
Cada vivero se divide en zonas donde se ubican los productos o plantas.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador único de la zona | Numérico | 12 |
| `Nombre` | Nombre o código de la zona | Texto | “Zona A - Plantas ornamentales” |
| `Tipo` | Clasificación de la zona | Texto | “Interior”, “Exterior” |
| `Geolocalización` | Ubicación específica dentro del vivero | Texto | “Sector norte” |

---

### 3. **Producto**
Representa los productos disponibles en cada zona del vivero.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador único del producto | Numérico | 101 |
| `Nombre` | Nombre del producto o planta | Texto | “Rosa roja” |
| `Tipo` | Clasificación del producto | Texto | “Planta ornamental” |
| `Precio` | Valor unitario del producto | Decimal positivo | 12.50 |
| `Cantidad vendida` | Número de unidades vendidas | Entero ≥ 0 | 15 |
| `Cantidad restante` | Stock disponible | Entero ≥ 0 | 85 |

---

### 4. **Stock**
Controla la disponibilidad y movimientos de productos.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador único del registro de stock | Numérico | 501 |
| `Cantidad restante` | Unidades disponibles en inventario | Entero ≥ 0 | 120 |
| `Cantidad vendida` | Unidades vendidas | Entero ≥ 0 | 30 |

---

### 5. **Empleado**
Representa a los trabajadores del vivero.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador del empleado | Numérico | 2001 |
| `DNI` | Documento nacional de identidad | Numérico o alfanumérico | “45123987” |
| `Nombre` | Nombre completo | Texto | “María López” |
| `Teléfono` | Número de contacto | Texto | “+54 9 341 555-9876” |
| `Email` | Correo electrónico | Texto (formato válido) | “mlopez@vivero.com” |

---

### 6. **Horario Funcional**
Define los turnos de trabajo asignados a los empleados.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador del horario | Numérico | 301 |
| `Fecha entrada` | Fecha de inicio del turno | Fecha | “2025-03-10” |
| `Fecha salida` | Fecha de finalización | Fecha | “2025-03-10” |

---

### 7. **Puesto**
Define el cargo o función que desempeña un empleado.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador del puesto | Numérico | 25 |
| `Nombre` | Nombre del puesto | Texto | “Jardinero” |

---

### 9. **Cliente**
Representa a las personas que realizan pedidos al vivero.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `DNI` | Identificador del cliente | Numérico / Alfanumérico | “48201987” |
| `Nombre` | Nombre completo | Texto | “Carlos Fernández” |
| `Teléfono` | Contacto | Texto | “+54 9 341 666-3210” |
| `Email` | Correo electrónico | Texto (formato válido) | “cfernandez@gmail.com” |
| `Bonificación` | Descuento asociado al cliente | Porcentaje (0–100%) | 10 |
| `Membresía cliente` | Tipo de cliente | Texto | “Premium”, “Regular” |

---

### 10. **Pedido**
Registra los pedidos realizados por los clientes.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID pedido` | Identificador del pedido | Numérico | 9001 |
| `Teléfono` | Contacto para el pedido | Texto | “+54 9 341 666-3210” |
| `Email` | Correo de contacto | Texto | “pedidos@vivero.com” |

---

## Modificación Entidad Incluida

### 8. **Mantenimiento**
Registra las tareas de mantenimiento realizadas en las zonas o viveros.

| Atributo | Descripción | Dominio | Ejemplo |
|-----------|--------------|----------|----------|
| `ID` | Identificador del mantenimiento | Numérico | 700 |
| `Tipo` | Tipo de mantenimiento | Texto | “Riego”, “Poda” |
| `Duración` | Tiempo de ejecución | Entero (horas o minutos) | 2 |
| `Fecha` | Fecha de realización | Fecha | “2025-03-10” |
| `Descripción` | Detalles del mantenimiento | Texto | “Riego por aspersión en Zona A” |
| `Hora inicio` | Hora de inicio | Hora | “08:00” |
| `Hora fin` | Hora de finalización | Hora | “10:00” |

## 🔗 Relaciones y Cardinalidades

| Relación | Entidades involucradas | Cardinalidad | Descripción |
|-----------|------------------------|---------------|--------------|
| **Pertenecer** | Zona – Vivero | (1,N) – (1,1) | Cada zona pertenece a un único vivero, y un vivero puede tener múltiples zonas. |
| **Contener** | Zona – Producto | (1,N) – (N,0) | Una zona puede contener varios productos, pero un producto puede no estar asignado a ninguna zona. |
| **Registro** | Producto – Stock | (1,N) – (N,0) | Un producto puede tener múltiples registros de stock, pero el stock puede existir sin producto si aún no se asocia. |
| **Mantener** | Zona – Mantenimiento | (1,N) – (1,N) | Cada zona puede requerir varios mantenimientos y cada mantenimiento se aplica a una o varias zonas. |
| **Ejecuta** | Puesto – Mantenimiento | (1,N) – (1,N) | Cada puesto puede ejecutar distintos mantenimientos, y un mantenimiento puede ser realizado por varios puestos. |
| **Asignación** | Empleado – Horario Funcional | (1,1) – (1,N) | Cada empleado tiene asignado un horario funcional, pudiendo desempeñar distintos turnos. |
| **Encargado** | Empleado – Pedido | (N,N) | Un pedido puede ser gestionado por varios empleados, y un empleado puede encargarse de varios pedidos. |
| **Realiza** | Cliente – Pedido | (1,N) – (N,N) | Un cliente puede realizar varios pedidos, y un pedido puede involucrar a varios clientes (por ejemplo, pedidos conjuntos). |
| **Geolocalización** | Vivero – Zona | (0,1) – (1,N) | Cada vivero posee una geolocalización única y las zonas heredan esa ubicación. |

---

## ⚙️ Restricciones Semánticas

1. **Un producto no puede estar disponible si su cantidad restante es 0.**  
   → Restricción: `Cantidad_restante > 0` para que el producto sea visible o vendible.

3. **Cada empleado debe tener al menos un horario funcional asignado.**  
   → Restricción de existencia obligatoria entre *Empleado* y *Horario Funcional*.

4. **Un pedido no puede existir sin al menos un cliente asociado.**

5. **Un cliente no puede recibir bonificación si su membresía no es “Premium”.**

---

## 📄 Conclusión

Este modelo entidad–relación permite una gestión integral del vivero, abarcando la organización de sus zonas, los productos disponibles, la planificación del personal, el control de mantenimientos y la administración de pedidos y clientes. Las relaciones y restricciones aseguran la integridad y coherencia de los datos en el sistema.
