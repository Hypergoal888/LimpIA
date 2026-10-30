# INFORME TÉCNICO
## LimpIA 2.0: Sistema inteligente de gestión de salas y limpieza

**Proyecto:** LimpIA 2.0  
**Autor:** Benjamin Donoso  
**Tecnologías:** Python, Gradio, SQLite, RAG y Gemini API.

---

## 1. Introducción

El presente informe tiene como finalidad describir la arquitectura, el funcionamiento y la toma de decisiones del agente inteligente LimpIA 2.0, un prototipo desarrollado para apoyar la gestión de salas educativas y la planificación de actividades de limpieza.

El sistema integra diferentes componentes tecnológicos que permiten registrar clases, administrar tareas, consultar estados de salas y utilizar un chatbot basado en inteligencia artificial. Su funcionamiento combina reglas de negocio programadas en Python, almacenamiento de información mediante SQLite y generación de respuestas utilizando Gemini API.

Además, incorpora un mecanismo de recuperación de información documental (RAG), que permite complementar las consultas del chatbot con documentos relacionados con los protocolos de limpieza, seguridad, sensores y gestión de tareas.

El desarrollo busca demostrar cómo la integración de herramientas de software y modelos de inteligencia artificial puede facilitar la administración de espacios educativos.

## 2. Objetivos

### 2.1 Objetivo general

Describir el funcionamiento y la arquitectura del agente LimpIA 2.0, demostrando cómo sus componentes permiten procesar información, validar condiciones del entorno y apoyar la toma de decisiones relacionadas con la gestión de salas y limpieza.

### 2.2 Objetivos específicos

- Demostrar mediante ejemplos las decisiones que toma el agente frente a diferentes condiciones del entorno.
- Representar mediante un diagrama la orquestación y comunicación entre los componentes del sistema.
- Justificar la selección de herramientas y tecnologías utilizadas en el desarrollo.
- Explicar técnicamente el funcionamiento del agente mediante ejemplos concretos del código implementado.

## 3. IE7. Demostración de la toma de decisiones del agente

LimpIA 2.0 utiliza reglas de negocio y procesamiento de información para responder a las condiciones registradas en el sistema. Las decisiones se ejecutan principalmente mediante funciones desarrolladas en Python, que consultan y modifican los registros almacenados en SQLite.

El chatbot complementa este funcionamiento interpretando las consultas de los usuarios mediante Gemini y utilizando información recuperada desde la base de datos y los documentos del sistema.

### 3.1 Validación de conflictos en el registro de clases

Cuando un usuario registra una clase, LimpIA verifica que no exista otra actividad en la misma sala y horario.

El sistema considera una duración predeterminada de 90 minutos por clase. Si el horario solicitado se superpone con un registro existente, la operación es rechazada.

**Ejemplo:** Si existe una clase en la sala A101 a las 10:00 horas y se intenta registrar otra a las 10:30, el sistema identifica el conflicto y evita guardar el nuevo registro.

Esta decisión se implementa mediante la función `registrar_clase()`, que consulta SQLite y compara los horarios antes de insertar la información.

### 3.2 Validación del estado de las salas

El sistema permite actualizar manualmente el estado de una sala, indicando si se encuentra ocupada y cuántas personas hay en ella.

Antes de guardar la información, LimpIA comprueba que los valores sean coherentes. Por ejemplo, no permite declarar una sala como vacía si se registran personas en su interior.

**Ejemplo:** Si un usuario intenta registrar la sala B203 como vacía con cinco personas, el sistema rechaza la actualización y muestra un mensaje de validación.

Esta decisión se implementa mediante la función `actualizar_sensor()`.

### 3.3 Organización de las tareas de limpieza

LimpIA permite crear tareas y asignarles diferentes niveles de prioridad: baja, media, alta o urgente.

Al consultar las actividades, el sistema organiza los registros para mostrar primero las tareas de mayor prioridad.

**Ejemplo:** Si existen tres tareas con prioridades urgente, media y alta, el sistema presenta primero la urgente, después la alta y finalmente la media.

Esta funcionalidad se desarrolla mediante la función `consultar_tareas()`, utilizando una consulta SQL con condiciones `CASE`.

### 3.4 Respuesta del chatbot ante consultas del usuario

El chatbot recibe preguntas relacionadas con las salas, clases, tareas y protocolos de limpieza. Para generar una respuesta, recupera información desde SQLite y selecciona documentos relacionados mediante el mecanismo RAG.

Posteriormente, entrega estos antecedentes a Gemini, que procesa la consulta y genera una respuesta en lenguaje natural.

**Ejemplo:** Cuando un usuario pregunta qué tareas de limpieza están pendientes en la sala A102, LimpIA recupera las tareas que todavía no están completadas y entrega esa información al modelo para elaborar una respuesta.

