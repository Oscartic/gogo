# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

.Command: 
- rake db.rollcack = Deshace la ultima migración. Si se le agrega al final "STEP=#" 
borrará las ultimas #tantas migraciones.

- rails g model Articulo titulo:string contenido:text autor:references. 
autor:references hará que ese campo sea foreano a la tabla autor

MIGRACIONES 

Añadir campos a la categoria de articulos:
$~ rails g migration add_categoria_id_to_articulos categoria_id:integer:index

Cambiar el tipo de dato de categoria_id recien creada.
$~ rails g migration change_data_type_for_articulos 
Creo una nueva migracion y en dicho archivo colocar: 
    change_column :articulos, :categoria_id, :text

Cambiar Nombre de una columna, se hace lo mismo que con el cambio de tipo de dato,
pero en el archivo resultante se escribe: 
    rename_column :tabla, :columna, :nuevo nombre

Eliminar campos de tablas:
$~ rails g migration remove_categoria_id_form_articulos categoria_id:text 

!importante: para más informacion: 
http://edgeguides.rubyonrails.org/active_record_migrations.html

DEVISE
1- Agregar la gema en el gemfile
2- $~ rails generate devise:install
3- Asegurar que exista una ruta en el root. Ej. root to: "home#index"
4- Asegurar que se incluya en alguna parte los mensajes de notice.
5. para crear las vistas de devise y su costumizacion se debe ejecutar: 
        $~ rails g devise:views

Para generar un modelo de usuario será de esta forma: 
$~ rails generate devise Autor
