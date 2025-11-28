# Evaluación de Programación Reactiva y Funcional

## Información General

- **Fecha de entrega del código:** Viernes hasta las 23:59
- **Fecha de defensa oral:** Sábado 07:00 AM
- **Enlace Zoom:** https://utpl.zoom.us/j/84861000609
- **Duración de la defensa:** 15-20 minutos por estudiante
- **Modalidad:** Virtual (Zoom)
- **Puntaje total:** 10 puntos

### Distribución de Calificaciones

| Componente | Descripción | Puntos |
|------------|-------------|--------|
| **[APEB1]** | Fundamentos - Aprendizaje Práctico Experimental | 3.5 |
| **[AAB1]** | Aplicación Avanzada - Aprendizaje Autónomo | 3.0 |
| **[ACDB1]** | Defensa Oral - Contacto con Docente | 3.5 |
| **TOTAL** | | **10.0** |

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

## FASE 1: [APEB1] Fundamentos (3.5 puntos)

**Objetivo:** Dominar los conceptos básicos de programación funcional aplicados en JavaScript y Scala.

Esta fase evalúa tu capacidad de implementar código funcional básico y comprender las diferencias entre paradigmas.

---

### Ejercicio 1.1: Paradigmas de Programación - JavaScript (0.8 puntos)

**Concepto evaluado:** Diferencias entre programación imperativa y declarativa

**Requisito:** Implementa la siguiente funcionalidad en **AMBOS paradigmas**:

Filtrar libros disponibles (no prestados) de una categoría específica y ordenarlos por año de publicación.

```javascript
const libros = [
  { id: 1, titulo: "Clean Code", categoria: "Programacion", anio: 2008, prestado: false },
  { id: 2, titulo: "Design Patterns", categoria: "Programacion", anio: 1994, prestado: true },
  { id: 3, titulo: "Refactoring", categoria: "Programacion", anio: 1999, prestado: false },
  { id: 4, titulo: "Calculus", categoria: "Matematicas", anio: 2010, prestado: false }
];

// Implementación 1: Paradigma IMPERATIVO (0.4 puntos)
function filtrarLibrosImperativo(libros, categoria) {
  // Tu implementacion usando for/while, mutación de variables
}

// Implementación 2: Paradigma DECLARATIVO (0.4 puntos)
function filtrarLibrosDeclarativo(libros, categoria) {
  // Tu implementacion usando filter, sort (métodos funcionales)
}
```

**Criterios de evaluación:**
- Correcta implementación imperativa con loops y mutación (0.4 pts)
- Correcta implementación declarativa sin mutación (0.4 pts)

**Archivo:** `javascript/1.1-paradigmas.js`

---

### Ejercicio 1.2: Inmutabilidad - Scala (0.7 puntos)

**Concepto evaluado:** Datos inmutables y transformación sin mutación

**Requisito:** Implementa una función que actualice el estado de un préstamo **sin mutar** los datos originales.

```scala
case class Prestamo(
  id: Int,
  usuarioId: Int,
  libroId: Int,
  activo: Boolean,
  fechaPrestamo: String
)

/**
 * Devuelve un libro (marca el préstamo como inactivo)
 * SIN mutar la lista original de préstamos
 */
def devolverLibro(prestamos: List[Prestamo], prestamoId: Int): List[Prestamo] = {
  // Tu implementacion
  // Pista: usa map para crear una nueva lista transformada
}

// Ejemplo de uso:
val prestamos = List(
  Prestamo(1, 101, 201, true, "2024-01-15"),
  Prestamo(2, 102, 202, true, "2024-01-20")
)

val prestamosActualizados = devolverLibro(prestamos, 1)
// prestamos NO debe cambiar (inmutabilidad)
// prestamosActualizados debe tener el préstamo 1 con activo = false
```

**Criterios de evaluación:**
- Implementación correcta sin mutación (0.5 pts)
- Uso apropiado de operaciones inmutables de Scala (0.2 pts)

