# Lavavajillas de ordenado automático

Trabajo de Fin de Grado centrado en el diseño conceptual y la simulación de un lavavajillas inteligente con capacidad de ordenado automático de vajilla mediante una etapa robotizada.

## Descripción del proyecto

Este proyecto plantea una evolución del lavavajillas convencional, incorporando una etapa adicional tras el ciclo de lavado y secado. En esta etapa, un brazo robótico accede al interior del lavavajillas, recoge las piezas de vajilla y las deposita automáticamente en una zona de almacenamiento integrada en el propio mueble.

El objetivo principal no es desarrollar un producto comercial final, sino estudiar la viabilidad técnica de la etapa robotizada mediante modelado, simulación y comparación de alternativas en RoboDK.

El trabajo se centra especialmente en:

- Selección del brazo robótico.
- Selección del efector final.
- Diseño conceptual del sistema.
- Modelado de tres alternativas de distribución.
- Programación de trayectorias en RoboDK.
- Comparación de resultados de simulación.
- Elección de la alternativa más equilibrada.
- Análisis de viabilidad técnica, económica y de integración.

## Objetivo principal

El objetivo del proyecto es estudiar y definir una solución robotizada viable para automatizar la descarga y el ordenado de la vajilla tras la finalización del ciclo de lavado.

Para ello se comparan tres configuraciones diferentes, valorando criterios como:

- Accesibilidad del robot.
- Facilidad de integración.
- Complejidad de las trayectorias.
- Tiempo estimado de ciclo.
- Distancia recorrida por el TCP.
- Número de movimientos.
- Validez del programa en RoboDK.
- Riesgo de colisiones.
- Viabilidad de implementación en un entorno doméstico.

## Concepto general del sistema

El sistema propuesto está formado por los siguientes subsistemas:

### Módulo de lavado

Corresponde al lavavajillas convencional, encargado de realizar las fases de lavado, aclarado y secado.

### Etapa robotizada

Está formada por un brazo robótico encargado de manipular la vajilla una vez finalizado el ciclo de lavado. El robot recoge las piezas desde el interior del lavavajillas y las transporta hasta la zona de almacenamiento.

### Efector final

Se utiliza un efector de vacío para realizar el agarre de las piezas. Esta solución resulta adecuada para objetos con superficies lisas, como platos y vasos.

### Sistema de desplazamiento vertical

El robot se integra sobre un sistema de desplazamiento vertical que permite modificar su altura de trabajo. Esto facilita el acceso a diferentes niveles del lavavajillas y de la zona de almacenamiento.

### Zona de almacenamiento

Es el espacio donde se deposita la vajilla una vez manipulada por el robot. En el proyecto se estudian diferentes configuraciones de almacenamiento mediante baldas y cajonera.

### Sistema de control e interfaz

El sistema debe coordinar la secuencia de funcionamiento del lavavajillas, la apertura lateral, la etapa robotizada y la comunicación con el usuario.

## Funcionamiento previsto

El ciclo de funcionamiento planteado es el siguiente:

1. El usuario introduce la vajilla en el lavavajillas.
2. El sistema ejecuta el ciclo convencional de lavado, aclarado y secado.
3. Una vez finalizado el ciclo, se habilita la apertura lateral del lavavajillas.
4. El robot accede al interior del lavavajillas.
5. El efector final recoge cada pieza de vajilla.
6. El robot transporta la pieza hasta la zona de almacenamiento.
7. La vajilla queda colocada automáticamente en su ubicación final.
8. El sistema informa al usuario de la finalización del proceso.

## Herramientas utilizadas

- RoboDK
- Modelado 3D del sistema
- Programación de trayectorias robóticas
- Simulación de movimientos
- Análisis comparativo de alternativas

## Robot y efector final

| Elemento | Selección |
|---|---|
| Robot para aplicación real | FANUC LR Mate 200iD/7WP Wash |
| Robot utilizado en simulación | FANUC LR Mate 200iD |
| Efector final | RobotiQ EPick Vacuum Gripper 1 Cup |
| Tipo de agarre | Vacío |
| Objetos manipulados | Platos y vasos |
| Entorno de simulación | RoboDK |

La elección del robot se basa en su tamaño compacto, precisión, capacidad de carga, alcance y posibilidad de integración en un espacio reducido.

