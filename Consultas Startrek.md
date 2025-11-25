## **d1-c1) Amosar nomes de personaxes que teñan unha letra 'a'  e unha letra 'n' no seu nome

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

## **d1-c1') Amosar nomes de actores  que teñan unha letra 'y'  ou unha letra 'j' no seu nome**

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

## **d1-c3) De cantos actores non se coñece a data de nacemento?

### Consulta SQL

```sql
SELECT COUNT(datan) FROM actores WHERE datan IS null;
```

### Resultado esperado

```
5
```

---

## **d1-c3') De cantos interpretes de series  non se coñece as horas que levan traballadas?

### Consulta SQL

```sql
SELECT COUNT(*) FROM interpretesser WHERE horas IS null;
```

### Resultado esperado

```
8
```

---

## **d1-c4) Cantas horas de rodaxe empregou o actor de codigo 'a1' en todas as series nas que interviu.

### Consulta SQL

```sql
SELECT sum(horas) FROM interpretesser WHERE coda='a1';
```

### Resultado esperado

```
800
```

---

## **d1-c4') Media por hora actores de nacionalidad 'espanha'**

**ES:** Cuánto cobran de media por hora los actores de nacionalidad 'España'.

### Consulta SQL

```sql
SELECT avg(cachehora) FROM actores WHERE nacionalidade='espanha';
```

### Resultado esperado

```
233.333333
```

---

## **d1-c5) Naves usadas en serie 's1'**

**ES:** Mostrar los nombres de las naves que se usan para visitar planetas en la serie de código 's1'.

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

## **d1-c6) Amosa nome de planetas da galaxia 'via_lactea'**

**ES:** Mostrar nombres de planetas de la galaxia 'via_lactea'.

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

## **d1-c6') Personaxes con graduación 'oficial'**

**ES:** Mostrar nombres de personajes que tengan graduación 'oficial'.

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE ...;
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

## **d2-c0) Personaxes sen película asociada**

**ES:** Mostrar nombres de personajes que están en la base de datos pero no están relacionados todavía con ninguna película.

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

## **d2-c0') Amosar nomes de planetas que non foron visitados**

**ES:** Mostrar nombres de planetas que no fueron visitados.

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

## **d2-c3) Amosar nomes de actores que participan polo menos unha vez nunha pelicula**

**ES:** Mostrar nombres de actores que participan al menos una vez en una serie y al menos una vez en una película.

### Consulta SQL

```sql
SELECT noma FROM actores WHERE coda IN (SELECT coda FROM interpresser) AND coda in (SELECT coda FROM interprespel)
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

## **d2-c3') Personaxes que non participan en series ni películas**

**ES:** Mostrar nombres de personajes que no participan en series ni películas.

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE codper NOT IN (SELECT codper FROM interpretesser) AND codper NOT IN (SELECT codper from interpretespel)
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

## **d2-c4) Soldados independentes**

**ES:** Mostrar nombres de personajes que son soldados y no dependen de ningún otro personaje.

### Consulta SQL

```sql
SELECT nomper FROM personaxes WHERE graduacion='soldado' AND codper2 IS null;
```

### Resultado esperado

```
vekor
lag
kamala
garak
```

---

## **d2-c4') Actores que cobran 200 sin fecha de nacimiento**

**ES:** Mostrar nombres de actores que cobran 200 de cachehora y cuya fecha de nacimiento es desconocida.

### Consulta SQL

```sql
SELECT noma FROM actores WHERE cachehora=200 AND datan IS null;
```

### Resultado esperado

```
koenig
ana
```

---

## **d2-c5) Número de personajes interpretados por actor 'a18' en serie 'deep_space_nine'**

### Consulta SQL

```sql
SELECT COUNT(*) FROM interpretesser WHERE coda='a18' AND cods IN (SELECT cods FROM series WHERE titulo='deep_space_nine');
```

### Resultado esperado

```
2
```

---

## **d2-c6) Naves que non teñen lanzadeiras**

### Consulta SQL

```sql
-- Tu consulta aquí
```

### Resultado esperado

```
speedo
```

---

## **d3-c7) [NON FACER] Cantos klingon proceden de planetas visitados na serie que ten por titulo 'enterprise'**

### Consulta SQL

```sql
SELECT COUNT(*) FROM klingon WHERE codpla IN (SELECT codpla FROM visitas WHERE cods IN (SELECT cods FROM series WHERE titulo='enterprise'));
```

### Resultado esperado

```
14
```

---

## **d3-c8) Media de cachehora con nulos**

### Consulta SQL

```sql
SELECT sum(cachehora)*1.0/COUNT(*) FROM actores;
```

### Resultado esperado

```
192.592593
```

---

## **d3- c10 ) [NON FACER] Amosar codigos de lanzaderas que se usaron para visitar o planeta 'mart' na serie 'next_generation'.**

### Consulta SQL

```sql
SELECT codn, numero FROM lanzaderas WHERE codn IN (SELECT codn FROM visitas WHERE cods IN (SELECT cods FROM series WHERE titulo='next_generation' AND codpla IN (SELECT codpla FROM planetas WHERE nompla='mart')));
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
## d3-c12) **Amosar nomes de actores de series que interpreten personaxes que teñen una letra 'y' no seu nome de personaxe**:

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

## **d3-c13) [DIFICIL] Amosar nomes de actores que teñan polo menos unha letra ' a' ,  de series  interpretadas por  personaxes que teñen una letra 'a' no seu nome de personaxe**

### Consulta SQL

```sql
SELECT noma FROM actores WHERE noma LIKE '%a%' AND (SELECT coda FROM interpretesser WHERE codper IN (SELECT codper FROM personaxes WHERE nomper LIKE '%a%')); [ESTA MAL]
```

### Resultado esperado

```
yuan
beatriz
veronica
gray
```

---

## **d3-c14) [DIFICIL] Amosar os nomes dos personaxes dos que dependen directamente soldados**

### Consulta SQL

```sql
SELECT DISTINCT m.nomper FROM personaxes o, personaxes m WHERE o.graduacion='soldado' AND o.codper2=m.codper;
```

### Resultado esperado

```
word
letek
ardor
solok
```