**Archivo:** `scala/1.2-inmutabilidad.scala`

---

### Ejercicio 1.3: Funciones Puras - JavaScript (0.8 puntos)

**Concepto evaluado:** Características de funciones puras (sin efectos secundarios, determinísticas)

**Requisito:** Implementa las siguientes funciones **PURAS**:

```javascript
/**
 * Calcula días de retraso de un préstamo
 * Función PURA: mismo input = mismo output, sin efectos secundarios
 */
function calcularDiasRetraso(fechaPrestamo, fechaDevolucion, diasPermitidos) {
  // Tu implementacion (0.4 puntos)
  // NO uses Date.now() ni console.log ni variables externas
  // Solo calcula con los parámetros recibidos
}

/**
 * Calcula multa por días de retraso
 * Regla: $0.50 por día de retraso
 */
function calcularMulta(diasRetraso) {
  // Tu implementacion (0.4 puntos)
  // Debe ser determinística: siempre el mismo resultado para el mismo input
}

// Ejemplos de prueba:
console.log(calcularDiasRetraso("2024-01-01", "2024-01-20", 14)); // 6 días
console.log(calcularMulta(6)); // $3.00
```

**En comentarios, explica:**
- ¿Por qué estas funciones son puras?
- ¿Qué pasaría si usaras `Date.now()` dentro?
- Ventaja de funciones puras para testing

**Archivo:** `javascript/1.3-funciones-puras.js`

---

### Ejercicio 1.4: Funciones vs Métodos - Scala (0.6 puntos)

**Concepto evaluado:** Diferencias entre funciones y métodos en programación funcional

**Requisito:** Implementa la misma funcionalidad de **DOS formas diferentes**:

```scala
case class Libro(id: Int, titulo: String, autor: String, categoria: String)

// FORMA 1: Como método de una clase (0.3 puntos)
class Biblioteca(libros: List[Libro]) {
  def buscarPorAutor(autor: String): List[Libro] = {
    // Tu implementacion
  }
}

// FORMA 2: Como función pura (0.3 puntos)
object FuncionesBiblioteca {
  def buscarPorAutor(libros: List[Libro], autor: String): List[Libro] = {
    // Tu implementacion
  }
}

// Ejemplos de uso:
val libros = List(
  Libro(1, "Clean Code", "Robert Martin", "Programacion"),
  Libro(2, "Refactoring", "Martin Fowler", "Programacion")
)

// Uso con método:
val biblioteca = new Biblioteca(libros)
val resultado1 = biblioteca.buscarPorAutor("Robert Martin")

// Uso con función:
val resultado2 = FuncionesBiblioteca.buscarPorAutor(libros, "Robert Martin")
```

**En comentarios, explica:**
- ¿Cuál es la diferencia conceptual?
- ¿Cuándo usar métodos vs funciones puras?
- ¿Cuál facilita más el testing y por qué?

**Archivo:** `scala/1.4-funciones-vs-metodos.scala`

---

### Ejercicio 1.5: Operaciones con Listas - JavaScript (0.6 puntos)

**Concepto evaluado:** Uso básico de operaciones funcionales sobre colecciones

**Requisito:** Implementa usando **métodos de arrays** (NO loops):

```javascript
/**
 * Genera un reporte completo de la biblioteca
 * Usa SOLO: map, filter, reduce, sort, etc.
 */
function generarReporteCompleto(libros, prestamos, usuarios) {
  return {
    // Total de libros por categoria (0.15 puntos)
    librosPorCategoria: /* implementar con reduce */,

    // Top 5 usuarios más activos (0.15 puntos)
    usuariosMasActivos: /* implementar con sort y slice */,

    // Libros más prestados (0.15 puntos)
    librosMasPrestados: /* implementar con reduce y sort */,

    // Tasa de préstamos activos (0.15 puntos)
    tasaPrestamosActivos: /* calcular porcentaje */
  };
}
```

**Archivo:** `javascript/1.5-operaciones-listas.js`

---

**Total FASE 1 (APEB1): 3.5 puntos**

