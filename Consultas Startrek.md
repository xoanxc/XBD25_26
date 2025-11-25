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
-- Tu consulta aquí
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
-- Tu consulta aquí
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
-- Tu consulta aquí
```

### Resultado esperado

```
enterprise
voyager
```

---

## **d1-c6) Planetas da galaxia 'via_lactea'**

**ES:** Mostrar nombres de planetas de la galaxia 'via_lactea'.

### Consulta SQL

```sql
-- Tu consulta aquí
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
-- Tu consulta aquí
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
-- Tu consulta aquí
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

## **d2-c0') Planetas non visitados**

**ES:** Mostrar nombres de planetas que no fueron visitados.

### Consulta SQL

```sql
-- Tu consulta aquí
```

### Resultado esperado

```
lobar
gork
neptuno
vulcano
```

---

## **d2-c3) Actores que participan en serie y película**

**ES:** Mostrar nombres de actores que participan al menos una vez en una serie y al menos una vez en una película.

### Consulta SQL

```sql
-- Tu consulta aquí
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
-- Tu consulta aquí
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
-- Tu consulta aquí
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
-- Tu consulta aquí
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
-- Tu consulta aquí
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

## **d3-c8) Media de cachehora con nulos**

### Consulta SQL

```sql
-- Tu consulta aquí
```

### Resultado esperado

```
192.592593
```

---

## **d3-c12) Actores con personaje que teñen 'y' no nome**

### Consulta SQL

```sql
-- Tu consulta aquí
```

### Resultado esperado

```
beatriz
kelley
luis
```

---

## **d3-c13) Actores con letra 'a' en serie interpretando personajes con letra 'a'**

### Consulta SQL

```sql
-- Tu consulta aquí
```

### Resultado esperado

```
yuan
beatriz
veronica
gray
```

---

## **d3-c14) Personaxes dos que dependen directamente soldados**

### Consulta SQL

```sql
-- Tu consulta aquí
```

### Resultado esperado

```
word
letek
ardor
solok
```
