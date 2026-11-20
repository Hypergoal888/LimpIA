# 🧹 LimpIA 2.0 – Sistema Inteligente de Gestión de Salas y Limpieza

## 1. Descripción del proyecto

LimpIA 2.0 es un sistema inteligente diseñado para apoyar la gestión de salas y la planificación de tareas de limpieza dentro de una institución educativa.

La plataforma permite administrar clases, consultar estados de salas, registrar tareas de limpieza y utilizar un asistente de inteligencia artificial para responder preguntas relacionadas con la información almacenada.

El proyecto integra Python, Gradio, SQLite, Groq API y un sistema de recuperación documental basado en RAG.

## 2. Objetivo general

Desarrollar una plataforma que permita optimizar la gestión de salas y actividades de limpieza mediante la integración de inteligencia artificial, almacenamiento de información y visualización de indicadores operativos.

## 3. Objetivos específicos

- Administrar el registro de clases y horarios.
- Consultar y actualizar los estados de las salas.
- Crear, asignar y gestionar tareas de limpieza.
- Incorporar un asistente de inteligencia artificial conectado a Groq.
- Implementar recuperación de información mediante RAG.
- Visualizar indicadores operativos mediante un dashboard.
- Registrar métricas de rendimiento y actividad del asistente.
- Generar reportes para respaldar la toma de decisiones.

## 4. Arquitectura del sistema

El sistema utiliza una arquitectura modular donde cada componente cumple una función específica.

### Componentes principales

| Componente | Función |
|---|---|
| Gradio | Interfaz gráfica de usuario. |
| Python | Lógica de negocio y procesamiento de información. |
| SQLite | Almacenamiento de clases, salas, tareas y eventos. |
| Groq API | Procesamiento de consultas mediante inteligencia artificial. |
| RAG | Recuperación de documentos relevantes para proporcionar contexto. |
| Matplotlib | Generación de gráficos y visualizaciones. |
| CSV | Exportación de información. |
| ReportLab | Generación de informes en PDF. |

### Flujo de funcionamiento

1. El usuario interactúa con la interfaz de Gradio.
2. Python procesa las solicitudes y valida la información.
3. SQLite almacena y proporciona los datos necesarios.
4. El módulo RAG recupera información documental relevante.
5. Groq procesa las consultas del asistente IA.
6. El sistema registra métricas y eventos.
7. El dashboard presenta indicadores y gráficos para facilitar el análisis.

## 5. Tecnologías utilizadas

### Python
Se utiliza como lenguaje principal para desarrollar la lógica del sistema, gestionar los datos e integrar los diferentes componentes.

### Gradio
Permite construir una interfaz web organizada en pestañas, facilitando el acceso a las funcionalidades del proyecto.

### SQLite
Se utiliza como base de datos para almacenar información relacionada con clases, sensores, tareas y eventos.

### Groq API
Proporciona la capacidad de procesamiento de lenguaje natural para el asistente de inteligencia artificial.

### RAG (Retrieval-Augmented Generation)
Permite recuperar información desde documentos disponibles y utilizarla como contexto para generar respuestas más relacionadas con el proyecto.

La versión actual utiliza coincidencias de palabras clave para recuperar información, sin implementar embeddings.

### Matplotlib
Se utiliza para generar gráficos que permiten visualizar indicadores y métricas del sistema.

## 6. Funcionalidades principales

### 📊 Dashboard
Panel visual que permite consultar indicadores generales del sistema.

Incluye:
- Cantidad de salas registradas.
- Salas ocupadas.
- Salas marcadas como vacías.
- Porcentaje de ocupación declarada.
- Clases registradas durante el día.
- Tareas pendientes y en ejecución.
- Actividad reciente.

### 📚 Registro de clases
Permite registrar información de las actividades académicas:

- Profesor.
- Asignatura.
- Fecha.
- Hora.
- Sala.

También contempla validaciones para evitar conflictos de horarios en una misma sala.

### 🚪 Sensores y salas
Permite consultar y actualizar los estados declarados de las salas.

Se pueden registrar:
- Estado de ocupación.
- Cantidad de personas.
- Última actualización.

**Importante:** los sensores de esta versión son simulados y no corresponden a dispositivos físicos conectados.

### 🧹 Gestión de limpieza
Permite crear y administrar tareas de limpieza.

Cada tarea contiene:
- Sala correspondiente.
- Descripción de la actividad.
- Responsable.
- Prioridad.
- Estado de ejecución.

Los estados disponibles son:
- Pendiente.
- En progreso.
- Completada.

