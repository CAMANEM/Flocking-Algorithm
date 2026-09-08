Instituto Tecnol´ogico de Costa Rica

Escuela de Ingenier´ıa en Computadores

CE4302 — Arquitectura de Computadores II

## Proyecto Grupal 1

Framework experimental de modelos de ejecuci´on Multithreading

| Fecha de asignaci´on: 1/2 septiembre 2026 | Fecha de entrega: 15/16 octubre 2026 |   |
| --- | --- | --- |
| Grupos: 3-4 personas | Profesores: | Luis Barboza Artavia |
|   |   | Luis Chavarr´ıa Zamora |

## 1. Objetivo

Mediante el desarrollo de este proyecto, la persona estudiante aplicar´a conceptos de parale- lismo a nivel de hilo, modelos de ejecuci´on concurrente y evaluaci´on de desempe˜no en sistemas multin´ucleo. El objetivo principal consiste en dise˜nar e implementar un problema altamente paralelizable y evaluar su comportamiento bajo distintos modelos de ejecuci´on que aproximen mecanismos utilizados en arquitecturas modernas.

Las personas estudiantes deber´an comprender las diferencias entre modelos de ejecuci´on a nivel de software y mecanismos soportados directamente por hardware, as´ı como las limitaciones pr´acticas de su implementaci´on en computadores de prop´osito general.

## 2. Atributos relacionados

A continuaci´on se describen los atributos del graduado que se pretenden abordar con el desarrollo del proyecto.

## 2.1. Habilidades de Comunicaci´on (HC)

Se comunica de manera efectiva e inclusiva sobre actividades de ingenier´ıa complejas con la comunidad de ingenieros y con la sociedad en general, es capaz de comprender y escribir informes efectivos y documentaci´on de dise˜no, hacer presentaciones efectivas, tomando en cuenta las diferencias culturales, de idioma y de aprendizaje.

## 3. Descripci´on general

Los sistemas computacionales modernos utilizan m´ultiples niveles de paralelismo para incre- mentar el desempe˜no, incluyendo paralelismo a nivel de hilo, ejecuci´on simult´anea y multipro- cesamiento multin´ucleo. Sin embargo, muchos de estos mecanismos corresponden a decisiones microarquitect´onicas que no siempre pueden implementarse directamente desde el software de aplicaci´on.


En este proyecto se dise˜nar´a un sistema experimental que permita comparar distintos mo- delos de ejecuci´on concurrente mediante implementaci´on directa, simulaci´on o aproximaci´on experimental. La persona estudiante deber´a desarrollar una plataforma de pruebas que permita ejecutar un problema altamente paralelizable bajo distintos esquemas de ejecuci´on, recolectar m´etricas de desempe˜no y analizar las diferencias observadas con base en la teor´ıa de arquitectura de computadores y paralelismo.

El enfoque del proyecto es experimental y comparativo, enfatizando la medici´on rigurosa y el an´alisis cr´ıtico de resultados.

## 4. Especificaci´on

En este proyecto la persona estudiante debe proponer un problema altamente paralelizable y evaluar su comportamiento bajo distintos modelos de ejecuci´on concurrente. Dependiendo del modelo, la implementaci´on podr´a ser directa, simulada o aproximada experimentalmente.

- 1. El sistema debe ejecutarse bajo los siguientes modelos (aplicando simulaci´on o aproxima- ci´on cuando el mecanismo sea microarquitect´onico):

- a) Multihilo de grano fino (Fine-Grained Multithreading): Debe implementarse me- diante un modelo de planificaci´on cooperativa o simulaci´on de ejecuci´on por ciclos o cuantums, donde el cambio de hilo ocurre en cada ciclo (o cuantum m´ınimo) en forma round-robin, independientemente de si el hilo actual ha sufrido un stall.

