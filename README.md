# gambito_webOwStudio

## Instalacion

Sigue los pasos para correr el proyecto

- creo una Base de Datos en Postgresql (nn01)
- cambio el nombre en el app/config/db.py linea 17 --> 'NAME': 'nn01'
- instala  virtualenv

```sh
pip install virtualenv
```
2.- creo el entorno virtual --> python -m venv env
3.- activo el entorno virtual --> env\scripts\activate o source env/bin/activate
4.- entrar a la carpte app --> cd app/
5.- instalar los requerimientos --> pip install -r requirements.txt 
6.- crear las migraciones --> python manage.py makemigrations
7.- migrar los modelos --> python manage.py migrate
8.- creo una nueva Base de Datos en Postgresql (nn02)
9.- cambio el nombre en el app/config/db.py linea 17 --> 'NAME': 'nn02',
10.- restauras el backup (wcBackup_180620212158) sobre la base de datos creada (nn02) en Postgresql
11.- verificar que todo este ok --> python manage.py check
12.- levatar el server --> python manage.py runserver

username: admin
password: Th3H4ck3r$$c0mp@ny**


## Configuración

### TCRM 

#### Service: app/core/finanzas/services.py

Para la configuracion del TCRM se debe cambiar la URL de la API en la linea 6 e implementar las configuraciones correspondientes segun la API que se va a utilizar.

Luego se debe cambiar la linea de codigo 187 y 189 del archivo views.py (modulo Paginas), actualmente esta trabajando con el modulo Moneda para los calculos de descuentos y ganancias.

### SCRAP

#### Modelo: app/core/scrap/models.py

Este modulo posee el diseño del modelo de las paginas que se utilizaran en el consumo para los pagos, el modelo es una representacion de las Tablas de la DB que nos trae el scraper.

Cuando se desee agregar nuevas paginas, primeramente se tendra que agregar los modelos en este Modulo.

### PAGINAS

#### Views: app/core/finanzas/views/pago/views.py

Para agregar nuevas paginas se debe seguir el formato del bloque de codigo de la linea 175 a 191, este bloque hace referencia a la pagina "xmodels". No olvidar que se debe tener el modelo agregado en el modulo Scrap.

Es importante que el array "data_cuenta" tenga los mismo campos para el consumo en el Frontend, puede tener mas, pero no se debe quitar ninguno, en caso de quitar algun campo se tendra que cambiar tambien en el frontend (app/core/finanzas/static/pago/cuentas_list.js)

##### Es muy importante que el nombre de las paginas siga un formato estandar, para que el filtrado y consumo desde el Scraper sea optimo, se deben respetar letras mayúsculas y minúsculas.

### EMAIL

#### Template: app/templates/email.html
#### Views: app/core/finanzas/views/pago/views.py
#### Config: app/config/settings.py

Para el envio de correo primeramente se deben configurar las credenciales del correo en las lineas 179 y 180 del archivo de configuracion.

El nombre de Dominio para el envio de correo es automatico, en caso de necesitar un dominio estatico, se debe editar la linea 291 del archivo views.py

Para cambiar el diseño del template tener en cuenta las variables {{variables}} que se encuentran en el archivo html, ya que estas se renderizan automaticamente con los valores que se les envia desde el la vista views.py

En el caso del logo, se esta renderizando automaticamente con el logo de la compañia, si se desea cambiarlo se tendra que editar la linea 292 del archivo views.py o en su defecto, cambiar el logo de la compañia.

### Nota

En caso de existir dudas comunicarse a d.cruz@outlook.com

Saludos.

