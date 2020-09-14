# Jetson Intelrealsense Cameras : SIN COMPILACION

Instalar librerias para poder utilizar las Camaras de Realsense de Intel en las placas Jetson. Última versión existente.

Info sacada de aquí: https://github.com/IntelRealSense/librealsense/blob/master/doc/installation_jetson.md


**¡IMPORTANTE!** :Desconectar las camaras INTEL Realsense para al compilar/instalar las librerías.



1. Register the server's public key:  

  ```
  sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE
  ```

2. Add the server to the list of repositories:

  ```
  sudo add-apt-repository "deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic main" -u
  ```
  
3. Install the SDK:

  ```
  sudo apt-get install librealsense2-utils
  sudo apt-get install librealsense2-dev
  ```
  
  
## Desinstalar

  ```
  dpkg -l | grep "realsense" | cut -d " " -f 3 | xargs sudo dpkg --purge
  ```
