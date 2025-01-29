# DOM: Atributos y Propiedades

### **1. Atributos y Propiedades DOM**
- **Atributos HTML**: Son lo que está escrito en el HTML. Se acceden con métodos como `getAttribute`, `setAttribute`, `hasAttribute`, y `removeAttribute`.
- **Propiedades DOM**: Son las propiedades de los objetos JavaScript que representan los nodos del DOM. No siempre coinciden con los atributos HTML.
- **Sincronización**: Cambiar un atributo estándar actualiza la propiedad correspondiente, pero no siempre viceversa (ejemplo: `input.value`).

#### Ejercicio Resuelto
**Enunciado**: Dado el siguiente código HTML, muestra cómo cambiar el valor del atributo `value` y de la propiedad `value` de un elemento input, y explica la diferencia entre ambos.

Código HTML:
```html
<input id="miInput" type="text" value="Hola">
```
Script en JavaScript:
```javascript
const input = document.getElementById('miInput');

// Cambiar el valor del atributo
input.setAttribute('value', 'Nuevo Valor');

// Cambiar la propiedad DOM
input.value = 'Texto Actualizado';

// Mostrar ambos valores
console.log('Atributo value:', input.getAttribute('value'));
console.log('Propiedad value:', input.value);
```
---

### **2. Métodos para trabajar con atributos**
- **`elem.hasAttribute(name)`**: Verifica si existe un atributo.
- **`elem.getAttribute(name)`**: Obtiene el valor de un atributo.
- **`elem.setAttribute(name, value)`**: Establece un valor para un atributo.
- **`elem.removeAttribute(name)`**: Elimina un atributo.
- **`elem.attributes`**: Colección de todos los atributos.

#### Ejercicio Resuelto
**Enunciado**: Crea un elemento HTML dinámicamente, añade un atributo personalizado, modifícalo, elimínalo y muestra la lista completa de atributos.

Script en JavaScript:
```javascript
// Crear el elemento div
const div = document.createElement('div');
div.setAttribute('data-role', 'admin');

// Verificar si existe el atributo
console.log('¿Existe data-role?:', div.hasAttribute('data-role'));

// Cambiar el valor del atributo
div.setAttribute('data-role', 'editor');
console.log('Nuevo valor de data-role:', div.getAttribute('data-role'));

// Eliminar el atributo
div.removeAttribute('data-role');
console.log('¿Existe data-role después de eliminarlo?:', div.hasAttribute('data-role'));

// Mostrar todos los atributos
console.log('Lista de atributos:', div.attributes);
```
---

### **3. Propiedades DOM**
- Las propiedades DOM pueden ser de cualquier tipo (string, boolean, objeto, etc.).
- **Ejemplos**:
  - `input.checked` es un booleano.
  - `elem.style` es un objeto CSS.
  - `href` en un enlace siempre es una URL completa.

#### Ejercicio Resuelto
**Enunciado**: Trabaja con las propiedades DOM de un checkbox para marcarlo, cambiar su estilo y verificar si está marcado.

Script en JavaScript:
```javascript
// Referencia al checkbox
const checkbox = document.getElementById('miCheckbox');

// Marcar el checkbox
checkbox.checked = true;

// Cambiar el color del texto asociado
checkbox.style.color = 'red';

// Verificar si está marcado
console.log('¿Checkbox marcado?:', checkbox.checked);
```
---

### **4. Atributos no estándar y `dataset`**
- Los atributos no estándar son útiles para pasar datos personalizados de HTML a JavaScript.
- Para evitar conflictos con futuros estándares, se usan atributos `data-*`, accesibles a través de `elem.dataset`.

#### Ejercicio Resuelto
**Enunciado**: Usa un elemento con atributos `data-*` para leer y modificar valores personalizados desde JavaScript, y añade un nuevo atributo dinámicamente.

Script en JavaScript:
```javascript
const elemento = document.getElementById('miElemento');

// Leer valores de data-user-id y data-role
console.log('User ID:', elemento.dataset.userId);
console.log('Role:', elemento.dataset.role);

// Cambiar data-role a "user"
elemento.dataset.role = 'user';

// Añadir un nuevo atributo data-status
elemento.dataset.status = 'activo';

// Mostrar todos los valores
console.log('Dataset completo:', elemento.dataset);
```
---

### **5. Manipulación del DOM**
- **Creación de elementos**:
  - **`document.createElement(tag)`**: Crea un nuevo elemento.
  - **`document.createTextNode(text)`**: Crea un nodo de texto.
- **Inserción de elementos**:
  - **`node.append(...nodes)`**: Inserta nodos al final.
  - **`node.prepend(...nodes)`**: Inserta nodos al principio.
  - **`node.before(...nodes)`**: Inserta nodos antes del elemento.
  - **`node.after(...nodes)`**: Inserta nodos después del elemento.
  - **`node.replaceWith(...nodes)`**: Reemplaza el nodo.
- **Eliminación de nodos**: **`node.remove()`**.
- **Clonación de nodos**: **`elem.cloneNode(true)`** clona un nodo y sus hijos.

#### Ejercicio Resuelto
**Enunciado**: Crea dinámicamente un elemento HTML, modifícalo, reemplázalo por otro, y finalmente elimínalo del DOM.

Script en JavaScript:
```javascript
const contenedor = document.getElementById('contenedor');

// Crear un div con texto
const div = document.createElement('div');
div.textContent = 'Hola Mundo';
contenedor.appendChild(div);

// Reemplazar el div por un span
const span = document.createElement('span');
span.textContent = 'Texto Reemplazado';
div.replaceWith(span);

// Eliminar el span
span.remove();
```
---

