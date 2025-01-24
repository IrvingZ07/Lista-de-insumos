# Proyecto de Gestión de Productos y Pedidos

Este proyecto permite a los usuarios gestionar un inventario de productos, crear una lista de pedidos con cantidades seleccionadas y eliminar productos de esa lista en caso de error. Además, es posible visualizar la lista generada en una interfaz amigable.

## Funcionalidades Principales

1. **Generación de Lista de Pedido:**
   - Los productos se cargan desde la base de datos y se presentan en una tabla con botones para aumentar o disminuir la cantidad de cada uno.
   - Los usuarios pueden elegir los productos y sus cantidades, y luego generar una lista de pedido.
   - La lista generada se guarda en la base de datos en una tabla llamada `pedido`, donde se almacenan el código, nombre y cantidad de cada producto seleccionado.

2. **Eliminación de Productos:**
   - En la interfaz, cada producto tiene un botón "Eliminar" que permite al usuario eliminar un producto de la lista si lo ha añadido por error.
   - Esto se maneja mediante un simple `remove()` en el DOM, eliminando visualmente la fila correspondiente.

3. **Visualización de la Lista de Pedido:**
   - En una página separada, se puede consultar la lista de pedidos generada. Esta página obtiene los datos directamente desde la base de datos y los presenta en una tabla, mostrando el código, nombre y cantidad de cada producto.

## Estructura del Proyecto

El proyecto está compuesto por dos archivos principales para interactuar con la base de datos:

1. **`index.php`**: 
   - Este archivo es responsable de mostrar la lista de productos desde la base de datos, permitir la modificación de cantidades y enviar la lista de productos seleccionados al servidor cuando el usuario hace clic en "Generar Lista".
   - La información se envía al servidor a través de una petición `POST`, que actualiza la tabla `pedido` en la base de datos.

2. **`ver_lista.php`**:
   - Esta página muestra la lista de pedidos generada. Los datos se extraen de la tabla `pedido` y se presentan en una tabla HTML, lo que permite a los usuarios ver los productos seleccionados y sus cantidades.

## Detalles Técnicos

### Conexión a la Base de Datos

La conexión a la base de datos se realiza mediante PDO (PHP Data Objects), que proporciona una capa de abstracción de base de datos, permitiendo trabajar con múltiples tipos de bases de datos. La base de datos utilizada en este proyecto es MySQL.

### Estructura de la Base de Datos

1. **Tabla `productos`**: Contiene los productos disponibles para añadir al pedido. Los productos se cargan desde esta tabla al iniciar la página principal.
   - `codigo`: Código único del producto.
   - `nombre`: Nombre del producto.
   - `cantidad`: La cantidad disponible (en este caso no se usa directamente, pero podría extenderse).
   - `categoria`: categoria del prodycto

2. **Tabla `pedido`**: Almacena los productos seleccionados y sus cantidades. Esta tabla es limpiada cada vez que se genera una nueva lista de pedido.
   - `id`: Identificador único del pedido.
   - `codigo`: Código del producto.
   - `nombre`: Nombre del producto.
   - `cantidad`: Cantidad del producto seleccionada para el pedido.

### Seguridad

- Las consultas SQL están preparadas y utilizan declaraciones `bind` para evitar inyecciones SQL, asegurando la seguridad de la aplicación.
- Los datos se validan antes de ser insertados en la base de datos, para prevenir posibles errores o datos corruptos.

## Instalación

### Requisitos Previos

1. Un servidor local con PHP (por ejemplo, XAMPP o MAMP).
2. Una base de datos MySQL con la tabla `productos` (que debe estar precargada con algunos productos).
3. El archivo PHP debe estar en el directorio raíz de tu servidor local.


## Contribuciones

Este proyecto está en desarrollo, junto con mi demas equipo

## Autores

Este proyecto fue desarrollado por Irving como parte de un proyecto académico.
