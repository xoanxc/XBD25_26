## c1) Amosar nomes de hospitais que tenhan mais de 100 camas

### Consulta SQL

```sql
SELECT nomh FROM hospital WHERE numc>100;
```

### Resultado esperado

```
canalejo
xeral
meixoeiro
paz
sofia
sonic
povisa
provincial
nicolas
```

---

## c2) Amosar nomes de hospitais  concertados que tenhan mais de 100 camas

### Consulta SQL

```sql
SELECT nomh FROM hospital WHERE numc>100 AND codh IN (SELECT codh FROM concertado WHERE concertado.codh=hospital.codh);
```

### Resultado esperado

```
sofia
sonic
povisa
```

---

## c3) Amosar cantos asegurados hay en cada poliza que ten asegurados

### Consulta SQL

```sql
SELECT codp, count(*) FROM asegurado WHERE numas IS NOT null GROUP BY codp;
```

### Resultado esperado

```
p12  |     1
p6   |     1
p3   |     2
p5   |     2
p14  |     1
p11  |     1
p4   |     2
p9   |     1
p7   |     1
p10  |     1
p13  |     1
p8   |     1
p2   |     2
p15  |     2
p1   |     2
```

---

## c4 ) Amosar nomes de asegurados que tenhan una letra -e- ou unha letra -o- no seu nome

### Consulta SQL

```sql
SELECT nomas FROM asegurado WHERE nomas LIKE '%e%' OR nomas LIKE '%o%';
```

### Resultado esperado

```
pedro
carlos
bieito
xoan
eva
dorotea
elisa
olores
xose
andrea
comba
jose
```

---

## c5 ) Amosar codigo e nome  dos medicos que non hospitalizaron  a ningun asegurado de ningunha das categorias existentes

### Consulta SQL

```sql
SELECT
```

### Resultado esperado

```
m3   | virginia
```

---

## c6) Amosar para todos e cada un dos códigos de áreas existentes cantos médicos teñen adscritos

### Consulta SQL

```sql
SELECT
```

### Resultado esperado

```
a1   |     2
a5   |     1
a6   |     0
a3   |     1
a7   |     0
a4   |     1
a2   |     1
```

---

## c7) Amosar código e nome de médicos que non teñen ningún médico que mande neles

### Consulta SQL

```sql
SELECT
```

### Resultado esperado

```
m1   | luis
m2   | ana
```

---

## c8) Amosar código dos asegurados de primeira categoría hospitalizados entre o 10/2/16 e o 23/3/2017 (datas incluidas)

### Consulta SQL

```sql
SELECT
```

### Resultado esperado

```
p3   | 1
p10  | 1
p6   | 1
```

---

## c9) Amosar o número total de camas dos hospitais concertados

### Consulta SQL

```sql
SELECT
```

### Resultado esperado

```
950
```

---

## c10) Amosar código e nome de hospitais cuxo número de camas corresponda polo menos a un hospital propio e a un hospital concertado

### Consulta SQL

```sql
SELECT
```

### Resultado esperado

```
h3   | meixoeiro
h5   | sofia
h11  | provincial
```

---
