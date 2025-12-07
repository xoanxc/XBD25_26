## 1) Amosar nomes de balnearios cuxo coste diario supere os 45 euros

### Consulta SQL

```sql
SELECT nomb FROM balnearios WHERE costed > 45;
```

## 2) Amosar nomes de pacientes que vivan na poboacion denominada brea

### Consulta SQL

```sql
SELECT nomp FROM pacientes 
WHERE codp IN (SELECT codp FROM poboacions WHERE nomp='brea'); 
```

## 3) Indicar os tipos de augas que estarian indicadas para os pacientes que sufren de ril

### Consulta SQL

```sql
SELECT tipo FROM augas 
WHERE coda IN (
    SELECT coda FROM indicadas WHERE codz IN (
        SELECT codz FROM zonas_corporais WHERE nomz='ril'
    )
);
```

## 4) Amosar codigos de poboacions onde viven os pacientes e o numero de pacientes que ten cada unha desas poboacions

### Consulta SQL

```sql
SELECT codp, count(*) FROM pacientes GROUP BY codp; 
```

## 5) Amosar de cantos minerais se compon cada tipo de auga

### Consulta SQL

```sql
SELECT tipo, count(*) 
FROM augas, compon 
WHERE augas.coda = compon.coda 
GROUP BY tipo;
```

## 6) Amosar sen repeticion os codigos de medicos que asignaron balneario a cronico e prescribiron a agudo

> **Nota:** Deben cumprir ambas condicións (estar na táboa `asignan` E na táboa `prescriben`).

### Consulta SQL

```sql
SELECT distinct(codme) FROM asignan WHERE codme IN (SELECT codme FROM prescriben);
```

## 7) Amosar nif e nome de todos e cada un dos pacientes e ademais a poboacion onde viven

> **Nota:** Úsase `LEFT JOIN` para asegurar que saian todos os pacientes, teñan ou non poboación asignada.

### Consulta SQL

```sql
SELECT nif, pacientes.nomp, poboacions.nomp 
FROM pacientes LEFT JOIN poboacions ON pacientes.codp = poboacions.codp;
```

## 8) Amosar o nome do balneario onde supostamente se atopaba o paciente agudo de nif 3615 o 8/7/2020

> **Lóxica de datas:** Para saber se estaba nese día, a data de entrada (`dea`) debe ser anterior ou igual ao día, e a de saída (`dsa`) posterior ou igual.

### Consulta SQL

```sql
SELECT nomb FROM balnearios 
WHERE codb IN (
    SELECT codb FROM prescriben 
    WHERE nif='3615' AND dea <= '8/7/2020' AND dsa >= '8/7/2020'
);
```

## 9) Amosar os nif de todos os pacientes se o numero de pacientes cronicos e igual ao numero de pacientes agudos

### Consulta SQL

```sql
SELECT nif FROM pacientes 
WHERE (SELECT count(*) FROM cronicos) = (SELECT count(*) FROM agudos);
```

## 10) Amosar os nomes das poboacions que non posuan balnearios

### Consulta SQL

```sql
SELECT nomp FROM poboacions WHERE codp NOT IN (SELECT codp FROM balnearios);
```

## 11) Amosar nomes de balnearios que se chamen exactamente igual que nomes de poboacions

### Consulta SQL

```sql
SELECT nomp FROM poboacions INTERSECT SELECT nomb FROM balnearios;
```

## 12) Amosar nomes de pacientes distintos aos nomes de calquera medico

### Consulta SQL

```sql
SELECT nomp FROM pacientes WHERE nomp NOT IN (SELECT nomme FROM medicos);
```

## 13) Amosar os nomes de pacientes sen que se repitan

### Consulta SQL

```sql
SELECT distinct(nomp) FROM pacientes;
```

## 14) Amosar os nomes de pacientes que posuan polo menos unha letra 'a' e polo menos unha letra 'o' no seu nome

### Consulta SQL

```sql
SELECT nomp FROM pacientes WHERE nomp LIKE '%a%' AND nomp LIKE '%o%';
```

## 15) Amosar os nomes de todos e cada un dos medicos e os nomes dos seus xefes

> **Nota:** Autocombinación (Self Join).

### Consulta SQL

```sql
SELECT m.nomme AS medico, x.nomme AS xefe
FROM medicos m LEFT JOIN medicos x ON m.xef = x.codme;
```

## 16) Amosar os nomes dos hoteis que posuan algunha habitacion con interede

### Consulta SQL

```sql
-- O campo interede terá unha letra 's' se a posúe
SELECT nomh FROM hoteis 
WHERE codh IN (SELECT codh FROM habitacions WHERE interede='s');
```

## 17) Amosar cales son os ingresos mensuais dos pacientes cronicos

### Consulta SQL

```sql
SELECT ingm FROM pacientes WHERE nif IN (SELECT nif FROM cronicos);
```

## 18) Amosar os nomes dos balnearios que posuan fisioterapeuta

### Consulta SQL

```sql
SELECT nomb FROM balnearios 
WHERE codb IN (SELECT codb FROM cat1 WHERE fisioterapeuta='s');
```

## 20) Amosar os nomes dos pacientes cuxa estancia no hotel 'melia' transcurriu en parte ou totalmente entre os dias 15/7/2020 e 20/7/2020

> **Lóxica de Solapamento de Datas:**
> Para detectar solapamento, a data de entrada do rexistro (`de`) debe ser menor ou igual á data fin do rango buscado, e a data de saída do rexistro (`ds`) debe ser maior ou igual á data de inicio do rango buscado.

### Consulta SQL

```sql
SELECT nomp FROM pacientes 
WHERE nif IN (
    SELECT nif FROM aloxan 
    WHERE codh IN (SELECT codh FROM hoteis WHERE nomh='melia') 
    AND de <= '20/7/2020' 
    AND ds >= '15/7/2020' 
);
```