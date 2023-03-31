<style>
r { color: Red }
g { color: Green }
center { text-align:center }
</style>

<html><h1 style="text-align:center">UNIVERSIDAD DE ALMERÍA</h1><br>

<h2 style="text-align:center">Escuela Superior de Ingeniería</h2>
<p style="text-align:center"><img  style="text-align:center" src="logo.png"></p>
<h3 style="text-align:center">Grado: 	Ingeniería Informática</h3>
<h3 style="text-align:center">Asignatura:	Procesos de Ingeniería del Software 2</h3>
<h4 style="text-align:center">Curso Académico: 	2022/23</h4>
<h2 style = "text-align:center;color: blue;">Prácticas: Lab 2 SourceMonitor</h2>
<p style="text-align:center">
Profesora: 	Isabel María del ÁGUILA CANO<br>
&copy; Ángel Joaquín GARCÍA MÁRQUEZ<br> 
Fecha: 	28 de marzo de 2023<br>
</p></html>

# Introducción

SourceMonitor es una aplicación para recopilar métricas de código fuente escrito en Java, C++, C, C#, Visual Basic (VB6), VB.NET, Delphi o HTML.

En el caso de código fuente escrito en Java las métricas que recopila son las siguientes:
* **Lines**: nº de líneas de código incluyendo las líneas vacías y líneas de comentarios.
* **Statements**: nº de líneas de código compilable, sin incluir las llaves. Se incluyen las declaraciones (clase, método, if, for, while, …) y sentencias (terminadas en ;).
* **% Branches**: % de nº de **ramas** (declaraciones if, for, while, …) respecto a Statements.<br>
  ```console 
  %Branches = (ramas/Statements)*100
  ```
* **Calls**: nº total de llamadas a métodos en las sentencias.
* **% Comments**: % de líneas de **comentarios** respecto a Statements<br>
  ```console 
  %Comm = (comentarios/Statements)*100 
  ```
* **Classes**: nº de declaraciones de clase y de interface en el fichero. Suele tener el valor 1.
* **Methods/Class**: relación de nº de **métodos** respecto a Classes. .
Met/Class = métodos/Classes
* **Avg Stmts/Method**: media del nº de **sentencias** (líneas terminadas en ;) de los métodos.<br>
  ```console   
  AvgSt/Met = sentencias/métodos
  ```
* **Max Complexity**: valor máximo de las **complejidades** ciclomáticas (CC=1+nodos predicado) de los métodos.
* **Avg Complexity**: media de las complejidades ciclomáticas de los métodos.<br>
  ```console   
  AvgCC:= complejidades/métodos 
  ``` 