- b) Multihilo de grano grueso (Coarse-Grained Multithreading): Implementaci´on di- recta mediante hilos tradicionales donde el cambio de contexto ocurre ´unicamente ante eventos de bloqueo costosos (sincronizaci´on, fallo de cach´e, espera o E/S).

- c) Multihilo simult´aneo (SMT – Simultaneous Multithreading): Debe aproximarse mediante ejecuci´on concurrente con sobre-suscripci´on de hilos respecto a los n´ucleos f´ısicos o mediante simulaci´on de unidades funcionales compartidas. Nota impor- tante: Para aislar el efecto de SMT en las mediciones, la persona estudiante debe deshabilitar SMT (Hyper-Threading en Intel, SMT en AMD) desde la configuraci´on del BIOS/UEFI del sistema de pruebas y comparar los resultados contra la ejecuci´on con SMT habilitado. Esto permite cuantificar el impacto real del multihilo simult´aneo por hardware versus la aproximaci´on por software.

- d) Multiprocesamiento multin´ucleo (CMP – Chip Multiprocessing): Implementaci´on directa usando paralelismo real sobre m´ultiples n´ucleos mediante procesos o hilos del sistema operativo.


- 2. Deben utilizar cualquier lenguaje de programaci´on. Debe justificar las decisiones de im- plementaci´on considerando el modelo de concurrencia del lenguaje, sus mecanismos de sincronizaci´on y sus limitaciones respecto al paralelismo real. No se permite el uso de lenguajes de alto nivel de abstracci´on como Python o C#.

- 3. Los problemas propuestos por las personas estudiantes. Se recomienda analizar suites de benchmarks paralelizables para inspiraci´on conceptual. A continuaci´on se sugieren algunos temas relevantes que presentan alto grado de paralelismo:

- Procesamiento de Big Data: operaciones masivas sobre bases de datos no re- lacionales (NoSQL), por ejemplo, consultas paralelas sobre MongoDB, agregaciones distribuidas o procesamiento map-reduce sobre grandes vol´umenes de datos.

- Simulaci´on de part´ıculas: simulaciones N-body, din´amica molecular o sistemas de part´ıculas donde las interacciones pueden particionarse espacialmente para su ejecu- ci´on concurrente.

- Ray tracing: renderizado de escenas 3D mediante trazado de rayos, donde cada rayo o regi´on de la imagen puede procesarse de forma independiente, siendo un problema inherentemente paralelizable.

Cada grupo debe proponer tantos problemas como integrantes. Estos deben ser altamente paralelizable y contrastarlos.

- 4. Para cuantificar la mejora deben proveer al menos las siguientes m´etricas:

- a) Tiempo total de ejecuci´on.

- b) Speedup respecto a la versi´on secuencial.

- c) Eficiencia paralela.

- d) Escalabilidad en funci´on del n´umero de hilos o procesos.

Adicionalmente, la persona estudiante deber´a utilizar al menos una herramienta de perfi- lado que permita analizar de forma expl´ıcita el comportamiento bajo SMT (hilos l´ ogicos), tales como:

- perf en Linux, usando contadores de hardware y eventos relacionados con SMT. V´ease la documentaci´on oficial en https://perfwiki.github.io/main/. [URL 🔗](https://perfwiki.github.io/main/)

- Intel® VTune Profiler, para an´alisis detallado de threading, microarquitectura y uso de recursos. Disponible en https://www.intel.com/content/www/us/en/developer/tools/oneapi/vtun profiler.html. [URL 🔗](https://www.intel.com/content/www/us/en/developer/tools/oneapi/vtune-profiler.html)


Se deben incluir en el documento capturas o res´umenes de las m´etricas relevantes obtenidas con estas herramientas (por ejemplo, ciclos, instrucciones, uso de CPU por hilo l´ ogico, stalls, etc.), discutiendo c´ omo se relacionan con los distintos modelos de ejecuci´on (fine-grained, coarse-grained, SMT, CMP). Sugerencia: Implemente mediante scripts la generaci´on de datos y gr´aficas de manera automatizada.

