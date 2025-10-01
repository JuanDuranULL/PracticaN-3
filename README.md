# Modelo Entidad–Relación de Vívero

Readme Exigido Práctica Nº3

---

## 📌 Entidades y Atributos  

### **Cliente**  
- **Código**: Identificador único del cliente (ej. `C123`).  
- **Nombre**: Nombre completo del cliente (ej. `Juan Pérez`).  
- **Teléfono**: Número de contacto (ej. `3001234567`).  
- **Dirección**: Dirección de residencia (ej. `Calle 10 #45-23, Bogotá`).  

---

### **Compra**  
- **N° Compra**: Identificador único de la compra (ej. `CMP001`).  
- **Fecha**: Fecha en la que se realiza la compra (ej. `2025-09-30`).  

---

### **Medicamento**  
- **Código**: Identificador único del medicamento (ej. `MED123`).  
- **Nombre**: Nombre comercial del medicamento (ej. `Paracetamol`).  
- **Tipo**: Clasificación del medicamento (ej. `Analgesico`).  
- **CondiciónVenta**: Especifica si requiere receta o no (ej. `Con receta` / `Libre`).  
- **Stock**: Cantidad disponible en inventario (ej. `250 unidades`).  
- **Vendidos**: Cantidad vendida (ej. `120 unidades`).  
- **Precio**: Valor unitario del medicamento (ej. `$5.000`).  

---

### **Familia**  
- **CódigoFamilia**: Identificador único de la familia de medicamentos (ej. `FAM001`).  
- **NombreFamilia**: Nombre del grupo farmacológico (ej. `Antibióticos`).  

---

### **Farmacia**  
- **Código**: Identificador único de la farmacia (ej. `FAR001`).  
- **Nombre**: Nombre comercial de la farmacia (ej. `Farmacia Salud+`).  
- **Dirección Postal**: Dirección física de la farmacia.  
- **Teléfono**: Número de contacto de la farmacia.  
- **Fax**: Número de fax de la farmacia.  

---

### **Laboratorio**  
- **Código**: Identificador único del laboratorio (ej. `LAB001`).  
- **Nombre**: Nombre del laboratorio (ej. `Laboratorios Genéricos S.A.`).  
- **Dirección Postal**: Dirección física del laboratorio.  
- **Teléfono**: Número de contacto.  
- **Fax**: Número de fax.
- **Persona de Contacto**: Gerente del Laboratorio (ehj. `Julian`, `3227931513`)

---

## 🔗 Relaciones y Cardinalidades  

1. **Cliente – Compra (Puede Hacer)**  
   - Un cliente **(1,N)** puede realizar muchas compras.  
   - Cada compra está asociada a un solo cliente **(1,1)**.  

2. **Compra – Medicamento (Contener)**  
   - Una compra **(1,N)** puede contener varios medicamentos.  
   - Un medicamento puede estar en varias compras **(N,1)**.  

3. **Medicamento – Familia (Clasifica)**  
   - Una familia **(0,N)** puede clasificar varios medicamentos.  
   - Un medicamento pertenece a una sola familia **(1,1)**.  

4. **Medicamento – Farmacia (Pertenecer)**  
   - Una farmacia **(1,N)** puede tener varios medicamentos en stock.  
   - Cada medicamento pertenece a una sola farmacia **(1,1)**.  

5. **Medicamento – Laboratorio (Pertenece/Fabrica)**  
   - Un laboratorio **(1,N)** fabrica muchos medicamentos.  
   - Cada medicamento es producido por un único laboratorio **(1,1)**.  


---

## ⚖️ Restricciones Semánticas  

- **Restricción de stock**: El atributo `Stock` de un medicamento nunca puede ser negativo.  
- **Restricción de precio**: El `Precio` debe ser mayor que 0.  
- **Relación Compra–Cliente**: Una compra no puede existir sin estar asociada a un cliente válido.  
- **Persona de contacto**: Cada laboratorio debe tener al menos una persona de contacto registrada.  
