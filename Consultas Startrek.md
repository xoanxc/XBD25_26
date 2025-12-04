## d1-c1) Amosar nomes de personaxes que teñan unha letra 'a'  e unha letra 'n' no seu nome

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE nomper LIKE '%a%' AND nomper LIKE '%n%';
```

### Resultado esperado

```
karnas
lian
tagana
```

---

## d1-c1') Amosar nomes de actores  que teñan unha letra 'y'  ou unha letra 'j' no seu nome

### Consulta SQL

```sql
SELECT noma FROM actores WHERE noma LIKE '%y%' OR noma LIKE '%j%';
```

### Resultado esperado

```
nimoy
kelley
yuan
julia
gray
brandy
```

---

## d1-c3) De cantos actores non se coñece a data de nacemento?

### Consulta SQL

```sql
SELECT COUNT(datan) FROM actores WHERE datan IS NULL;
```

### Resultado esperado

```
5
```

---

## d1-c3') De cantos interpretes de series  non se coñece as horas que levan traballadas?

### Consulta SQL

```sql
SELECT COUNT(*) FROM interpretesser WHERE horas IS NULL;
```

### Resultado esperado

```
8
```

---

## d1-c4) Cantas horas de rodaxe empregou o actor de codigo 'a1' en todas as series nas que interviu.

### Consulta SQL

```sql
SELECT sum(horas) FROM interpretesser WHERE coda='a1';
```

### Resultado esperado

```
800
```

---

## d1-c4') Canto cobran de media por hora os actores de nacionalidade 'espanha' ( nota o que cobra por hora un actor e o que se denomina cachehora)

### Consulta SQL

```sql
SELECT avg(cachehora) FROM actores WHERE nacionalidade='espanha';
```

### Resultado esperado

```
233.333333
```

---

## d1-c5) Amosar os nomes  dos naves que se usan para visitar planetas na serie de codigo 's1' enterprise   

### Consulta SQL

```sql
SELECT nomen FROM naves WHERE codn IN (SELECT codn FROM visitas WHERE cods='s1');
```

### Resultado esperado

```
enterprise
voyager
```

---

## d1-c6) Amosar os nomes dos planetas da galaxia  'via_lactea'

### Consulta SQL

```sql
SELECT nompla FROM planetas WHERE galaxia='via_lactea';
```

### Resultado esperado

```
terra
mart
xupiter
saturno
neptuno
vulcano
```

---

## d1-c6') Amosar os nomes dos personaxes que teñan de graduación 'oficial'

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE graduacion ='oficial';
```

### Resultado esperado

```
chekov
ear
prak
tomalak
ronin
sissy
kira
```

---

## d2-c0) Amosar os nomes dos personaxes que estando na base de datos non están relacionados todavía con ninguna película

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE codper NOT IN (SELECT codper FROM interpretespel);
```

### Resultado esperado

```
sovak
kor
ronin
devour
letek
ardor
solok
lag
kurn
comic
karnas
lian
lures
kamala
maccoy
tagana
gilora
kraal
grilka
morn
garak
nog
rom
tiron
brunt
scott
ducat
boogie
gull
quark
dax
sissy
kira
```

---

## d2-c0') Amosar nomes de planetas que non foron visitados

### Consulta SQL

```sql
SELECT nompla FROM planetas WHERE codpla NOT IN (SELECT codpla FROM visitas);
```

### Resultado esperado

```
lobar
gork
neptuno
vulcano
```

---

## d2-c3) Amosar nomes de actores que participan  polo menos unha vez nunha serie e polo menos unha vez nunha pelicula (as duas cousas a vez)

### Consulta SQL

```sql
SELECT noma FROM actores WHERE coda IN (SELECT coda FROM interpresser) AND coda IN (SELECT coda FROM interprespel);
```

### Resultado esperado

```
shatner
nimoy
kelley
doohan
luis
pedro
yuan
```

---

## d2-c3') Amosar nomes de personaxes que non  participan  en series nen en peliculas

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE codper NOT IN (SELECT codper FROM interpretesser) AND codper NOT IN (SELECT codper from interpretespel);
```

### Resultado esperado

```
lures
tagana
gilora
lian
solok
brunt
ducat
lag
sissy
devour
comic
kraal
letek
nog
ardor
tiron
dax
karnas
garak
rom
grilka
gull
quark
kira
morn
boogie
kamala
kurn
```

