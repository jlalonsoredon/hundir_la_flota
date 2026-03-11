# 🎮 Hundir la Flota

Un juego interactivo de **Hundir la Flota** (Battleship) implementado en Python, donde puedes jugar contra la máquina con opción de colocación manual o automática de barcos.

## 📋 Características

- ✅ Juego completo de Hundir la Flota
- ✅ Dos modos de colocación de barcos:
  - **Automático**: Los barcos se colocan de forma aleatoria
  - **Manual**: El jugador ingresa las coordenadas de cada barco
- ✅ Interfaz clara en consola con emojis
- ✅ IA para los disparos de la máquina
- ✅ Validación de coordenadas y movimientos
- ✅ Tableros ocultos del enemigo (solo se muestran impactos y agua)
- ✅ Turnos alternados entre jugador y máquina

## 🎯 Barcos del Juego

| Barco | Tamaño | Cantidad |
|-------|--------|----------|
| 🚤 Lancha | 1 casilla | 1 |
| 🛥️ Patrullera | 2 casillas | 2 |
| 🚢 Crucero | 3 casillas | 3 |
| ⛴️ Acorazado | 4 casillas | 4 |

## 🕹️ Símbolos del Juego

- 🟡 Agua sin disparar
- 🌊 Agua (disparo fallido)
- 💥 Impacto (barco tocado)

## 📦 Requisitos

- Python 3.7+
- NumPy
- Sistema operativo: Windows, macOS o Linux

## 🚀 Instalación

1. **Clonar o descargar el proyecto:**
```bash
cd 1-RampUp/9-Hundir\ la\ flota/proyecto
```

2. **Instalar dependencias:**
```bash
pip install numpy
```

## 🎮 Cómo Jugar

1. **Ejecutar el juego:**
```bash
python main.py
```

2. **Elegir modo de colocación:**
   - **Opción 1**: Colocación automática
   - **Opción 2**: Colocación manual (ingresarás las coordenadas)

3. **Durante el juego:**
   - El tablero izquierdo es **tu tablero** (tus barcos y defensa)
   - El tablero derecho es **tablero de disparos** (enemigo)
   - Ingresa coordenadas en formato: `A5`, `B10`, `J1`, etc.
   - Las letras (A-J) representan filas
   - Los números (1-10) representan columnas

4. **Objetivo:**
   - ¡Hundir todos los barcos del enemigo antes de que hundan los tuyos!

## 📂 Estructura del Proyecto

```
proyecto/
├── main.py                 # Punto de entrada del juego
├── README.md              # Este archivo
├── requirements.txt       # Dependencias del proyecto
├── src/
│   ├── __init__.py
│   ├── board/            # Módulo de tableros
│   │   ├── __init__.py
│   │   ├── board.py      # Clase Board (tablero)
│   │   └── cell.py       # Clase Cell (celda)
│   ├── game/             # Módulo de lógica del juego
│   │   ├── __init__.py
│   │   ├── game.py       # Mecánica principal del juego
│   │   ├── ship.py       # Clase Ship (barco)
│   │   └── turn.py       # Funciones de turno y validación
│   ├── players/          # Módulo de jugadores
│   │   ├── __init__.py
│   │   ├── player.py     # Clase Player (jugador)
│   │   └── ai_player.py  # Clase AIPlayer (máquina)
│   └── utils/            # Utilidades y constantes
│       ├── __init__.py
│       ├── constants.py  # Constantes (gráficos, barcos, etc.)
│       └── helpers.py    # Funciones auxiliares
└── tests/                # Pruebas (si las hay)
```

## 🔧 Clases Principales

### `Board`
Gestiona el tablero del juego. Métodos principales:
- `_crear_tablero()`: Crea una matriz 11x11 con encabezados
- `put_ships()`: Coloca barcos automáticamente
- `put_ships_manual()`: Coloca barcos manualmente
- `put_ships_pc()`: Coloca barcos de la máquina
- `mostrar_dos_tableros()`: Muestra ambos tableros en la consola
- `disparar()`: Realiza un disparo
- `have_ships()`: Verifica si quedan barcos
- `get_ship_count()`: Devuelve cantidad de barcos restantes

### `Ship`
Representa un barco. Métodos principales:
- `__init__(name, size, table)`: Inicializa el barco
- `place()`: Coloca manualmente el barco
- `generate_random_position()`: Genera una posición aleatoria válida
- `ship_orientation()`: Pregunta la orientación (H/V)
- `validar_coordenadas()`: Valida formato de coordenadas

### `Turn`
Funciones para gestionar los turnos:
- `obtener_coordenadas_usuario()`: Obtiene input del usuario
- `disparar_a_maquina()`: Genera disparo aleatorio de la máquina
- `validar_coordenadas()`: Valida coordenadas
- `comprobar_acierto()`: Verifica si fue acierto o fallo

## 🎮 Ejemplo de Uso

```
¿Cómo deseas colocar tus barcos?
1. Automáticamente (aleatorio)
2. Manualmente (ingresa las coordenadas)

Selecciona 1 o 2: 1
```

Una vez que el juego comienza:

```
   TU TABLERO                                TABLERO DISPAROS
   1   2   3   4   5   6   7   8   9  10     1   2   3   4   5   6   7   8   9  10
A 🟡  🟡 🚤 🚤  🟡  🟡  🟡  🟡  🟡  🟡     A 🟡  🟡  🟡  🟡  🟡  🟡  🟡  🟡  🟡  🟡
...

Turno del jugador: Dispara a coordenadas del enemigo
Introduce las coordenada (ej: A5): A1
```

## 💡 Características Técnicas

- **Orientación de barcos**: Horizontal (H) o Vertical (V)
- **Validación de coordenadas**: Formato A-J y 1-10
- **Prevención de sobreposición**: Los barcos no pueden superponerse
- **Límites del tablero**: Se validan los rangos válidos
- **Historial de disparos**: Se evita disparar en la misma posición dos veces

## 🐛 Solución de Problemas

**Problema**: `ModuleNotFoundError: No module named 'numpy'`
- Solución: Instala NumPy con `pip install numpy`

**Problema**: Barcos saliendo del tablero
- Véase que al colocar manualmente, ingresa coordenadas válidas

**Problema**: Entrada inválida rechazada
- Usa formato correcto: `A5`, `J10`, etc. (letra mayúscula + número)

## 📝 Notas de Desarrollo

- El proyecto usa **NumPy** para las matrices de tableros
- Los tableros incluyen encabezados (fila 0 y columna 0) con coordenadas
- La lógica diferencia entre índices de matriz (0-10) e índices de juego (1-10)
- Se emplean **emojis** para mejor visualización en consola

## 👨‍💻 Autor

Creado como práctica de programación en Python (POO, manejo de archivos, lógica de juegos).

## 📄 Licencia

Libre para uso educativo.

---

¡Disfruta del juego! 🎮⚓
