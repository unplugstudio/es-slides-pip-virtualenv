# Pip y Virtualenv

**Eduardo Rivas**

<small>ed@unplug.studio | @je92rivas</small>

---

# 📂 Módulos

-

En Python el código existe en módulos (modules). Cada módulo es una unidad de organización que contiene objetos.

Puedes pensarlo como carpetas que organizan el código en unidades más pequeñas.

-

```python
# helpers.py
def say_hello():
    print("Hello world!")
```

```python
# program.py
from .helpers import say_hello

say_hello()
```

*`program.py` importa una función del módulo `helpers.py`*

-

```python
from .helpers import say_hello
```

Nota: el `.` indica que el módulo `helpers` está en el mismo directorio que `program.py`

-

```python
# program.py
from . import helpers

helpers.say_hello()
```

También puedes importar el módulo completo y acceder a un objecto particular usando el .

---

# ✅ Librería standard

-

Además de permitirnos escribir nuestros propios módulos, Python nos ofrece una colección de módulos ya incluidos con la instalación.

Estos módulos son conocidos como la librería standard (standard library).

-

### Módulos en la librería standard

- Servicios de procesamiento de texto
    - `re`: expresiones regulares
    - `unicodedata`: base de datos Unicode
- Tipos de datos
    - `datetime`: manejo de tiempo y fechas
    - `copy`: operaciones de copia llana y profunda
- Números y matemáticas
    - `math`: funciones matemáticas
    - `random`: números pseudo-aleatorios

-

- Acceso a archivos y carpetas
    - `pathlib`: rutas de archivos
    - `tempfile`: generación de archivos temporales
- Compresión de datos
    - `zipfile`: compresión con gzip
    - `tarfile`: compresión con tar
- Formatos de archivos
    - `csv`
    - `json`
    - `xml`

-

```python
import json

from datetime import date

json.dumps(...)

my_date = date(2018, 1, 1)
```

Podemos importar los módulos de la librería standard en nuestros módulos sin especificar su ruta.

-

# 🤔

¿Qué pasa si el módulo que necesitamos no se encuentra en la librería standard?

-

Podemos hacer usos de *paquetes* instalados del *Python Package Index (PyPI)* a través de la herramienta `pip`.

---

# ⏬ pip

-

`pip` nos permite instalar paquetes alojados en el Python Package Index (PyPI).

https://pypi.org/

<small>Existen miles de paquetes para todo tipo de aplicación en PyPI</small>

-

### Instalando paquetes

```
python -m pip install package-name
```

Pip descargará el paquete y lo añadirá al *PATH* de Python, para que nuestros módulos puedan usarlo.

-

```bash
python -m pip install numpy
```

```python
import numpy

my_array = numpy.array([1, 2, 3])
```

-

### Los paquetes tienen versiones

Cada paquete publicado en PyPI tiene una versión asociada, ya que los paquetes cambian con el tiempo recibiendo arreglos o nuevas características. Para ver las versiones de los paquetes instalados:

```
python -m pip list
```

-

```
Package                            Version
---------------------------------- ---------
asn1crypto                         0.24.0
backports.shutil-get-terminal-size 1.0.0
bcrypt                             3.1.4
certifi                            2018.8.13
cffi                               1.11.5
chardet                            3.0.4
configparser                       3.5.0
```

-

Puedes actualizar un paquete a su última versión con:

```
python -m pip install --upgrade package-name
```

También puedes indicar versiones específicas con:

```
python -m pip install "package-name==1.2.3"
```

-

# 💾

### ¿Donde se instalan los paquetes?

Por defecto pip instala los paquetes de manera global, lo que significa que los archivos se copian a la carpeta donde Python están instalado.

<small>Ya que pip modifica carpetas que requieren acceso de administrador, es necesario correrlo con `sudo` para instalaciones globales</small>

-

# 🔢

### Múltiples versiones de un paquete

¿Qué pasa si trabajamos en varios proyectos y cada proyecto necesita su propia versión de un paquete?

¿Tenemos que cambiar la instalación global cada vez que cambiamos de proyecto?

-

# 😱

---

# 📦 Virtualenv

-

`virtualenv` (virtual environment) permite que tengamos múltiples versiones de un paquete instaladas en nuestra computadora.

Lo hace creando un *entorno virtual* donde los paquetes existen sin entrar en conflicto con otros.

-

### No más instalaciones globales

Cada entorno virtual tiene una lista propia de paquetes independientes de la instalación global y otros entornos.

-

### 1. Crea un virtualenv

```
python -m venv my_env
```

Esto creará una carpeta `my_env` en el directorio actual donde se instalarán todos los paquetes. Este es el virutal environment.

-

### ¿Estoy utilizando un virtual environment?

Cuando activas un entorno virtual, el *prompt* de la línea de comandos muestra el nombre del venv en paréntesis.

-

```
user@host:~$
```
<small>virtualenv no activado</small>

```
(my_env)user@host:~$
```
<small>virtualenv "my_env" activado</small>

-

### 2. Activa tu virtualenv

A medida que cambies de proyecto, deberás activar manualmente el entorno en el que quieras trabajar. Esto se hace ejecutando el script `activate` dentro de cada virtual env.

```
# Mac y Linux
source <venv>/bin/activate

# Windows
<venv>\Scripts\activate.bat
```

-

### 3. Instala paquetes

Ahora puedes instalar tantos paquetes como quieras en tu virtualenv y estos no afectarán la instalación global ni otros entornos.

```
python -m pip install ...
python -m pip list
```

-

### 4. Desactiva tu virtualenv

Simplemente ejecuta el comando:

```
deactivate
```

Ahora está de vuelta en la instalación global

---

# 🏁 Resumen

-

- Python está compuesto por módulos
- Los módulos incluidos por defecto componen la librería standard
- Puedes instalar paquetes para añadir módulos de terceros

-

### Mejores prácticas con pip y virtualenv

- Crea un virtualenv para cada proyecto
- Nunca instales paquetes en la instalación global de Python
- Siempre activa el virtualenv adecuado al trabajar en cada proyecto

---

# 🙋🏻‍♂️ ¿Preguntas?
