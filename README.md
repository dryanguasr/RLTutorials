# RLTutorials

Tutorial introductorio de Reinforcement Learning con Python, Gymnasium y Jupyter.

El repositorio contiene un cuaderno principal:

- `S4_D16_reinforcement_learning_gymnasium.ipynb`

El objetivo del cuaderno es que el estudiante compare politicas aleatorias,
heuristicas y aprendidas, entendiendo como cambian cuando el ambiente, la
recompensa y el espacio de acciones son distintos.

## Contenido del cuaderno

El cuaderno esta organizado en cuatro bloques:

1. **Ejemplo continuo:** `InvertedPendulum-v5`.
2. **Ejemplo discreto por discretizacion:** `MountainCar-v0`.
3. **Ejercicio continuo de control:** `LunarLander-v3`.
4. **Ejercicio discreto puro:** `FrozenLake-v1`.

En cada bloque se trabaja con la misma estructura:

1. Explicacion del problema.
2. Codigo del ambiente.
3. Recompensa y sliders de sintonizacion.
4. Video de politica aleatoria.
5. Video de politica heuristica.
6. Entrenamiento y video de politica aprendida.
7. Preguntas de reflexion del problema.

Al final hay una comparacion general y reflexiones finales.

## Que se aprende

El cuaderno cubre:

- agente, ambiente, estado, accion, recompensa, politica y episodio;
- diferencia entre espacios continuos, discretizados y discretos;
- politica aleatoria como linea base;
- politicas heuristicas construidas con intuicion de ingenieria;
- politicas aprendidas con CEM y Q-learning;
- recompensas originales frente a recompensas moldeadas;
- historia del entrenamiento con selectores interactivos;
- ecuacion de Bellman e intuicion de valor futuro;
- riesgos de reward shaping y reward hacking;
- conexion conceptual con sim2real y human-in-the-loop.

## Metodos usados

El cuaderno usa dos familias de aprendizaje:

- **CEM (Cross-Entropy Method):** busqueda de parametros guiada por recompensa.
  Se usa en `InvertedPendulum-v5` y `LunarLander-v3`.
- **Q-learning:** aprendizaje de valores con la ecuacion de Bellman.
  Se usa en `MountainCar-v0` y `FrozenLake-v1`.

Los modelos aprendidos pueden entrenarse con:

- **recompensa original:** la funcion de recompensa del ambiente;
- **recompensa moldeada:** una version mas informada, con senales adicionales
  para facilitar el aprendizaje.

Despues de entrenar, el cuaderno evalua la politica aprendida con ambas
metricas para comparar si la recompensa moldeada realmente ayuda.

## Requisitos

Antes de empezar, instala:

- Python 3.11 o 3.12.
- Git.
- Un entorno para notebooks, por ejemplo JupyterLab o VS Code.

En Windows, si `python` no funciona en PowerShell, prueba:

```powershell
py --version
```

Si tampoco funciona, instala Python desde <https://www.python.org/downloads/>
y marca la opcion **Add python.exe to PATH** durante la instalacion.

## Descargar el repositorio

```powershell
git clone https://github.com/dryanguasr/RLTutorials.git
cd RLTutorials
```

## Crear el entorno virtual

### Windows PowerShell

```powershell
python -m venv .venv
& ".\.venv\Scripts\python.exe" -m pip install --upgrade pip setuptools wheel
```

Si tu instalacion usa el lanzador `py`, tambien puedes crear el entorno asi:

```powershell
py -m venv .venv
& ".\.venv\Scripts\python.exe" -m pip install --upgrade pip setuptools wheel
```