```
Ejercicio 1.1: 0.8 pts (Paradigmas JS)
Ejercicio 1.2: 0.7 pts (Inmutabilidad Scala)
Ejercicio 1.3: 0.8 pts (Funciones Puras JS)
Ejercicio 1.4: 0.6 pts (Funciones vs Métodos Scala)
Ejercicio 1.5: 0.6 pts (Operaciones Listas JS)
-------------------
TOTAL:        3.5 pts
```

---

## FASE 2: [AAB1] Aplicación Avanzada (3.0 puntos)

**Objetivo:** Aplicar conceptos avanzados de programación funcional en problemas complejos.

Esta fase evalúa tu capacidad de investigación autónoma y aplicación de técnicas avanzadas.

---

### Ejercicio 2.1: Funciones de Orden Superior - JavaScript (0.8 puntos)

**Concepto evaluado:** Funciones que reciben o retornan otras funciones

**Requisito A: Closure - Función que retorna función (0.4 puntos)**

```javascript
/**
 * Crea un filtrador personalizado usando closures
 * Retorna una función que puede usarse con Array.filter()
 */
function crearFiltrador(criterio) {
  // Tu implementacion
  // Debe retornar una función que filtre según el criterio

  return function(libro) {
    // Lógica de filtrado
  };
}

// Ejemplo de uso:
const libros = [ /* datos */ ];
const filtrarProgramacion = crearFiltrador({ categoria: "Programacion" });
const librosProgramacion = libros.filter(filtrarProgramacion);

const filtrarRecientes = crearFiltrador({ anio: 2020, operador: "mayor" });
const librosRecientes = libros.filter(filtrarRecientes);
```

**Requisito B: Función como parámetro (0.4 puntos)**

```javascript
/**
 * Procesa préstamos aplicando una estrategia (función) a cada uno
 */
function procesarPrestamos(prestamos, estrategia) {
  // Tu implementacion
  // estrategia es una función que define cómo procesar cada préstamo
}

// Ejemplos de uso:
const calcularMultas = (prestamo) => { /* lógica */ };
const enviarRecordatorios = (prestamo) => { /* lógica */ };

procesarPrestamos(prestamos, calcularMultas);
procesarPrestamos(prestamos, enviarRecordatorios);
```

**Archivo:** `javascript/2.1-orden-superior.js`

---

### Ejercicio 2.2: Composición de Funciones - Scala (0.7 puntos)

**Concepto evaluado:** Composición y encadenamiento de transformaciones

**Requisito:** Implementa transformaciones componibles:

```scala
case class Libro(
  id: Int,
  titulo: String,
  precio: Double,
  descuento: Double = 0,
  impuesto: Double = 0
)

// Define funciones de transformación (0.3 puntos)
val aplicarDescuento: Libro => Libro = libro => {
  // Aplica 15% de descuento
}

val aplicarImpuesto: Libro => Libro = libro => {
  // Aplica 12% de IVA sobre precio con descuento
}

val redondearPrecio: Libro => Libro = libro => {
  // Redondea precio final a 2 decimales
}

// Usa composición de funciones (0.4 puntos)
val procesarPrecioFinal = aplicarDescuento andThen aplicarImpuesto andThen redondearPrecio

// Aplica a lista de libros
val libros = List(
  Libro(1, "Clean Code", 45.99),
  Libro(2, "Refactoring", 39.99)
)

val librosConPrecioFinal = libros.map(procesarPrecioFinal)
```

**En comentarios, explica:**
- ¿Qué ventaja tiene la composición vs un solo método grande?
- ¿Cómo facilita el testing?

**Archivo:** `scala/2.2-composicion.scala`

---

### Ejercicio 2.3: Map, Filter, Reduce Avanzado - JavaScript (1.0 puntos)

**Concepto evaluado:** Uso avanzado de operaciones funcionales en problema complejo

**Requisito:** Sistema de recomendación de libros usando **SOLO** map, filter, reduce:

