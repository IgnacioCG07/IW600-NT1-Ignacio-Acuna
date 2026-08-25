# Mercado Ñuble Digital

## Estudiante
Ignacio Acuña

## Descripción
Mercado Ñuble Digital es un prototipo de aplicación web desarrollado en Vue 3 para conectar a pequeños productores de la Región de Ñuble (comunas como San Carlos, Quirihue, Chillán, Coihueco, El Carmen, entre otras) con posibles compradores. La plataforma permite revisar un catálogo de productos locales, filtrar la información por comuna y contactar con la organización.

---

## Parte A - Estructura y navegación
Para estructurar el proyecto creé cuatro vistas principales en la carpeta `src/views/`:
- `InicioView.vue`: Presentación del proyecto.
- `ProductosView.vue`: Catálogo de productos.
- `ProductoresView.vue`: Información de los productores.
- `ContactoView.vue`: Formulario de contacto.

Para la navegación instalé y configuré Vue Router en `src/router/index.js`. Luego, en `App.vue` implementé el menú principal utilizando `<router-link>` para cambiar entre vistas sin recargar la página y la etiqueta `<router-view>` para mostrar el contenido correspondiente.

---

## Parte B - Componentes y Props
Creé un componente reutilizable llamado `ProductCard.vue` dentro de la carpeta `src/components/`. Este componente define las `props` necesarias para recibir la información de cada producto (`nombre`, `categoria`, `productor`, `comuna` y `precio`). 

En la vista padre `ProductosView.vue` definí un arreglo con 6 productos pertenecientes a distintas comunas de la región y le pasé los datos a cada componente hijo mediante sus respectivas props.

## Parte C - Listas y condicionales
Se implementó la generación dinámica del catálogo mediante la directiva `v-for`, recorriendo la propiedad computada `productosFiltrados`. Para la lógica condicional se incorporó un filtro de selección por comuna (`v-model="comunaSeleccionada"`). Mediante las directivas `v-if` y `v-else`, si la lista de productos filtrados contiene elementos, se renderizan las tarjetas de producto; en caso de que no existan resultados para la comuna seleccionada (por ejemplo, al elegir "Bulnes"), se despliega un mensaje que informa al usuario que no hay productos disponibles.

## Parte D - Comunicación mediante Emit
Agregué un botón llamado "Me interesa" dentro de cada tarjeta de producto (`ProductCard.vue`). 

Cuando el usuario presiona este botón, el componente hijo emite un evento personalizado mediante `defineEmits(['interes'])`, enviando la información del producto. El componente padre (`ProductosView.vue`) escucha este evento con `@interes="agregarInteres"` y ejecuta una función que guarda el nombre del producto en un arreglo reactivo. Esto hace que en la parte superior del catálogo se actualice automáticamente un contador y una lista con los productos seleccionados por el usuario.

## Parte E - Formulario y validación
Implementé el formulario de contacto en la vista `ContactoView.vue` solicitando los 5 campos requeridos (`nombre`, `email`, `telefono`, `comuna` y `mensaje`), todos vinculados mediante la directiva `v-model`.

Antes de procesar el envío, se validan los datos con JavaScript: si falta algún campo o el correo no incluye un formato válido, se muestra un mensaje de alerta en pantalla. Cuando todos los campos son válidos, el formulario se oculta y la aplicación despliega un cuadro de confirmación con el resumen de la información ingresada.