### 🤖 Asistente de inteligencia artificial
El asistente permite realizar consultas sobre salas, clases, tareas y documentación.

Utiliza Groq API junto con información recuperada desde SQLite y documentos incorporados al sistema.

### 📅 Calendario
Permite consultar las clases programadas durante los próximos siete días.

### 📥 Reportes
Permite exportar información de clases, tareas y estados de sensores mediante archivos CSV compatibles con Excel.

### 📈 Observabilidad IA
Permite supervisar el comportamiento del asistente mediante indicadores como:

- Cantidad de consultas.
- Latencia de respuesta.
- Tasa de errores.
- Memoria estimada.
- Evaluación de respuestas.
- Consistencia aproximada.
- Retroalimentación humana.

También incorpora gráficos, detección de anomalías y recomendaciones.

## 7. Dashboard y visualizaciones

El dashboard tiene como propósito facilitar la interpretación de los datos mediante indicadores y representaciones gráficas.

### Indicadores principales

| Indicador | Descripción |
|---|---|
| Salas registradas | Total de salas almacenadas. |
| Salas ocupadas | Salas declaradas como ocupadas. |
| Salas libres | Salas declaradas como vacías. |
| Ocupación | Porcentaje de salas declaradas ocupadas. |
| Clases del día | Cantidad de clases registradas para la fecha actual. |
| Tareas abiertas | Tareas pendientes y en progreso. |

### Gráficos implementados

**1. Estado de ocupación de salas**

Permite comparar la cantidad de salas ocupadas con aquellas declaradas como vacías.

**2. Estado de tareas de limpieza**

Permite identificar la distribución de tareas pendientes, en progreso y completadas.

**3. Rendimiento del asistente IA**

Permite visualizar la latencia de las consultas recientes y analizar el comportamiento del asistente.

**4. Observabilidad**

Incluye gráficos relacionados con latencia, errores y memoria estimada.

## 8. Decisiones de diseño y justificación técnica

Las decisiones de diseño se tomaron considerando la simplicidad, organización y facilidad de mantenimiento del prototipo.

| Decisión | Justificación |
|---|---|
| Utilizar Gradio | Facilita la creación de una interfaz web sin desarrollar un frontend independiente. |
| Utilizar SQLite | Permite almacenar información de manera sencilla y estructurada. |
| Integrar Groq | Permite incorporar un asistente conversacional mediante una API externa. |
| Implementar RAG | Permite entregar contexto documental a las respuestas de la IA. |
| Incorporar un dashboard | Facilita la interpretación de indicadores y el seguimiento de actividades. |
| Incorporar observabilidad | Permite supervisar el rendimiento y detectar posibles problemas. |
| Exportar información CSV | Facilita el análisis externo de los registros. |
| Registrar eventos | Mejora la trazabilidad de las operaciones realizadas. |

### Justificación de la validación de horarios

Se incorporaron validaciones para evitar que dos clases se registren en una misma sala durante horarios que se superponen.

Esta decisión busca reducir conflictos de planificación y mejorar la organización de los espacios.

### Separación entre ocupación y limpieza

Una sala declarada como vacía no se considera automáticamente lista para realizar una limpieza.

Es necesario contrastar la información con los horarios de clases y las condiciones operativas correspondientes.

## 9. Observabilidad y evaluación de inteligencia artificial

El módulo de observabilidad permite analizar el comportamiento del asistente mediante información registrada durante las interacciones.

Se consideran los siguientes indicadores:

- Latencia promedio y máxima.
- Cantidad de consultas procesadas.
- Errores registrados.
- Memoria estimada del proceso.
- Coincidencia de conceptos esperados.
- Consistencia textual aproximada.
- Evaluaciones realizadas por usuarios.

Las métricas automáticas proporcionan una aproximación del rendimiento, por lo que deben complementarse con evaluaciones humanas.

## 10. Seguridad y privacidad

El proyecto considera aspectos básicos de seguridad durante su implementación.

Entre ellos:

- Uso de variables de entorno para gestionar credenciales.
- Consultas SQL parametrizadas.
- Registro de eventos.
- Separación de información almacenada y lógica de procesamiento.
- Recomendación de evitar el uso de información personal o institucional confidencial.

Actualmente, el prototipo todavía no incorpora autenticación robusta ni permisos diferenciados por rol.

## 11. Limitaciones identificadas

Durante el análisis técnico se identificaron las siguientes limitaciones:

