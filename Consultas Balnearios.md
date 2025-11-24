
## 1) Amosar nomes de balnearios cuxo coste diario supere os 45 euros

**ES:** Mostrar nombres de balnearios cuyo coste diario supere los 45
euros.

### Consulta SQL

``` sql
SELECT nomb FROM balnearios WHERE costed > 45;
```

### Resultado esperado

    banos_de_molgas
    mondariz
    toxa

------------------------------------------------------------------------

## 2) Amosar nomes de pacientes que vivan na poboación 'brea'

**ES:** Mostrar nombres de pacientes que vivan en la población 'brea'.

### Consulta SQL

``` sql
SELECT pacientes.nomp
FROM pacientes, poboacions
WHERE poboacions.codp = pacientes.codp
  AND poboacions.nomp = 'brea';
```

### Resultado esperado

    pedro
    bieito
    mario

------------------------------------------------------------------------

## 3) Indicar os tipos de augas que estarian indicadas para os pacientes que sufren de 'ril'

### Consulta SQL

``` sql
SELECT tipo
FROM augas
WHERE coda IN (
    SELECT coda
    FROM indicadas
    WHERE codz IN (
        SELECT codz FROM zonas_corporais WHERE nomz = 'ril'
    )
);
```

### Resultado esperado

    bicarbonatadas
    oligometalicas
    sulfatadas

------------------------------------------------------------------------

## 4) Amosar codigos de poboacions onde viven os pacientes e o numero de pacientes que ten cada unha desas poboacions

### Consulta SQL

``` sql
SELECT codp, COUNT(nif) FROM pacientes GROUP BY codp;
```

### Resultado esperado

    2
    p10   2
    p7    3
    p21   1
    p4    2
    p2    1
    p8    2
    p9    4
    p5    1

------------------------------------------------------------------------

## 5) Amosar de cantos minerais se compón cada tipo de auga

### Consulta SQL

``` sql
SELECT tipo, COUNT(*) FROM augas, compon WHERE augas.coda = compon.coda GROUP BY tipo;
```

### Resultado esperado

    sulfatadas        1
    ferruginosas      1
    bicarbonatadas    2
    sulfuradas        4
    cloradas          1

------------------------------------------------------------------------

## 6) Amosar os codigos de medicos que cumplan que asignaron polo menos un balneario a un paciente crónico e prescribiron polo menos un balneario a un enfermo agudo (e dicir, que si asignaron un balneario a un paciente cronico pero non prescribiron ningun a un paciente agudo, ou viceversa,  non deben aparecer no listado)

### Consulta SQL

``` sql
SELECT nomme FROM medicos WHERE codme IN (SELECT DISTINCT codme FROM asignan WHERE codme IN (SELECT codme FROM prescriben));
```

### Resultado esperado

    m4
    m1
    m5

------------------------------------------------------------------------

## 6.1) Amosar os nomes de medicos que cumplan que asignaron polo menos un balneario a un paciente crónico e prescribiron polo menos un balneario a un enfermo agudo (e dicir, que si asignaron un balneario a un paciente cronico pero non prescribiron ningun a un paciente agudo, ou viceversa,  non deben aparecer no listado)

### Consulta SQL

``` sql
SELECT nomme FROM medicos WHERE codme IN (SELECT codme FROM asignan WHERE codme IN (SELECT codme FROM prescriben));
```

### Resultado esperado

    m4
    m1
    m5

------------------------------------------------------------------------
## 7) Amosar  nif e nome de todos e cada un dos pacientes e ademais a poboacion onde viven

### Consulta SQL

``` sql
SELECT nif,pacientes.nomp,poboacions.nomp FROM poboacions right JOIN pacientes ON pacientes.codp=poboacions.codp;
```

### Resultado esperado

    362   ana       arteixo
    3612  elisa     mondariz
    363   carlos    mondariz
    3618  iria      lugo
    3613  mario     brea
    3610  bieito    brea
    364   pedro     brea
    369   xoan      davila
    365   bea       davila
    3617  antia     carballo
    3614  palmira   carballo
    368   carlos    carballo
    366   eva       carballo
    3616  xose      carballino
    3615  lucia     carballino
    361   luis      moimenta
    3611  carmen
    367   bea

------------------------------------------------------------------------

## 8) [MODIFICADA] Amosar o nome do balneario se atopaba o paciente agudo de nif 3615 o 8/7/2020


### Consulta SQL

``` sql
SELECT nomb FROM balnearios WHERE codb IN (SELECT codb FROM prescriben WHERE nif='3615' AND dea<='8/7/2020' AND dsa>='8/7/2020');
```