De esta manera, el agente utiliza información registrada en el sistema y evita depender exclusivamente del conocimiento general del modelo.

### 3.5 Conclusión del indicador IE7

LimpIA demuestra la toma de decisiones mediante validaciones programadas, consultas a la base de datos y procesamiento de lenguaje natural. Estas funcionalidades permiten controlar conflictos de horarios, validar información de las salas, organizar tareas y responder consultas utilizando datos del entorno.

Es importante señalar que los sensores de esta versión son simulados y se actualizan manualmente. Por lo tanto, el prototipo todavía no recibe mediciones de dispositivos físicos ni ejecuta automáticamente las tareas de limpieza.

## 4. IE8. Diagrama de orquestación y arquitectura general del agente

La arquitectura de LimpIA 2.0 está organizada mediante componentes que cumplen funciones específicas y se comunican entre sí a través de Python.

Gradio permite la interacción con el usuario, Python ejecuta las reglas de negocio, SQLite almacena los registros y el módulo RAG recupera información documental. Finalmente, Gemini procesa las consultas del chatbot y genera respuestas utilizando el contexto proporcionado.

### 4.1 Descripción de la arquitectura

El flujo general comienza cuando el usuario interactúa con la interfaz de Gradio. Según la operación solicitada, Python ejecuta la función correspondiente y aplica las validaciones necesarias.

Cuando se requiere consultar información, el sistema obtiene los registros desde SQLite. En el caso del chatbot, también se recuperan documentos relacionados mediante el módulo RAG. Ambos contextos se combinan y se envían a Gemini para generar una respuesta.

Los resultados se presentan nuevamente en la interfaz de Gradio.

### 4.2 Componentes principales

**Gradio:** proporciona la interfaz web que permite registrar clases, administrar tareas, actualizar salas y realizar consultas.

**Python:** coordina el funcionamiento de los módulos, ejecuta las reglas de negocio y administra la comunicación entre los componentes.

**SQLite:** almacena la información de las clases, salas, tareas y eventos del sistema.

**Sistema RAG:** recupera documentos relacionados con las consultas mediante coincidencias de palabras clave.

**Gemini API:** interpreta las consultas y genera respuestas en lenguaje natural utilizando la información entregada por LimpIA.

**Dashboard y reportes CSV:** permiten visualizar indicadores y exportar los registros para su revisión.

### 4.3 README y repositorio GitHub

Para documentar la arquitectura y facilitar la comprensión del proyecto, se considera la incorporación de un archivo `README.md` en el repositorio GitHub.

Este archivo debe describir el propósito de LimpIA, las tecnologías utilizadas, sus principales funcionalidades, la arquitectura general, los pasos de ejecución y las limitaciones actuales del prototipo.

El README permite que otros desarrolladores comprendan cómo está organizado el proyecto y qué función cumple cada componente.

## 5. IE9. Justificación de la elección de componentes

Los componentes utilizados en LimpIA 2.0 fueron seleccionados considerando las necesidades funcionales del proyecto, la facilidad de integración y la posibilidad de desarrollar un prototipo que combine almacenamiento de datos e inteligencia artificial.

### 5.1 Python

Python fue seleccionado como lenguaje principal porque permite desarrollar la lógica del sistema, implementar validaciones y conectar diferentes servicios mediante bibliotecas externas.

En LimpIA se utiliza para gestionar las clases, actualizar estados de salas, administrar tareas y coordinar el funcionamiento del chatbot.

### 5.2 Gradio

Gradio permite construir una interfaz web interactiva sin necesidad de desarrollar una aplicación web completa desde cero.

Su utilización facilita que los usuarios puedan acceder a las distintas funcionalidades mediante pestañas, formularios y botones.

### 5.3 SQLite

SQLite fue seleccionado para almacenar la información del sistema de manera estructurada.

Permite mantener registros de clases, sensores simulados, tareas y eventos sin requerir un servidor de base de datos independiente. Además, facilita las consultas necesarias para obtener información actualizada.

### 5.4 Gemini API

Gemini fue integrado para incorporar capacidades de procesamiento de lenguaje natural al chatbot.

Su función consiste en interpretar las consultas de los usuarios y generar respuestas utilizando las instrucciones del sistema, los registros recuperados desde SQLite y los documentos proporcionados mediante RAG.

### 5.5 Sistema RAG

El mecanismo RAG permite complementar las respuestas del modelo con información documental relacionada con el proyecto.

En esta versión se utiliza una recuperación basada en coincidencias de palabras clave. Esto permite seleccionar documentos sobre protocolos de limpieza, seguridad, sensores, gestión de tareas y reservas de salas.