1. Los sensores son simulados y requieren integración con dispositivos físicos.
2. El sistema RAG utiliza coincidencias de palabras clave y no embeddings.
3. Las métricas de evaluación de respuestas requieren validación humana.
4. La memoria del proceso corresponde a una estimación.
5. SQLite se ejecuta dentro del entorno actual de Colab y requiere almacenamiento persistente para una operación continua.
6. No existe todavía un sistema completo de autenticación y autorización por roles.

## 12. Recomendaciones de mejora

Para futuras versiones se proponen las siguientes mejoras:

- Integrar sensores físicos de movimiento y ocupación.
- Incorporar autenticación y permisos por usuario.
- Implementar almacenamiento persistente.
- Incorporar embeddings y búsqueda vectorial para mejorar la recuperación documental.
- Ampliar las pruebas de evaluación del asistente.
- Incorporar filtros por fecha y sala en el dashboard.
- Mejorar el historial de métricas y generar reportes periódicos.

## 13. Conclusión

LimpIA 2.0 representa una solución tecnológica que integra gestión de salas, planificación de limpieza, almacenamiento de información e inteligencia artificial.

La incorporación de un dashboard permite visualizar indicadores relevantes, mientras que el módulo de observabilidad facilita el análisis del rendimiento del asistente.

Las decisiones de diseño buscan mantener una arquitectura sencilla, organizada y ampliable, permitiendo incorporar nuevas funcionalidades en futuras versiones.

Aunque el proyecto todavía presenta limitaciones relacionadas con los sensores simulados, la seguridad y la persistencia de datos, constituye una base funcional para continuar desarrollando un sistema inteligente de gestión de espacios.

---

## 14. Evidencias visuales

En esta sección se incorporan capturas de pantalla del funcionamiento de LimpIA 2.0.

### Dashboard principal

# 🧹 LimpIA 2.0 – Sistema Inteligente de Gestión de Salas y Limpieza

## 1. Descripción del proyecto

LimpIA 2.0 es un sistema inteligente diseñado para apoyar la gestión de salas y la planificación de tareas de limpieza dentro de una institución educativa.

La plataforma permite administrar clases, consultar estados de salas, registrar tareas de limpieza y utilizar un asistente de inteligencia artificial para responder preguntas relacionadas con la información almacenada.

El proyecto integra Python, Gradio, SQLite, Groq API y un sistema de recuperación documental basado en RAG.

## 2. Objetivo general

Desarrollar una plataforma que permita optimizar la gestión de salas y actividades de limpieza mediante la integración de inteligencia artificial, almacenamiento de información y visualización de indicadores operativos.

## 3. Objetivos específicos

- Administrar el registro de clases y horarios.
- Consultar y actualizar los estados de las salas.
- Crear, asignar y gestionar tareas de limpieza.
- Incorporar un asistente de inteligencia artificial conectado a Groq.
- Implementar recuperación de información mediante RAG.
- Visualizar indicadores operativos mediante un dashboard.
- Registrar métricas de rendimiento y actividad del asistente.
- Generar reportes para respaldar la toma de decisiones.

## 4. Arquitectura del sistema

El sistema utiliza una arquitectura modular donde cada componente cumple una función específica.

### Componentes principales

| Componente | Función |
|---|---|
| Gradio | Interfaz gráfica de usuario. |
| Python | Lógica de negocio y procesamiento de información. |
| SQLite | Almacenamiento de clases, salas, tareas y eventos. |
| Groq API | Procesamiento de consultas mediante inteligencia artificial. |
| RAG | Recuperación de documentos relevantes para proporcionar contexto. |
| Matplotlib | Generación de gráficos y visualizaciones. |
| CSV | Exportación de información. |
| ReportLab | Generación de informes en PDF. |

### Flujo de funcionamiento

1. El usuario interactúa con la interfaz de Gradio.
2. Python procesa las solicitudes y valida la información.
3. SQLite almacena y proporciona los datos necesarios.
4. El módulo RAG recupera información documental relevante.
5. Groq procesa las consultas del asistente IA.
6. El sistema registra métricas y eventos.
7. El dashboard presenta indicadores y gráficos para facilitar el análisis.

## 5. Tecnologías utilizadas

### Python
Se utiliza como lenguaje principal para desarrollar la lógica del sistema, gestionar los datos e integrar los diferentes componentes.

### Gradio
Permite construir una interfaz web organizada en pestañas, facilitando el acceso a las funcionalidades del proyecto.

### SQLite
Se utiliza como base de datos para almacenar información relacionada con clases, sensores, tareas y eventos.

### Groq API
Proporciona la capacidad de procesamiento de lenguaje natural para el asistente de inteligencia artificial.

### RAG (Retrieval-Augmented Generation)
Permite recuperar información desde documentos disponibles y utilizarla como contexto para generar respuestas más relacionadas con el proyecto.

