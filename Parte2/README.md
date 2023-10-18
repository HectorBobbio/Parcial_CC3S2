# Introduccion a Rails

En esta seccion creamos una app sencilla de Rails, y aprovechamos los generadores de Rails para ahorrar trabajo. Utilizando **generate scaffold** Rails genera casi todo lo que necesitamos: Una migracion inicial, un modelo **todo**, un controlador para **todo**, las vistas para las operaciones CRUD, asi como metodos helper, para pruebas unitarias, etc.

![](./imgs/ScaffoldGenerated.png)

Al incluir **description:string** en el comando de generacion del scaffold ya estamos definiendo el esquema de nuestra base de datos. Solo nos falta realizar la migracion para crear una tabla.

![](./imgs/Migration.png)

Tambien podemos agregar valores mediante seeding:

![](./imgs/seeding.png)

Y podemos confirmar que se han adicionado los datos que queriamos utilizando la consola de Rails.

![](./imgs/SeededCorrectly.png)

Ahora, queremos añadir una nueva columna para que cada ToDo tenga una fecha de vencimiento. Para esto creamos una nueva migracion:

![](./imgs/newMigration.png)

Y editamos esta migracion para que añada una columna "fechaVencimiento", con el tipo de dato "date" a la base de datos del recurso "todo".

![](./imgs/AddColumnMigration.png)

Despues de realizar la migracion con **rails db:migrate** podemos observar en la consola de Rails que se realizo satisfactoriamente: ahora tenemos una nueva columna fechaVencimiento con valores **nil**

![](./imgs/MigratedCorrectly.png)

Observamos tambien que el contenido del archivo **schema.rb** se ha modificado de acorde:

![](./imgs/SchemaChange.png)

Luego, agregamos una ruta '/hello' a la que asignaremos la accion 'hello' del controlados de 'todos'.

![](./imgs/helloRoute.png)

Luego modificamos el archivo **todos_controller.rb** para agragarle un metodo **hello** que renderice una vista **hello**, previamente definida en **app/views/todos**

![](./imgs/RouteHelloDone.png)


Ahora, queremos agregarle un nuevo atributo al modelo **todo**, un booleano que nos indique si una tarea ya fue realizada o no. Generamos una nueva migracion para adicionar esta columna: 

![](./imgs/TodoDoneMigration.png)

![](./imgs/DoneMigrationCode.png)

Verificamos que se adiciono la columna satisfactoriamente:

![](./imgs/DoneMigrationExecuted.png)

Para tener una ruta new_todo que nos direccione a una pagina para crear un nuevo item Todo no es necesario realizar algun cambio, pues al utilizar **generate scaffold**, por defecto se ha agregado al archivo de rutas de rails la expresion **resources :todos**, que nos proporciona las rutas CRUD por defecto de rails. Podemos verificar esto con el comando **rails routes**

![](./imgs/newTodoRoute.png)

Si queremos que nuestra pagina inicial sea **todos#index** solo tenemos que agregar la expresion **root 'todos#index'** en el archivo de rutas.

![](./imgs/rootRoute.png)

Verificamos que en efecto la pagina inicial sea la indicada:

![](./imgs/indexAsHomePage.png)

Hasta ahora hemos realizado dos migraciones: para agregar la columna fechaVencimiento, y para agregar la columna done. Podemos retroceder a la version anterior de la base de datos deshaciendo la migracion, con el comando **rails db:rollback**.

![](./imgs/MigrationRollback.png)




