# Jetson Tensorflow 

Instalar lo siguiente para habilitar el uso de trabajar con tensorflow-gpu:

1. Dependencias

   ```bash
   sudo apt-get install python3-pip libhdf5-serial-dev hdf5-tools
   ```

   

2. Libreria para usar GPU

   ```bash
   sudo pip3 install --pre --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v42 tensorflow-gpu
   ```

   