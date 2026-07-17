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