### Resultado esperado

    arteixo

------------------------------------------------------------------------

## 9) Amosar os nif de todos os pacientes se o numero de pacientes cronicos e igual  ao numero de pacientes agudos

### Consulta SQL

``` sql
SELECT nif FROM pacientes WHERE (SELECT COUNT(*) FROM cronicos)=(SELECT COUNT(*) FROM agudos);
```

### Resultado esperado

    361
    3610
    3611
    3612
    3613
    3614
    3615
    3616
    3617
    3618
    362
    363
    364
    365
    366
    367
    368
    369

------------------------------------------------------------------------

## 10) Amosar os nomes das poboacions que non posuan balnearios

### Consulta SQL

``` sql
 --- Introducir Consulta
```

### Resultado esperado

    lugo
    moimenta
    carballo
    santiago
    carballino
    coruna
    guitiriz
    ourense
    cangas
    vigo
    bueu

------------------------------------------------------------------------

## 11) Amosar nomes de balnearios que se chamen exactamente igual que nomes de poboacions

### Consulta SQL

``` sql
 --- Introducir Consulta
```

### Resultado esperado

    arnoia
    arteixo
    mondariz
    toxa

------------------------------------------------------------------------

## 12) Amosar nomes de pacientes distintos aos nomes de calquera medico, sen repeticion

### Consulta SQL

``` sql
SELECT DISTINCT nomp FROM pacientes WHERE nomp NOT IN (SELECT nomme FROM medicos);
```

### Resultado esperado

    ana
    antia
    bea
    bieito
    carlos
    carmen
    elisa
    eva
    iria
    lucia
    luis
    palmira
    pedro
    xoan
    xose

------------------------------------------------------------------------

## 12_2) Amosar nomes de pacientes e nomes dos medicos

### Consulta SQL

``` sql
SELECT nomp nomes_pac-med FROM pacientes UNION SELECT nomme FROM medicos;
```

### Resultado esperado

    eva
    rosa
    antia
    pedro
    francisco
    mario
    elisa
    carmen
    palmira
    anabel
    bieito
    ana
    manuel
    bea
    xoan
    iria
    lucia
    elena
    federico
    luis
    carlos
    xose

------------------------------------------------------------------------

## 13) Amosar nomes de pacientes sen repetición

### Consulta SQL

``` sql
SELECT DISTINCT nomp FROM pacientes;
```

### Resultado esperado

    carlos
    bieito
    elisa
    xoan
    iria
    antia
    mario
    palmira
    ana
    bea
    carmen
    xose
    lucia
    luis
    pedro
    eva

------------------------------------------------------------------------

## 14) Pacientes con polo menos unha 'a' e unha 'o'

### Consulta SQL

``` sql
SELECT nomp FROM pacientes WHERE nomp LIKE '%a%' AND nomp LIKE '%o%'
```

### Resultado esperado

    carlos
    carlos
    xoan
    mario

------------------------------------------------------------------------
## [NON FACER] 15) Amosar os nomes de todos e cada un dos medicos e os  nomes dos seus xefes
### Consulta SQL

``` sql
SELECT m.nomme medico,mx.nomme xefe FROM medicos m left JOIN medicos mx ON m.xef=mx.codme;
```

### Resultado esperado

    francisco	federico
    rosa		federico
    manuel		anabel
    elena		anabel
    mario		elena
    anabel
    federico

------------------------------------------------------------------------
## 16) Amosar os nomes dos hoteis que posuan  algunha habitacion con interede

### Consulta SQL

``` sql
SELECT nomh FROM hoteis WHERE codh IN (SELECT codh FROM habitacions WHERE interede='s');
```

### Resultado esperado

    mexico
    andurina
    solpor
    melia

------------------------------------------------------------------------

## 17) Amosar cales son os ingresos mensuais  dos pacientes cronicos

### Consulta SQL

``` sql
SELECT ingm FROM pacientes WHERE nif IN (SELECT nif FROM cronicos);
```

### Resultado esperado

    1000
    1200
    1300
    900
    850
    1400
    1600
    1250
    1100

------------------------------------------------------------------------

## 18) Amosar os nomes dos balnearios que posuan  fisioterapeuta

### Consulta SQL

``` sql
SELECT nomb FROM balnearios WHERE codb IN (SELECT codb FROM cat1 WHERE fisioterapeuta='s')
```

### Resultado esperado

    banos_de_molgas
    termas_de_cuntis
    caldas_de_partovia

------------------------------------------------------------------------

## 20) Pacientes que estiveron no hotel 'melia' entre 15/7/2020 e 20/7/2020

### Resultado esperado

    ana
    elisa
