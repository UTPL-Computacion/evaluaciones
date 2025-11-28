# Evaluación de Programación Reactiva y Funcional

## Información General

- **Fecha de entrega del código:** Viernes hasta las 23:59
- **Fecha de defensa oral:** Sábado (hora a coordinar)
- **Duración de la defensa:** 15-20 minutos por estudiante
- **Modalidad:** Presencial
- **Puntaje total:** 10 puntos

### Distribución de Calificaciones

- **[ACDB1] Aprendizaje en Contacto con el Docente - Bimestre I:** 3.5 puntos
- **[APEB1] Aprendizaje Práctico Experimental - Bimestre I:** 3.5 puntos
- **[AAB1] Aprendizaje Autónomo - Bimestre I:** 3 puntos

---

## Caso de Uso: Sistema de Gestión de Biblioteca Digital

Desarrollarás un sistema de gestión para una biblioteca digital que permita administrar libros, usuarios y préstamos. El sistema debe implementarse utilizando paradigmas de programación funcional en **JavaScript** y **Scala**.

### Contexto del Problema

La Biblioteca UTPL necesita un sistema que:
- Gestione un catálogo de libros técnicos y académicos
- Administre usuarios y sus preferencias de lectura
- Procese solicitudes de préstamo y devoluciones
- Genere reportes y estadísticas
- Recomiende libros basándose en el historial del usuario

---

## COMPONENTE 1: [ACDB1] Aprendizaje en Contacto con el Docente (3.5 puntos)

**Evaluación:** Defensa oral presencial el día sábado

Durante la defensa oral deberás explicar y defender tu código implementado. Se evaluará tu comprensión conceptual y capacidad de argumentación sobre las decisiones técnicas tomadas.

### Rúbrica de Evaluación - Defensa Oral

| Criterio | Excelente | Bueno | Regular | Deficiente | Peso |
|----------|-----------|-------|---------|------------|------|
| **Comprensión de Paradigmas** | Explica claramente las diferencias entre imperativo y declarativo con ejemplos concretos de su código | Identifica diferencias pero con explicaciones superficiales | Confunde conceptos o no puede ejemplificar adecuadamente | No comprende las diferencias fundamentales | 0.9 pts |
| **Funciones Puras e Inmutabilidad** | Demuestra dominio total: explica por qué sus funciones son puras, consecuencias de inmutabilidad, ventajas en testing | Comprende el concepto pero no profundiza en las implicaciones | Explica de manera superficial o con errores conceptuales | No puede explicar o justificar su implementación | 0.9 pts |
| **Funciones de Orden Superior** | Explica fluidamente cómo funcionan, por qué las usó, y alternativas; domina closures | Explica el funcionamiento básico pero no profundiza en el "por qué" | Explica con dificultad o confunde conceptos | No puede explicar su implementación | 0.7 pts |
| **Map, Filter, Reduce** | Explica con claridad cuándo usar cada uno, ventajas sobre loops, y defiende sus decisiones de diseño | Explica el uso básico pero no puede justificar decisiones de diseño | Conoce la sintaxis pero no el propósito o ventajas | No comprende las operaciones | 0.7 pts |
| **Capacidad de Refactorización** | Ante sugerencias, puede refactorizar mentalmente y explicar alternativas superiores | Comprende sugerencias pero con dificultad para proponer alternativas | No puede mejorar su código o proponer alternativas | No comprende las sugerencias | 0.3 pts |

**Total Componente 1: 3.5 puntos**

### Preguntas Tipo para la Defensa Oral

**Sobre Paradigmas:**
- ¿Por qué elegiste este enfoque declarativo en lugar de imperativo aquí?
- ¿Qué problemas podrían surgir si mutas este dato?
- ¿Cómo mejoraría esto el testing de tu aplicación?

**Sobre Funciones:**
- ¿Esta función es pura? ¿Por qué sí o por qué no?
- ¿Qué pasaría si esta función tuviera efectos secundarios?
- ¿Cómo se diferencia esta función de un método tradicional?

**Sobre Operaciones Funcionales:**
- ¿Por qué usaste `reduce` aquí en lugar de `map`?
- ¿Podrías resolver esto con un solo `reduce` en lugar de encadenar operaciones?
- ¿Cómo optimizarías esta cadena de transformaciones?

**Sobre Lenguajes:**
- ¿Qué características de Scala facilitan la programación funcional vs JavaScript?
- ¿Cuándo preferirías usar Scala sobre JavaScript para este tipo de problemas?

