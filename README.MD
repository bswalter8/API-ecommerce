# _Proyecto Backend API FULL REST ECOMMERCE_

## RESUMEN
El proyecto Backend es una api rest full, creada para ser contactada desde un frontend, el cual debe ser capaz de 
recibi, procesar y mostrar los datos enviados por el backend.

## INFORMACION
Nuestra API esta desarrollada en JavaScript y nuestro servidor esta desarrollado con [Node.js](https://nodejs.org/). 
Es una API de Ecommerce, con lo cual entre sus funciones estan: 
+ Crear productos
+ Modificar productos
+ Eliminar productos
+ Crear usuarios
+ Logear usuarios
+ Crear carrito de compra
+ Agregar productos al carrito
+ Eliminar productos del carrito
+ Vaciar carrito de compras

Los datos son almacenados en una base de datos en la nube, en este caso se eligio Mongo Atlas para el proyecto.

## INSTALACION
Para instalar la API se debe rescargar el proyecto alojado en github.
Una vez descargado el proyecto, desde la carpeta principal del proyecto, debemos correr en un CLI el siguiente comando
para instalar los paquetes necesario para correr la API.

```sh
npm install
```

Luego debemos iniciar el servidor con el siguiente comando dependiendo del modo de ejecucion requerido. 

```sh
npm run start:prd (Para entrar en modo de producción)
```
```sh
npm run start:dev (Para entrar en modo de desarollo)
```


##  ENTORNO
El servidor posee dos archivos diferenciados de variable de entorno: production.env, development.env.
Ambas contienen las variables para cada una de las variables de configuracion.

- NODE_ENV= Modo en que se iniciará el servidor.
- PORT= puerto en el que se inicará el servidor.
- connectDB= conexion a la DB de mongo atlas.
- PERS= seleccion de la DB que se utilizara. (en este caso solo contamos con la DB mongoose)
- PRIVATE_JWT= Clave privada de JWT. 
- MONGOURL_ENV= Direccion de MongoDB Atlas
- EMAIL= casilla de correo del servidor.
- MAIL_PASS= password del servidor de correo 


ENDPOINTS DE LA API
Las siguientes direcciones estan configuradas con el proposito de devolver los datos a las que se hace referencia.
Las direcciones (endpoints):

>Para administrar los productos:
>Es necesario setear desde la DB en el user la propiedad "admin", 
>ya que por defecto se crean las cuentas como 'user' y se deben setear a admin.

Nuestros productos deben contener los siguientes parametros para ser admintidos en nuetra DB.

Ejemplo producto en JSON:
```sh
        {
            title: { type: String, required: true },
            price: { type: Number, required: true },
            descripcion: { type: String, required: true },
            categoria: { type: String, required: true },
            thumbnail: { type: String, required: true },
        }

```
	

Las rutas de productos:
+ localhost:port/product/add	- se envia a travez de un metodo post, con el producto a cargar.
+ localhost:port/product/list- se envia a travez de un metodo get, devuelve el listado de productos
+ localhost:port/product/	- se envia a travez de un metodo put, con el producto a modificar
+ localhost:port/product/	- se envia a travez de un metodo delete, con el producto a eliminar
+ localhost:port/product/add	- se envia a travez de un metodo get, devuelve una web para crear productos
+ localhost:port/product/	- se envia a travez de un metodo get, devuelve la lista de productos por categoria(se debe pasar por json la clave:valor {"category":"alguna"})
+ localhost:port/product/:id	- se envia a travez de un metodo get, muestra el producto con ese ID.

>Para registrarse y logearse:
>Se debe acceder a la ruta principal que simplemente redirecciona al loguin en la API.
>Los usuarios para registrarse deben contener los siguientes parametros para ser admintidos en nuetra DB.

Ejemplo user en JSON:
```sh
	 {
     username: String,
     password: String,
     email: String,
     address: String,
     cellphone: String,
     age: String,
    }

```
>Importante. Cuando un usuario se registre inmediantamente se creara en la base de datos el siguiente documente en una colección MongoDB. Dicha coleccion tendra siempre el rol de "user", por una cuestion de seguridad el rol de admin solo se puede cambiar desde la base de datos misma. 

```sh
    {
        userName: { type: String, required: true },
        role: { type: String, required: true },
    }
```

+ localhost:port/	-Ruta inicial de la API
+ localhost:port/login	-Ruta para realizar el login	
+ localhost:port/signup -Ruta para realizar el registro

>Para utilisar el carrito de compras:
>Se accede a traves de las siguientes rutas en la API.
>Los usuarios para utilizar el carrito de compras deben utilizar el siguiente formato.

Ejemplo user en JSON:

```sh
	{
    idUser: { type: String, required: true },
    timestamp: { type: Date, required: true },
    products: { type: Array, required: true },
    delivery: { type: Array, required: true }
  }
```
	

+ localhost:port/carritos/:id/productos	- se envia a travez de un metodo get, devuelve el listado de productos dentro del carrito.
+ localhost:port/carritos/:id/productos/:idProd'	- se envia a travez de un metodo put, se cargara un producto al carrito, pasado por body con los parametros definidos en el ejemplo.		
+ localhost:port/carritos/:id/productos/:idProd	- se envia a travez de un metodo delete, se elimina un producto del carrito, pasado por body con el parametros definido en el ejemplo solo el id.

## IMPLEMENTACION DE FRONTEND
El Front End es una implementación en React para probar las caracteristicas de la API de manera completamente independiente.



## LIBRERIAS Y COMPLEMENTOS 

| Librerias | Complementos |
| ------ | ------ |
| bcrypt | Github |
| connect-mongo | Mongo Atlas |
| dotenv | NPM |
| ejs |  |
| express |  |
| express-session |  |
| mongoose |  |
| nodemailer |  |
| nodemon |  |
| passport |  |
| passport-local |  |
| socket.io |  |