Por razones de validez experimental, no se permite realizar las mediciones princi- pales en entornos virtualizados (m´aquinas virtuales, contenedores, WSL u otros). Las pruebas deben ejecutarse directamente sobre hardware f´ısico dedicado, ya que la virtua- lizaci´on introduce sobrecarga, contenci´on de recursos y variabilidad que distorsionan los resultados de benchmarking y perfilado. la persona estudiante deber´a analizar cr´ıticamente posibles sesgos experimentales y validar la coherencia de sus resultados con la teor´ıa.

Las personas estudiantes deben contrastar los dos problemas escogidos en funci´on de las m´etricas.

El sistema debe ser probado exhaustivamente al menos 200 ejecuciones en cada caso (depen- diendo del problema, puede requerir m´as o menos ejecuciones en funci´on de sus variables), esto para cuantificar la mejora. Se sugiere implementar scripting (e.g., Makefile). El sistema debe generar gr´aficas de las m´etricas, esto facilitar´a la interpretaci´on. Usen como base el problema sin esquema de hilos.

Justificaci´on de pruebas repetidas: la persona estudiante debe justificar expl´ıcitamente el n´umero de iteraciones realizadas para cada configuraci´on (al menos 200 ejecuciones m´ınimas como referencia, pero adaptadas al problema y tama˜no de entrada). Se requiere:

- C´alculo del intervalo de confianza (por ejemplo, 95 %) de las m´etricas principales (tiempo, speedup) usando estad´ıstica descriptiva (media, desviaci´on est´andar).

- Gr´aficas de boxplot o histograma mostrando la distribuci´on de los resultados de todas las iteraciones por configuraci´on (hilos, modelo de ejecuci´on).

- Discusi´on sobre la convergencia de los resultados, identificando si se necesita mayor n´umero de iteraciones para estabilidad.

Esto debe documentarse en la secci´on de resultados del paper, incluyendo c´ odigo o script utilizado para las repeticiones (e.g., bash loop, Makefile target). Las gr´aficas deben generarse autom´ati- camente desde los datos recolectados.

## 4.1. Notas adicionales

- 1. El desarrollo de este proyecto es grupal.


- 2. En la defensa se implementar´a que, si no justifica la funcionalidad de cualquier l´ınea de c´ odigo que escoja el profesor se eliminar´a y ejecutar´a el c´ odigo. Esto tendr´a penalidad en la nota pues significa que no conoce su c´ odigo o estaban programando l´ıneas sin utilidad.

- 3. Deben usar Github, este debe ser privado, usen la Metodolog´ıa indicada en la secci´on 5. [URL 🔗](#page-0)

- 4. El proyecto tendr´a dos demostraciones o evaluaciones antes de la entrega final, estos ser´an los requerimientos m´ınimos de los avances:

- a) Demostraci´on 1: D´ıa 2 semana 6. El grupo de estudiantes persona estudiante debe mostrarle al profesor el problema escogido, las razones para fundamentar su selec- ci´on. Aqu´ı deber´a proponer mediante diagramas (con base en la teor´ıa) sobre c´ omo implementar´a el multihilo de grano fino (fine-grained) y el multihilo de grano grueso (coarse-grained).

- b) Demostraci´on 2: D´ıa 2 semana 8. El grupo de estudiantes debe mostrarle al profesor los diagramas de las soluciones esquematizadas preliminares (indicando los cambios m´as significativos). Ejecuci´on del sistema base (sin hilos). Identificaci´on de las variables m´as importantes del problema que aumenten su paralelizaci´on. Una ejecuci´on dummy o trivial de cada esquema multihilo con las mediciones, puede ser en partes parciales del problema.

Estas demostraciones son obligatorias pues permiten tener certeza que el producto final llegue con menos fallas.

- 5. Todo dise˜no deber´a tener al menos 2 propuestas detalladas adecuadamente y comparadas seg´un criterios.

