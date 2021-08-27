# gambito_webOwStudio

## Instalacion

Sigue los pasos para correr el proyecto

- creo una Base de Datos en Postgresql (nn01)
- cambio el nombre en el app/config/db.py linea 17 --> 'NAME': 'nn01'
- instala  virtualenv

```sh
pip install virtualenv
```
- creo el entorno virtual
```sh
virtualenv env
```
- activo el entorno virtual
```sh
 env\scripts\activate
 ```
en linux
 ```sh
 source env/bin/activate
```
- entrar a la carpte app --> cd app/
- instalar los requerimientos
```sh
 pip install -r requirements/requirements.txt
 ```
- crear las migraciones
```sh
 python manage.py makemigrations
```
- migrar los modelos
```sh
 python manage.py migrate
```
- creo una nueva Base de Datos en Postgresql (nn02)
- cambio el nombre en el app/config/db.py linea 17 --> 'NAME': 'nn02'
- restauras el backup (wcBackup_180620212158) sobre la base de datos creada (nn02) en Postgresql
- verificar que todo este ok
```sh
 python manage.py check
```
- levatar el server
```sh
 python manage.py runserver
```
<!-- username: admin
password: Th3H4ck3r$$c0mp@ny** -->

### Credenciales

#### username:
admin
#### password:
Th3H4ck3r$$c0mp@ny**