```javascript
/**
 * Sistema de recomendación de libros
 *
 * Algoritmo:
 * 1. Filtrar libros de categorías que el usuario ha leído (0.3 pts)
 * 2. Calcular score de recomendación para cada libro (0.4 pts):
 *    - Popularidad: +1 punto por cada 10 préstamos
 *    - Recencia: libros 2020+ tienen +2 puntos
 *    - Rating: rating * 10 puntos
 * 3. Reducir a top 10 libros con mayor score (0.3 pts)
 */
function recomendarLibros(libros, usuario, historialPrestamos) {
  // PASO 1: Filtrar por categorías favoritas del usuario
  const librosRelevantes = /* usa filter */;

  // PASO 2: Agregar score a cada libro
  const librosConScore = /* usa map */;

  // PASO 3: Obtener top 10
  const top10 = /* usa reduce o sort + slice */;

  return top10;
}

// Ejemplo de datos:
const usuario = {
  id: 1,
  categoriasFavoritas: ["Programacion", "Matematicas"]
};

const historialPrestamos = [
  { libroId: 1, cantidad: 45 },
  { libroId: 2, cantidad: 23 }
];
```

**Restricciones:**
- NO usar loops (for, while)
- NO mutar arrays/objetos
- SOLO usar map, filter, reduce, sort

**Archivo:** `javascript/2.3-recomendaciones.js`

---

### Ejercicio 2.4: Tuplas y Análisis Funcional - Scala (0.5 puntos)

**Concepto evaluado:** Uso de tuplas y operaciones funcionales en Scala

**Requisito:** Función que retorna estadísticas usando tuplas:

```scala
case class Prestamo(
  id: Int,
  libroId: Int,
  usuarioId: Int,
  fechaPrestamo: String,
  activo: Boolean
)

/**
 * Retorna estadísticas de un usuario usando tuplas
 * Tupla: (totalPrestamos, prestamosActivos, promedioLibrosPorMes)
 */
def obtenerEstadisticasUsuario(
  prestamos: List[Prestamo],
  usuarioId: Int
): (Int, Int, Double) = {
  // Tu implementacion usando operaciones funcionales
  // Usa filter, map, foldLeft/reduce según necesites
}

// Ejemplo:
val prestamos = List(
  Prestamo(1, 101, 1, "2024-01-15", false),
  Prestamo(2, 102, 1, "2024-02-10", true),
  Prestamo(3, 103, 1, "2024-03-05", true)
)

val (total, activos, promedio) = obtenerEstadisticasUsuario(prestamos, 1)
println(s"Total: $total, Activos: $activos, Promedio: $promedio")
```

**Archivo:** `scala/2.4-tuplas-analisis.scala`

---

**Total FASE 2 (AAB1): 3.0 puntos**

```
Ejercicio 2.1: 0.8 pts (Orden Superior JS)
Ejercicio 2.2: 0.7 pts (Composición Scala)
Ejercicio 2.3: 1.0 pts (Map/Filter/Reduce Avanzado JS)
Ejercicio 2.4: 0.5 pts (Tuplas Scala)
-------------------
TOTAL:        3.0 pts
```

---

## FASE 3: [ACDB1] Defensa Oral (3.5 puntos)

**Objetivo:** Demostrar dominio conceptual y capacidad de explicar decisiones técnicas.

**Formato:** Presentación virtual por Zoom el día sábado (15-20 minutos)

**Información de la sesión:**
- 📅 **Fecha:** Sábado 07:00 AM
- 🔗 **Enlace Zoom:** https://utpl.zoom.us/j/84861000609
- ⏱️ **Duración:** 15-20 minutos por estudiante

Durante la defensa oral deberás:
1. Compartir tu pantalla mostrando el código de las Fases 1 y 2
2. Explicar y ejecutar tu código
3. Justificar decisiones de diseño
4. Responder preguntas sobre conceptos
5. Proponer mejoras o alternativas

---

### Rúbrica de Evaluación - Defensa Oral

