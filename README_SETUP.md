# Configuracion del RL Tutorial

Este proyecto contiene el notebook `S4_D16_reinforcement_learning_gymnasium.ipynb`.

El entorno local ya fue creado en `.venv` usando Python 3.12.13 y se verifico con:

- `gymnasium` 1.3.0
- `numpy` 2.5.0
- `pandas` 2.3.3
- `matplotlib` 3.11.0
- `ipywidgets` 8.1.8
- `mujoco` para `InvertedPendulum-v5`
- `box2d` para `LunarLander-v3`

Tambien se registro el kernel de Jupyter como `Python (RL Tutorial)`.

## Activar el entorno

PowerShell:

```powershell
& ".\.venv\Scripts\Activate.ps1"
```

Si PowerShell bloquea la activacion por politicas de ejecucion, usa el Python del entorno directamente:

```powershell
& ".\.venv\Scripts\python.exe" --version
```

## Reinstalar o actualizar dependencias

```powershell
& ".\.venv\Scripts\python.exe" -m pip install --upgrade pip setuptools wheel
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements.txt
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements-box2d.txt
```

## Registrar el kernel si hace falta

```powershell
& ".\.venv\Scripts\python.exe" -m ipykernel install --user --name rl-tutorial --display-name "Python (RL Tutorial)"
```

## Abrir JupyterLab

```powershell
& ".\.venv\Scripts\jupyter-lab.exe"
```

Abre `S4_D16_reinforcement_learning_gymnasium.ipynb` y selecciona el kernel `Python (RL Tutorial)`.

## Crear el entorno desde cero

Si borras `.venv`, puedes reconstruirlo con:

```powershell
& "C:\Users\User\.cache\codex-runtimes\codex-primary-runtime\dependencies\python\python.exe" -m venv .venv
& ".\.venv\Scripts\python.exe" -m pip install --upgrade pip setuptools wheel
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements.txt
& ".\.venv\Scripts\python.exe" -m pip install --upgrade -r requirements-box2d.txt
& ".\.venv\Scripts\python.exe" -m ipykernel install --user --name rl-tutorial --display-name "Python (RL Tutorial)"
```
