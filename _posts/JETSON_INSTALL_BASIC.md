# Jetson installation : BASICS

Proceso para dejar la Jetson (cualquier modelo) funcionando correctamente:



1. Descargar SDK manager de la última versión en release (a fecha de  Junio 2020 es la 4.3) en tu ordenadro personal

   ```bash
   https://developer.nvidia.com/jetpack-43-archive
   ```

   

2. Instalar OS (flashear) en Jetson mediante SDK manager conectando mediante cable la placa Jetson (iniciando la Jetson en modo recovery). Si falla la instalación de componentes extras no pasa nada, mientras se instale el OS ya está.

3. **¡Importante!**: Por defecto la Jetson viene sin los paquetes de instalación de Canonical y de Source code habilitados, se deben habilitar para poder instalar cualquier paquete externo:

   ```bash
   # 1) Abrir Software & Updates
   # 2) En pestaña "Ubuntu Software", marcar todas las opciones. Download from "Main Server"
   # 3) En pestaña "Other Software", Marcar las dos primeras opciones de Canonical (aparte de lo demás que tengas marcado)
   # 4) En pestaña "Updates", seleccionar "Automatically check for updates" -> Never
   ```

   

4. Si ha fallado la instalación de los componentes extras (CUDA, OpenCV, etc), instalar lo siguiente:

   ```bash
   sudo apt update
   ```

   ```bash
   sudo apt-get install nvidia-jetpack
   ```

5. Instalar **PIP** para poder instalar paquetes python facilmente en local (independientemente que luego se cree un entorno virtual):

   ```bash
   sudo apt-get install python-pip
   ```
   

6. Instalar **jtop** para tener control y monitorizar el estado de la jetson

   ```bash
   sudo -H pip install -U jetson-stats
   ```

   Utilizar jtop. Desde terminal lanzar:

   ```bash
   sudo jtop
   ```
   

7. CPU & GPU 

   En el caso de la Jetson TX2 existen 5 modos de funcionamiento difeferentes:

   | Mode | Mode Name      | Denver 2 | Frequency | ARM A57 | Frequency | GPU Frequency |
   | ---- | -------------- | -------- | --------- | ------- | --------- | ------------- |
   | 0    | Max-N          | 2        | 2.0 GHz   | 4       | 2.0 GHz   | 1.30 Ghz      |
   | 1    | Max-Q          | 0        |           | 4       | 1.2 Ghz   | 0.85 Ghz      |
   | 2    | Max-P Core-All | 2        | 1.4 GHz   | 4       | 1.4 GHz   | 1.12 Ghz      |
   | 3    | Max-P ARM      | 0        |           | 4       | 2.0 GHz   | 1.12 Ghz      |
   | 4    | Max-P Denver   | 1        | 2.0 GHz   | 1       | 2.0 GHz   | 1.12 Ghz      |

   Para seleccionar un modo de trabajo lanzar en terminal lo siguiente:

   ```bash
   sudo nvpmodel -m [mode]
   ```

   Dónde [mode] es el número del modo a utiliar. En nuestro caso, necesitamos el máximo de potencia, por eso marcaremos lo siguiente:

   ```bash
   sudo nvpmodel -m 0
   ```

   Check mode:

   ```bash
   sudo nvpmodel -q 
   ```

   
