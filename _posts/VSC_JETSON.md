# Visual Studio Code @ JETSON

Para trabajar con Visual Studio Code en la Jetson (cualquier modelo), instalar mediante:

```bash
# Install the rep keys and setup
wget -O script.deb.sh https://packagecloud.io/install/repositories/headmelted/codebuilds/script.deb.sh 
# sudo chmod +x script.deb.sh
sudo bash script.deb.sh
# Run the installation script
wget -O vscodeInstall.sh https://code.headmelted.com/installers/apt.sh
# sudo chmod +x vscodeInstall.sh
sudo bash vscodeInstall.sh
```

Lanzar lo de arriba en terminal en ubicación dónde se quiera guardar el instalador.