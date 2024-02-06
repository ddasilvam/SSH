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