La versión actual utiliza coincidencias de palabras clave para recuperar información, sin implementar embeddings.

### Matplotlib
Se utiliza para generar gráficos que permiten visualizar indicadores y métricas del sistema.

## 6. Funcionalidades principales

### 📊 Dashboard
Panel visual que permite consultar indicadores generales del sistema.

Incluye:
- Cantidad de salas registradas.
- Salas ocupadas.
- Salas marcadas como vacías.
- Porcentaje de ocupación declarada.
- Clases registradas durante el día.
- Tareas pendientes y en ejecución.
- Actividad reciente.

### 📚 Registro de clases
Permite registrar información de las actividades académicas:

- Profesor.
- Asignatura.
- Fecha.
- Hora.
- Sala.

También contempla validaciones para evitar conflictos de horarios en una misma sala.

### 🚪 Sensores y salas
Permite consultar y actualizar los estados declarados de las salas.

Se pueden registrar:
- Estado de ocupación.
- Cantidad de personas.
- Última actualización.

**Importante:** los sensores de esta versión son simulados y no corresponden a dispositivos físicos conectados.

### 🧹 Gestión de limpieza
Permite crear y administrar tareas de limpieza.

Cada tarea contiene:
- Sala correspondiente.
- Descripción de la actividad.
- Responsable.
- Prioridad.
- Estado de ejecución.

Los estados disponibles son:
- Pendiente.
- En progreso.
- Completada.

### 🤖 Asistente de inteligencia artificial
El asistente permite realizar consultas sobre salas, clases, tareas y documentación.

Utiliza Groq API junto con información recuperada desde SQLite y documentos incorporados al sistema.

### 📅 Calendario
Permite consultar las clases programadas durante los próximos siete días.

### 📥 Reportes
Permite exportar información de clases, tareas y estados de sensores mediante archivos CSV compatibles con Excel.

### 📈 Observabilidad IA
Permite supervisar el comportamiento del asistente mediante indicadores como:

- Cantidad de consultas.
- Latencia de respuesta.
- Tasa de errores.
- Memoria estimada.
- Evaluación de respuestas.
- Consistencia aproximada.
- Retroalimentación humana.

También incorpora gráficos, detección de anomalías y recomendaciones.

## 7. Dashboard y visualizaciones

El dashboard tiene como propósito facilitar la interpretación de los datos mediante indicadores y representaciones gráficas.

### Indicadores principales

| Indicador | Descripción |
|---|---|
| Salas registradas | Total de salas almacenadas. |
| Salas ocupadas | Salas declaradas como ocupadas. |
| Salas libres | Salas declaradas como vacías. |
| Ocupación | Porcentaje de salas declaradas ocupadas. |
| Clases del día | Cantidad de clases registradas para la fecha actual. |
| Tareas abiertas | Tareas pendientes y en progreso. |

### Gráficos implementados

**1. Estado de ocupación de salas**

Permite comparar la cantidad de salas ocupadas con aquellas declaradas como vacías.

**2. Estado de tareas de limpieza**

Permite identificar la distribución de tareas pendientes, en progreso y completadas.

**3. Rendimiento del asistente IA**

Permite visualizar la latencia de las consultas recientes y analizar el comportamiento del asistente.

**4. Observabilidad**

Incluye gráficos relacionados con latencia, errores y memoria estimada.

## 8. Decisiones de diseño y justificación técnica

Las decisiones de diseño se tomaron considerando la simplicidad, organización y facilidad de mantenimiento del prototipo.

| Decisión | Justificación |
|---|---|
| Utilizar Gradio | Facilita la creación de una interfaz web sin desarrollar un frontend independiente. |
| Utilizar SQLite | Permite almacenar información de manera sencilla y estructurada. |
| Integrar Groq | Permite incorporar un asistente conversacional mediante una API externa. |
| Implementar RAG | Permite entregar contexto documental a las respuestas de la IA. |
| Incorporar un dashboard | Facilita la interpretación de indicadores y el seguimiento de actividades. |
| Incorporar observabilidad | Permite supervisar el rendimiento y detectar posibles problemas. |
| Exportar información CSV | Facilita el análisis externo de los registros. |
| Registrar eventos | Mejora la trazabilidad de las operaciones realizadas. |

### Justificación de la validación de horarios

Se incorporaron validaciones para evitar que dos clases se registren en una misma sala durante horarios que se superponen.

Esta decisión busca reducir conflictos de planificación y mejorar la organización de los espacios.

### Separación entre ocupación y limpieza

