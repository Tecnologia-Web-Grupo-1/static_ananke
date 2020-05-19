---
date: 2017-04-14T11:25:05-04:00
description: "Articulo de Julio"
featured_image: "/images/Julio-Villacis.jpg"
tags: []
title: "Articulo: Sistemas Distribuidos"
disable_share: false
---
Un sistema distribuido es un conjunto de ordenadores que trabajan juntos de forma coordinada, a través del intercambio de mensajes, para conseguir un objetivo. En dicho sistema, el estado y los programas se guardan en múltiples ordenadores. A pesar de que los procesos que tienen lugar están separados entre los diferentes participantes, para el usuario parece que está trabajando con un único ordenador.

## ¿Qué caracteriza un sistema distribuido?

Podemos decir que tienen 3 características principales:

### Concurrencia:
Cada ordenador de la red ejecuta eventos de forma independiente y al mismo tiempo que los otros.

#### Falta de un reloj global
Para que el sistema distribuido funcione correctamente, necesitamos encontrar alguna forma de ordenar los eventos que tienen lugar. Para un sistema cuyos integrantes están espacialmente separados a veces es imposible decir el orden en el que tienen lugar los eventos. O lo que es lo mismo, no existe un reloj global en la red que determine la secuencia de los eventos.

#### Fallos independientes de los componentes
Los sistemas distribuidos tienen que trabajar con componentes que pueden fallar.

Estos fallos los podemos clasificar en:

Crash: los componentes dejan de funcionar
Omisión: un componente envía un mensaje, pero no es recibido por los demás
Bizantino: los componentes de la red empiezan a actuar de forma arbitraria.
El fin de todo sistema distribuido es diseñar un protocolo que consiga su objetivo a pesar de los fallos que puedan tener los componentes. Por tanto, debemos considerar si, además de soportar los fallos de sus componentes, podrá sobrevivir incluso cuando algunos de los ordenadores se desvíe del comportamiento normal.

Con el objetivo de diseñar un sistema distribuido podemos decir que hay dos modelos:

##### Simple fault-tolerance

En estos sistemas se asume que las partes sólo mostrarán dos tipos de comportamientos: o siguen el protocolo o fallan. Este modelo maneja correctamente los fallos de los componentes. Sin embargo, no está pensado para entornos donde pueda haber fallos Bizantinos.
Byzantine fault-tolerance
En este modelo se asume que los componentes puede fallar o comportarse de forma maliciosa.

##### BAR fault tolerance
Se podría decir que este modelo es una ampliación del anterior, ya que algunos expertos argumentan que el modelo tolerante a fallos bizantinos es muy genérico y no tiene en cuenta los fallos “racionales”. Es decir, que los nodos de una red se desvíen del comportamiento marcado para conseguir sus propios intereses. En este sentido, lo que se propone es la existencia de incentivos que puedan influir en los nodos para actuar de forma honesta y deshonesta. Por tanto, para este modelo se asumen tres tipos de actores:

* Bizantinos: maliciosos, buscarán dañar la red.
* Altruistas: honestos, siempre seguirán el protocolo
* Racionales: solo seguirán el protocolo si les viene bien.

### ¿Cómo se comunican los nodos?

Como se comentó al principio, la comunicación de los nodos se basa en el intercambio de mensajes entre los mismos, permitiendo la coordinación entre éstos. Se puede identificar dos escenarios en el intercambio de mensajes:

1.- Síncrono

En este escenario se asume que los mensajes llegarán en un determinado lapso de tiempo. Diseñar un sistema basándonos en esta idea es, a primera vista, más sencillo, ya que cuando los usuarios envían un mensaje, se sabe que el receptor lo tendrá en el tiempo establecido. Por lo que el sistema se podría diseñar sobre la duración que tiene el envío de mensajes.
Sin embargo, no es un sistema práctico, ya que en el mundo real los ordenadores pueden dejar de funcionar, perder la conexión, etc. En estas situaciones los mensajes se podrían perder, duplicar, retrasar, etc.

2.- Asíncrono
Se asume que los mensajes pueden retrasarse infinitamente, duplicarse o entregarse en cualquier orden. Por tanto, ya no tenemos ese límite máximo de tiempo que teníamos en la opción anterior.
Además de la distinción antes hecha, podemos identificar dos modelos en el intercambio de mensajes:
Invocación remota: desde una máquina poder invocar un código que hay en otra
* Comunicación grupales: comunicación de uno a muchos.
Dependiendo si estamos en el primer caso o en el segundo podemos detectar diferentes roles y responsabilidades en los nodos:

