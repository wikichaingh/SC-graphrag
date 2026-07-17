# SC-graphrag
Archivos para caso GraphRAG

GraphRAG para resiliencia en cadena de suministro
Este repositorio contiene un caso didáctico para desarrollar un prototipo de GraphRAG aplicado a cadena de suministro con datos estructurados de proveedores, materiales, plantas, productos, órdenes y rutas logísticas. Un README en GitHub debe explicar por qué el proyecto es útil, qué contiene y cómo empezar a usarlo, por lo que este documento está redactado como guía inicial para estudiantes de maestría. 

Propósito del repositorio
El objetivo académico de este repositorio es que el estudiante construya un modelo de grafo sobre una red de suministro y lo utilice después en un flujo de recuperación aumentada con grafos (GraphRAG). GitHub recomienda que el README explique qué hace el proyecto, por qué es útil y cómo comenzar, y en proyectos de datos también es recomendable documentar la estructura de archivos, significado de variables y forma de reutilización. 

Este caso está pensado para analizar preguntas de resiliencia operativa como las siguientes:
¿Qué productos quedan afectados si falla un proveedor crítico?
¿Qué plantas dependen de un material sin sustituto inmediato?
¿Qué órdenes y clientes se ven comprometidos por una interrupción?
¿Qué rutas o proveedores alternativos pueden reducir el impacto?

Resultados de aprendizaje
Al completar este ejercicio, el estudiante será capaz de:
Diseñar un modelo de grafo a partir de tablas CSV de cadena de suministro.
Importar datos en Neo4j Aura usando herramientas web.
Formular consultas Cypher para identificar dependencias, cuellos de botella y rutas alternativas.
Conectar el grafo con una capa GraphRAG mediante LangChain o LlamaIndex.
Redactar una interpretación ejecutiva de riesgo y resiliencia a partir de evidencia estructurada.
Estructura del repositorio
GitHub muestra el README.md en la raíz del repositorio y esa ubicación es la recomendada para que los visitantes entiendan el proyecto desde la página principal. En proyectos de datos también es buena práctica describir la estructura del repositorio y el propósito de cada archivo. 

Se sugiere la siguiente organización:
supply-chain-graphrag/
├── README.md

├── data/

│   ├── proveedores.csv

│   ├── materias_primas.csv

│   ├── plantas.csv

│   ├── productos.csv

│   ├── bom.csv

│   ├── relaciones_proveedor_material.csv

│   ├── ordenes_abiertas.csv

│   └── rutas_transporte.csv

├── cypher/

│   ├── 01_constraints.cypher

│   ├── 02_nodos.cypher

│   └── 03_relaciones.cypher

├── notebooks/

│   └── graphrag_colab.ipynb

└── docs/

    └── guia_del_caso.md
    
Modelo conceptual
El grafo se construye transformando tablas relacionales en entidades y relaciones. GraphAcademy y la documentación de importación de Neo4j recomiendan definir primero el modelo lógico, después crear restricciones y finalmente importar nodos y relaciones desde CSV. 
neo4j
+2

Modelo propuesto:

(:Proveedor)-[:SUMINISTRA]->(:Material)

(:Producto)-[:REQUIERE]->(:Material)

(:Planta)-[:PRODUCE]->(:Producto)

(:Orden)-[:ES_DE_PRODUCTO]->(:Producto)

(:Orden)-[:SE_FABRICA_EN]->(:Planta)

(:Orden)-[:DESTINADA_A]->(:Cliente)

(:Planta)-[:TIENE_RUTA]->(:Ruta)

Requisitos mínimos
Para desarrollar el caso completamente en plataformas web se requiere una instancia de Neo4j AuraDB, un repositorio de GitHub para alojar los CSV y un notebook web, por ejemplo Google Colab, para la fase GraphRAG. Neo4j documenta Aura como entorno en la nube para cargar datos e interactuar con Browser o Data Importer, y el uso de CSV remotos por URL pública es compatible con LOAD CSV. 
neo4j
+2

Herramientas recomendadas
Neo4j AuraDB Free

Neo4j Data Importer