Una sala declarada como vacía no se considera automáticamente lista para realizar una limpieza.

Es necesario contrastar la información con los horarios de clases y las condiciones operativas correspondientes.

## 9. Observabilidad y evaluación de inteligencia artificial

El módulo de observabilidad permite analizar el comportamiento del asistente mediante información registrada durante las interacciones.

Se consideran los siguientes indicadores:

- Latencia promedio y máxima.
- Cantidad de consultas procesadas.
- Errores registrados.
- Memoria estimada del proceso.
- Coincidencia de conceptos esperados.
- Consistencia textual aproximada.
- Evaluaciones realizadas por usuarios.

Las métricas automáticas proporcionan una aproximación del rendimiento, por lo que deben complementarse con evaluaciones humanas.

## 10. Seguridad y privacidad

El proyecto considera aspectos básicos de seguridad durante su implementación.

Entre ellos:

- Uso de variables de entorno para gestionar credenciales.
- Consultas SQL parametrizadas.
- Registro de eventos.
- Separación de información almacenada y lógica de procesamiento.
- Recomendación de evitar el uso de información personal o institucional confidencial.

Actualmente, el prototipo todavía no incorpora autenticación robusta ni permisos diferenciados por rol.

## 11. Limitaciones identificadas

Durante el análisis técnico se identificaron las siguientes limitaciones:

1. Los sensores son simulados y requieren integración con dispositivos físicos.
2. El sistema RAG utiliza coincidencias de palabras clave y no embeddings.
3. Las métricas de evaluación de respuestas requieren validación humana.
4. La memoria del proceso corresponde a una estimación.
5. SQLite se ejecuta dentro del entorno actual de Colab y requiere almacenamiento persistente para una operación continua.
6. No existe todavía un sistema completo de autenticación y autorización por roles.

## 12. Recomendaciones de mejora

Para futuras versiones se proponen las siguientes mejoras:

- Integrar sensores físicos de movimiento y ocupación.
- Incorporar autenticación y permisos por usuario.
- Implementar almacenamiento persistente.
- Incorporar embeddings y búsqueda vectorial para mejorar la recuperación documental.
- Ampliar las pruebas de evaluación del asistente.
- Incorporar filtros por fecha y sala en el dashboard.
- Mejorar el historial de métricas y generar reportes periódicos.

## 13. Conclusión

LimpIA 2.0 representa una solución tecnológica que integra gestión de salas, planificación de limpieza, almacenamiento de información e inteligencia artificial.

La incorporación de un dashboard permite visualizar indicadores relevantes, mientras que el módulo de observabilidad facilita el análisis del rendimiento del asistente.

Las decisiones de diseño buscan mantener una arquitectura sencilla, organizada y ampliable, permitiendo incorporar nuevas funcionalidades en futuras versiones.

Aunque el proyecto todavía presenta limitaciones relacionadas con los sensores simulados, la seguridad y la persistencia de datos, constituye una base funcional para continuar desarrollando un sistema inteligente de gestión de espacios.

---

## 14. Evidencias visuales

<img width="591" height="380" alt="image" src="https://github.com/user-attachments/assets/e751b936-61e0-46e5-9148-3787e6f8b08c" />

<img width="1580" height="478" alt="image" src="https://github.com/user-attachments/assets/b5a575a8-483d-4520-a839-92ce6710fc2f" />



### Dashboard principal

<img width="1272" height="623" alt="image" src="https://github.com/user-attachments/assets/0602616e-e404-4c9d-8bfd-3b8caf46cff8" />


### Arquitectura del sistema

<img width="1574" height="222" alt="image" src="https://github.com/user-attachments/assets/21798f6c-b1a5-43cb-b672-67dcae7889ed" />


### Asistente de inteligencia artificial

<img width="1526" height="488" alt="image" src="https://github.com/user-attachments/assets/caadb030-7d2c-4133-bd29-9030dd62b600" />


### Observabilidad

<img width="1622" height="537" alt="image" src="https://github.com/user-attachments/assets/c4c50e68-7fd0-428d-9f37-a8c74b13ac8b" />

<img width="1483" height="507" alt="image" src="https://github.com/user-attachments/assets/48b17572-816c-4f8b-8b72-6eec06562571" />



### Gestión de limpieza

<img width="1678" height="431" alt="image" src="https://github.com/user-attachments/assets/65dd7911-b29f-4baf-a19c-86302d405f4f" />




**Proyecto académico: LimpIA 2.0**  
**Tecnologías:** Python · Gradio · SQLite · Groq API · RAG · Matplotlib  
**Autor:** Benjamin Donoso


