## 1) Amosar nif e nome de clientes que viven na zona de codigo z1

### Consulta SQL

```sql
SELECT nif, nome FROM cliente WHERE codz='z1';
```

## 2) Amosar nif e nome de clientes que dos que se descoñece a zona onde viven

### Consulta SQL

```sql
SELECT nif, nome FROM cliente WHERE  codz IS NULL;
```

## 3) Amosar nif e nome de clientes dos que se coñece a zona onde viven

### Consulta SQL

```sql
SELECT nif, nome FROM cliente WHERE codz IS NOT NULL;
```

## 4) Amosar nif, nome e correo de clientes

### Consulta SQL

```sql
SELECT nif, nome, email FROM cliente;
```

-----

> **Nota sobre ORDER BY:**
> `ORDER BY campo [asc/desc]`: ordea o resultado da consulta polos campos que se indiquen, ascendente (opcion por defecto) ou descendentemente.

## 5) Amosar nif, nome e correo de clientes ordeados por nome

### Consulta SQL

```sql
SELECT nif, nome, email FROM cliente ORDER BY nome;
```

## 6) Amosar nif, nome e correo de clientes da zona que ten por codigo 'z1' ordeados por nome

### Consulta SQL

```sql
SELECT nif, nome, email FROM cliente WHERE codz='z1' ORDER BY nome;
```

## 7) Amosar nif, nome e mail dos clientes da zona 'z1' ou que vivan na 'r/coruxo'

### Consulta SQL

```sql
SELECT nif, nome, email FROM cliente WHERE codz='z1' OR direcion='r/coruxo';
```

-----

> **Funcións de agregación:**
>
>   * `COUNT(*)`: conta filas dun select.

## 8) Amosar cantos clientes hai

### Consulta SQL

```sql
SELECT count(*) FROM cliente;
```

## 9) Amosar cantos clientes hai na zona de codigo 'z1'

### Consulta SQL

```sql
SELECT count(*) FROM cliente WHERE codz='z1';
```

## 10) Amosar cantos clientes non teñen zona asignada

### Consulta SQL

```sql
SELECT count(*) FROM cliente WHERE codz IS NULL;
```

-----

> **Funcións de agregación:**
>
>   * `SUM(campo)`: suma os valores contidos no campo especificado.

## 11) Amosa a suma ou total final de todos os pedidos

### Consulta SQL

```sql
SELECT sum(total) FROM pedido;
```

## 13) Calcula o total final dos pedidos do cliente de nif '368h'

### Consulta SQL

```sql
SELECT sum(total) FROM pedido WHERE nif='368h';
```

## 14) Calcula a suma dos totais dos pedidos 'p14', 'p15' e 'p16'

### Consulta SQL

```sql
SELECT sum(total) FROM pedido WHERE codp='p14' OR codp='p15' OR codp='p16';
```

-----

> **Funcións de agregación:**
>
>   * `AVG(campo)`: calcula a media dos valores contidos no campo especificado.
>   * **NOTA:** `avg` non ten en conta os valores nulos (igual que `count` ou `sum`).

## 15) Calcula o valor medio dos totais dos pedidos 'p14', 'p15' e 'p16'

### Consulta SQL

```sql
-- Opción A: Usando OR
SELECT avg(total) FROM pedido WHERE codp='p14' OR codp='p15' OR codp='p16';

-- Opción B: Usando IN
SELECT avg(total) FROM pedido WHERE codp IN ('p14','p15','p16');
```

## 16) Calcula o valor medio dos totais dos pedidos 'p14', 'p15' e 'p16' tendo en conta os nulos para o cálculo da media

### Consulta SQL

```sql
-- Forzamos a división flotante multiplicando por 1.0 e usamos COUNT(*) para incluír nulos no denominador
SELECT 1.0*sum(total)/count(*) FROM pedido WHERE codp='p14' OR codp='p15' OR codp='p16';

-- Alternativa con IN
SELECT 1.0*sum(total)/count(*) FROM pedido WHERE codp IN ('p14','p15','p16');
```