| Criterio | Excelente (100%) | Bueno (75%) | Regular (50%) | Deficiente (0%) | Peso |
|----------|------------------|-------------|---------------|-----------------|------|
| **Comprensión de Paradigmas** | Explica claramente diferencias entre imperativo y declarativo con ejemplos de su código | Identifica diferencias básicas pero superficiales | Confunde conceptos o no ejemplifica bien | No comprende las diferencias | 0.9 pts |
| **Funciones Puras e Inmutabilidad** | Explica por qué sus funciones son puras, ventajas de inmutabilidad, ejemplos de testing | Comprende concepto pero no profundiza | Explicación superficial o con errores | No puede explicar su implementación | 0.9 pts |
| **Funciones de Orden Superior** | Explica fluidamente closures, callbacks, ventajas y cuándo usarlos | Explica funcionamiento básico sin profundizar | Explica con dificultad o confunde conceptos | No puede explicar | 0.7 pts |
| **Map, Filter, Reduce** | Explica cuándo usar cada uno, ventajas sobre loops, defiende decisiones de diseño | Explica uso básico sin justificar diseño | Conoce sintaxis pero no propósito | No comprende las operaciones | 0.7 pts |
| **Capacidad de Análisis** | Propone mejoras y alternativas superiores, refactoriza mentalmente | Comprende sugerencias con dificultad para mejorar | No puede mejorar su código | No comprende sugerencias | 0.3 pts |

**Total FASE 3 (ACDB1): 3.5 puntos**

---

### Preguntas Tipo para la Defensa Oral

**Sobre Paradigmas (Ejercicio 1.1):**
- ¿Por qué tu versión declarativa es mejor que la imperativa?
- ¿Qué problemas tiene la mutación en programas grandes?
- Muéstrame dónde está la mutación en tu código imperativo

**Sobre Inmutabilidad (Ejercicio 1.2):**
- ¿Cómo garantizas que no estás mutando la lista original?
- ¿Qué pasa en memoria cuando creas una nueva lista?
- ¿Es esto eficiente? ¿Cuándo sí y cuándo no?

**Sobre Funciones Puras (Ejercicio 1.3):**
- ¿Tu función `calcularDiasRetraso` es realmente pura? Demuéstralo
- ¿Qué pasaría si usaras `Date.now()` internamente?
- ¿Cómo testearías esta función?

**Sobre Orden Superior (Ejercicio 2.1):**
- Explica cómo funciona el closure en `crearFiltrador`
- ¿Qué variables "recuerda" la función interna?
- ¿Podrías hacer esto sin closures? ¿Cómo?

**Sobre Composición (Ejercicio 2.2):**
- ¿Por qué usar `andThen` en lugar de llamar las funciones anidadas?
- ¿Cómo cambiarías el orden de las transformaciones?
- ¿Qué ventaja tiene para testing?

**Sobre Map/Filter/Reduce (Ejercicio 2.3):**
- ¿Por qué usaste `reduce` aquí en lugar de `map`?
- ¿Podrías resolver todo con un solo `reduce`?
- ¿Cómo optimizarías esta cadena de operaciones?

**Sobre Scala vs JavaScript:**
- ¿Qué facilita Scala para programación funcional?
- ¿Cuándo preferirías JavaScript sobre Scala?
- ¿Qué aprendiste de cada lenguaje?

---

## Estructura de Entregables

```
evaluacion-reactiva-funcional/
│
├── javascript/
│   ├── 1.1-paradigmas.js
│   ├── 1.3-funciones-puras.js
│   ├── 1.5-operaciones-listas.js
│   ├── 2.1-orden-superior.js
│   └── 2.3-recomendaciones.js
│
├── scala/
│   ├── 1.2-inmutabilidad.scala
│   ├── 1.4-funciones-vs-metodos.scala
│   ├── 2.2-composicion.scala
│   └── 2.4-tuplas-analisis.scala
│
└── README.md (instrucciones de ejecución)
```

### Contenido Mínimo del README.md