## 5. Metodolog´ıa de trabajo

El proyecto debe seguir los siguientes aspectos de desarrollo, sino, la parte funcional no ser´a calificada y obtendr´a nota de cero. la persona estudiante deber´a seguir los siguientes lineamientos:

- 1. Los estudiantes pueden usar herramientas de inteligencia artificial u otras fuentes para gu´ıa. Debe documentar los procedimientos automatizados y los mismos deben ser validados por usted contra referencias verificadas y confiables 1. En este proyecto usted ser´a un dise˜nador(a), no un copiloto(a) sin criterio t´ecnico cr´ıtico. Esto debe formar parte de los anexos en el documento entregado. [URL 🔗](#page-0)

- 2. Todo c´ odigo debe ser documentado de forma interna.


## 3. Manejo por repositorio:

- a) Utilice una cuenta de repositorio gratuita.

- b) El repositorio debe ser enviado al profesor no m´as de 5 h´abiles despu´es de la entrega de este enunciado. Sino, habr´a penalizaci´on de un punto por hora en la nota final del proyecto despu´es de las 11:59 pm del quinto d´ıa h´abil.

- c) Cree un repositorio con el siguiente nombre: <user id> a2 2026 s1. El user id estar´a compuesto por la primera letra del nombre y el apellido. Por ejemplo, para la persona estudiante Fulanito P´erez, el nombre del repositorio ser´a: fperez a2 2026 s1.

- d) El repositorio debe ser mediante el uso de GitHub, debe ser privado, proporcione acceso a luchazam (Grupo 01) o rgarciatec (Grupo 02). Si no es privado desde el inicio recibir´a penalizaci´on de 10 puntos.

- e) El repositorio de Git contendr´a dos ramas principales: master y development.

- f) Inicialmente, la rama de development se crea a partir del master.

- g) Al trabajar en un proyecto, la persona estudiante debe crear una nueva rama de trabajo desde develop y cuando la funci´on est´e lista, la rama debe fusionarse para develop. Cualquier correcci´on o modificaci´on adicional despu´es de merge deber´ıa requerir que se repita el proceso (es decir, crear la rama desde develop y fusionar los cambios m´as tarde). Una vez que el c´ odigo de desarrollo est´e listo, se fusionar´a con master y se debe crear una tag. El proceso se describe en la Figura 1. [URL 🔗](#page-0)

*Figura 1: Git workflow*

Adicionalmente se coloca este enlace recomendado. [URL 🔗](https://nvie.com/posts/a-successful-git-branching-model/)


CE4302 — Arquitectura de Computadores II

- h) Solo debe contemplar c´ odigo, recuerde que es un repositorio de versiones de c´ odigo, no un Drive. [URL 🔗](https://www.google.com/drive/)

- i) Despu´es de haber realizado algunos proyectos la rama master debe verse as´ı:

- master/

- proyecto 1

- proyecto 2

· · ·

Donde cada directorio de proyecto x contiene todos los entregables para cada pro- yecto.

No es permitido realizar todo el trabajo en un solo commit, es decir, que realice el trabajo de forma local y solo suba el ´ultimo entregable en el repositorio. Si no, ser´a penalizado en todos los rubros de evaluaci´on de la defensa disminuyendo un escalaf´on en la calificaci´on de cada rubro. Debe mostrar avance incremental (se revisar´an estad´ısticas).

## 6. Entregables

Como entregables en este proyecto se evaluar´a lo siguiente:

- Presentaci´on funcional completa de 30 minutos (70 %): Cada estudiante deber´a demostrar en una sesi´on (previa cita con el profesor) las diferentes pruebas sobre el sistema. El profesor evaluar´a las pruebas seg´un r´ubrica correspondiente, se realizar´an preguntas orales de lo implementado (todo debe ser fundamentado, sino habr´a penalidad conceptual). En la sesi´on se har´an preguntas relacionadas sobre cualquier etapa del sistema, se contrastar´a contra la . El d´ıa de la presentaci´on, la persona estudiante cargar´a el ´ultimo commit antes de la primera revisi´on.

- Art´ıculo tipo paper en formato PDF (15 %): El art´ıculo deber´a tener una extensi´on no mayor a 4 p´aginas y debe seguir el formato IEEE Transactions. Se recomienda el uso de LATEX para su elaboraci´on, sin embargo, no es obligatorio; la persona estudiante puede utilizar cualquier herramienta de edici´on siempre que el documento final se entregue en formato PDF y respete el formato IEEE indicado. En general el paper deber´a contar con las siguientes secciones:

- 1. Abstract (en ingl´es): Un buen abstract tiene las siguientes caracter´ısticas:

- a) Un abstract permite a los lectores obtener la esencia o esencia de su art´ıculo o art´ıculo r´ apidamente, para decidir si leer el art´ıculo completo.