### macOS o Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
```

## Instalar dependencias

Instala primero las dependencias principales:

```powershell
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements.txt
```

En macOS o Linux, si ya activaste el entorno:

```bash
python -m pip install --upgrade -r requirements.txt
```

Luego instala el soporte opcional de Box2D para `LunarLander-v3`:

```powershell
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements-box2d.txt
```

En macOS o Linux:

```bash
python -m pip install --upgrade -r requirements-box2d.txt
```

Si Box2D falla, puedes continuar con el resto del cuaderno. Solo la parte de
`LunarLander-v3` podria no ejecutarse.

## Registrar el kernel de Jupyter

Windows PowerShell:

```powershell
& ".\.venv\Scripts\python.exe" -m ipykernel install --user --name rl-tutorial --display-name "Python (RL Tutorial)"
```

macOS o Linux:

```bash
python -m ipykernel install --user --name rl-tutorial --display-name "Python (RL Tutorial)"
```

## Ejecutar el cuaderno

Windows PowerShell:

```powershell
& ".\.venv\Scripts\jupyter-lab.exe"
```

macOS o Linux:

```bash
jupyter lab
```

Luego abre:

```text
S4_D16_reinforcement_learning_gymnasium.ipynb
```

Selecciona el kernel:

```text
Python (RL Tutorial)
```

## Orden recomendado de trabajo

1. Ejecuta las celdas desde arriba hacia abajo.
2. Lee el contexto antes de cada problema.
3. Mira los videos en este orden: aleatoria, heuristica y aprendida.
4. Antes de mover sliders, observa primero el resultado base.
5. Compara entrenamiento con recompensa `original` y `moldeada`.
6. Usa los selectores de historial para ver momentos intermedios del aprendizaje.
7. Si una celda tarda demasiado, interrumpe el kernel y reduce episodios,
   poblacion, iteraciones o pasos maximos.

## Notas sobre rendimiento

El cuaderno esta pensado para que los entrenamientos base sean razonables en una
sesion de clase. Algunas maquinas pueden tardar mas, especialmente en
`LunarLander-v3`.

Para acelerar:

- reduce `episodes` o `episodios`;
- reduce `population` o `poblacion` en CEM;
- reduce `iterations` o `iteraciones`;
- reduce `max_steps` o `pasos`;
- aumenta `frame_skip` en las animaciones.

Las barras de progreso muestran el avance de los entrenamientos interactivos.

## Problemas comunes

### PowerShell bloquea la activacion del entorno

No necesitas activar el entorno si usas el Python directamente:

```powershell
& ".\.venv\Scripts\python.exe" --version
```

Tambien puedes activar permisos solo para la sesion actual:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
& ".\.venv\Scripts\Activate.ps1"
```

### No aparece el kernel en Jupyter

Vuelve a registrarlo:

```powershell
& ".\.venv\Scripts\python.exe" -m ipykernel install --user --name rl-tutorial --display-name "Python (RL Tutorial)"
```

### `InvertedPendulum-v5` no funciona

Este entorno usa MuJoCo. Primero verifica que las dependencias principales se
instalaron correctamente:

```powershell
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements.txt
```

Si el problema continua, reinicia Jupyter y vuelve a seleccionar el kernel
`Python (RL Tutorial)`.

### `LunarLander-v3` no funciona

Instala las dependencias opcionales:

```powershell
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements-box2d.txt
```

Si sigue fallando, continua con los otros entornos. El resto del cuaderno sigue
siendo util para estudiar politicas, recompensas y aprendizaje.

### Los videos tardan o pesan mucho

Los videos se generan dentro del notebook como HTML. Si tu computador va lento:

- reduce `max_steps`;
- aumenta `frame_skip`;
- reinicia el kernel antes de repetir muchas animaciones.

## Archivos importantes

- `S4_D16_reinforcement_learning_gymnasium.ipynb`: cuaderno principal.
- `requirements.txt`: dependencias principales.
- `requirements-box2d.txt`: dependencias opcionales para `LunarLander`.
- `.gitignore`: evita subir `.venv/`, caches y checkpoints.
- `README_SETUP.md`: notas de configuracion local usadas durante la preparacion.

## Licencia

Consulta el archivo `LICENSE`.