```markdown
# Evaluación Programación Funcional - [Tu Nombre Completo]

## Información del Estudiante
- **Nombre:** [Tu nombre]
- **Cédula/ID:** [Tu identificación]
- **Fecha:** [Fecha de entrega]

## Instrucciones de Ejecución

### JavaScript
```bash
# Para ejecutar los archivos JavaScript:
node javascript/1.1-paradigmas.js
node javascript/1.3-funciones-puras.js
# ... etc
```

### Scala
```bash
# Para compilar y ejecutar Scala:
scalac scala/1.2-inmutabilidad.scala
scala Inmutabilidad
# ... etc
```

## Dependencias
- Node.js v18+ (para JavaScript)
- Scala 2.13+ (para Scala)

## Estructura del Proyecto
[Explica brevemente qué contiene cada archivo]

## Notas Adicionales
[Cualquier aclaración sobre tu implementación]
```

---

## Criterios de Penalización

- **Código que no ejecuta:** -2 puntos del ejercicio
- **Uso de mutación donde debe ser inmutable:** -0.5 puntos por ocurrencia
- **Funciones impuras presentadas como puras:** -0.5 puntos por ocurrencia
- **Uso de loops donde se requiere map/filter/reduce:** -1 punto
- **Entrega tardía:** -1 punto por día
- **No presentarse a defensa oral:** 0 puntos en ACDB1 (Fase 3)
- **Plagio o código copiado:** 0 puntos en toda la evaluación

---

## Fechas Importantes

| Actividad | Fecha | Hora |
|-----------|-------|------|
| Publicación de evaluación | 27 de noviembre | - |
| Consultas permitidas | Hasta el viernes | 18:00 |
| **Entrega del código** | **Viernes** | **23:59** |
| **Defensa oral (Zoom)** | **Sábado** | **07:00 AM** |

**Enlace Zoom para defensa oral:** https://utpl.zoom.us/j/84861000609

---

## Formato de Entrega

1. **Repositorio Git** (recomendado) o archivo ZIP
2. **Nombre del archivo:** `ApellidoNombre_EvaluacionFuncional.zip`
   - Ejemplo: `AsanzaIsrael_EvaluacionFuncional.zip`
   - Ejemplo: `BeltranJorge_EvaluacionFuncional.zip`
   - Ejemplo: `CuencaAndres_EvaluacionFuncional.zip`
3. Incluir **todos** los archivos de la estructura especificada
4. Asegurar que el código **ejecute sin errores**
5. Incluir README.md con instrucciones

---

## Ejemplo de Datos para Pruebas

```javascript
// JavaScript - Datos de ejemplo
const librosEjemplo = [
  { id: 1, titulo: "Functional Programming in JavaScript", autor: "Luis Atencio", categoria: "Programacion", anio: 2016, rating: 4.5, precio: 45.99 },
  { id: 2, titulo: "Scala for the Impatient", autor: "Cay Horstmann", categoria: "Programacion", anio: 2016, rating: 4.3, precio: 39.99 },
  { id: 3, titulo: "Clean Code", autor: "Robert Martin", categoria: "Programacion", anio: 2008, rating: 4.7, precio: 42.99 },
  { id: 4, titulo: "Introduction to Algorithms", autor: "Cormen", categoria: "Algoritmos", anio: 2009, rating: 4.6, precio: 89.99 }
];

const usuariosEjemplo = [
  { id: 1, nombre: "Israel Asanza", email: "iasanza@utpl.edu.ec", categoriasFavoritas: ["Programacion", "Matematicas"] },
  { id: 2, nombre: "Jorge Beltran", email: "jbeltran@utpl.edu.ec", categoriasFavoritas: ["Programacion", "Bases de Datos"] },
  { id: 3, nombre: "Andres Cuenca", email: "acuenca@utpl.edu.ec", categoriasFavoritas: ["Algoritmos", "Programacion"] },
  { id: 4, nombre: "Matthew Flores", email: "mflores@utpl.edu.ec", categoriasFavoritas: ["Programacion", "Arquitectura"] }
];

const prestamosEjemplo = [
  { id: 1, libroId: 1, usuarioId: 1, fechaPrestamo: "2024-01-15", fechaDevolucion: "2024-02-01", activo: false },
  { id: 2, libroId: 2, usuarioId: 1, fechaPrestamo: "2024-02-10", fechaDevolucion: null, activo: true },
  { id: 3, libroId: 3, usuarioId: 2, fechaPrestamo: "2024-01-20", fechaDevolucion: "2024-02-15", activo: false },
  { id: 4, libroId: 1, usuarioId: 3, fechaPrestamo: "2024-03-01", fechaDevolucion: null, activo: true }
];
```

