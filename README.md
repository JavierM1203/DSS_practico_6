# Resumen Ejecutivo

## Resultados de SonarQube vs vulnerabilidades previamente identificadas. 

## Falsos positivos y falsos negativos identificados. 

## Limitaciones de la versión Community de SonarQube en el análisis de archivos JSP.  
La versión Community no analiza el codigo Java dentro de los archivos JSP. 
El rastreo avanzado de datos para archivos JSP solo está disponible a partir de la edición Developer de SonarQube (v8.3+).



## Limitaciones de los tipos de vulnerabilidades que puede detectar la versión Community SonarQube. 

1. **No realiza un rastreo de flujo de datos**
No realiza un analisis profundo para detectar problemas inyecciones SQL, ya que no verifica si:**
   a. La entrada proviene de una fuente externa (introducida por un usuario), es decir, no rastrea si una variable está "manchada" con 
      datos no confiables.
   b. Los datos inseguros alcanzan un "sink" (punto de riesgo) vulnerable, como un método de ejecución SQL, sin ser sanitizados.

**El rastreo de flujo de datos está disponible a partir de la edición Developer, como se indica en sus características:**
"Configuración personalizada del motor de seguridad para un análisis de manchas más potente"

Esto significa que la Community no analiza cómo los datos fluyen a través de diferentes componentes en el código ni detecta vulnerabilidades que dependen de este análisis.

**Nota:** Aunque puede detectar inyecciones SQL a través de Security Hotspots, este enfoque solo utiliza reglas simples que buscan patrones estáticos comunes en el código. 

2. **Se limita a errores básicos como código muerto, mal uso de variables o complejidad alta.**
Debido a que:

La Community realiza únicamente análisis estático básico, como se indica en sus características:
"Detectar errores y vulnerabilidades básicas en el código" y "Revisión de los puntos de acceso de seguridad".
**Esto se traduce en problemas menores como:**
a. Variables no utilizadas (Código que reserva memoria pero no se ejecuta)
b. Código duplicado (Fragmentos repetidos que dificultan el mantenimiento)
c. complejidad ciclomatica alta (Código con demasiadas ramificaciones o caminos posibles, lo que lo hace difícil de entender, probar y mantener)

**La edición Developer amplía esta capacidad con:**
"Análisis de contaminación con SAST más profundo para Java, C#, JavaScript y TypeScript" y "Detección de errores avanzados que causan errores de tiempo de ejecución y bloqueos".

3. **No detecta vulnerabilidades avanzadas ni problemas de configuración**. 
*No detecta:* Deserialización insegura, Cross-Site Scripting (XSS) ni problemas de configuración de seguridad, como credenciales por defecto o malas configuraciones de permisos.
Esto se debe a la falta de motores avanzados de análisis estático de seguridad (SAST) y rastreo de flujo de datos, que solo están disponibles en las ediciones Developer y superiores. 
