# RLTutorials

Tutorial introductorio de Reinforcement Learning con Python, Gymnasium y Jupyter.

El repositorio contiene un cuaderno principal:

- `S4_D16_reinforcement_learning_gymnasium.ipynb`

En el cuaderno vas a comparar tres tipos de politicas:

1. Politica aleatoria.
2. Politica heuristica.
3. Politica aprendida por un metodo apropiado para el problema.

Los entornos usados son:

- `InvertedPendulum-v5` o `CartPole-v1` como respaldo.
- `MountainCar-v0`.
- `LunarLander-v3`.

## Requisitos

Antes de empezar, instala:

- Python 3.11 o 3.12.
- Git.
- Un editor o entorno para notebooks, por ejemplo JupyterLab o VS Code.

En Windows, si `python` no funciona en PowerShell, prueba:

```powershell
py --version
```

Si tampoco funciona, instala Python desde <https://www.python.org/downloads/> y marca la opcion **Add python.exe to PATH** durante la instalacion.

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

Despues instala el soporte opcional de Box2D para `LunarLander-v3`:

```powershell
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements-box2d.txt
```

En macOS o Linux:

```bash
python -m pip install --upgrade -r requirements-box2d.txt
```

Si Box2D falla, puedes continuar con el resto del cuaderno. Solo la parte de `LunarLander-v3` podria no ejecutarse.

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
2. Lee el contexto antes de cada ejemplo.
3. Compara los videos en este orden: aleatoria, heuristica y aprendida.
4. Ajusta los parametros de los widgets solo despues de entender el resultado base.
5. Si una celda parece tardar demasiado, interrumpe el kernel antes de volver a ejecutarla.

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

### `LunarLander-v3` no funciona

Instala las dependencias opcionales:

```powershell
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements-box2d.txt
```

Si sigue fallando, continua con los otros entornos. El cuaderno esta preparado para avisar cuando `LunarLander` no esta disponible.

### Los videos tardan o pesan mucho

Los videos se generan dentro del notebook como HTML. Si tu computador va lento:

- reduce `max_steps`;
- aumenta `frame_skip`;
- reinicia el kernel antes de repetir muchas animaciones.

## Archivos importantes

- `requirements.txt`: dependencias principales.
- `requirements-box2d.txt`: dependencias opcionales para `LunarLander`.
- `.gitignore`: evita subir `.venv/`, caches y checkpoints.
- `README_SETUP.md`: notas de configuracion local usadas durante la preparacion del entorno.

## Licencia

Consulta el archivo `LICENSE`.