Para una aplicación real se considera especialmente adecuada la versión Wash del FANUC LR Mate 200iD, debido a las condiciones de humedad y posibles salpicaduras asociadas al entorno de un lavavajillas.

El efector final seleccionado es una solución de vacío con una ventosa, adecuada para la manipulación de piezas de vajilla con superficies lisas.

## Alternativas simuladas

En el proyecto se desarrollan y comparan tres alternativas de diseño.

| Alternativa | Descripción | Archivo |
|---|---|---|
| Alternativa 1 | Diseño modular con lavavajillas en zona baja | `ALTERNATIVA 1 - PYTHON.rdk` |
| Alternativa 2 | Diseño modular con lavavajillas en altura | `ALTERNATIVA 2 - PYTHON.rdk` |
| Alternativa 3 | Diseño con cajonera y lavavajillas en altura | `ALTERNATIVA 3 - PYTHON.rdk` |

## Alternativa 1: lavavajillas en zona baja

Esta alternativa sitúa el lavavajillas en la parte inferior del conjunto, manteniendo una disposición próxima a la de un lavavajillas doméstico convencional.

Su principal ventaja es que resulta una configuración compacta y familiar para el usuario. Sin embargo, obliga al robot a realizar desplazamientos verticales más amplios para transportar la vajilla desde la zona baja hasta los módulos de almacenamiento superiores.

Esto puede aumentar la longitud de las trayectorias y exigir una mayor coordinación entre el brazo robótico y el sistema de desplazamiento vertical.

## Alternativa 2: lavavajillas en altura

Esta alternativa sitúa el lavavajillas en una posición elevada respecto a la configuración convencional.

El objetivo es mejorar la accesibilidad del robot a las piezas de vajilla y reducir movimientos verticales extremos. Esta configuración permite que el manipulador trabaje en una posición más favorable, facilitando la extracción lateral de la vajilla y el desplazamiento hacia la zona de almacenamiento.

Es la alternativa seleccionada como solución final, ya que ofrece el mejor equilibrio entre accesibilidad, eficiencia, integración y viabilidad técnica.

## Alternativa 3: cajonera y lavavajillas en altura

Esta alternativa mantiene el lavavajillas en altura, pero incorpora una cajonera como parte del sistema de almacenamiento.

La cajonera puede mejorar la organización de la vajilla, pero también aumenta la complejidad del sistema. El robot debe acceder a zonas más cerradas y con menor margen de maniobra, lo que incrementa la dificultad de las trayectorias y el número de movimientos necesarios.

Aunque es viable en simulación, resulta más compleja que la alternativa 2.

## Métricas analizadas

Para comparar las alternativas se han utilizado métricas obtenidas en RoboDK:

- Tiempo estimado de ciclo.
- Distancia recorrida por el TCP.
- Instrucciones válidas.
- Total de instrucciones.
- Total de movimientos.
- Número de movimientos articulares MoveJ.
- Número de movimientos lineales MoveL.

Estas métricas permiten valorar tanto la eficiencia de cada alternativa como la complejidad de la programación robótica.

## Resultados obtenidos

| Métrica | Alternativa 1 | Alternativa 2 | Alternativa 3 |
|---|---:|---:|---:|
| Tiempo de ciclo | 138,405 s | 156,356 s | 179,306 s |
| Distancia recorrida por el TCP | 52,537 m | 48,591 m | 50,979 m |
| Instrucciones válidas | 77 | 87 | 103 |
| Total de instrucciones | 79 | 87 | 103 |
| Total de movimientos | 48 | 70 | 85 |
| Movimientos MoveJ | 33 | 41 | 83 |
| Movimientos MoveL | 15 | 29 | 2 |

## Análisis de resultados

La alternativa 1 presenta el menor tiempo de ciclo, pero requiere una mayor distancia recorrida por el TCP. Esto se debe a que el lavavajillas se encuentra en una posición baja y el robot debe realizar desplazamientos verticales más marcados para alcanzar las zonas de almacenamiento.

La alternativa 2 presenta la menor distancia recorrida por el TCP y un comportamiento más equilibrado. Aunque su tiempo de ciclo es algo superior al de la alternativa 1, ofrece mejores condiciones de accesibilidad, una disposición más favorable para el robot y una integración más coherente con el sistema completo.

