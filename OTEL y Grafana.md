# Open telemetry
*Importante destacar que para profundizar en ciertos conceptos es mejor que se busque directamente en la documentación de Open Telemetry. Esta guía no pretende ofrecer todos los conocimientos y particularidades de la Telemetria con Open Telemetry*

Open telemetry es una herramienta OSS que nos permite recopilar trazas, logs, métricas y perfilado de CPU de nuestros procesos y aplicaciones.
Es una herramienta estandar que se utiliza normalmente en múltiples herramientas como protocolo habitual. 

Su principal útilidad es la de recopilar el comportamiento y multiples datos relacionados con los servicios que corren en una aplicación.

## Grafana + Open Telemetry
En este caso usaremos Grafana y Open Telemetry para el analisis y captura de datos.


## Configurar software para la captura de telemetría.
En el caso de la observabilidad de las aplicaciones, primero se debe configurar en la propia aplicación ya sea mediante la SDK de Open Telemetry para auto inyectar código y exportar la telemetría o, para entrar más en profundidad, inyectando código directamente en los servicios.

## Trazas distribuidas.
Cada llamada que se hace a la API que este en este protocolo, genera spans y trazas que se comparten y comunican durante el ciclo de vida de la llamada de un servicio/api. Esto permite que indiferentemente de donde se este generando la traza, esta pueda tener un historial del inicio y el fin de dicha llamada.

## OTEL Collector
Los collectors son piezas que nos permiten recopilar esta los datos que se comparten mediante el protocolo otlp y recopilarlos en un mismo lugar desde distintos sistemas y entornos, para luego poder tratarlos antes de enviarlos al punto de "almacenaje".

Luego de recopilarla, `otel collector` se encarga de filtrar la información irrelevante para poder ser analizada posteriormente; además, permite recopilar información de los sistemas que se estan utilizando para la generación de las trazas. 

## Convesiones
Uno de los puntos más importantes de la telemetría con OTEL es la de que se tiene una convesión muy clara de como los datos van a ser tratados, filtrados y almacenados de manera que todos los sistemas que funcionen bajo este protocolo, sean compatibles entre sí. Esta es una de las caracteristicas que hacen que open telemetry sea una herramienta tan potente indiferentemente del lenguaje o de las herramientas que se esten utilizando.

## Datos procesados y filtrados ¿Ahora qué?
Luego de tener los datos almacenados y organizados, debemos buscar un lugar donde poder almacenarlos para que consecuentemente, podemos crear visualizaciones a partir de este. Es aquí donde entra el `stack de Grafana`.

`Grafana Labs` cuanta con una amplia variedad de herramientas que nos permiten almacenar, consultar y visualizar los datos que nos envian desde diferentes fuentes. En este caso, veremos las soluciones que `Grafana labs` nos ofrece para poder analizar los datos de la telemetría de OTEL.

## Grafana Labs (LTM stack)

OTEL no ofrece almacenamiento de la telemetría que procesa y tampoco visualización de la misma, pero para este fin, grafana ofrece las siguientes soluciones de almacenamiento y visualización:

- Grafana: Visualizaciones.
- Loki: Almacenamiento de Logs.
- Tempo: Almacenamiento de trazas.
- Mimir: Almacenamiento de métricas.

Cada una de estas soluciones ofrecen una forma de poder consultar los datos que se almacenan.