### **6. Propiedades de los nodos**
- **`nodeType`**: Indica el tipo de nodo (1 para elementos, 3 para texto, 9 para el documento).
- **`nodeName` y `tagName`**: Devuelven el nombre de la etiqueta (en mayúsculas en HTML).
- **`innerHTML`**: Contenido HTML del elemento.
- **`outerHTML`**: HTML completo del elemento (incluyendo el propio elemento).
- **`textContent`**: Texto dentro del elemento, sin etiquetas HTML.
- **`hidden`**: Oculta el elemento (equivalente a `display: none`).

#### Ejercicio Resuelto
**Enunciado**: Trabaja con las propiedades de un nodo para obtener su contenido y cambiar su texto interno.

Script en JavaScript:
```javascript
const miDiv = document.getElementById('miDiv');

// Obtener y mostrar los valores
console.log('innerHTML:', miDiv.innerHTML);
console.log('outerHTML:', miDiv.outerHTML);
console.log('textContent:', miDiv.textContent);

// Cambiar contenido de texto
miDiv.textContent = 'Nuevo Contenido';
```
---

### **7. Navegación en el DOM**
- **Nodos principales**:
  - **`document.documentElement`**: Nodo `<html>`.
  - **`document.body`**: Nodo `<body>`.
  - **`document.head`**: Nodo `<head>`.
- **Hijos y hermanos**:
  - **`childNodes`**: Todos los nodos hijos (incluyendo texto).
  - **`children`**: Solo los nodos hijos que son elementos.
  - **`firstChild`**, **`lastChild`**, **`nextSibling`**, **`previousSibling`**: Navegación entre nodos.
  - **`parentNode`**: Nodo padre.
  - **`parentElement`**: Nodo padre que es un elemento.

#### Ejercicio Resuelto
**Enunciado**: Usa las propiedades de navegación para acceder a los elementos hijos, hermanos y padre de una lista.

Script en JavaScript:
```javascript
const lista = document.getElementById('lista');

// Obtener el primer y último hijo
console.log('Primer hijo:', lista.firstElementChild.textContent);
console.log('Último hijo:', lista.lastElementChild.textContent);

// Navegar al siguiente y anterior hermano
const segundoItem = lista.children[1];
console.log('Hermano anterior:', segundoItem.previousElementSibling.textContent);
console.log('Hermano siguiente:', segundoItem.nextElementSibling.textContent);

// Mostrar el nodo padre
console.log('Nodo padre:', lista.parentElement.tagName);
```
---

### **8. Colecciones del DOM**
- Las colecciones como `childNodes` son "vivas", es decir, se actualizan automáticamente cuando el DOM cambia.
- No son arrays, pero se pueden convertir con **`Array.from`**.

#### Ejercicio Resuelto
**Enunciado**: Accede a los elementos de una lista, conviértelos en un array, recórrelos y añade un nuevo elemento para comprobar la actualización automática.

Script en JavaScript:
```javascript
const lista = document.getElementsByTagName('ul')[0];

// Obtener todos los elementos li
const items = lista.getElementsByTagName('li');

// Convertir en array y mostrar texto de cada li
Array.from(items).forEach((item, index) => {
  console.log(`Item ${index + 1}:`, item.textContent);
});

// Añadir un nuevo elemento li
const nuevoItem = document.createElement('li');
nuevoItem.textContent = 'Item 3';
lista.appendChild(nuevoItem);

// Verificar actualización automática
console.log('Número de items:', items.length);
```
---

### **9. Tipos de nodos**
- **Elementos**: Nodos que representan etiquetas HTML.
- **Texto**: Nodos que contienen texto.
- **Comentarios**: Nodos que representan comentarios en el HTML.
- **Documento**: El nodo raíz del DOM.

#### Ejercicio Resuelto
**Enunciado**: Identifica el tipo de un nodo, comprueba si es un comentario y muestra su tipo.

Script en JavaScript:
```javascript
const div = document.querySelector('div');

// Identificar el tipo de nodo
const primerHijo = div.firstChild;
console.log('Tipo de nodo:', primerHijo.nodeType);

// Verificar si es un comentario
if (primerHijo.nodeType === 8) {
  console.log('Es un comentario');
} else {
  console.log('No es un comentario');
}
```
---

### **10. Autocorrección del navegador**
- El navegador corrige automáticamente el HTML mal formado al construir el DOM (ejemplo: añade `<tbody>` en las tablas).

#### Ejercicio Resuelto
**Enunciado**: Crea dinámicamente una tabla mal formada y verifica cómo el navegador la corrige automáticamente.

Script en JavaScript:
```javascript
// Crear la tabla mal formada
const tabla = document.createElement('table');
tabla.innerHTML = '<tr><td>Celda 1</td></tr>';
document.body.appendChild(tabla);

// Mostrar contenido de la tabla
console.log('innerHTML de la tabla:', tabla.innerHTML);

// Verificar si el navegador añadió <tbody>
console.log('¿Contiene tbody?:', tabla.querySelector('tbody') !== null);
```
---

### **11. Herramientas de desarrollo**
- **Inspección del DOM**: Usa las herramientas de desarrollador del navegador para inspeccionar y modificar el DOM.
- **Consola**: Puedes interactuar con el DOM desde la consola usando comandos como **`$0`** para referirte al elemento seleccionado.
