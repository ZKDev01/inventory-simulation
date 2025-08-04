- [Introducción](#introducción)
- [Componentes Estructurales](#componentes-estructurales)
- [Sistemas de Atención](#sistemas-de-atención)
  - [Sistemas de Atención con un Solo Servidor](#sistemas-de-atención-con-un-solo-servidor)
  - [Sistema de Atención con dos servidores en serie](#sistema-de-atención-con-dos-servidores-en-serie)
  - [Sistema de Atención con dos servidores en paralelo](#sistema-de-atención-con-dos-servidores-en-paralelo)

# Introducción

**Simulación de Eventos Discretos**: herramienta que representa un modelo dinámico de un sistema real, donde los cambios en el estado ocurren en instantes específicos denominados *eventos*. A diferencia de modelos continuos, esta simulación se enfoca en eventos puntuales que alteran el flujo o el estado del sistema, lo cual la hace ideal para procesos que tienen características discretas y aleatorias. 

**Evento Discreto**: Representa un cambio puntual y específico que altera el estado del sistema en una simulación. Por ejemplo: la llegada de una materia prima, el inicio o fin de una operación, o la disponibilidad de un recurso. Los eventos son la base sobre el cual se estructura el modelo, ya que cada evento desencadena la modificación de variables y el avance temporal de la simulación. 

**Sistemas de Eventos Discretos vs. Sistemas de Eventos Continuos**:
- *Sistemas de Eventos Discretos*: Experimentan cambios abruptos en instantes específicos (ej: colas en un banco), usando herramientas como autómatas o listas de eventos.
- *Sistemas de Eventos Continuos*: Caracterizados por cambios suaves en variables de estado a lo largo del tiempo, modelados mediante ecuaciones diferenciables (ej: movimiento de un péndulo)

# Componentes Estructurales

**Componentes Estructurales de una Simulación de Eventos Discretos**: Dicha estructura se compone de elementos interdependientes para modelar dinámicas complejas:

- *Estado del Sistema*: Conjunto de variables que definen las propiedades críticas del sistema en un instante determinado (ejemplo: número de clientes en una cola, disponibilidad de máquinas)
- *Variable de tiempo*: Se refiere a la cantidad de tiempo de simulación que ha transcurrido ($t$) 
	- *Variables contadoras*: Estas variables cuentan la cantidad de veces que un evento ha transcurrido hasta el tiempo $t$
- *Secuencia de Eventos*: Estructura de datos que agenda eventos de forma organizada, priorizando su ejecución. 
- *Entidades*: Elementos dinámicos que fluyen a través del sistema, generando eventos y modificando el estado. Representan los objetos o agentes que participan activamente en la simulación. Se clasifican en: 
	- *Temporales*: Permanecen un tiempo limitado (ejemplo: clientes en un banco, vehículos en una autopista, paquetes en una red logística)
	- *Permanentes*: Existen durante toda la simulación, aunque pueden cambiar de estado (ejemplo: máquinas en una fábrica, semáforos en un cruce, servidores en un centro de datos). Estas suelen ser estructuras que atienden a entidades temporales.
- *Recursos*: Elementos estáticos limitados que proveen capacidad para atender entidades. Son pasivos: no generan eventos por sí mismos, pero son requeridos por las entidades para avanzar. La disponibilidad de estos recursos definen la eficiencia del sistema, ya que si no hay recursos disponibles, las entidades esperan en colas. Se clasifican en:
	- *Fijos*: Capacidad finita que se libera tras su huso (ejemplo: cajeros en un supermercado, grúas en un puerto, canales de comunicación). Las entidades los ocupan y liberan, como un cliente usa un cajero 5 min y luego lo suelta
	- *Consumibles*: Se agotan físicamente al ser usados (ejemplo: materias primas en manufacturas, dinero en una caja registradora). Las entidades los consumen (disminuyendo su stock permanentemente)

# Sistemas de Atención

## Sistemas de Atención con un Solo Servidor

**Definición**: Sistema donde un único servidor atiende a todos los clientes, quienes forman una sola cola de espera

**Estructura**: Cola $\to$ Servidor $\to$ Salida

**Funcionamiento**: Si el servidor está ocupado, los nuevos clientes esperan en la cola (bajo políticas como FIFO, LIFO o prioridades). Al finalizar un servicio, el servidor atiende al siguiente cliente en la cola.

## Sistema de Atención con dos servidores en serie

**Definición**: Sistema donde los clientes deben ser atendidos secuencialmente por dos servidores independientes, primero por el servidor 1 y luego por el servidor 2.

**Estructura**: Cola Inicial $\to$ Servidor 1 $\to$ Cola Intermedia $\to$ Servidor 2 $\to$ Salida

**Funcionamiento**: Tras ser atendidos por el servidor 1, los clientes ingresan a una cola intermedia. Si el servidor 2 está ocupado, esperan en esta cola hasta ser atendidos.

## Sistema de Atención con dos servidores en paralelo

**Definición**: Sistema donde dos servidores atienden clientes desde una única cola compartida, operando de forma independiente. 

**Estructura**: Cola $\to$ Servidor 1 / Servidor 2 $\to$ Salida

**Funcionamiento**: Los clientes se asignan al primer servidor disponible. Si ambos están libres, se aplica una regla de asignación (ej: priorizar al servidor con mayor tiempo inactivo).