CE4302 — Arquitectura de Computadores II

- b) Un abstract prepara a los lectores para seguir la informaci´on detallada, los an´alisis y los argumentos en su art´ıculo completo.

- c) Un abstract ayuda a los lectores a recordar puntos clave de su pap.

- d) Un abstract es de entre 150 y 250 palabras.

- 2. Introducci´on: Una buena introducci´ on muestra el contexto del problema o lo que se va a solucionar, introduce el tema al lector. Al final de la introducci´on se indica la organizaci´on del documento (primero se muestra la investigaci´on, luego....).

- 3. Marco te´orico.

- 4. Sistema desarrollado con opciones de soluci´on.

- 5. Resultados y an´alisis con respecto a la teor´ıa.

- 6. Conclusiones escritas en prosa.

- 7. Bibliograf´ıa, en formato IEEE y referenciadas en el texto (usar cite). Referencia bien para evitar problemas de plagio.

- Video de presentaci´on (15 %): Video de entre 3 y 5 minutos. Debe exponer de forma intuitiva sus hallazgos, inspir´andose en el estilo de divulgaci´on del canal, y todas las per- sonas del grupo deben participar. Two Minute Papers [2]. Debe considerar que el p´ublico meta de su presentaci´on no tiene necesariamente el background t´ecnico, por lo que deber´a exponer de forma clara lo que se ha realizado, as´ı como los resultados m´as importantes de su dise˜no y conclusiones. Por motivos de acreditaci´on del programa, se recomienda vehe- mente que el enlace proporcionado est´e disponible por cualquier persona que tenga acceso a ´el, hasta un a˜no despu´es de entregada esta evaluaci´on. [URL 🔗](#page-0)

Si tienen dudas puede escribir al profesor al correo electr´onico de Luis Chavarr´ıa, correo electr´onico de Luis Barboza. Los documentos ser´an sometidos a control de plagios para eliminar cualquier intento de plagio con trabajos de semestres anteriores, actual o copias textuales, tendr´an nota de cero los casos detectados. La entrega se debe realizar por medio de TEC-Digital en la pesta˜na de evaluaci´on a m´as tardar las 11:59 pm, no se aceptan entregas extratemporales. Los documentos ser´ an sometidos a control de plagios. Se proh´ıbe el uso de referencias hacia sitios no confiables. [URL 🔗](mailto:lachavarria@itcr.ac.cr)

## 7. Referencias

## Referencias

- [1] Hennessy, J. L., & Patterson, D. A. (2017). Computer Architecture: A Quantitative Approach. Elsevier.


Instituto Tecnol´ogico de Costa Rica

Escuela de Ingenier´ıa en Computadores

CE4302 — Arquitectura de Computadores II

- [2] Zsolnai-Feh´er, K. Two Minute Papers. Canal oficial de YouTube: https://www.youtube.com/channel/UCbfYPyITQ-7l4upoX8nvctg