1º caso: cliente-servidor es un modelo muy utilizado (web). Dentro de un conjunto de máquinas puede que un servidor sea cliente de otro.

2º caso: Peer to peer: todos los nodos ejecutan el mismo programa, la misma forma de comunicación, se pueden comunicar entre ellos sin distinción. No hay diferencia entre cliente y servidor.

¿Qué retos nos encontramos a la hora de diseñar un sistema distribuido?
Heterogeneidad: Los ordenadores que físicamente forman parte de la red pueden ser muy diversos por diferentes motivos (hardware, SO, etc).
Apertura: es la extensibilidad para nuevas funciones y aplicaciones (no quiere decir necesariamente que sea open source). En general, la apertura quiere decir que los interfaces son públicos, es necesario una forma de acuerdo que normalmente son estándar o son estandarizados.
* Seguridad: debe ser multidimensional:
  * Confidencialidad, limitar el acceso a la información sólo a los autorizados a ello. En este aspecto la criptografía juega un papel importante.
  * Disponibilidad, es la garantía que los usuarios autorizados puedan acceder a la información.
  * Integridad: asegurar que la información es veraz y no fue modificada. Hay que tener en cuenta los nodos maliciosos y cómo controlarlos.
  * Escalabilidad: trata de que el sistema siga siendo efectivo cuando hay un incremento muy grande de los usuarios (más peticiones) o la cantidad de recursos que la red tiene que gestionar. Si un sistema no es escalable no será capaz de mantener la capacidad de respuesta y el rendimiento.
  * Gestión del fallo: los fallos en un sistema distribuidos son parciales, puede caer unos nodos, porcentaje de nodos, puede quedar partida, es decir, la casuística es múltiple. Hay varios preguntas:
  * La detección de fallo: puede que el error de un nodo no sea detectable
  * Mitigar el fallo: habría que reenviar los mensajes o no, etc.
  * Tolerancia de fallos: qué redundancia tiene el sistema
  * Recuperación del sistema
  * Concurrencia: cada nodo puede recibir varios mensajes y tiene que ser capaz de gestionar estos mensajes que se reciben a la vez. Los nodos los suelen serializar los mensajes y los tratan como si unos llegaran antes que otros.
  * Transparencia: muchos sistemas distribuidos ocultan la heterogeneidad con la transparencia así el sistema es percibido como un entero más que como un conjunto independiente de componentes. La ocultación de detalles afecta a muchos aspectos: al acceso, localización, fallo, replicación, escalabilidad, movilidad, etc. Esto permite simplificar el desarrollo de protocolos de nivel de aplicación.
  * Calidad del servicio: Hace referencia a la capacidad de llegar a ciertas garantías en cuanto al tiempo.
  * Ventajas de un sistema distribuido

### Vamos a enumerar algunas de las ventajas de los sistemas distribuidos:
* Al estar los nodos de la red conectados entre sí el hecho de compartir información entre ellos es más sencillo
* Nuevos nodos pueden añadirse al sistema fácilmente, por tanto, la escalabilidad del sistema es más sencilla.
* Al ser independiente del fallo de los componentes, el hecho de que un nodo falle, no lleva al fallo de todo el sistema
### Desventajas de un sistema distribuido
Estos sistemas también presentan una serie de desventajas, veamos algunas:
* Es muy complicado proveer una seguridad adecuada en un sistema distribuido, ya que hay que proteger a los nodos como a las conexiones entre ellos.
* Algunos mensajes e información pueden perderse en la red cuando los nodos se comunican entre ellos.
* La base de datos conectada al sistema será complicada y difícil de manejar si la comparamos a un sistema centralizado.
* Puede producirse una sobrecarga en la red si todos los nodos del sistema intentan enviar mensajes a la vez.

## Fuentes:

https://rancher.com/blog/2019/considerations-when-designing-distributed-systems/

https://www.oreilly.com/ideas/distributed-systems-a-quick-and-simple-definition

https://thenewstack.io/distributed-systems-hard/

https://www.youtube.com/watch?v=7VbL89mKK3M

https://en.wikipedia.org/wiki/Distributed_computing

https://www.freecodecamp.org/news/a-thorough-introduction-to-distributed-systems-3b91562c9b3c/
