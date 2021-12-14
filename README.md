# VO-ESTRANGERIA
```
Realitzat per: Departament d’Operacions
```
```
Versió: 1.
```
```
Data: 24/11/
```
## Via Oberta – Estrangeria - Dades de

## residència legal

# Document d’integració del servei


```
i
```
```
Integració del servei Via Oberta - Estrangeria - Dades
de residència legal
```
```
DI - Via Oberta - Estrangeria - Dades de residència legal.doc,
```
```
pàg 1/
```
## Control del document

### Informació general

Títol: Via Oberta – Estrangeria Dades de residència legal

Creat per: Departament d’Operacions

A revisar per: Departament d’Operacions

A aprovar per: Departament d’Operacions

Llista de distribució:

Nom del document: DI - Via Oberta - Estrangeria - Dades de residència
legal.doc

### Històric de revisions

```
Versió Data Autor Comentaris
```
```
V1.0 11/12/2013 Carlos Mena Fernandez Creació del document
```

```
ii
```
```
Integració del servei Via Oberta - Estrangeria - Dades
de residència legal
```
```
DI - Via Oberta - Estrangeria - Dades de residència legal.doc,
```
```
pàg 2/
```
## Índex

##### 1 Introducció ...................................................................................................................................

##### 2 Transmissions de dades disponibles ..........................................................................................

##### 3 Missatgeria dels serveis ..............................................................................................................

##### 3.1 Verificació de les dades de residència legal (RESIDENCIA_LEGAL) .......................................

##### 3.1.1 Petició – dades genèriques ................................................................................ 1

##### 3.1.2 Petició – dades específiques .............................................................................. 2

##### 3.1.3 Resposta – dades específiques ......................................................................... 2


DI - Via Oberta - Estrangeria - Dades de residència legal.doc

```
Integració del servei Via Oberta - Estrangeria -
Dades de residència legal
```
```
pàg 1/
```
## 1 Introducció

Aquest document detalla la missatgeria associada al servei d’obtenció de les dades de residència
legal del Ministerio de Interior.

Per a poder realitzar la integració cal conèixer prèviament la següent documentació:

- Document de Missatgeria Genèrica de la PCI del Consorci AOC.

## 2 Transmissions de dades disponibles

Les dades disponibles a través del servei són les que es presenten a continuació:

###### EMISSOR

```
Ministerio de Interior
PRODUCTE MODALITAT DESCRIPCIÓ
ESTRANGERIA RESIDENCIA_LEGAL Consulta de les dades de residència legal.
```
La consulta del producte té disponible la versió imprimible del resultat de la consulta en format PDF.
Per més detalls adreceu-vos a l’apartat Extensions de missatgeria del document de missatgeria
genèrica.

## 3 Missatgeria dels serveis

```
L’emissor de les dades requereix que s’informin les dades del funcionari que realitza la consulta.
Així, cal informar els següents camps de l’element Funcionario del bloc de dades genèriques:
```
```
/Peticion/Funcionario/NombreCompletoFuncionario,
/Peticion/Funcionario/NifFuncionario,
//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NombreCompletoFuncionario i
//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NifFuncionario
```
### 3.1 Verificació de les dades de residència legal

### (RESIDENCIA_LEGAL)

#### 3.1.1 Petició – dades genèriques

```
Element Descripció
```
//DatosGenericos/Titular/TipoDocumentacion (^) Tipus de documentació (NIE ).
//DatosGenericos/Titular/Documentacion Documentació.


DI - Via Oberta - Estrangeria - Dades de residència legal.doc

```
Integració del servei Via Oberta - Estrangeria -
Dades de residència legal
```
```
pàg 2/
```
#### 3.1.2 Petició – dades específiques

Element Descripció
peticioConsultaDadesResidenciaLegal/
dataNaixement

```
Any de naixement del titular (format AAAA).
```
peticioConsultaDadesResidenciaLegal/
nacionalitat

```
Nacionalitat del titular (codificació ISO 3166-
Alpha 3).
```
#### 3.1.3 Resposta – dades específiques

Element Descripció
respostaVerificacioDadesResidencia/
EstadoSituacion

```
Bloc de dades corresponent a la informació sobre
les dades de residencia legal del titular.
```
respostaVerificacioDadesResidencia/
resultat/codiResultat

```
Codi de resultat:
```
- 0000 : existeix autorització de residència o
    estància.
- 0001 : no existeix autorització de residència o
    estància.
- 0002 : ciutadà nacionalitzat espanyol.
- 0003 : no s’ha localitzat cap ciutadà amb la
    documentació aportada.
- 0004 : existeix més d’un estranger amb les
    dades proporcionades. Cal informar més a la
    consulta per a distingir-los.
- 0502 : error realitzant la consulta.

respostaVerificacioDadesResidencia/
resultat/descripcio

```
Descripció del resultat.
```

```
DI - Via Oberta - Estrangeria - Dades de residència legal.doc
```
```
Integració del servei Via Oberta - Estrangeria -
Dades de residència legal
```
```
pàg 3/
```
```
3.1.3.1 EstadoSituacion
```
Element Descripció
//EstadoSituacion/Residencia
Tipus d’autorització de residència:

- 0 : Sense permís.
- 1 : Comunitari.
- 2 : Familiar de comunitari.
- 3 : Extracomunitari.

```
Pot donar-se el cas que el codi de residència
sigui 0 i el codi de resultat sigui 0000. Aquest
cas indica que el ciutadà disposa de permís
d’estància però no de residència.
```
//EstadoSituacion/DescripcionAutorizacion
Descripció literal del tipus d’autorització de la residència.

//EstadoSituacion/FechaResolucion
Data de resolució del tràmit de residència (format
DD/MM/AAAA ).

//EstadoSituacion/FechaCaducidad
Data de caducitat de la residència legal (format
DD/MM/AAAA ).

//EstadoSituacion/Renovacion
/FechaSolicitudRenovacion

```
Data de la sol·licitud de renovació de la residència legal.
```
```
En cas de que l’autorització hagi caducat, el camp vindrà
informat només en el cas que el titular hagi presentat una
sol·licitud de renovació.
```
```
Durant el tràmit de renovació, s’estén la vigència anterior.
```
//EstadoSituacion/EstanciaEspecial
Indicador de si té permís d’Estància Especial segons Art
37 RD 557/2011:

- 1 : Estudis.
- 2 : Investigació o formació.
- 3 : Mobilitat alumnes.
- 4 : Pràctiques no laborables.
- 5 : Serveis de voluntariat.
- 6 : Estudis MIR.
- 7 : Altres estàncies.
- 8 : Estudis / intercanvi.
- 10 : Estudis familiar.
- 11 : Investigació o formació familiar.
- 12 : Mobilitat d’alumnes familiar.
- 13 : Pràctiques no laborables familiar.
- 14 : Serveis de voluntariat familiar.


DI - Via Oberta - Estrangeria - Dades de residència legal.doc

```
Integració del servei Via Oberta - Estrangeria -
Dades de residència legal
```
```
pàg 4/
```