---

## d2-c4) Amosar os nomes dos personaxes que son soldados e non dependen de ningun outro personaxe

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE graduacion='soldado' AND codper2 IS NULL;
```

### Resultado esperado

```
vekor
lag
kamala
garak
```

---

## d2-c4') Amosar os nomes dos actores que cobren 200 de cachehora dos que non se sepa a data de nacemento

### Consulta SQL

```sql
SELECT noma FROM actores WHERE datan IS NULL AND cachehora=200;
```

### Resultado esperado

```
koenig
ana
```

---

## d2-c5) Amosa o numero de  personaxes que interpreta o actor de codigo 'a18'  na serie de nome 'deep_space_nine'

### Consulta SQL

```sql
SELECT COUNT(codper) FROM interpretesser WHERE coda='a18' AND cods IN (SELECT cods FROM series WHERE titulo='deep_space_nine');
```

### Resultado esperado

```
2
```

---

## d2-c6) Amosar nomes de naves que non  teñen lanzaderas

### Consulta SQL

```sql
SELECT nomen FROM naves WHERE codn NOT IN (SELECT codn FROM lanzaderas);
```

### Resultado esperado

```
speedo
```

---

## d3-c7) [NON FACER] Cantos klingon proceden de planetas visitados na serie que ten por titulo 'enterprise'

### Consulta SQL

```sql
SELECT COUNT(*) FROM klingon WHERE codpla IN (SELECT codpla FROM visitas WHERE cods IN (SELECT cods FROM series WHERE titulo='enterprise'));
```

### Resultado esperado

```
14
```

---

## d3-c8) Canto cobran de media por hora os actores tendo en conta os nulos

### Consulta SQL

```sql
select sum(cachehora)/count(*) from actores;
```

### Consulta alternativa (da un resultado mas exacto, en este caso entrega todos los decimales que pide el ejercicio)

```sql
SELECT sum(cachehora)*1.0/COUNT(*) FROM actores;
```

### Resultado esperado

```
192.592593
```

---

## d3- c10) [NON FACER] Amosar codigos de lanzaderas que se usaron para visitar o planeta 'mart' na serie 'next_generation'

### Consulta SQL

```sql
SELECT codn, numero FROM lanzaderas WHERE codn IN (SELECT codn FROM visitas WHERE codpla IN (SELECT codpla FROM planetas WHERE nompla='mart' ) AND cods IN (SELECT cods FROM series WHERE titulo='next_generation'));
```

### Resultado esperado

```
n4          11
n4          10
n4           9
n4           8
n4           7
n4           6
n4           5
n4           4
n2           3
n2           2
n2           1
```

---
## d3-c12) Amosar nomes de actores de series que interpreten personaxes que teñen una letra 'y' no seu nome de personaxe

### Consulta SQL

```sql
SELECT noma FROM actores WHERE coda in (SELECT coda FROM interpretesser WHERE codper IN (SELECT codper FROM personaxes WHERE nomper LIKE '%y%'));
```

### Resultado esperado

```
beatriz
kelley
luis
```

---

## d3-c13) [DIFICIL] Amosar nomes de actores que teñan polo menos unha letra ' a' ,  de series  interpretadas por  personaxes que teñen una letra 'a' no seu nome de personaxe

### Consulta SQL

```sql
SELECT noma FROM actores WHERE noma LIKE '%a%' AND coda IN (SELECT coda FROM interpretesser WHERE codper IN (SELECT codper FROM personaxes WHERE nomper LIKE '%a%'));
```

### Resultado esperado

```
yuan
beatriz
veronica
gray
```

---

## d3-c14) [DIFICIL] Amosar os nomes dos personaxes dos que dependen directamente soldados

### Consulta SQL

```sql
SELECT DISTINCT m.nomper FROM personaxes o, personaxes m WHERE o.graduacion='soldado' AND o.codper2=m.codper;
```

#### Consulta alternativa

```sql
SELECT nomper FROM personaxes WHERE codper IN (SELECT codper2 FROM personaxes WHERE codper2 IS NOT NULL AND graduacion= 'soldado');
```

### Resultado esperado

```
word
letek
ardor
solok
```