---

## COMPONENTE 2: [APEB1] Aprendizaje Práctico Experimental (3.5 puntos)

**Evaluación:** Implementación de código funcional en JavaScript y Scala

### Parte 1: Paradigmas y Datos Inmutables (1 punto)

#### 1.1 Programación Imperativa vs Declarativa - JavaScript (0.5 puntos)

Implementa la siguiente funcionalidad en **ambos paradigmas**:

**Requisito:** Filtrar libros disponibles (no prestados) de una categoría específica y ordenarlos por año de publicación.

```javascript
const libros = [
  { id: 1, titulo: "Clean Code", categoria: "Programacion", anio: 2008, prestado: false },
  { id: 2, titulo: "Design Patterns", categoria: "Programacion", anio: 1994, prestado: true },
  { id: 3, titulo: "Refactoring", categoria: "Programacion", anio: 1999, prestado: false },
  { id: 4, titulo: "Calculus", categoria: "Matematicas", anio: 2010, prestado: false }
];
```

**Debes entregar:**
- Versión imperativa (usando loops, mutación)
- Versión declarativa (usando métodos funcionales)

#### 1.2 Datos Inmutables - Scala (0.5 puntos)

Implementa una función que actualice el estado de un préstamo sin mutar los datos originales.

**Requisito:** Crear una nueva versión de la colección de préstamos cuando se devuelve un libro.

```scala
case class Prestamo(id: Int, usuarioId: Int, libroId: Int, activo: Boolean, fechaPrestamo: String)

def devolverLibro(prestamos: List[Prestamo], prestamoId: Int): List[Prestamo] = {
  // Tu implementacion
}
```

---

### Parte 2: Funciones Puras - JavaScript (1 punto)

Implementa las siguientes funciones puras:

**a) Calcular días de retraso (0.5 puntos)**
```javascript
// Debe ser pura: mismo input = mismo output, sin efectos secundarios
function calcularDiasRetraso(fechaPrestamo, fechaDevolucion, diasPermitidos) {
  // Tu implementacion
}
```

**b) Calcular multa por retraso (0.5 puntos)**
```javascript
// Regla: $0.50 por dia de retraso
function calcularMulta(diasRetraso) {
  // Tu implementacion (debe ser pura)
}
```

---

### Parte 3: Funciones de Orden Superior - JavaScript (0.5 puntos)

**a) Función que retorna una función (Closure) (0.25 puntos)**
```javascript
// Crear un filtrador personalizado
function crearFiltrador(criterio) {
  // Debe retornar una funcion que filtre libros segun el criterio
  // Ejemplo de uso:
  // const filtrarProgramacion = crearFiltrador({ categoria: "Programacion" });
  // const librosProgramacion = libros.filter(filtrarProgramacion);
}
```

**b) Función que recibe función como parámetro (0.25 puntos)**
```javascript
// Procesar prestamos con diferentes estrategias
function procesarPrestamos(prestamos, estrategia) {
  // estrategia es una funcion que define como procesar cada prestamo
}
```

---

### Parte 4: Map, Filter, Reduce - JavaScript (1 punto)

Implementa un sistema de recomendaciones usando **solo** `map`, `filter`, y `reduce`:

```javascript
/**
 * Sistema de recomendacion de libros
 *
 * Requisitos:
 * 1. Filtrar libros de categorias que el usuario ha leido antes
 * 2. Mapear para agregar un score de recomendacion basado en:
 *    - Popularidad del libro (cantidad de prestamos)
 *    - Anio de publicacion (mas recientes tienen mayor score)
 *    - Rating promedio
 * 3. Reducir para obtener los top 10 libros recomendados
 */

function recomendarLibros(libros, usuario, historialPrestamos) {
  // Tu implementacion usando SOLO map, filter, reduce
  // NO usar loops ni mutacion
}
```

**Total Componente 2: 3.5 puntos**

---

## COMPONENTE 3: [AAB1] Aprendizaje Autónomo (3 puntos)

**Evaluación:** Investigación, análisis y aplicación en Scala

### Parte 1: Funciones vs Métodos en Scala (1 punto)

Implementa la misma funcionalidad de "buscar libros por autor" de dos formas:

**a) Como método de una clase**
```scala
case class Libro(id: Int, titulo: String, autor: String, categoria: String)

class Biblioteca(libros: List[Libro]) {
  def buscarPorAutor(autor: String): List[Libro] = {
    // Tu implementacion
  }
}
```

