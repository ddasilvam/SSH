# SSH
## Creación de claves público-privada
Para generar un par de claves público-privada, desde el cliente usamos el comando ssh-keygen:
```console
ssh-keygen
```
Cuando se nos pida establecer una “passphrase” la dejaremos en blanco, de esta forma no se nos pedirá ninguna contraseña cuando iniciemos sesión usando estas claves.

## Carga de clave pública al lado servidor
Ahora neceitamos establecer el "candado" del lado del servidor al que nos queremos conectar. Para esto, subiremos la clave pública al servidor utilizando el comando:
```console
ssh-copy-id usuario_servidor@ip_servidor
```
Se nos pedirá la clave del usuario con el que estamos intentando iniciar sesión en el servidor remoto, y una vez introducida se cargará la clave pública.

## Iniciando sesión via SSH en el servidor
Para iniciar sesión en el servidor remoto lo haremos como habitualmente con el comando:
```console
ssh usuario_servidor@ip_servidor
```
Si dejamos la "passphrase" en blanco al crear las claves, se iniciará sesión automáticamente. En caso contrario, se nos requerirá dicha clave.

## Utilizando SSH para realizar cambios en repositorio de GitHub
Primeramente necesitamos establecer nuestra clave pública en el servidor de GitHub. Para ello, haciendo click en nuestra foto de perfil y dirigiéndonos a "Settings". Luego, en la columna de la izquierda vamos a "SSH and GPG keys", y hacemos click en "New SSH key". Aquí pegaremos el contenido de nuestra clave pública que creamos en el primer paso. Podremos verlo si está en la ruta por defecto mediante el comando:
```console
cat /home/usuario/.ssh/id_rsa.pub
```

Para trabajar con un proyecto, necesitaremos disponer de la copia local de un repositorio en nuestro dispositivo. Si no la tenemos, podemos realizar utilizando el comando:
```console
git clone git@github.com:usuario_github/repo.git
```
La dirección de la que clonar el repositorio podemos obtenerla desde GitHub, desde la pantalla princiapal del repositorio haciendo click en el botón [<> Code], seleccionando la pestaña SSH.

Ahora, si editamos de forma local los archivos de esta copia local del repositorio, y hacemos push a un commit de la forma habitual, se hará utilizando nuestras claves público-privadas. Como siempre, los comandos serían:
```console
git add archivo
git commit -m "Descripción"
git push origin main
```