-----

> **Operador LIKE:**
>
>   * `%` : sustitúe a calquera número de caracteres.
>   * `_` : sustitúe a un único caracter.

## 17) Amosar nif, nome e telefono dos clientes cuxo nome remate na letra 'a'

### Consulta SQL

```sql
SELECT nif, nome, telefono FROM cliente WHERE nome LIKE '%a';
```

## 18) Amosar nif, nome e mail de todas as persoas que teñen correo en gmail

### Consulta SQL

```sql
SELECT nif, nome, email FROM cliente WHERE email LIKE '%gmail.com';
```

## 19) Amosar nif, nome e mail de todos os clientes que teñan unha 'o' na penúltima letra do seu nome

### Consulta SQL

```sql
SELECT nif, nome, email FROM cliente WHERE nome LIKE '%o_';
```

-----

## 20) Amosar datos dos produtos correspondentes a marca de codigo de marca 'm6'

### Consulta SQL

```sql
SELECT * FROM produto WHERE codm='m6';
```

## 21) Amosar datos de produtos cuxo prezo este comprendido entre 5 e 10 (ambolos dous incluidos)

### Consulta SQL

```sql
SELECT * FROM produto WHERE prezo >= 5 AND prezo <= 10;
-- Alternativa:
-- SELECT * FROM produto WHERE prezo BETWEEN 5 AND 10;
```

## 21) Amosar datos de produtos da marca 'm6', cuxo prezo este comprendido entre 5 e 10

### Consulta SQL

```sql
SELECT * FROM produto WHERE codm='m6' AND prezo >= 5 AND prezo <= 10;
-- Alternativa:
-- SELECT * FROM produto WHERE codm='m6' AND prezo BETWEEN 5 AND 10;
```

## 22) Amosar media de prezos dos produtos de codigo de marca 'm6'

### Consulta SQL

```sql
SELECT avg(prezo) FROM produto WHERE codm='m6';
```

-----

## 23) Amosar codigo de cada marca e media de produtos correspondentes a cada marca

### Consulta SQL

```sql
SELECT codm, avg(prezo) FROM produto GROUP BY codm ORDER BY codm;
```

## 24) Amosar codigo de cada marca e cantos produtos corresponden a cada marca

### Consulta SQL

```sql
SELECT codm, count(*) FROM produto GROUP BY codm ORDER BY codm;
```

## 25) Amosar cantos clientes viven na zona de codigo 'z1'

### Consulta SQL

```sql
SELECT count(*) FROM cliente WHERE codz='z1';
```

## 26) Amosa para cada codigo de zona cantos clientes viven nela

### Consulta SQL

```sql
SELECT codz, count(*) FROM cliente GROUP BY codz;
```

## 27) Amosar cantos clientes hai para cada nome

### Consulta SQL

```sql
SELECT nome, count(*) FROM cliente GROUP BY nome;
```

## 28) Amosar cantos clientes temos de cada dominio de correo electronico

### Consulta SQL

```sql
-- Extrae o subcadena dende a posición da '@'
SELECT substr(email, strpos(email,'@')), count(*) 
FROM cliente 
GROUP BY substr(email, strpos(email,'@'));
```

-----

### Subconsultas (Subqueries)

## 29) Amosar cantos clientes viven na zona 'centro'

### Consulta SQL

```sql
SELECT count(*)
FROM cliente
WHERE codz = (SELECT codz FROM zona WHERE nomz='centro');
```

## 30) Amosar dni e nome de repartidores da zona 'centro'

### Consulta SQL

```sql
SELECT dni, nomr
FROM repartidor
WHERE codz = (SELECT codz FROM zona WHERE nomz='centro');
```

## 31) Amosar nif do cliente que ten por email 'carlosr@gmail.com'

### Consulta SQL

```sql
SELECT nif FROM cliente WHERE email='carlosr@gmail.com';
```

## 31) Amosar codigos de pedidos do cliente que ten por email 'carlosr@gmail.com'

### Consulta SQL

