# Jetson Remote Desktop (VNC)

Proceso para habilitar escritorio remoto en Jetson:

1. Editar el fichero de esquemas gnome VINO:

   ```bash
   sudo nano /usr/share/glib-2.0/schemas/org.gnome.Vino.gschema.xml
   ```

   

2. Añadir al final lo siguiente:

   ```bash
   <key name='enabled' type='b'>
   	<summary>Enable remote access to the desktop</summary>
   	<description>
   		If true, allows remote access to the desktop via the RFB
   		protocol. Users on remote machines may then connect to the
   		desktop using a VNC viewer.
   	</description>
   	<default>true</default>
   </key>
   ```

   

3. En un terminal lanzar lo siguiente:

   ```bash
   sudo glib-compile-schemas /usr/share/glib-2.0/schemas
   ```

   

4. Abrir `Desktop Sharing` en `System Settings`

5. Marcar `Allow other users to view you desktop`  y `Allow other users to control your desktop`

6. En un terminal lanzar lo siguiente:

   ```bash
   gsettings set org.gnome.Vino require-encryption false
   ```

   ```bash
   gsettings set org.gnome.Vino prompt-enabled false
   ```

   

   