* **Max Depth**: valor máximo de los **niveles** de sangría que hay de los Statements. [
* **Avg Depth**: media de los niveles de sangría de los Statements.<br>
  ```console   
  AvgDep = niveles/Statements
  ```

- - -

Los intervalos propuestos por la heurística se indican en la tabla siguiente:
|Métrica|%Comm|Met/Class| AvgSt/Met | MaxCC | AvgCC	 | MaxDep	 | AvgDep  |  
|---|---|---|---|---|---|---|---|
|**Intervalo**|[8,0-20,0]|[4,0-16,0]|[6,0-12,0]|[2-8]	 |[2,0-4,0]	 |[3-7]	 |[1,0-2,2] |  

<html><p style="text-align:center"><b>Tabla 0.1</b>: Rangos heurísticos de las métricas</p></html>

# Proyecto 1
Consta de 6 archivos. La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 1.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado. Al analizar el código se obtienen los datos que se muestran en las tablas 1.2, 1.3 y 1.4.

|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|Linea         |30   |	17 |5,9	 |1	   |**3,3**|1	|4,00	|&nbsp;**2,50**|2	   |**1,25**|3	   |1,53|
|Poligono      |68   |39	 |15,4 |49	 |**7,4**|1	|4,00	|&nbsp;7,75	   |4	   |2,50	   |4	   |1,97|
|Punto	       |33	 |17	 |0,0	 |2	   |**0,0**|1	|6,00	|&nbsp;**1,17**|**1**|**1,00**|**2**|1,29|
|UsoPoligono   |57	 |41	 |0,0	 |40	 |**5,3**|1	|1,00	|*37,00*       |**1**|**1,00**|**2**|1,83|
|Vector	       |33	 |17	 |0,0	 |10	 |**0,0**|1	|6,00	|&nbsp;**1,17**|**1**|**1,00**|**2**|1,29|
|PoligonoTest  |5		 |2	   |0,0	 |0	   |**0,0**|1	|0,00	|&nbsp;**0,00**|**0**|**0,00**|**0**	|**0,00**|
|**PROYECTO&nbsp;1**|226	 |133	 |5,3	 |102	 |**4,0**|6	|3,50	|&nbsp;**4,38**|4	|**1,33**|4	|1,67|

<html><p style="text-align:center"><b>Tabla 1.1</b>: Métricas de los archivos .java del proyecto 1 obtenidas por SourceMonitor</p></html>

|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Linea       |30	|17	|1	|1	|4	|10	|1,1,1,2	|2|1,25
|Poligono    |68	|39	|6	|5	|4	|31	|1,4,4,1	|4|2,50|
|Punto	     |33	|17	|0	|0	|6	|7	|1,1,1,1,1,1	|1|1,00|
|UsoPoligono |57	|41	|0	|3	|1	|37	|1	|1|1,00|
|Vector	     |33  |17	|0	|0	|6	|7	|1,1,1,1,1,1|1|1,00|
|PoligonoTest|5	  |2	|0	|0	|0	|0	|-	|-|-|
|**PROYECTO&nbsp;1**|226	|133|7	|9	|21	|92 |1,...,4|4|1,33|
<html><p style="text-align:center"><b>Tabla 1.2</b>: Métricas del proyecto 1 obtenidas del código</p></html>

|File        |Nivel&nbsp;0|Nivel&nbsp;1|Nivel&nbsp;2|Nivel&nbsp;3|Nivel&nbsp;4|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:   |---:   |---:   |---:   |---:   |---:    |---: |---:    | ---: |
|Linea         |2	|5	|9	|1	|0	|**3**|26	|17	|**1,53**|
|Poligono      |3	|5	|22	|8	|1	|**4**|77	|39	|**1,97**|
|Punto	       |2	|8	|7	|0	|0	|**2**|22	|17	|**1,29**|
|UsoPoligono   |3	|1	|37	|0	|0	|**2**|75	|41	|**1,83**|
|Vector	       |2	|8	|7	|0	|0	|**2**|22	|17	|**1,29**|
|PoligonoTest  |2	|0	|0	|0	|0	|**0**|0	|2	|**0,00**  |
|**PROYECTO&nbsp;1**|14|27	|82	|9	|1	|**4**|222|133|**1,67**|
<html><p style="text-align:center"><b>Tabla 1.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del proyecto 1</p></html>

|File        |<td colspan="6"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td>  ||||||
|---         |:---    |---       |---         |---        |---   |---    |
|Linea       |Linea&rarr;1	|toString&rarr;1	|implicita&rarr;1	|puntoCorte&rarr;2 |||
|Poligono    |Poligono&rarr;1|concavo&rarr;4	|centroide&rarr;4	|toString&rarr;1 |||		
|Punto	     |Punto&rarr;1	|getPosX&rarr;1	|setPosX&rarr;1	|getPosY&rarr;1	|setPosY&rarr;1	|toString&rarr;1|
|UsoPoligono |main&rarr;1	||||||				
|Vector	     |Vector&rarr;1	|coordenadaX&rarr;1	|coordenadaX&rarr;1	|modulo&rarr;1	|productoVectorial&rarr;1	|toString&rarr;1|
|PoligonoTest| - ||||||
<html><p style="text-align:center"><b>Tabla 1.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del proyecto 1</p></html>

**Conclusiones:**
* **Falta implementar** *PoligonoTest.java*. 
* Se necesita **refactorizaión** en *UsoPoligono.java* ya que tiene un sólo método con demasiadas sentencias.
* **Faltan comentarios** en los códigos, excepto en el de *Poligono.java*.


 # Proyecto 2
Consta de 5 archivos. La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 2.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Al analizar el código se obtienen los datos que se muestran en las tablas 2.2, 2.3 y 2.4.


|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|App	            |107	|81	|28,4	|81	|**0,0**|1	|&nbsp;**2,00**|*37,50*|*16*        |*12,50*|6	|*3,54*|
|interpolacion    |121	|66	|16,7	|37	|  8,3  |1	|&nbsp;4,00	   |*13,25*|&nbsp;*9*   |&nbsp;4,00	|5	|2,20|
|polinomio        |286	|192|33,9	|116|**0,7**|1	|12,00|*14,33* |*32*   |&nbsp;*6,83*|*9+*|*3,53*|
|InterpolacionTest|	81	|37	|10,8	|20 |**7,4**|1	|&nbsp;5,00	   |&nbsp;**4,40**|&nbsp;2|&nbsp;**1,80**|3	|1,59|
|PolinomioTest    |255	|183|2,2	|115|**7,5**|1	|&nbsp;6,00	   |*26,50*|&nbsp;3	|&nbsp;**1,67**|4	|1,87|
|**PROYECTO&nbsp;2**   |850	|559|19,1	|369|**4,4**|5	|&nbsp;**5,80**|*16,59*|*32*|&nbsp;*4,90*|*9+*|*2,70*|
<html><p style="text-align:center"><b>Tabla 2.1</b>: Métricas de los archivos .java del proyecto 2 obtenidas por SourceMonitor</p></html>

|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|App	            |107	|81	|23	|0	|2	|75	|16,9	    |16|12,50|
|interpolacion    |121	|66	|11	|10	|4	|53	|9,4,1,2  |9	|4,00|
|polinomio        |286	|192|65	|2	|12	|172|1,1,2,1,3,5,<br>9,2,1,2,32,23	|9|12,00|
|InterpolacionTest|81	  |37	|4	|6	|5	|22	|2,1,2,2,2	|2|5,00
|PolinomioTest    |255 	|183|4	|19	|6	|159|1,1,3,1,3,1	|3|6,00
|**PROYECTO&nbsp;2**   |850	|559|107|37	|29	|481|1,...,9|9|5,80
<html><p style="text-align:center"><b>Tabla 2.2</b>: Métricas del proyecto 2 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|N&nbsp;7|N&nbsp;8|N&nbsp;9|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:      | ---:  |---:    |---:    |---:    |---: | ---:   |---: |
|App	            |4	|2	|21	|15	|6	|24	|9  |0	|0	|0	|**6**|287 |81	|**3,54**|
|interpolacion    |7	|6	|32	|11	|8	|2	|0  |0	|0	|0	|**5**|145 |66	|**2,20**|
|polinomio        |6	|14	|48	|39	|30	|25	|16	|4	|8	|2	|**9**|678 |192	|**3,53**|
|InterpolacionTest|10	|5	|12	|10	|0	|0	|0	|0	|0	|0	|**3**|59	 |37	|**1,59**|
|PolinomioTest    |8	|16	|151|7	|1	|0	|0	|0	|0	|0	|**4**|342 |183	|**1,87**|
|**PROYECTO&nbsp;2**   |35	|43	|264|82	|45	|51	|25	|4	|8	|2	|**9**|1511|559	|**2,70**|
<html><p style="text-align:center"><b>Tabla 2.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del proyecto 2</p></html>

File        |<td colspan="6"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td> ||||||
|---         |:---    |---       |---         |---        |---   |---    |
|App	            |main&rarr;6	|operaciones&rarr;9	|||||			
|interpolacion    |interpol&rarr;9	|sustitucion&rarr;4	|calculoXr&rarr;1	|main&rarr;2	|||	
|polinomio        |polinomio&rarr;1<br>ruffini&rarr;9	|add&rarr;1<br>eliminarX&rarr;2	|listaPolinomios&rarr;2<br>getResto&rarr;1	|getPolinomio&rarr;1<br>calculoRouth&rarr;2	|suma&rarr;3<br>routh&rarr;32	|multiplicacion&rarr;5<br>poliToString&rarr;23|
|InterpolacionTest|…Mismos&rarr;2	|sustitucionTest&rarr;1	|precisionTest&rarr;2	|…GranError&rarr;2		|…PeqError&rarr;2||
|PolinomioTest    |Before&rarr;1	|Sumatest&rarr;1	|productoTest&rarr;3	|ruffiniTest&rarr;1	|Equals&rarr;3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	|routhTest&rarr;1|
<html><p style="text-align:center"><b>Tabla 2.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del proyecto 2</p></html>

**Conclusiones:**
* Se necesita **refactorización** en *App.java*, *polinomio.java* y *PolinomioTest.java* ya que tienen demasiadas sentencias por método.<BR>
En *App.java* y *PolinomioTest.java* , además, hay demasiada complejidad ciclomática.
* **Faltan comentarios** en los códigos de *App.java* y *polinomio.java*.

 # Proyecto 3
Consta de 17 archivos. La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 3.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Al analizar el código se obtienen los datos que se muestran en las tablas 3.2 y 3.3.


|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|Poligono	         |387	|244 |25,8  |151|11,9	|1|*21,00*	|10,19	|*27*	|*4,90*|*9+*|*2,84*
|Poligono01	       |309	|166 |28,3	|81	|*23,3*|1| 14,00	|10,43	|*27*	|*5,43*|*9+*|*3,02*
|PoligonosJPanel   |58	|30	 |20,0	|11	|*29,3*	|1| 2,00	|9,50	  |7	|4,00	|4	|1,80
|Punto	           |72	|25	 |12,0	|2	|*38,9*	|1| 7,00	|**2,14**|3	|**1,57**	|3	|1,60
|Recta	           |239	|119 |25,2	|47	|*26,4*	|1| 14,00	|7,21	  |*15*	|3,50	|6	|*3,06*
|Triangulo	       |312	|130 |23,8	|78	|*34,6*	|1| 15,00	|7,20	  |*33*	|3,60	|7	|*2,98*
|TriangulosJPanel	 |84	|55	 |21,8	|36	|11,9	 |1|**2,00**|*21,00*	|*11*	|*7,00*|4	|*2,31*
|UsoPoligono01	   |78	|38	 |7,9	  |32	|*33,3*	|1|**3,00**|10,00	|4	|2,00	|3	|2,21
|UsoTriangulacion	 |95	|45	 |15,6  |35	|*27,4*	|1|**1,00**|*38,00*	|8	|*8,00*|4	|*2,64*
|Main	             |30	|20	 |5,0	  |13	|**0,00**|1|**2,00**|**5,50**|2	|**1,50**|3	|1,60
|PoligonoController|232	|196 |14,3	|164|**0,00**	|2|**3,50**|*18,86*|*29*	|*6,29*|6	|*2,93*
|DoublyLinkedList	 |158	|118 |11,0	|28	|8,9	|3|	6,67	|**4,15**|4	|**1,65**|4	|*2,23*
|lector	           |23	|8	 |0,00	|3	|*34,8*	|1|**2,00**|**1,00**|**1**|**1,00**|**2**|**0,88**
|Poligono01test	   |62	|43	 |0,00	|24	|**0,00**|1|	4,00	|7,75	  |**1**|**1,00**|**2**|1,63
|Puntotest	       |37	|28	 |0,00	|29	|**0,00**|1|**3,00**|6,33	  |**1**|**1,00**|**2**|1,50
|Rectatest	       |115	|84	 |0,00	|72	|**0,00**|1|	9,00	|6,89	  |**1**|**1,00**|**2**|1,68
|TriangulacionTest |38	|24	 |0,00	|16	|**0,00**|1|**2,0**|8,00	  |**1**|**1,00**|**2**|1,42
|**PROYECTO&nbsp;3**|2329|1373|17,8	|822|17,9	|20|6,40	|8,35	  |*33*|*3,35*|*9+*|*2,57*
<html><p style="text-align:center"><b>Tabla 3.1</b>: Métricas de los archivos .java del proyecto 3 obtenidas por SourceMonitor</p></html>

|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Poligono	         |387	|244 |63 |46	|21	|214|1,2,1,2,10,16,4,4,1,27,<br>1,1,6,2,15,2,2,1,1,2,2	|27 |4,90
|Poligono01	       |309	|166 |47 |72	|14	|146|1,2,10,16,4,4,1,1,1,1,<br>27,1,1,6	|27 |5,43
|PoligonosJPanel   |58	|30	 |6	 |17	|2	|19	|7,1	|7|4,00
|Punto	           |72	|25	 |3	 |28	|7	|15	|3,1,1,1,1,1,3 |3 |1,57
|Recta	           |239	|119|30	 |63	|14	|101|3,1,1,1,6,14,2,15,<br>1,1,1,1,1,1	|15 |3,50
|Triangulo	       |312	|130 |31 |108	|15	|108|1,1,3,5,1,1,1,1,1,1,33<br>2,1,1,1	|33 |3,60
|TriangulosJPanel	 |84	|55	 |12 |10	|2	|42	|11,3	  |11|7,00
|UsoPoligono01	   |78	|38	 |3	 |26	|3	|30	|4,1,1	|4 |2,00
|UsoTriangulacion	 |95	|45	 |7	 |26	|1	|38	|8      |8 |8,00
|Main	             |30	|20	 |1	 |0	  |2	|11	|2,1	  |2 |1,50
|PoligonoController|232	|196 |28 |0	  |7	|132|1,3,1,3,2,29,5	|29 |6,29
|DoublyLinkedList	 |158	|118 |13 |14	|20	|83	|1,1,2,3,3,1,1,1,1,1,1,<br>2,2,2,4,1,2,1,1,2	|4 |1,65
|lector	           |23	|8	 |0	 |8	  |2	|2	|1,1	    |1 |1,00
|Poligono01test	   |62	|43	 |0	 |0	  |4	|31	|1,1,1,1	|1 |1,00
|Puntotest	       |37	|28	 |0	 |0	  |3	|19	|1,1,1	  |1 |1,00
|Rectatest	       |115	|84	 |0	 |0	  |9	|62	|1.1.1.1.1.1.1.1.1	|1 |1,00
|TriangulacionTest |38	|24	 |0	 |0	  |2	|16	|1,1	    |1 |1,00
|**PROYECTO&nbsp;3**|2329|1373|244|418	|128|1069|1,...,33|33|3,35
<html><p style="text-align:center"><b>Tabla 3.2</b>: Métricas del proyecto 3 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|N&nbsp;7|N&nbsp;8|N&nbsp;9|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:      | ---:  |---:    |---:    |---:    |---: | ---:   |---: |
|Poligono	         |7	|23	|82	|71	|35	|15	|4	|3	|3	|1	|**9**|693	|244	|**2,84**|
|Poligono01	       |5	|15	|49	|47	|25	|14	|4	|3	|3	|1	|**9**|501	|166	|**3,02**|
|PoligonosJPanel   |6	|5	|10	|7	|2	|0	|0	|0	|0	|0	|**4**|54	  |30	  |**1,80**|
|Punto	           |2	|8	|13	|2	|0	|0	|0	|0	|0	|0	|**3**|40	  |25	  |**1,60**|
|Recta	           |3	|15	|29	|27	|20	|20	|5	|0	|0	|0	|**6**|364	|119	|**3,06**|
|Triangulo	       |6	|16	|41	|20	|19	|16	|11	|1	|0	|0	|**7**|387	|130	|**2,98**|
|TriangulosJPanel	 |6	|7	|12	|24	|6	|0	|0	|0	|0	|0	|**4**|127	|55	  |**2,31**|
|UsoPoligono01	   |4	|4	|10	|20	|0	|0	|0	|0	|0	|0	|**3**|84	  |38	  |**2,21**|
|UsoTriangulacion	 |5	|2	|11	|13	|14	|0	|0	|0	|0	|0	|**4**|119	|45	  |**2,64**|
|Main	             |7	|2	|3	|8	|0	|0	|0	|0	|0	|0	|**3**|32	  |20	  |**1,60**|
|PoligonoController|18|44	|40	|17	|12	|45	|22	|0	|0	|0	|**6**|574	|196	|**2,93**|
|DoublyLinkedList	 |4	|16	|49	|47	|2	|0	|0	|0	|0	|0	|**4**|263	|118	|**2,23**|
|lector	           |3	|3	|2	|0	|0	|0	|0	|0	|0	|0	|**2**|7	  |8	  |**0,88**|
|Poligono01test	   |4	|8	|31	|0	|0	|0	|0	|0	|0	|0	|**2**|70	  |43	  |**1,63**|
|Puntotest	       |5	|4	|19	|0	|0	|0	|0	|0	|0	|0	|**2**|42	  |28	  |**1,50**|
|Rectatest	       |5	|17	|62	|0	|0	|0	|0	|0	|0	|0	|**2**|141	|84	  |**1,68**|
|TriangulacionTest |6	|2	|16	|0	|0	|0	|0	|0	|0	|0	|**2**|34	  |24	  |**1,42**|
|**PROYECTO&nbsp;3**|96|191|479|303|135|110|46	|7	|6	|2	|**9**|3533	|1373	|**2.57**|
<html><p style="text-align:center"><b>Tabla 3.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del proyecto 3</p></html>


**Conclusiones:**
* Se necesita **refactorización** en *UsoTriangulacion.java*, *TiangulosPanel.java* y *PoligonoController.java* ya que tienen <u>demasiadas sentencias por método</u>. Hay que definir más métodos y repartir el código en varios.
* Se necesita **refactorización** en *Poligono.java*, *Poligono01.java* y *Triángulo.java* ya que tienen algunos métodos con <u>demasiada complejidad ciclomática</u>. Hay que definir más métodos y repartir el código en varios.
* Se necesita **revisar los comentarios** porque no tienen o tienen demasiados, excepto en *Poligono.java*, *TriángulosJPanel.java* y *DoublyLinkedList.java*.


# Proyecto 4
Consta de 6 archivos. La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 4.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado. Al analizar el código se obtienen los datos que se muestran en las tablas 4.2, 4.3 y 4.4.

|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|Ejercicio2	       |104	|58	|15,5	|26	|17,3	  |1	|**2,00**|*23,50* |10	|5,50	|4	|2,14
|Ejercicio3	       |133	|69	|20,3	|41	|16,5	  |1	|5,00	   |11,06	  |8	|3,80	|4	|2,10
|Ejercicio3Programa|35	|20	|5,0	|13	|**5,7**|1	|**1,00**|*15,00* |2	|2.00	|3	|1,60
|Polinomio	       |106	|50	|32,0	|48	|**5,7**|2	|**1,00**|**0,50**|**1**|**1,00**|4	|*2,28*
|Ejercicio2Test	   |223	|148|0,0	|137|**3,6**|1	|4,00	   |*34,75* |**1**|**1,00**|**2**|1.91
|PolinomiosTest	   |148	|96	|0,0	|82	|**0,0**|1	|5,00	   |*16,80* |2	|**1,20**|3	|1,82
|**PROYECTO&nbsp;4**|749	|441|9,1	|347|**7,5**|7	|**2,71**|*18,11* |10	|2,32	|4	|1,98
<html><p style="text-align:center"><b>Tabla 4.1</b>: Métricas de los archivos .java del proyecto 4 obtenidas por SourceMonitor</p></html>

|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Ejercicio2	       |104	|58	|9	|18	|2	|47	|1,10	    |10|5,50
|Ejercicio3	       |133	|69	|14	|22	|5	|58	|1,3,8,5,2|8 |3,80
|Ejercicio3Programa|35	|20	|1	|2	|1	|15	|2	      |2 |2.00
|Polinomio	       |106	|50	|16	|6	|2	|1	|1,1	    |1 |1,00
|Ejercicio2Test	   |223	|148|0	|8	|4	|139|1,1,1,1	|1 |1,00
|PolinomiosTest	   |148	|96	|0	|0	|5	|84	|1,1,1,1,2|1 |1,20
|**PROYECTO&nbsp;4**|749	|441|40	|56	|19	|344|1,...,10 |10|2,32
<html><p style="text-align:center"><b>Tabla 4.2</b>: Métricas del proyecto 4 obtenidas del código</p></html>

|File        |Nivel&nbsp;0|Nivel&nbsp;1|Nivel&nbsp;2|Nivel&nbsp;3|Nivel&nbsp;4|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:   |---:   |---:   |---:   |---:   |---:    |---: |---:    | ---: |
|Ejercicio2	       |3	|8	|32	|8	|7	|**4**|124	|58	|**2,14**|
|Ejercicio3	       |4	|7	|39	|16	|3	|**4**|145	|69	|**2,10**|
|Ejercicio3Programa|4	|1	|14	|1	|0	|**3**|32	  |20	|**1,60**|
|Polinomio	       |3	|2	|27	|14	|4	|**4**|114	|50	|**2,28**|
|Ejercicio2Test	   |5	|4	|139|0	|0	|**2**|283	|148|**1.91**|
|PolinomiosTest	   |7	|5	|83	|2	|0	|**3**|175	|96	|**1,82**|
|**PROYECTO&nbsp;4**|26|27	|334|41	|14	|**4**|872	|441|**1,98**|
<html><p style="text-align:center"><b>Tabla 4.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del proyecto 4</p></html>

|File        |<td colspan="5"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td>  |||||
|---         |:---    |---       |---         |---        |--- |   
|Ejercicio2	       |Ejercicio2&rarr;1	|ruthHurtwitz&rarr;10|			
|Ejercicio3	       |Ejercicio3&rarr;1	|interpolate&rarr;3	|comprobarRaiz&rarr;8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	|evaluaciones&rarr;5	|arrayAsList&rarr;2|
|Ejercicio3Programa|main&rarr;2|		
|Polinomio	       |…Error&rarr;1	|…Error&rarr;1|			
|Ejercicio2Test	   |testEstable&rarr;1	|testDegeneracion&rarr;1	|testInestable&rarr;1	|testCritico&rarr;1|
|PolinomiosTest	   |…Iguales&rarr;1	|…PrimeroMayor&rarr;1	|…SegundoMayor&rarr;1	|testProducto&rarr;1	|testDivision&rarr;2|
<html><p style="text-align:center"><b>Tabla 4.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del proyecto 4</p></html>

**Conclusiones:**
* Se necesita **refactorización** en *Ejercicio2.java*  y *Ejercicio3Programa.java* ya que tienen <u>pocos métodos</u> y <u>demasiadas sentencias por método</u>. Hay que definir más métodos y repartir el código en varios.<BR>
En *Ejercicio2.java*, además, los métodos tienen <u>demasiada complejidad</u>.
* Se podría necesitar **más comentarios**, excepto en *Ejercicio2.java* y *Ejercicio3.java*.

# Proyecto 5
Consta de 7 archivos. La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 5.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Al analizar el código se obtienen los datos que se muestran en las tablas 5.2 y 5.3.


|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|Line		               |133	|45	|6,7	|44	|*25,6*|1	|12,00	|**2,33**|3	|**1,25**|3	|1,64|
|Polygon		           |291	164	|20,1	|140|17,5	|1	|15,00	|*9,60*  |11	|3,47	   |6	|*2,43*|
|Vertex		             |69	|25	|8,0	|2	|*27,5*|1	|8,00	  |**1,63**|4	|**1,38**|3	|1,52|
|Main		               |74	|39	|5,1	|19	|14,9	|1	|5,00	  |**4,60**|2	|**1,40**|3	|1,67|
|MainOverviewController|440	|283|11,3	|275|11,6	|1	|15,00	|*14,60* |9	|3,53	   |5	|*2,38*|
|LineTest	             |77	|38	|0,0	|56	|**0,0**|1|9,00	  |**2,56**|**1**|**1,00**|**2**|1,47|
|PolygonTest	         |270	|183|0,5	|216|13,0	|1	|13,00	|*12,15* |2	|**1,08**|3	|1,84|
|**PROYECTO&nbsp;5**   |1354|777|9,4	|752|14,8	|7	|11,00	|7,90	   |11	|2,09	   |6	|2,11|
<html><p style="text-align:center"><b>Tabla 5.1</b>: Métricas de los archivos .java del proyecto 5 obtenidas por SourceMonitor</p></html>


|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Line		               |133	|45	|3	|34	|12	|28	|1,1,1,1,1,3<br>1,2,1,1,1,1	      |3 |1,25|
|Polygon		           |291	|164	|33	|51	|15	|144|1,1,1,1,9,4,4,2<br>2,3,11,2,1,9,1|11|3,47|
|Vertex		             |69	|25	|2	|19	|8	|13	|1,1,1,1,1,1,1,4 |4	|1,38|
|Main		               |74	|39	|2	|11	|5	|23	|1,2,2,1,1	     |2 |1,40| 
|MainOverviewController|440	|283|32	|51	|15	|219|1,1,9,1,3,1,4,2<br>2,3,9,1,8,4,4	|9 |3,53|
|LineTest	             |77	|38	|0	|0	|9	|23	|1,1,1,1,1,1,1,1,1|1 |1,00|
|PolygonTest	         |270	|183|72	|35	|13	|158|1,1,1,1,1,1,1,1,<br>2,1,1,1,1|2	|1,08|
|**PROYECTO&nbsp;5**   |1354|777|144|201|77	|608|1,...,11                     |11	|2,09|
<html><p style="text-align:center"><b>Tabla 5.2</b>: Métricas del proyecto 5 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|N&nbsp;7|N&nbsp;8|N&nbsp;9|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:      | ---:  |---:    |---:    |---:    |---: | ---:   |---: |
|Line		               |3	|14	|24	|4	|0	|0	|0	|0	|0	|0	|**3**|	74	|133 |**1,64**|
|Polygon		           |3	|17	|84	|32	|24	|3	|1	|0	|0	|0	|**6**|	399	|291 |**2,43**|
|Vertex		             |2	|10	|11	|2	|0	|0	|0	|0	|0	|0	|**6**|	38	|69	 |**1,52**|
|Main		               |9	|7	|11	|12	|0	|0	|0	|0	|0	|0  |**3**|	65	|74	 |**1,67**|
|MainOverviewController|18|46	|66	|125|23	|6	|0	|0	|0	|0	|**5**|	674 |440 |**2,38**|
|LineTest	             |5	|10	|23	|0	|0	|0	|0	|0	|0	|0	|**2**|	56	|77	 |**1,47**|
|PolygonTest	         |5	|20	|157|1	|0	|0	|0	|0	|0	|0	|**3**|	337	|270 |**1,84**|
|**PROYECTO&nbsp;5**   |45|124|376|176|47	|9	|1	|0	|0	|0	|**5**| 1642|1354|**2,11**|
<html><p style="text-align:center"><b>Tabla 5.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del proyecto 5</p></html>


**Conclusiones:**
* Se necesita **refactorización** en *Polygon.java* y *MainOverviewController.java* ya que tienen métodos con <u>demasiada complejidad ciclomática</u>. Hay que definir más métodos y repartir el código en varios.
* Se necesita **revisar los comentarios** en *Line.java* y Vertex.java (tienen demasiados) y **poner comentarios** en *LineTest.java*.



# Proyecto 6
Consta de 7 archivos. La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 5.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Al analizar el código se obtienen los datos que se muestran en las tablas 6.2 y 6.3.


|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|Monomio	          |121|59	|18,6	|15	|19,8	  |1	|13,00|**3,00**|4	|2,00	   |3	  |1,61|
|Polinomio	        |200|105|15,2	|72	|*28,0* |1	|14,00|**5,86**|5	|2,14	   |6	  |2,36|
|PruebaPolinomios	  |54	|37	|0,0	|46	|**0,0**|1 |**1,00**|*32,00* |**1**|**1,00**|**2**|1,76|
|Ejercicio3	        |56	|41	|0,0	|13	|**1,8**|1	|6,00	|4,33	   |**1**|**1,00**|**2**|1,59|
|usoEjercicio3	    |77	|51	|7,8	|46	|**3,9**|1	|**1,00**|*47,00* |5	|5,00	   |4	  |2,82|
|PolinomioTest	    |72	|45	|0,0	|39	|11,1	  |1	|**2,00**|*15,50* |**1**|**1,00**|**2**|1,53|
|Ejercicio3Test	    |58	|43	|0,0	|15	|**0,0**|1	|4,00	|7,00	   |**1**|**1,00**|**2**|1,56|
|**PROYECTO&nbsp;6**|678|381|8,1	|246|14,4	  |7	|5,86	|6,95	   |5	|**1,80**|6	  |1,98|
<html><p style="text-align:center"><b>Tabla 6.1</b>: Métricas de los archivos .java del proyecto 6 obtenidas por SourceMonitor</p></html>


|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Monomio	          |121|59	|11	|24	|13	|39	|1,1,2,4,4,3,3<br>1,1,1,3,1,1	|4 |2,00
|Polinomio	        |200|105|16	|56	|14	|82	|1,1,2,2,1,1,5<br>1,3,5,5,1,1,1|5	|2,14
|PruebaPolinomios	  |54	|37	|0	|0	|1	|32	|1	        |1 |1,00
|Ejercicio3	        |56	|41	|0	|1	|6	|26	|1,1,1,1,1,1|1	|1,00
|usoEjercicio3	    |77	|51	|4	|3	|1	|47	|5	        |5 |5,00
|PolinomioTest	    |72	|45	|0	|8	|2	|31	|1,1        |1 |1,00
|Ejercicio3Test	    |58	|43	|31	|0	|4	|28	|1,1,1,1|1	|1,00
|**PROYECTO&nbsp;6**|678|381|62	|92	|41	|285|1,...,5	|1 |1,80
<html><p style="text-align:center"><b>Tabla 6.2</b>: Métricas del proyecto 6 obtenidas del código</p>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|N&nbsp;7|N&nbsp;8|N&nbsp;9|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:      | ---:  |---:    |---:    |---:    |---: | ---:   |---: |
|Monomio	          |4	|16	|38	|1	|0	|0	|0	|0	|0	|0	|**3**| 177	|59	|**1,61**|
|Polinomio	        |7	|16	|43	|23	|7	|5	|4	|0	|0	|0	|**6**|	630	|105|**2,36**|
|PruebaPolinomios	  |4	|1	|32	|0	|0	|0	|0	|0	|0	|0	|**2**|	74	|37	|**1,76**|
|Ejercicio3	        |2	|13	|26	|0	|0	|0	|0	|0	|0	|0	|**2**|	82	|41	|**1,59**|
|usoEjercicio3	    |3	|1	|21	|3	|23	|0	|0	|0	|0	|0	|**4**|	204	|51	|**2,82**|
|PolinomioTest	    |7	|7	|31	|0	|0	|0	|0	|0	|0	|0	|**2**|	90	|45	|**1,53**|
|Ejercicio3Test	    |4	|11	|28	|0	|0	|0	|0	|0	|0	|0	|**2**|	86	|43	|**1,56**|
|**PROYECTO&nbsp;6**|31	|65	|219|27	|30	|5	|4	|0	|0	|0	|**6**|	1343|381|**1,98**|
<html><p style="text-align:center"><b>Tabla 6.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del proyecto 6</p></html>


**Conclusiones:**
* Se necesita **refactorización** en *PruebaPolinomios.java* y *usoEjercicio3.java* ya que tienen solamente un método con <u>demasiadas sentencias</u>. Hay que definir más métodos y repartir el código en varios. Igualmente hay que **refactorizar** *PolinomioTest.java* que solamente tiene 2 métodos.
* Se necesita **revisar los comentarios** en *Polinomio.java* (tiene demasiados) y **poner comentarios** en *PruebaPolinomios.java*, *EjercicioTest.java* (no tienen) y *Ejercicio3.java* (solo tiene una linea de comentario).

# Proyecto versionado
Consta de tres archivos .java y tiene 5 versiones (casos), consistentes en pequeñas mejoras sucesivas.

## Caso 1
La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 7.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Al analizar el código se obtienen los datos que se muestran en las tablas 7.2, 7.3 y 7.4.

|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|Customer.java	|74	|44	|29,5	|18	|**6,8**|1	|4,00	   |8,50	  |*10* |3,25	   |6	|*2,89*|
|Movie.java	    |29	|16	|0,0	|0	|**0,0**|1	|4,00	   |**1,25**|**1**|**1,00**|2	|1,19  |
|Rental.java	  |20	|11	|0,0	|0	|**0,0**|1	|**3,00**|**1,33**|**1**|**1,00**|2	|1,18  |
|**CASO&nbsp;1**|123|71	|18,3	|18	|**4,1**|3	|**3,67**|**3,91**|*10* |**1,82**|6	|*2,24*|
<html><p style="text-align:center"><b>Tabla 7.1</b>: Métricas de los archivos .java del caso 1 obtenidas por SourceMonitor</p></html>


|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Customer.java	|74	|44	|13	|5	|4	|34	|1,1,1,10	  |10|3,25
|Movie.java	    |29	|16	|0	|0	|4	|5	|1,1,1,1	  |1  |1,00
|Rental.java	  |20	|11	|0	|0  |3	|4	|1,1,1	    |4  |1,00
|**CASO&nbsp;1**|123|71	|13	|5	|11	|43	|1,...,10	  |10|1,82
<html><p style="text-align:center"><b>Tabla 7.2</b>: Métricas del caso 1 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---: | ---:   |---: |
|Customer.java	|4	|6	|11	|6	|6	|9	|2	|**6**|264	|44	|**2,89**|
|Movie.java	    |2	|9	|5	|0	|0	|0	|0	|**2**|32	  |16	|**1,19**|
|Rental.java	  |2	|5	|4	|0	|0	|0	|0	|**2**|22	  |11	|**1,18**|
|**CASO&nbsp;1**|8	|20	|20	|6	|6	|9	|2	|**6**|318	|71	|**2,24**|
<html><p style="text-align:center"><b>Tabla 7.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del caso 1</p></html>

|File        |<td colspan="5"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td>|||||
|---         |:---    |---       |---         |---        |--- |
| ${\color{red}Customer.java}$|Customer&rarr;1	|addRenta1&rarr;1	|getName&rarr;1	| ${\color{red}statement=10}$||
|Movie.java	    |Movie&rarr;1	|getPriceCode&rarr;1	|setPriceCode&rarr;1	|getTitle&rarr;1||
|Rental.java	  |Rental&rarr;1	|getDaysRented&rarr;1	|getMovie&rarr;1||	
<html><p style="text-align:center"><b>Tabla 7.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del caso 1</p></html>


**Conclusiones:**
* Se necesita **refactorización** en *Customer.java* ya que tiene un método con <u>demasiada complejidad</u>, *statement()*. Hay que definir más métodos y repartir el código en varios. 
* Se necesita **revisar los comentarios** en *Customer.java* (tiene pocos) y **poner comentarios** en *Movie.java* y *Rental.java* (no tienen).

## Caso 2
La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 8.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Además, se usa el color verde para indicar el  ${\color{green}archivo mejorado}$.
Al analizar el código se obtienen los datos que se muestran en las tablas 8.2, 8.3 y 8.4.

|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
| ${\color{green}Customer.java}$|80	|48	|27,1	|18	|**6,3**|1	|5,00	   |7,40	  |7    |2,80	   |5	|*2,48*|
|Movie.java	    |29	|16	|0,0	|0	|**0,0**|1	|4,00	   |**1,25**|**1**|**1,00**|2	|1,19  |
|Rental.java	  |20	|11	|0,0	|0	|**0,0**|1	|**3,00**|**1,33**|**1**|**1,00**|2	|1,18  |
|**CASO&nbsp;2**|123|71	|18,3	|18	|**4,1**|3	|**3,67**|**3,83**|7    |**1,75**|5	|2,01  |
<html><p style="text-align:center"><b>Tabla 8.1</b>: Métricas de los archivos .java del caso 2 obtenidas por SourceMonitor</p></html>


|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Customer.java	|**80**|**48**|13	|5	|**5**|**37**|1,1,1,4,7	|**7**|**2,80**
|Movie.java	    |29	|16	|0	|0	|4	|5	|1,1,1,1	  |1    |1,00
|Rental.java	  |20	|11	|0	|0  |3	|4	|1,1,1	    |4    |1,00
|**CASO&nbsp;2**|129|75	|13	|5	|**12**|**46**|1,...,10	  |**7**|**1,75**
<html><p style="text-align:center"><b>Tabla 8.2</b>: Métricas del caso 2 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---: | ---:   |---: |
|Customer.java	|4	|7	|13	|12	|10	|2	|0	|**5**|240	|48	|**2,48**|
|Movie.java	    |2	|9	|5	|0	|0	|0	|0	|**2**|32	  |16	|**1,19**|
|Rental.java	  |2	|5	|4	|0	|0	|0	|0	|**2**|22	  |11	|**1,18**|
|**CASO&nbsp;2**|8	|21	|22	|12	|10	|2	|0	|**5**|294	|75	|**2,01**|
<html><p style="text-align:center"><b>Tabla 8.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del caso 2</p></html>

|File        |<td colspan="5"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td>|||||
|---         |:---    |---       |---         |---        |--- |
| ${\color{green}Customer.java}$|Customer&rarr;1	|addRenta1&rarr;1	|getName&rarr;1	| ${\color{green}statement=4}$|**amountOf&rarr;7**|
|Movie.java	    |Movie&rarr;1	|getPriceCode&rarr;1	|setPriceCode&rarr;1	|getTitle&rarr;1||
|Rental.java	  |Rental&rarr;1	|getDaysRented&rarr;1	|getMovie&rarr;1||	
<html><p style="text-align:center"><b>Tabla 8.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del caso 2</p></html>


**Conclusiones:**
* La **refactorización** en *Customer.java*, consistente en crear un nuevo método, *amountOf()*, y repartir el código del método complejo, *statement()*, entre ambos métodos <u>ha reducido su complejidad</u>. Hay que definir más métodos y repartir el código en varios. 
* Se sigue necesitando **revisar los comentarios** en *Customer.java* (tiene pocos) y **poner comentarios** en *Movie.java* y *Rental.java* (no tienen).

## Caso 3
La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 9.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Además, se usa el color verde para indicar el  ${\color{green}archivo mejorado<}$>.
Al analizar el código se obtienen los datos que se muestran en las tablas 9.2, 9.3 y 9.4.

|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
| ${\color{green}Customer.java}$  |55	|30	|6,7	|12	|9,1    |1	|4,00	|**4,75**|4    |1,75	  |3	|1,77|
|Movie.java	    |29	|17	|0,0	|0	|**0,0**|1	|4,00	|**1,25**|**1**|**1,00**|2	|1,18  |
| ${\color{green}Rental.java}$  |42	|30	|36,7	|7	|**0,0**|1	|4,00 |**5,50**|7    |2,50    |4	|*2,57*|
| ${\color{green}CASO 3}$|126|77	|16,9	|19	|**4,0**|3	|4,00 |**3,83**|7    |**1,75**|4	|1,95  |
<html><p style="text-align:center"><b>Tabla 9.1</b>: Métricas de los archivos .java del caso 3 obtenidas por SourceMonitor</p></html>


|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Customer.java	|**55**|**30**|**2** |5	|**4**|**19**|1,1,1,4	|**4**|**1,75**
|Movie.java	    |29	   |17	  |0	   |0	|4	  |5	   |1,1,1,1	|1    |1,00
|Rental.java	  |**42**|**30**|**11**|0 |**4**|**22**|1,1,1,7 |**7**|**2,50**
|**CASO&nbsp;3**|126   |77	  |13	   |5	|**12**|46   |1,...,7	|7    |1,75
<html><p style="text-align:center"><b>Tabla 9.2</b>: Métricas del caso 3 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---: | ---:   |---: |
|Customer.java	|4	|7	|11	|8	|0	|0	|0	|**3**|90 	|30	|**1,77**|
|Movie.java	    |2	|10	|5	|0	|0	|0	|0	|**2**|34	  |17	|**1,18**|
|Rental.java	  |2	|6	|6	|5	|11	|0	|0	|**4**|120  |30	|**2,57**|
|**CASO&nbsp;3**|8	|23	|22	|13	|11	|0	|0	|**4**|244	|77	|**1,95**|
<html><p style="text-align:center"><b>Tabla 9.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del caso 3</p></html>

|File        |<td colspan="5"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td>|||||
|---         |:---    |---       |---         |---        |--- |
| ${\color{green}Customer.java}$|Customer&rarr;1	|addRenta1&rarr;1	|getName&rarr;1	|statement&rarr;4|  ${\color{green}---}$|
|Movie.java	    |Movie&rarr;1	|getPriceCode&rarr;1	|setPriceCode&rarr;1	|getTitle&rarr;1||
| ${\color{green}Rental.java}$  |Rental&rarr;1	|getDaysRented&rarr;1	|getMovie&rarr;1| ${\color{green}getCharge=7}$|	
<html><p style="text-align:center"><b>Tabla 9.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del caso 3</p></html>


**Conclusiones:**
* La **refactorización** consistente en cambiar el nombre del nuevo método a *getCharge()* y pasarlo de *Customer.java* a *Rental.java* hace que el código, y el proyecto globalmente, sea <u>más comprensible</u>. 
* Se necesita **poner comentarios** en *Movie.java* y *Rental.java* ya que no tienen.

## Caso 4
La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 10.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Además, se usa el color verde para indicar el  ${\color{green}archivo mejorado}$.
Al analizar el código se obtienen los datos que se muestran en las tablas 10.2, 10.3 y 10.4.

|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
| ${\color{green}Customer.java}$ |**53**|**28**|7,1  |12	|**7,5**|1	|4,00	|**4,25**|4    |1,75	  |3	|1,68|
|Movie.java	    |29	   |17	  |0,0	|0	|**0,0**|1	|4,00	|**1,25**|**1**|**1,00**|2	|1,18  |
|Rental.java>	  |42	   |30	  |36,7	|7	|**0,0**|1	|4,00 |**5,50**|7    |2,50    |4	|*2,57*|
| ${\color{green}CASO 4}$|126   |77	  |16,9	|19	|**4,0**|3	|4,00 |**3,67**|7    |**1,75**|4	|1,92  |
<html><p style="text-align:center"><b>Tabla 10.1</b>: Métricas de los archivos .java del caso 4 obtenidas por SourceMonitor</p></html>


|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Customer.java	|**53**|**28**|2 |**4**|4 |**17**|1,1,1,4	|4|1,75
|Movie.java	    |29	   |17	  |0 |0	   |4 |5	   |1,1,1,1	|1|1,00
|Rental.java	  |42    |30    |11|0    |4 |22    |1,1,1,7 |7|2,50
|**CASO&nbsp;4**|124   |75	  |13|4    |12|44    |1,...,7	|7|1,75
<html><p style="text-align:center"><b>Tabla 10.2</b>: Métricas del caso 4 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---: | ---:   |---: |
|Customer.java	|4	|7	|11	|**6** |0	  |0	|0	|**3**|90 	|**28**|**1,68**|
|Movie.java	    |2	|10	|5	|0	   |0	  |0	|0	|**2**|34	  |17	   |**1,18**|
|Rental.java	  |2	|6	|6	|5	   |11	|0	|0	|**4**|120  |30	   |**2,57**|
|**CASO&nbsp;4**|8	|23	|22	|**11**|11	|0	|0	|**4**|238	|**75**|**1,92**|
<html><p style="text-align:center"><b>Tabla 10.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del caso 4</p></html>

|File        |<td colspan="5"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td>|||||
|---         |:---    |---       |---         |---        |--- |
| ${\color{green}Customer.java}$|Customer&rarr;1	|addRenta1&rarr;1	|getName&rarr;1	| ${\color{green}statement=4}$||
|Movie.java	  |Movie&rarr;1	  |getPriceCode&rarr;1	|setPriceCode&rarr;1	|getTitle&rarr;1||
|Rental.java  |Rental&rarr;1	|getDaysRented&rarr;1	|getMovie&rarr;1|**getCharge&rarr;7**|	
<html><p style="text-align:center"><b>Tabla 10.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del caso 4</p></html>


**Conclusiones:**
* La **refactorización** consistente en el no declarar (ni usar) una variable, *thisAmount* en el método *statement*, implica un <u>código más eficiente</u>. 
* Se necesita  **revisar los comentarios** en *Customer.java* (tiene pocos) y **poner comentarios** en *Movie.java* y *Rental.java* ya que no tienen.

## Caso 5
La aplicación SourceMonitor proporciona las métricas que se muestran en la Tabla 11.1 y apareciendo en negrita las que se corresponden con **valores inferiores** al rango heurístico de la tabla 0.1 y en cursiva los *valores superiores* al rango mencionado.  Además, se usa el color verde para indicar el ${\color{green}archivo mejorado}$.
Al analizar el código se obtienen los datos que se muestran en las tablas 11.2, 11.3 y 11.4.

|File        |Lines|Stmts|%Bran|Calls|%Comm<br>[8-20]|Classes|Met/Class<br>[4-16]|AvgSt/Met<br>[6-12]|MaxCC<br>[2-8]|AvgCC<br>[2-4]|MaxDep<br>[3-7]|AvgDep<br>[1-2,2]|
|---         |---: |---: |---: |---: |:---:  |:---:   |:---:       |:---:   |:---:  |:---:  |:---:   |:---:   |
|${\color{green}Customer.java}$ |**48**|**26**|3,8  |10	|**4,2**|1	|4,00	|**3,75**|4    |**1,25**|3	|1,58|
|Movie.java	    |29	   |17	  |0,0	|0	|**0,0**|1	|4,00	|**1,25**|**1**|**1,00**|2	|1,18  |
|${\color{green}Rental.java>}$	  |**50**|**35**|37,1	|10	|**0,0**|1	|5,00 |**5,20**|7    |2,80    |4	|*2,46*|
|${\color{green}CASO 5}$|127   |78	  |17,9	|20	|**1,6**|3	|4,33 |**3,54**|7    |**1,77**|4	|1,88  |
<html><p style="text-align:center"><b>Tabla 11.1</b>: Métricas de los archivos .java del caso 5 obtenidas por SourceMonitor</p></html>


|File        |lineas|deCodigo|ramas|deComent|métodos|sentencias|Comlejidades|MaxCC|AvgCC|
|---         |---:  |---:    |---: |---:    |---:   |---:      |:---        |:---:|:---:|
|Customer.java	|**48**|**26**|**2** |**2**|4    |**15**|1,1,1,2	|**2**|**1,25**
|Movie.java	    |29	   |17	  |0     |0	   |4    |5	    |1,1,1,1	|1    |1,00
|Rental.java	  |**50**|**35**|**11**|0    |**5**|**26**|1,1,1,7,4|7    |**2,80**
|**CASO&nbsp;5**|127   |78	  |13    |2    |13   |46    |1,...,7	|7    |1,77
<html><p style="text-align:center"><b>Tabla 11.2</b>: Métricas del caso 5 obtenidas del código</p></html>

|File        |N&nbsp;0|N&nbsp;1|N&nbsp;2|N&nbsp;3|N&nbsp;4|N&nbsp;5|N&nbsp;6|*MaxDep*|Total|deCódigo|*AvgDep*&nbsp; &nbsp; &nbsp;<br>(=Total/deCódigo)|
|---         |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---:    |---: | ---:   |---: |
|Customer.java	|4	|7	   |11	  |4    |0	|0	|0	|**3**|78 	|**26**|**1,58**|
|Movie.java	    |2	|10	   |5	    |0	  |0	|0	|0	|**2**|34	  |17	   |**1,18**|
|Rental.java	  |2	|**7** |**10**|5	  |11	|0	|0	|**4**|140  |**35**|**2,46**|
|**CASO&nbsp;5**|8	|**24**|**26**|**9**|11	|0	|0	|**4**|252	|78	   |**1,88**|
<html><p style="text-align:center"><b>Tabla 11.3</b>: Detalles de los <i>niveles</i> de sangría de las líneas de código del caso 5</p></html>

|File        |<td colspan="5"><b>Complejidades&nbsp;ciclomáticas&nbsp;de&nbsp;métodos</b></td>|||||
|---         |:---    |---       |---         |---        |--- |
|${\color{green}Customer.java}$|Customer&rarr;1	|addRenta1&rarr;1	|getName&rarr;1	|${\color{green}statement=2}$||
|Movie.java	    |Movie&rarr;1	|getPriceCode&rarr;1	|setPriceCode&rarr;1	|getTitle&rarr;1|
|${\color{green}Rental.java}$  |Rental&rarr;1	|getDaysRented&rarr;1	|getMovie&rarr;1|getCharge&rarr;7|${\color{green}getFrecuentRenterPoints=4}$|	
<html><p style="text-align:center"><b>Tabla 11.4</b>: Detalles de las <i>complejidades ciclomáticas</i> de los métodos del caso 5</p></html>


**Conclusiones:**  
* La **refactorización** consistente en la creación del método *getFrecuentRenterPoints()* reduciendo el código en el método *statement()* hace que el código, y el proyecto globalmente, sea <u>más comprensible</u>. 
* Se necesita **revisar los comentarios** en *Customer.java* (tiene pocos) y **poner comentarios** en *Movie.java* y *Rental.java* ya que no tienen.
