# Mercado Ñuble Digital

## Estudiante
Ignacio Acuña

## Descripción
Mercado Ñuble Digital es un prototipo frontend de aplicación web modular (SPA) desarrollado en Vue 3 para conectar a pequeños productores locales de comunas de la Región de Ñuble (como Chillán, San Carlos, Quirihue, Coihueco, Pinto, Yungay, El Carmen, entre otras) con compradores y usuarios interesados. Esta plataforma permite visualizar y filtrar el catálogo de productos disponibles en la región, informarse sobre los productores locales, manifestar interés por artículos y establecer contacto.

---

## Parte A - Estructura y navegación

Para construir la estructura inicial y la navegación de la aplicación:
1. **Organización del proyecto**: Se implementó una estructura limpia separando el contenido principal de la siguiente forma:
   - `src/views/`: Contiene los componentes de vista principal de la aplicación (`InicioView.vue`, `ProductosView.vue`, `ProductoresView.vue`, `ContactoView.vue`).
   - `src/components/`: Reservado para los componentes reutilizables como la tarjeta de producto (`ProductCard.vue`) y productor (`ProducerCard.vue`).
   - `src/router/`: Contiene la definición del enrutador en `index.js`.
2. **Implementación de navegación**: 
   - Se instaló y configuró `vue-router` para manejar la navegación en el cliente.
   - En `src/router/index.js`, se configuró `createWebHashHistory` para optimizar la compatibilidad local y de despluegue estático, definiendo las rutas para las cuatro vistas principales (`/`, `/productos`, `/productores`, y `/contacto`).
   - En `src/App.vue`, se implementó la estructura de la aplicación (header de navegación responsivo, cuerpo principal de renderizado `<router-view>` con transiciones fluidas, y un pie de página).
   - Se utilizaron componentes `<router-link>` con clases activas para cambiar de vista de forma instantánea sin recargar la página entera.

---

## Parte B - Componentes y Props

Para la construcción del catálogo de productos:
1. **Componente Reutilizable**: Se creó el componente [ProductCard.vue](file:///e:/Proyectos/oli/PRUEBA/src/components/ProductCard.vue) en la carpeta `src/components/` para presentar individualmente la información de cada artículo de forma consistente.
2. **Uso de Props**:
   - El componente hijo `ProductCard` recibe mediante **props** el objeto `product` (con propiedades como `name`, `category`, `producer`, `commune`, `price` y `availability`) y un booleano `isInterested`.
   - Estos datos son enviados desde la vista padre [ProductosView.vue](file:///e:/Proyectos/oli/PRUEBA/src/views/ProductosView.vue), la cual define y almacena el listado de productos en una estructura de datos reactiva (`ref`) con 6 productos correspondientes a 6 comunas diferentes de la Región de Ñuble (San Carlos, Coihueco, Pinto, Quirihue, El Carmen y Chillán).
   - En la vista padre se utiliza `v-for` para iterar dinámicamente sobre la colección y renderizar cada tarjeta enviando las propiedades correspondientes.

---

## Parte C - Listas y condicionales
*Pendiente de desarrollo.*

---

## Parte D - Comunicación mediante Emit
*Pendiente de desarrollo.*

---

## Parte E - Formulario y validación
*Pendiente de desarrollo.*

---

## Parte F - Diseño y presentación
*Pendiente de desarrollo.*

---

## Tecnologías utilizadas
- **HTML5** y **Vanilla CSS**
- **JavaScript (ES6+)**
- **Vue 3 (Composition API, `<script setup>`)**
- **Vue Router**
- **Vite** (Herramienta de construcción)
- **Git** y **GitHub** (Control de versiones)

## Ejecución
Para ejecutar el proyecto localmente, siga los siguientes pasos:

1. Clonar el repositorio.
2. Instalar las dependencias con:
   ```bash
   npm install
   ```
3. Ejecutar el servidor de desarrollo local con:
   ```bash
   npm run dev
   ```
4. Abrir la URL indicada en el navegador (por defecto `http://localhost:5173`).

---

## Reflexión final
*Pendiente de desarrollo al finalizar el proyecto.*
