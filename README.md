# Resumen Ejecutivo

## Resultados de SonarQube vs vulnerabilidades previamente identificadas. 

## Falsos positivos y falsos negativos identificados. 

## Limitaciones de la versión Community de SonarQube en el análisis de archivos JSP.  
La versión Community no analiza el codigo Java dentro de los archivos JSP. 
El rastreo avanzado de datos para archivos JSP solo está disponible a partir de la edición Developer de SonarQube (v8.3+).



## Limitaciones de los tipos de vulnerabilidades que puede detectar la versión Community SonarQube. 

1. **No realiza un rastreo de flujo de datos**
No realiza un analisis profundo para detectar problemas inyecciones SQL, ya que no verifica si:**
   a. La entrada proviene de una fuente externa (introducida por un usuario), es decir una variable manchada.
   b. Los datos inseguros alcanzan un "sink" (punto de riesgo) vulnerable (como un método de ejecución SQL) sin ser sanitizados.

El rastreo de flujo de datos esta disponible a partir de la edición Developer. En ella se menciona:
"Configuración personalizada del motor de seguridad para un análisis de manchas más potente"

Por lo tanto, la Community no puede analizar cómo los datos se propagan a través de componentes del código ni detectar vulnerabilidades asociadas a ello.

Solo se puede detectar inyecciones SQL, a traves del Security Hotspots, que se basa en reglas simples, que buscan patrones comunes en el código, sin requerir rastreo de flujo de datos, sino una búsqueda estática basada en reglas definidas. 

2. **Se limita a errores básicos como código muerto, mal uso de variables o complejidad alta.**
Debido a que:

La Community realiza únicamente análisis estático básico, como se indica en sus características:
"Detectar errores y vulnerabilidades básicas en el código" y "Revisión de los puntos de acceso de seguridad".
**Esto se traduce en problemas menores como:**
Variables no utilizadas, Código duplicado o complejidad ciclomatica alta.

**La edición Developer amplía esta capacidad con:**
"Análisis de contaminación con SAST más profundo para Java, C#, JavaScript y TypeScript" y "Detección de errores avanzados que causan errores de tiempo de ejecución y bloqueos".
