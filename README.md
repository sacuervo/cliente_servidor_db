# IberoPet

## Descripción General

Este proyecto implementa una aplicación de servidor y cliente para gestionar servicios en una guardería de mascotas. El servidor permite crear, actualizar, consultar y eliminar pedidos de servicios. El cliente interactúa con el servidor para realizar estas operaciones a través de un menú en la consola.

## `Server.java`

### Descripción

El archivo `Server.java` implementa la lógica del servidor, que incluye la conexión a la base de datos, el procesamiento de las solicitudes de los clientes, y la ejecución de operaciones CRUD (Crear, Leer, Actualizar y Eliminar) en los pedidos de servicios.

### Dependencias

- **Java I/O:** Para el manejo de entradas y salidas de datos (`BufferedReader`, `PrintWriter`).
- **Java SQL:** Para interactuar con la base de datos (`Connection`, `PreparedStatement`, `ResultSet`).
- **Java Networking:** Para la comunicación entre el servidor y los clientes (`Socket`, `ServerSocket`).

### Funcionalidad Principal

1. **Métodos CRUD para la base de datos:**
   - `processServiceRequest`: Añade un nuevo pedido a la base de datos.
   - `processRequestFinalization`: Marca un pedido como finalizado.
   - `grabRequestInformation`: Obtiene información sobre un pedido específico.
   - `inquireAllRequestsInformation`: Recupera la información de todos los pedidos.
   - `deleteRequestEntry`: Elimina un pedido de la base de datos.
   - `verifyRequestExistence`: Verifica si un pedido existe en la base de datos.

2. **Métodos de funcionamiento del servidor:**
   - `handleClient`: Gestiona la conexión con los clientes y procesa las entradas que envían.
   - `processInput`: Procesa los comandos enviados por el cliente para interactuar con la base de datos.
   
3. **Comandos admitidos:**
   - `"showservices"`: Lista todos los servicios disponibles.
   - `"storeservice [service_id] [client_name]"`: Crea un nuevo pedido.
   - `"getrequeststate [request_id]"`: Muestra el estado de un pedido específico.
   - `"endrequest [request_id]"`: Marca un pedido como finalizado.
   - `"deleterequest [request_id]"`: Elimina un pedido.
   - `"exit"`: Finaliza la conexión con el cliente.

### Ejecución

Para iniciar el servidor, ejecuta el método `main` de `Server.java`. El servidor se ejecuta en el puerto 9999 y espera conexiones de los clientes. Cuando un cliente se conecta, el servidor procesa las entradas y responde según las solicitudes.

## `Client.java`

### Descripción

El archivo `Client.java` implementa la lógica del cliente, que se conecta al servidor y le envía comandos para interactuar con los servicios y pedidos.

### Dependencias

- **Java I/O:** Para el manejo de entradas y salidas de datos (`BufferedReader`, `PrintWriter`).
- **Java Networking:** Para la comunicación con el servidor (`Socket`).
- **Java Util:** Para capturar las entradas del usuario (`Scanner`).

### Funcionalidad Principal

1. **Menú de Usuario:** 
   - Ofrece al usuario un menú con las siguientes opciones:
     1. Ver servicios.
     2. Crear pedido.
     3. Ver estado de pedido.
     4. Finalizar pedido.
     5. Eliminar pedido.
     6. Salir.
   
2. **Interacción con el Servidor:**
   - Envia comandos al servidor de acuerdo con la selección del usuario.
   - Procesa las respuestas del servidor y las muestra en la consola.

3. **Métodos Clave:**
   - `printServerResponse`: Imprime las respuestas del servidor en la consola.
   - `main`: Contiene la lógica principal para conectar al servidor, mostrar el menú y manejar la entrada del usuario.

### Ejecución

Para ejecutar el cliente, ejecuta el método `main` de `Client.java`. El cliente se conecta al servidor en `localhost` y al puerto `9999`. A continuación, el usuario puede interactuar con el menú para gestionar los servicios y pedidos.

## Ejecución del Proyecto

### Overview 
1. Asegúrate de estar en el directorio raiz del proyecto.
2. Compilar el cliente y el servidor -> `javac ./src/Client.java ./src/Server.java`
3. Ejecutar el servidor añadiendo el .jar al CLASSPATH ->  `java -cp ".;sqlite-jdbc-3.46.1.3.jar;src" ./src/Server.java`
4. Ejecutar el cliente -> `java ./src/Client.java`


### Consideraciones

- El servidor debe ejecutarse antes que el cliente para que éste pueda conectarse correctamente.
- La base de datos se gestiona directamente desde el servidor. El cliente solo envía comandos para interactuar con los servicios y pedidos.

### Manejo de Errores

- El servidor y el cliente están diseñados para manejar ciertos errores, como:
- Verificación de la existencia de servicios y pedidos antes de realizar acciones.
- Validación de entradas del usuario en el cliente.

### Recursos

- Para utilizar esta aplicación es necesario contar con una base de datos configurada que contenga las tablas necesarias para guardar los servicios y pedidos.

## Resumen

Esta aplicación cliente-servidor en Java permite gestionar servicios en una guardería de mascotas. El servidor gestiona los datos y realiza las operaciones CRUD en la base de datos, mientras que el cliente proporciona una interfaz de consola para que el usuario interactúe con dichos servicios.