```sql
-- Paso a paso:
-- SELECT codp FROM pedido WHERE nif='368h';

-- Consulta xunta (anidada):
SELECT codp FROM pedido 
WHERE nif = (SELECT nif FROM cliente WHERE email='carlosr@gmail.com');
```

## 32) Amosar codigo de pedidos cargados na furgoneta de matricula 'ab121'

### Consulta SQL

```sql
SELECT codp FROM carga 
WHERE nf = (SELECT nf FROM furgoneta WHERE matricula='ab121');
```

## 33) Amosar nome e prezo de produtos da marca 'argal'

### Consulta SQL

```sql
SELECT nome, prezo FROM produto 
WHERE codm = (SELECT codm FROM marca WHERE nomm='argal');
```

## 34) Amosar nif dos clientes que viven na zona de nome 'centro'

### Consulta SQL

```sql
-- Comprobación previa de zona:
-- SELECT codz FROM zona WHERE nomz='centro';

SELECT nif FROM cliente 
WHERE codz = (SELECT codz FROM zona WHERE nomz='centro');
```

## 35) Amosar codigos de pedidos de clientes que viven na zona de nome 'centro'

### Consulta SQL

```sql
SELECT codp FROM pedido 
WHERE nif IN (
    SELECT nif FROM cliente WHERE codz IN (
        SELECT codz FROM zona WHERE nomz='centro'
    )
);
```

## 36) Amosar numeros de furgoneta onde se cargaron pedidos de clientes que viven na zona de nome 'centro'

### Consulta SQL

```sql
SELECT nf FROM carga 
WHERE codp IN (
    SELECT codp FROM pedido WHERE nif IN (
        SELECT nif FROM cliente WHERE codz IN (
            SELECT codz FROM zona WHERE nomz='centro'
        )
    )
);
```

## 37) Amosar sen repeticion os numeros de furgoneta onde se cargaron pedidos de clientes que viven na zona de nome 'centro'

### Consulta SQL

```sql
SELECT DISTINCT nf FROM carga 
WHERE codp IN (
    SELECT codp FROM pedido WHERE nif IN (
        SELECT nif FROM cliente WHERE codz IN (
            SELECT codz FROM zona WHERE nomz='centro'
        )
    )
);
```

-----

### Consultas Cruzadas (Joins)

## 38) Amosar nif, nome e codigo de zona dos clientes

### Consulta SQL

```sql
SELECT nif, nome, codz FROM cliente;
```

## 39) Amosar nif, nome e nome de zona onde viven dos clientes

### Consulta SQL

```sql
SELECT nif, nome, nomz 
FROM cliente, zona 
WHERE cliente.codz = zona.codz;
```

## 40) Amosar dni, nome e nome de zona onde reparten os repartidores

### Consulta SQL

```sql
SELECT dni, nomr, nomz 
FROM repartidor, zona 
WHERE repartidor.codz = zona.codz;
```

## 41) Amosar matricula de cada furgoneta e codigo dos pedidos que foron cargados nela

### Consulta SQL

```sql
SELECT matricula, codp 
FROM furgoneta, carga 
WHERE furgoneta.nf = carga.nf;
```

## 42) Amosar nome da marca e nome de todos os produtos

### Consulta SQL

```sql
SELECT nomm, nome 
FROM marca, produto 
WHERE marca.codm = produto.codm;
```

## 43) Amosar nome e orixe de cada froita

### Consulta SQL

```sql
SELECT nome, orixe 
FROM froitas, produto 
WHERE froitas.codm = produto.codm AND froitas.n = produto.n;
```

## 44) Amosar nif, nome de todos os clientes e ademais o nome de zona onde viven

### Consulta SQL

```sql
-- Aproximación (INNER JOIN implícito), pero non correcto se hai nulos:
SELECT nif, nome, nomz 
FROM cliente, zona 
WHERE cliente.codz = zona.codz;

-- Resultado correcto (LEFT JOIN para incluír clientes sen zona):
SELECT nif, nome, nomz 
FROM cliente LEFT JOIN zona ON cliente.codz = zona.codz;
```