**b) Como función pura**
```scala
def buscarPorAutor(libros: List[Libro], autor: String): List[Libro] = {
  // Tu implementacion
}
```

**Debes explicar en comentarios:**
- Diferencias conceptuales
- Ventajas y desventajas de cada enfoque
- Cuándo usar uno u otro

---

### Parte 2: Tuplas y Operaciones Funcionales en Scala (1 punto)

**a) Tuplas (0.5 puntos)**
```scala
// Funcion que retorna estadisticas de un usuario usando tuplas
def obtenerEstadisticasUsuario(prestamos: List[Prestamo], usuarioId: Int): (Int, Int, Double) = {
  // Retornar: (totalPrestamos, prestamosActivos, promedioLibrosPorMes)
}
```

**b) Map, Filter, Reduce en Scala (0.5 puntos)**
```scala
case class Libro(id: Int, titulo: String, autor: String, categoria: String, anio: Int, rating: Double, precio: Double)
case class Prestamo(libroId: Int, usuarioId: Int, fechaPrestamo: String, fechaDevolucion: Option[String])

/**
 * Generar reporte financiero
 *
 * Requisitos:
 * 1. Filtrar prestamos del ultimo anio
 * 2. Mapear para calcular ingresos por multas
 * 3. Agrupar por categoria de libro
 * 4. Reducir para obtener total de ingresos por categoria
 */

def generarReporteFinanciero(
  libros: List[Libro],
  prestamos: List[Prestamo],
  fechaActual: String
): Map[String, Double] = {
  // Tu implementacion usando map, filter, groupBy, reduce/fold
}
```

---

### Parte 3: Documento de Reflexión (1 punto)

Crea un archivo `REFLEXION.md` respondiendo (máximo 2 páginas):

1. **Comparación de Paradigmas (0.25 puntos):** ¿Qué ventajas encontraste al usar programación funcional en este caso de uso? ¿Qué desafíos enfrentaste al evitar la mutación?

2. **Análisis Crítico (0.25 puntos):** ¿En qué situaciones preferirías programación funcional sobre imperativa y viceversa?

3. **Comparación de Lenguajes (0.25 puntos):** Diferencias entre JavaScript y Scala para programación funcional. ¿Cuál te pareció más adecuado y por qué?

4. **Aplicación Práctica (0.25 puntos):** ¿Cómo aplicarías estos conceptos en un proyecto real? Da ejemplos concretos.

**Total Componente 3: 3 puntos**

---

## Entregables

### Estructura del Proyecto

```
evaluacion-reactiva-funcional/
│
├── javascript/
│   ├── parte1-paradigmas.js
│   ├── parte2-funciones-puras.js
│   ├── parte3-orden-superior.js
│   └── parte4-recomendaciones.js
│
├── scala/
│   ├── parte1-inmutabilidad.scala
│   ├── parte2-funciones-vs-metodos.scala
│   └── parte3-operaciones-funcionales.scala
│
├── REFLEXION.md
└── README.md (instrucciones de ejecución)
```

### Contenido Mínimo del README.md

- Nombre completo del estudiante
- Instrucciones para ejecutar el código JavaScript
- Instrucciones para compilar y ejecutar el código Scala
- Dependencias necesarias
- Breve explicación de la estructura del proyecto

---

## Criterios de Penalización

- **Código que no ejecuta:** -2 puntos del componente correspondiente
- **Uso de mutación donde debería ser inmutable:** -0.5 puntos por ocurrencia
- **Funciones impuras presentadas como puras:** -0.5 puntos por ocurrencia
- **No usar map/filter/reduce donde era requerido:** -1 punto
- **Entrega tardía:** -1 punto por cada día
- **No presentarse a la defensa oral:** 0 puntos en el Componente 1 (ACDB1)
- **Plagio o código copiado:** 0 puntos en toda la evaluación

---

## Recursos Permitidos Durante la Defensa

- Tu propio código impreso o en pantalla
- Documentación oficial de JavaScript/Scala (sin internet)
- Apuntes de clase

## Recursos NO Permitidos

- Internet o búsquedas en tiempo real
- Código de otros compañeros
- Asistencia externa durante la defensa
- Uso de IA generativa durante la defensa

---

## Fechas Importantes

| Actividad | Fecha | Hora |
|-----------|-------|------|
| Publicación de evaluación | [Fecha actual] | - |
| Consultas permitidas | Hasta el viernes | 18:00 |
| Entrega del código | Viernes | 23:59 |
| Defensa oral | Sábado | [A coordinar] |

