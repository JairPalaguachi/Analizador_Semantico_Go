# Analizadores Semántico
## Compilador para Go - Analizadores Léxico, Sintáctico y Semántico

Implementación completa de un compilador educativo para el lenguaje de programación Go, desarrollado en Python utilizando PLY (Python Lex-Yacc). Este proyecto cubre las tres fases fundamentales del análisis de código fuente.

## Autores

- **Jair Palaguachi** ([@JairPalaguachi](https://github.com/JairPalaguachi))
- **Javier Gutiérrez** ([@SKEIILATT](https://github.com/SKEIILATT))

## Descripción General

Este proyecto implementa un compilador completo en tres fases para Go:

1. **Analizador Léxico**: Identifica y clasifica tokens del código fuente
2. **Analizador Sintáctico**: Valida la estructura gramatical del código
3. **Analizador Semántico** : Verifica la coherencia lógica y tipos de datos



**Archivo**: `semantico_go.py`

Verifica la coherencia lógica del código más allá de la sintaxis:
- Variables declaradas antes de uso
- Compatibilidad de tipos en asignaciones y operaciones
- Inmutabilidad de constantes
- Alcance de variables (scope)
- Tipos de retorno en funciones
- Condiciones booleanas en estructuras de control
- Uso correcto de break/continue

**Reglas Implementadas** (12 reglas semánticas):

**Jair Palaguachi** - Identificadores, Asignación, Funciones y Estructuras:
1. ✅ Validación de declaración previa
2. ✅ Validación de alcance de variables
3. ✅ Verificación de tipos en asignación
4. ✅ Inmutabilidad de constantes
5. ✅ Tipo de retorno correcto en funciones
6. ✅ Múltiples retornos respetando orden y tipo

**Javier Gutiérrez** - Operaciones, Conversión, Funciones y Estructuras:
1. ✅ Homogeneidad de tipos en operaciones aritméticas
2. ✅ Concatenación solo con strings
3. ✅ Tipos convertibles en conversiones
4. ✅ Advertencia de truncamiento en conversiones
5. ✅ Condiciones booleanas en if/for
6. ✅ Break y continue solo en bucles/switch



**Uso**:
```bash
python semantico_go.py algoritmo3.go
```

**Salida**: Errores semánticos y tabla de símbolos

---

## Instalación Rápida

```bash
# Instalar dependencias
pip install ply

# Clonar el repositorio
git clone <url-del-repositorio>
cd Analizador_Sintactico_Go

# Verificar instalación
python semantico_go.py algoritmo1.go
```

## Uso Completo

### Análisis Paso a Paso

```bash
# 1. Análisis Léxico
python lexico_go.py mi_codigo.go

# 2. Análisis Sintáctico
python sintactico_go.py mi_codigo.go

# 3. Análisis Semántico
python semantico_go.py mi_codigo.go
```



## Ejemplos de Detección de Errores

### ❌ Error Semántico: Variable No Declarada

```go
// Código incorrecto
fmt.Println(contador)  // Error: contador no declarado
contador := 0
```

**Salida del analizador**:
```
Error semántico en línea 10: Variable 'contador' utilizada sin declaración previa
```

### ❌ Error Semántico: Incompatibilidad de Tipos

```go
// Código incorrecto
var edad int
edad = 25.5  // Error: float64 no compatible con int
```

**Salida del analizador**:
```
Error semántico en línea 18: Incompatibilidad de tipos: no se puede asignar 'float64' a 'int'
```

### ❌ Error Semántico: Modificar Constante

```go
// Código incorrecto
const PI = 3.14159
PI = 3.14  // Error: constante inmutable
```

**Salida del analizador**:
```
Error semántico en línea 22: No se puede asignar valor a constante 'PI'
```

### ✅ Código Correcto

```go
package main

import "fmt"

func main() {
    // Declaración correcta
    var edad int = 25
    const PI = 3.14159
    
    // Uso válido
    fmt.Println(edad)
    fmt.Println(PI)
    
    // Asignación válida
    edad = 30  // OK: mismo tipo
}
```

**Salida del analizador**:
```
✓ Programa analizado correctamente
✓ No se encontraron errores semánticos
```

## Estructura del Proyecto

```
Analizador_Sintactico_Go/
│
├── 📄 FASE 1: LÉXICO
│   └── lexico_go.py                  # Analizador léxico
│
├── 📄 FASE 2: SINTÁCTICO
│   └── sintactico_go.py              # Analizador sintáctico
│
├── 📄 FASE 3: SEMÁNTICO 
│   └── semantico_go.py               # Analizador semántico
│
├── 🧪 PRUEBAS
│   ├── algoritmo1.go                 # Variables y operadores
│   ├── algoritmo2.go                 # Estructuras de control
│   ├── algoritmo3.go                 # Estructuras de datos
│
├── 📊 LOGS
│   ├── logs/lexico-*.txt            # Logs léxicos
│   ├── logs/sintactico-*.txt        # Logs sintácticos
│   └── logs/semantico-*.txt         # Logs semánticos
│
├── 📖 DOCUMENTACIÓN
│   ── README.md                     # Este archivo
│
└── 🔧 AUXILIARES
    ├── parser.out                    # Tabla de parsing
    ├── parsetab.py                   # Cache del parser
    └── __pycache__/
```

## Formato de Logs

Cada fase genera logs con formato estandarizado:

```
{fase}-{usuario}-{archivo}-{fecha}-{hora}.txt

Ejemplos:
- lexico-JairPalaguachi-algoritmo1-15112025-19h46.txt
- sintactico-leodamac-algoritmo2-15112025-19h42.txt
- semantico-JairPalaguachi-algoritmo3-17112025-20h30.txt
```

## Tecnologías Utilizadas

- **Python 3.7+**: Lenguaje de implementación
- **PLY 3.11**: Framework Lex-Yacc para Python
- **Git**: Control de versiones
- **GitHub**: Repositorio y colaboración


## Soporte y Contacto

- **Repositorio**: [GitHub - Analizador_Sintactico_Go](https://github.com/usuario/Analizador_Sintactico_Go)
- **Issues**: Reporta problemas en la sección de Issues del repositorio
- **Documentación**: Consulta los archivos MD en el proyecto

## Referencias

- [The Go Programming Language Specification](https://go.dev/ref/spec)
- [Go by Example](https://gobyexample.com)
- [PLY Documentation](https://www.dabeaz.com/ply/)
- Donovan, A. A. A., & Kernighan, B. W. - The Go Programming Language

## Licencia

Este proyecto es con fines educativos para el curso de Lenguajes de Programación.

---

**Curso**: Lenguajes de Programación  
**Profesora**: Fanny Cisneros Carlota  
**Institución**: ESPOL  
**Período**: 2025-II


---