La alternativa 3 presenta el mayor tiempo de ciclo y el mayor número de movimientos. Esto se debe a la incorporación de la cajonera, que obliga al robot a realizar trayectorias más complejas y maniobras adicionales en espacios más limitados.

## Elección final

La alternativa seleccionada es la Alternativa 2: diseño modular con lavavajillas en altura.

Esta opción se considera la más adecuada porque ofrece un buen equilibrio entre:

- Accesibilidad del robot.
- Reducción de desplazamientos innecesarios.
- Menor distancia recorrida por el TCP.
- Facilidad de integración.
- Viabilidad técnica.
- Seguridad durante la manipulación.
- Distribución más favorable del espacio.
- Menor complejidad que la alternativa con cajonera.

Aunque no es la alternativa con menor tiempo de ciclo, sí es la que presenta un comportamiento más equilibrado desde el punto de vista global del sistema.

## Presupuesto estimado

El proyecto incluye una estimación económica conceptual para cada alternativa.

| Alternativa | Coste total estimado |
|---|---:|
| Alternativa 1 | 50.200 € |
| Alternativa 2 | 51.900 € |
| Alternativa 3 | 53.000 € |

La alternativa seleccionada tiene un coste estimado de 51.900 €.

Este presupuesto debe entenderse como una aproximación inicial, ya que el coste real dependería del proveedor, materiales, nivel de integración, diseño mecánico final, sensores, sistemas de seguridad y componentes seleccionados.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `ALTERNATIVA 1 - PYTHON.rdk` | Simulación RoboDK de la alternativa 1 |
| `ALTERNATIVA 2 - PYTHON.rdk` | Simulación RoboDK de la alternativa 2 |
| `ALTERNATIVA 3 - PYTHON.rdk` | Simulación RoboDK de la alternativa 3 |
| `README.md` | Descripción general del proyecto |

## Cómo abrir las simulaciones

Para visualizar las simulaciones:

1. Descargar el repositorio.
2. Abrir RoboDK.
3. Cargar el archivo `.rdk` correspondiente.
4. Revisar el entorno modelado.
5. Ejecutar o analizar los programas de movimiento.
6. Comparar las trayectorias, movimientos y resultados de cada alternativa.

## Limitaciones del proyecto

El proyecto se desarrolla a nivel conceptual y mediante simulación, por lo que presenta ciertas limitaciones:

- Las piezas de vajilla están estandarizadas.
- Las posiciones de recogida y depósito están predefinidas.
- No se implementa visión artificial real.
- El agarre por vacío se representa de forma simplificada.
- No se valida experimentalmente el agarre sobre vajilla húmeda.
- No se realiza un análisis estructural detallado del mueble.
- El sistema de desplazamiento vertical se modela de forma conceptual.
- No se incorporan sensores reales en la simulación.
- La seguridad se analiza de forma conceptual, no experimental.

## Trabajos futuros

Como continuación del proyecto se proponen las siguientes mejoras:

- Desarrollo de un prototipo físico.
- Validación experimental del efector de vacío.
- Incorporación de visión artificial para detectar la posición real de la vajilla.
- Optimización de trayectorias para reducir tiempos de ciclo.
- Diseño mecánico detallado del sistema de desplazamiento vertical.
- Análisis estructural del mueble y de las cargas generadas por el robot.
- Integración de sensores reales de posición, presencia y seguridad.
- Desarrollo de una interfaz de usuario funcional.
- Implementación de enclavamientos, parada de emergencia y protecciones físicas.
- Estudio de compatibilidad con diferentes tipos de vajilla.
- Validación del sistema en un entorno doméstico real.

## Estado del proyecto

Proyecto desarrollado como Trabajo de Fin de Grado en Ingeniería Electrónica Industrial y Automática.

El repositorio contiene las simulaciones principales utilizadas para comparar las alternativas de diseño y justificar la selección de la solución final.

## Autora

Lucía Martínez del Amo

Grado en Ingeniería Electrónica Industrial y Automática  
Universidad Alfonso X el Sabio  
Curso 2025/2026

## Nota

Este repositorio tiene finalidad académica. El sistema propuesto corresponde a una solución conceptual validada mediante simulación, no a un producto comercial ni a una implementación física completamente desarrollada.