---

## Formato de Entrega

1. **Repositorio Git** (recomendado) o archivo ZIP
2. Nombre del archivo: `ApellidoNombre_EvaluacionFuncional.zip`
   - Ejemplo: `AsanzaIsrael_EvaluacionFuncional.zip`
   - Ejemplo: `BeltranJorge_EvaluacionFuncional.zip`
   - Ejemplo: `CuencaAndres_EvaluacionFuncional.zip`
3. Incluir todos los archivos de la estructura especificada
4. Asegurar que el código ejecute sin errores

---

## Ejemplo de Datos para Pruebas

```javascript
// JavaScript
const librosEjemplo = [
  { id: 1, titulo: "Functional Programming in JavaScript", autor: "Luis Atencio", categoria: "Programacion", anio: 2016, rating: 4.5, precio: 45.99 },
  { id: 2, titulo: "Scala for the Impatient", autor: "Cay Horstmann", categoria: "Programacion", anio: 2016, rating: 4.3, precio: 39.99 },
  { id: 3, titulo: "Clean Code", autor: "Robert Martin", categoria: "Programacion", anio: 2008, rating: 4.7, precio: 42.99 },
  // ... mas libros
];

const usuariosEjemplo = [
  { id: 1, nombre: "Israel Asanza", email: "iasanza@utpl.edu.ec", categoriasFavoritas: ["Programacion", "Matematicas"] },
  { id: 2, nombre: "Jorge Beltran", email: "jbeltran@utpl.edu.ec", categoriasFavoritas: ["Programacion", "Bases de Datos"] },
  { id: 3, nombre: "Andres Cuenca", email: "acuenca@utpl.edu.ec", categoriasFavoritas: ["Algoritmos", "Programacion"] },
  { id: 4, nombre: "Matthew Flores", email: "mflores@utpl.edu.ec", categoriasFavoritas: ["Programacion", "Arquitectura"] },
  // ... mas usuarios
];

const prestamosEjemplo = [
  { id: 1, libroId: 1, usuarioId: 1, fechaPrestamo: "2024-01-15", fechaDevolucion: "2024-02-01", activo: false },
  { id: 2, libroId: 2, usuarioId: 1, fechaPrestamo: "2024-02-10", fechaDevolucion: null, activo: true },
  // ... mas prestamos
];
```

```scala
// Scala
case class Libro(
  id: Int,
  titulo: String,
  autor: String,
  categoria: String,
  anio: Int,
  rating: Double,
  precio: Double
)

case class Usuario(
  id: Int,
  nombre: String,
  email: String,
  categoriasFavoritas: List[String]
)

// Ejemplos de usuarios
val usuarios = List(
  Usuario(1, "Israel Asanza", "iasanza@utpl.edu.ec", List("Programacion", "Matematicas")),
  Usuario(2, "Jorge Beltran", "jbeltran@utpl.edu.ec", List("Programacion", "Bases de Datos")),
  Usuario(3, "Andres Cuenca", "acuenca@utpl.edu.ec", List("Algoritmos", "Programacion")),
  Usuario(4, "Matthew Flores", "mflores@utpl.edu.ec", List("Programacion", "Arquitectura"))
)

case class Prestamo(
  id: Int,
  libroId: Int,
  usuarioId: Int,
  fechaPrestamo: String,
  fechaDevolucion: Option[String],
  activo: Boolean
)
```

---

## Resumen de Evaluación

| Componente | Descripción | Puntos |
|------------|-------------|--------|
| **ACDB1** | Defensa oral - Contacto con docente | 3.5 |
| **APEB1** | Implementación práctica en JS | 3.5 |
| **AAB1** | Implementación Scala + Reflexión | 3.0 |
| **TOTAL** | | **10.0** |

---

## Consejos para el Éxito

1. **Conoce tu código:** No solo lo que hace, sino **por qué** lo hiciste así
2. **Practica explicar:** Ensaya explicar conceptos como inmutabilidad y funciones puras
3. **Identifica debilidades:** Reconoce qué partes podrían mejorarse
4. **Relaciona conceptos:** Conecta teoría vista en clase con tu implementación
5. **Sé honesto:** Si no entiendes algo o no pudiste implementarlo, es mejor admitirlo que inventar
6. **Prueba tu código:** Asegúrate de que todo funcione antes de entregar

---

¡Éxito en tu evaluación! Recuerda que lo más importante es comprender los conceptos y poder defenderlos con claridad.
