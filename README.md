# Arquitectura MVC

### Pregunta 1: ¿Qué camino sigue el código cuando el usuario accede por primera vez a `index.php`?
**Descripción**: Explica qué ocurre desde que el usuario carga `index.php` hasta que se muestra algo en pantalla. Incluye cómo intervienen el controlador, las vistas y el modelo, si es necesario.

---
Cuando el usuario carga el index, lo primero que hace es definir la constante de nombre "BASE_PATH" junto con la ruta del directorio "__DIR__" (constante que devuelve la ruta del archivo desde el que se le llama).

También carga el controlador, con la ruta "BASE_PATH" junto con el subdirectorio "/controllers" en busca del archivo "UserController.php". 

Todo esto junto hace que se ejecute el archivo "UserController.php" independientemente de la ubicación.

Termina instanciando la clase "UserController" (cargando el modelo de usuario y la conexión a la base de datos) y llamando al método "showForm()". Este método, utiliza el método "requiere_once" para mostrar por pantalla el formulario de creación de usuario. 
---

### Pregunta 2: ¿Qué camino sigue el código cuando el usuario introduce datos en el formulario?
**Descripción**: Detalla el proceso desde que el usuario envía el formulario hasta que se guarda la información y se muestra una respuesta en pantalla.

---
Cuando el usuario pulsa sobre "create user", mediante un POST, envia la información al archivo "saveUser.php". 

Una vez en el archivo vuelve a definir la constante "BASE_PATH" con la constante "__DIR__" y llama de nuevo al controlador. Esta vez, al crear la instancia del controlador, llama al método saveUser(). 

El método saveUser(), recoge el valor que ha introducido el usuario, crea un nuevo objeto "USER" y lo guarda en la base de datos mediante el método "save()" de la propia clase y dirige al usuario a "userSuccess".

El usuario encontrará un link que le redirigirá al archivo "index.php".
---


### Ejercicio 1: Mostrar Todos los Usuarios
**Descripción**: Extiende la funcionalidad de la aplicación para que se muestre una lista de todos los usuarios que están en la base de datos.
- Añadir un nuevo método en el controlador `UserController` llamado `getAllUsers()`.
- Crear una nueva vista `showUsers.php` para mostrar una tabla con los nombres de los usuarios.

>**Nota:** Al crear nuevas vistas, añade alguna forma de navegar entre ellas de modo que el usuario pueda acceder a todas las vistas sin tener que modificar la URL directamente.

### Ejercicio 2: Eliminar Usuario
**Descripción**: Implementa la funcionalidad para eliminar un usuario de la base de datos.
- Crear un método `deleteUser()` en `UserController`.
- Crear una acción en `showUsers.php` que permita eliminar usuarios, mostrando un botón "Eliminar" al lado de cada nombre en la lista de usuarios.