### 5.6 Requests

La biblioteca Requests permite realizar solicitudes HTTP hacia la API de Gemini, enviando las consultas y recibiendo las respuestas generadas por el modelo.

### 5.7 Justificación general

La selección de estos componentes permite desarrollar una arquitectura modular, donde cada tecnología cumple una función determinada.

Python coordina las operaciones, Gradio facilita la interacción, SQLite mantiene los registros y Gemini, complementado con RAG, permite incorporar consultas en lenguaje natural.

Esta integración responde a los requerimientos del proyecto y proporciona una base para futuras mejoras, como la incorporación de sensores físicos, autenticación de usuarios y mecanismos de recuperación documental más avanzados.

## 6. IE10. Utilización de lenguaje técnico y evidencias

Para explicar el funcionamiento de LimpIA 2.0 es necesario utilizar conceptos técnicos relacionados con la arquitectura de software, las bases de datos, la inteligencia artificial y la integración de servicios.

A continuación, se presentan los principales conceptos y sus evidencias dentro del código.

### 6.1 Orquestación de componentes

La orquestación corresponde a la coordinación de los diferentes módulos del sistema para cumplir una función determinada.

En LimpIA, Python actúa como componente central de coordinación, comunicando la interfaz Gradio con las funciones de negocio, SQLite y Gemini API.

### 6.2 Persistencia de datos

La persistencia permite almacenar información para que pueda ser consultada y utilizada posteriormente.

En el proyecto se implementa mediante SQLite, que contiene las tablas de clases, sensores, tareas y eventos.

### 6.3 Reglas de negocio

Las reglas de negocio corresponden a las condiciones que debe cumplir una operación antes de ser aceptada.

Un ejemplo es la validación de horarios realizada por `registrar_clase()`, que impide registrar clases que se superponen en una misma sala.

### 6.4 Recuperación aumentada por generación (RAG)

RAG es un mecanismo que permite complementar la generación de respuestas de un modelo de lenguaje con información recuperada desde documentos externos.

En LimpIA se implementa mediante la función `recuperar_documentos()`, que identifica documentos con coincidencias de palabras clave respecto de la consulta del usuario.

### 6.5 Integración mediante API

Una API permite que diferentes aplicaciones intercambien información mediante solicitudes y respuestas.

En este proyecto, Requests se utiliza para enviar consultas a Gemini API mediante una solicitud HTTP POST.

### 6.6 Trazabilidad

La trazabilidad permite mantener un historial de operaciones importantes realizadas en el sistema.

En LimpIA se implementa mediante la tabla `eventos` y la función `registrar_evento()`, que almacenan acciones como la creación de tareas, actualización de sensores y exportación de reportes.

### 6.7 Evidencias técnicas del código

Las siguientes funciones permiten respaldar las características presentadas:

| Función o componente | Evidencia técnica |
|---|---|
| `registrar_clase()` | Validación de horarios y prevención de conflictos. |
| `actualizar_sensor()` | Validación de estados y cantidades declaradas. |
| `consultar_tareas()` | Ordenamiento de tareas según prioridad. |
| `recuperar_documentos()` | Recuperación documental mediante palabras clave. |
| `contexto_datos()` | Consulta de información almacenada en SQLite. |
| `chatbot()` | Integración del contexto, RAG y Gemini API. |
| `registrar_evento()` | Registro de operaciones para mantener trazabilidad. |
| `dashboard()` | Generación de indicadores y actividad reciente. |

## 7. Conclusión general

El desarrollo de LimpIA 2.0 permite demostrar la integración de diferentes tecnologías para apoyar la gestión de salas educativas y la planificación de actividades de limpieza.

Mediante Python se implementan reglas de negocio y validaciones que permiten controlar las operaciones del sistema. SQLite proporciona almacenamiento estructurado, mientras que Gradio facilita la interacción de los usuarios mediante una interfaz web.

Por otra parte, la integración de Gemini API y el mecanismo RAG permite incorporar un chatbot capaz de interpretar consultas y generar respuestas utilizando información almacenada en el sistema y documentación relacionada.

Los indicadores IE7, IE8, IE9 e IE10 se respaldan mediante ejemplos de funcionamiento, la representación de la arquitectura, la justificación de las tecnologías y las evidencias presentes en el código.

Finalmente, aunque el prototipo utiliza sensores simulados y un mecanismo RAG basado en palabras clave, su arquitectura permite proyectar futuras mejoras, como la integración de dispositivos físicos, la incorporación de autenticación y la utilización de técnicas de recuperación documental mediante embeddings.






<img width="1886" height="1888" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/fbff7c13-f85a-49a9-abad-d6b8afef84ed" />