```scala
// Scala - Definiciones de datos
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

case class Prestamo(
  id: Int,
  libroId: Int,
  usuarioId: Int,
  fechaPrestamo: String,
  fechaDevolucion: Option[String],
  activo: Boolean
)

// Ejemplos de datos
val libros = List(
  Libro(1, "Functional Programming in JavaScript", "Luis Atencio", "Programacion", 2016, 4.5, 45.99),
  Libro(2, "Scala for the Impatient", "Cay Horstmann", "Programacion", 2016, 4.3, 39.99),
  Libro(3, "Clean Code", "Robert Martin", "Programacion", 2008, 4.7, 42.99)
)

val usuarios = List(
  Usuario(1, "Israel Asanza", "iasanza@utpl.edu.ec", List("Programacion", "Matematicas")),
  Usuario(2, "Jorge Beltran", "jbeltran@utpl.edu.ec", List("Programacion", "Bases de Datos")),
  Usuario(3, "Andres Cuenca", "acuenca@utpl.edu.ec", List("Algoritmos", "Programacion")),
  Usuario(4, "Matthew Flores", "mflores@utpl.edu.ec", List("Programacion", "Arquitectura"))
)

val prestamos = List(
  Prestamo(1, 1, 1, "2024-01-15", Some("2024-02-01"), false),
  Prestamo(2, 2, 1, "2024-02-10", None, true),
  Prestamo(3, 3, 2, "2024-01-20", Some("2024-02-15"), false)
)
```

---

## Resumen de Evaluación por Fase

| Fase | Componente | Ejercicios | Puntos |
|------|------------|------------|--------|
| **FASE 1: Fundamentos** | APEB1 | 1.1 a 1.5 | 3.5 |
| **FASE 2: Aplicación Avanzada** | AAB1 | 2.1 a 2.4 | 3.0 |
| **FASE 3: Defensa Oral** | ACDB1 | Presentación | 3.5 |
| | | **TOTAL** | **10.0** |

---

## Consejos para el Éxito

### Para la Implementación:
1. **Lee todo primero:** Entiende toda la evaluación antes de empezar
2. **Avanza secuencialmente:** Completa Fase 1 antes de pasar a Fase 2
3. **Prueba constantemente:** Ejecuta tu código frecuentemente
4. **Comenta tu código:** Explica decisiones importantes
5. **Evita copiar:** El código copiado se nota en la defensa

### Para la Defensa Oral:
1. **Conoce tu código:** No solo qué hace, sino **por qué** lo hiciste así
2. **Practica explicar:** Ensaya en voz alta los conceptos clave
3. **Prepara ejemplos:** Ten ejemplos listos de tu código
4. **Identifica debilidades:** Reconoce qué mejorarías
5. **Sé honesto:** Es mejor admitir dudas que inventar

### Conceptos Clave a Dominar:
- ✅ Diferencia imperativo vs declarativo
- ✅ Inmutabilidad y sus ventajas
- ✅ Características de funciones puras
- ✅ Closures y funciones de orden superior
- ✅ Composición de funciones
- ✅ Map, filter, reduce y cuándo usar cada uno

---

¡Éxito en tu evaluación! Recuerda: lo más importante es **comprender los conceptos** y poder **defenderlos con claridad**.
