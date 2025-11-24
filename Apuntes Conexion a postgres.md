Perfecto, Xoán. Te paso el contenido formateado en Markdown listo para Obsidian. Solo tienes que copiarlo en un archivo `.md` nuevo.

---

# PostgreSQL – Primeros Apuntes

## 🔹 Conectarse a PostgreSQL

1. Abrir terminal.
    
2. Conectarse con:
    
    ```bash
    psql postgres postgres
    ```
    

---

## 🔹 Lanzar un script SQL

```sql
\i 'arrastrar_aqui_el_script.sql'
```

---

## 🔹 Salir del terminal en caso de atasco y reconectar

1. Presiona `CTRL + Z`.
    
2. Conectarse de nuevo:
    
    ```bash
    psql postgres postgres
    ```
    

---

## 🔹 Comandos SQL básicos

### 1. Insertar una fila

```sql
INSERT INTO nombre_tabla VALUES (numero, 'texto', ...);
```

### 2. Ver contenido completo de una tabla

```sql
SELECT * FROM nombre_tabla;
```

### 3. Borrar una fila por clave

```sql
DELETE FROM nombre_tabla WHERE nombre_de_la_clave = valor;
-- valor entre comillas si es texto
```

### 4. Consultar filas concretas

```sql
SELECT ... FROM nombre_tabla WHERE campo = valor;
-- valor entre comillas si es texto
```

### 5. Consultar valores nulos

```sql
SELECT ... FROM nombre_tabla WHERE campo IS null;
SELECT ... FROM nombre_tabla WHERE campo IS NOT null;
```

### 6. Ver tablas existentes en la base

```sql
\dt
```

### 7. Ver descripción de los campos de una tabla

```sql
\d nombre_tabla
```

### 8. Volver a la consola del psql

```sql
\q
```

### 9. Modificar el valor de un campo en una fila

```sql
UPDATE nombre_tabla SET campo_a_modificar = nuevo_valor
WHERE campo_de_seleccion_de_filas = valor;
```

### 10. Operadores de comparación

```
=, >, <, >=, <=, <> o !=
```

### 11. Operadores lógicos

```
AND, OR
```

### 12. Ordenar la salida de un SELECT

```sql
SELECT ... FROM nombre_tabla ORDER BY nombre_campo [DESC];
```