Neo4j GraphAcademy

GitHub

Google Colab

Procedimiento sugerido
1. Crear el repositorio
Crear un repositorio público en GitHub y activar la opción de README. GitHub indica que el README es la primera pieza que un visitante suele ver y debe explicar utilidad, contenido y punto de partida del proyecto. 
2. Subir los CSV
Subir los archivos del directorio data/ al repositorio. GitHub permite cargar archivos desde la interfaz web y los CSV quedarán disponibles en el repositorio para consulta y descarga. 
3. Crear la base en Neo4j Aura
Crear una instancia gratuita de AuraDB y guardar la URI, el usuario y la contraseña. La documentación de Aura establece que la base debe existir antes de iniciar cualquier proceso de importación o conexión. 
neo4j
4. Importar los datos
Usar Neo4j Data Importer o LOAD CSV con URLs públicas tipo raw.githubusercontent.com. Neo4j documenta que en Aura los archivos CSV deben estar disponibles en una ubicación remota accesible por URL para ser consumidos con LOAD CSV. 
5. Validar el grafo
Comprobar el número de nodos, relaciones y consultas básicas de trazabilidad. Esta verificación forma parte del proceso recomendado de importación y control de calidad del modelo. 
6. Conectar GraphRAG
En Google Colab, conectar Python con Neo4j Aura y construir un prototipo de recuperación híbrida con LangChain o LlamaIndex para responder preguntas de resiliencia. Neo4j documenta flujos GraphRAG donde se combinan consultas al grafo, vector search y prompting dinámico. 

Ejemplo de pregunta de negocio
Una vez importado el modelo, el equipo debe ser capaz de responder una pregunta como esta:
Si el proveedor P001 se interrumpe durante 30 días, ¿qué materiales, productos, plantas, órdenes y clientes quedan afectados y qué alternativas existen para mitigar el impacto?
Esta pregunta obliga a recorrer múltiples relaciones del grafo, por lo que constituye un ejemplo adecuado de razonamiento relacional para GraphRAG. 

Recomendaciones metodológicas para el curso
Se recomienda que cada equipo documente explícitamente tres elementos: el modelo de grafo, la lógica de importación y la interpretación gerencial del caso. Los lineamientos para README y documentación de datos destacan que debe explicarse no sólo qué archivos existen, sino cómo se generaron, cómo se relacionan y cómo deben reutilizarse. 

Cada entrega puede incluir:
1. Diagrama del modelo conceptual.
2. Capturas del grafo en Neo4j.
3. Consultas Cypher de validación.
4. Una narrativa ejecutiva sobre riesgo y resiliencia.
5. Reflexión sobre limitaciones de datos, supuestos y mejoras futuras.

Buenas prácticas
No subir credenciales, contraseñas ni claves API al repositorio; GitHub recomienda usar mecanismos de exclusión como .gitignore para archivos que no deban versionarse. 
Mantener nombres de archivo simples y consistentes.
Usar encabezados claros en todos los CSV.
Incluir un diccionario de datos cuando el proyecto crezca en complejidad. La documentación de gestión de datos recomienda describir variables, unidades, códigos y convenciones de nulos o vacíos. 
Versionar cambios importantes del dataset con mensajes de commit descriptivos.

Criterios de evaluación sugeridos
Criterio	            Qué se espera

Diseño del modelo   	Correspondencia lógica entre CSV, nodos y relaciones

Calidad de importación	Carga correcta, sin duplicados y con tipos de datos consistentes

Consultas Cypher    	Capacidad para responder preguntas de trazabilidad y resiliencia

Implementación GraphRAG	Integración funcional entre grafo, recuperación y generación

Análisis gerencial	    Interpretación rigurosa del impacto operativo y alternativas


Créditos y uso académico
Este repositorio se ha concebido con fines didácticos para cursos de maestría en cadena de suministro, analítica y sistemas inteligentes aplicados a operaciones. La práctica puede adaptarse a otros contextos industriales, siempre que se mantenga la lógica de relaciones entre proveedores, materiales, instalaciones, productos y demanda.
