# Programación WEB (electiva)

## Maquina Virtual

La maquina virtual tiene instalado [Lubuntu Linux 17.04](http://lubuntu.net/), es la distribución más liviana de Ubuntu. Se puede descargar desde [aquí](https://www.dropbox.com/s/zvui8lkxq32bb24/lubuntu17.04_web.7z?dl=0)

### Requerimientos para el correcto funcionamiento de la maquina virtual

Para que funcione la maquina virtual es necesario tener instalado lo siguiente:

* Sistema Operativo de 64bits.

* para poder descomprimir el archivo es necesario tener instalado 7zip, se puede descargar desde [la web oficial de 7zip](http://www.7-zip.org/download.html)

* Vmware Workstation Player [se puede descargar desde la web oficial de VmWare](https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0)
o VirtualBox [se puede descargar desde la web oficial de VirtualBox](https://www.virtualbox.org/wiki/Downloads)

* 10GB de espacio libre en un disco.

### Pasos a seguir para iniciar la maquina Virtual

1. Descargar el archivo de la maquina virtual desde [aquí](https://www.dropbox.com/s/zvui8lkxq32bb24/lubuntu17.04_web.7z?dl=0)
1. Descomprimir el archivo en un disco Local.
1. Abrir la aplicación  de virtualización ( VmWare o VirtualBox), seleccionar el menu importar, abrirá el asistente donde tendremos que seleccionar dentro de la carpeta descomprimida el archivo **lubuntu17.04_web.ovf** y luego seguir el asistente, el proceso de importación va a demorar unos minutos, y luego quedará disponible la maquina virtual para iniciar.

## Instalar todo el software que usaremos

en caso de no poder ejecutar la maquina virtual se puede seguir los siguientes pasos para instalar todo el software que usaremos en una pc con ubuntu recién Instalado.

### 1. Actualizar la base de datos local de paquetes

```bash
sudo apt update -y
```

### 2. Actualizar los paquetes

```bash
sudo apt upgrade -y
```

### 3. Opcional (Si la maquina es Virtual es recomendable instalar open-vm-tools open-vm-tools-desktop)

si la maquina es virtual es recomendable instalar las tools para maquinas virtuales, para tener compatibilidad con la resolución de pantalla, permitir el uso del porta papeles entre la maquina virtual y el host, etc.

```bash
sudo apt install open-vm-tools open-vm-tools-desktop
```

### 4. Instalar Google Chrome y Visual Studio Code

**Visual Studio Code** y **Google Chrome** no están en los repositorios oficiales por lo que es necesario instalar desde el sitio web oficial de cada uno.

#### 4.1 [Descargar **visual estudio code** desde la web oficial](https://code.visualstudio.com/download)

#### 4.2 [Descargar **google chrome** desde desde la web oficial](https://www.google.com/chrome/index.html)

#### 4.3 abrir una terminal

#### 4.4 ir al directorio de Descargas 

```bash
cd Descargas/
```

#### 4.5 Instalar todos los paquetes con extensión **deb** que estén en el directorio Descargas

```bash
sudo dpkg -i *.deb
```

#### 4.6 instalar las dependencias que faltan para que funcione chrome y visual studio code

```bash
sudo apt --fix-broken install
```

#### 4.7 actualizar nuevamente la base de datos local de paquetes

```bash
sudo apt update -y
```

#### 4.8 actualizar los paquetes 

```bash
sudo apt upgrade -y
```

### 5 instalar utilidades

```bash
sudo apt install -y vim curl git git-flow git-gui
```

* **vim** es un editor de texto que funciona en la terminal de linux.
* **curl** es una herramienta para transferencia de archivos en la terminal de linux.
* **git** es la herramienta para control de versiones de archivos más utilizada en la actualidad.
* **git-flow** es un plugin para administrar el flujo de trabajo en **git**.
* **git-gui**  es una interfaz gráfica para **git**.

### 6 instalar MYSQL y el Workbench

Va a pedirles una **nueva contraseña para el usuario root de MySQL**, el usuario root de mysql no tiene nada que ver con el usuario del sistema operativo.

```bash
sudo apt install -y mysql-server mysql-workbench
```

### 7 Instalar NODEJS

#### 7.1 [instalar nodejs preferentemente con **nvm**](https://github.com/creationix/nvm)

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
# cerrar y volver a abrir la terminal
```

#### 7.2 instalar nodejs desde nvm

```bash
nvm install node
```

#### 7.3 utilidades en nodejs 

```bash
npm i -g json-server 
npm i -g eslint
```

### 8 Apache, PHP y Composer

```bash
sudo apt install -y apache2 php php-mysql php-mbstring php-token-stream php-xml
```

#### 8.1 [instalar composer según la web oficial](https://getcomposer.org/download/)

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

#### 8.2 habilitar composer para todos los usuarios

```bash
sudo mv composer.phar /usr/bin/composer
```

#### 8.3 crear un proyecto de prueba en laravel

```bash
composer create-project --prefer-dist laravel/laravel lara01
```

#### 8.4 verificar el funcionamiento de la nueva aplicación laravel

```bash
cd lara01
php artisan serve
```