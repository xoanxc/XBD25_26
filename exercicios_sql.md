# Exercicios SQL -- Obsidian

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

## 3) Indicar os tipos de augas indicadas para pacientes con 'ril'

**ES:** Indicar los tipos de aguas indicadas para pacientes que sufren
de 'ril'.

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

## 4) Amosar códigos de poboacións e número de pacientes

**ES:** Mostrar códigos de poblaciones donde viven pacientes y el número
de pacientes por población.

### Consulta SQL

``` sql
SELECT codp, COUNT(nif)
FROM pacientes
GROUP BY codp;
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

**ES:** Mostrar de cuántos minerales se compone cada tipo de agua.

### Consulta SQL

``` sql
SELECT tipo, COUNT(*)
FROM augas, compon
WHERE augas.coda = compon.coda
GROUP BY tipo;
```

### Resultado esperado

    sulfatadas        1
    ferruginosas      1
    bicarbonatadas    2
    sulfuradas        4
    cloradas          1

------------------------------------------------------------------------

## 6) Médicos que atenderon crónicos e agudos

### Resultado esperado

    m4
    m1
    m5

------------------------------------------------------------------------

## 7) Amosar NIF, nome e poboación dos pacientes

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

## 8) Balneario onde estaba o paciente 3615 o 8/7/2020

### Resultado esperado

    arteixo

------------------------------------------------------------------------

## 9) Amosar NIF dos pacientes se hai tantos crónicos coma agudos

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

## 10) Poboacións que non teñen balnearios

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

## 11) Balnearios que teñen o mesmo nome ca unha poboación

### Resultado esperado

    arnoia
    arteixo
    mondariz
    toxa

------------------------------------------------------------------------

## 12) Pacientes con nome distinto aos médicos

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

## 12_2) Amosar nomes de pacientes e nomes de médicos

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

### Resultado esperado

    carlos
    carlos
    xoan
    mario

------------------------------------------------------------------------

## 16) Hoteis con algunha habitación con internet

### Resultado esperado

    mexico
    andurina
    solpor
    melia

------------------------------------------------------------------------

## 17) Ingresos mensuais dos pacientes crónicos

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

## 18) Balnearios que teñen fisioterapeuta

### Resultado esperado

    banos_de_molgas
    termas_de_cuntis
    caldas_de_partovia

------------------------------------------------------------------------

## 20) Pacientes que estiveron no hotel 'melia' entre 15/7/2020 e 20/7/2020

### Resultado esperado

    ana
    elisa
