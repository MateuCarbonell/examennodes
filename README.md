¡Claro! Aquí tienes el contenido formateado de manera clara y organizada:

---

### **1. Atributos y Propiedades DOM**
- **Atributos HTML**: Son lo que está escrito en el HTML. Se acceden con métodos como `getAttribute`, `setAttribute`, `hasAttribute`, y `removeAttribute`.
- **Propiedades DOM**: Son las propiedades de los objetos JavaScript que representan los nodos del DOM. No siempre coinciden con los atributos HTML.
- **Sincronización**: Cambiar un atributo estándar actualiza la propiedad correspondiente, pero no siempre viceversa (ejemplo: `input.value`).
<input id="miInput" type="text" value="Hola">
<script>
  const input = document.getElementById("miInput");

  // Atributos HTML
  console.log(input.getAttribute("value")); // "Hola"
  input.setAttribute("value", "Mundo");
  console.log(input.getAttribute("value")); // "Mundo"

  // Propiedades DOM
  console.log(input.value); // "Mundo"
  input.value = "Nuevo Texto";
  console.log(input.value); // "Nuevo Texto"
</script>



---

### **2. Métodos para trabajar con atributos**
- **`elem.hasAttribute(name)`**: Verifica si existe un atributo.
- **`elem.getAttribute(name)`**: Obtiene el valor de un atributo.
- **`elem.setAttribute(name, value)`**: Establece un valor para un atributo.
- **`elem.removeAttribute(name)`**: Elimina un atributo.
- **`elem.attributes`**: Colección de todos los atributos.
<div id="miDiv" class="contenedor" data-info="123"></div>
<script>
  const div = document.getElementById("miDiv");

  // Verificar atributo
  console.log(div.hasAttribute("class")); // true

  // Obtener atributo
  console.log(div.getAttribute("data-info")); // "123"

  // Establecer atributo
  div.setAttribute("data-info", "456");
  console.log(div.getAttribute("data-info")); // "456"

  // Eliminar atributo
  div.removeAttribute("class");
  console.log(div.hasAttribute("class")); // false

  // Colección de atributos
  console.log(div.attributes);
</script>

---

### **3. Propiedades DOM**
- Las propiedades DOM pueden ser de cualquier tipo (string, boolean, objeto, etc.).
- **Ejemplos**:
  - `input.checked` es un booleano.
  - `elem.style` es un objeto CSS.
  - `href` en un enlace siempre es una URL completa.
    
<input type="checkbox" id="miCheckbox">
<script>
  const checkbox = document.getElementById("miCheckbox");

  // Propiedad booleana
  checkbox.checked = true;
  console.log(checkbox.checked); // true

  // Objeto CSS
  checkbox.style.color = "red";
  console.log(checkbox.style.color); // "red"
</script>

---

### **4. Atributos no estándar y `dataset`**
- Los atributos no estándar son útiles para pasar datos personalizados de HTML a JavaScript.
- Para evitar conflictos con futuros estándares, se usan atributos `data-*`, accesibles a través de `elem.dataset`.
  
<div id="miElemento" data-user-id="789" data-role="admin"></div>
<script>
  const elemento = document.getElementById("miElemento");

  // Leer `dataset`
  console.log(elemento.dataset.userId); // "789"
  console.log(elemento.dataset.role); // "admin"

  // Modificar `dataset`
  elemento.dataset.role = "editor";
  console.log(elemento.dataset.role); // "editor"
</script>

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
-   
<div id="contenedor"></div>
<script>
  const contenedor = document.getElementById("contenedor");

  // Crear elemento
  const nuevoDiv = document.createElement("div");
  nuevoDiv.textContent = "Hola Mundo";

  // Insertar elemento
  contenedor.append(nuevoDiv);

  // Reemplazar
  const reemplazo = document.createElement("span");
  reemplazo.textContent = "Nuevo Texto";
  nuevoDiv.replaceWith(reemplazo);

  // Eliminar
  reemplazo.remove();
</script>

---

### **6. Propiedades de los nodos**
- **`nodeType`**: Indica el tipo de nodo (1 para elementos, 3 para texto, 9 para el documento).
- **`nodeName` y `tagName`**: Devuelven el nombre de la etiqueta (en mayúsculas en HTML).
- **`innerHTML`**: Contenido HTML del elemento.
- **`outerHTML`**: HTML completo del elemento (incluyendo el propio elemento).
- **`textContent`**: Texto dentro del elemento, sin etiquetas HTML.
- **`hidden`**: Oculta el elemento (equivalente a `display: none`).
<div id="miDiv">Texto <span>adicional</span></div>
<script>
  const div = document.getElementById("miDiv");

  console.log(div.nodeType); // 1 (Elemento)
  console.log(div.nodeName); // "DIV"
  console.log(div.tagName); // "DIV"

  console.log(div.innerHTML); // "Texto <span>adicional</span>"
  console.log(div.textContent); // "Texto adicional"
</script>

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
<ul id="lista">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
<script>
  const lista = document.getElementById("lista");

  console.log(lista.children); // HTMLCollection de <li>
  console.log(lista.firstChild); // Nodo de texto (espacio en blanco)
  console.log(lista.firstElementChild); // Primer <li>
  console.log(lista.lastElementChild); // Último <li>
</script>


---

### **8. Colecciones del DOM**
- Las colecciones como `childNodes` son "vivas", es decir, se actualizan automáticamente cuando el DOM cambia.
- No son arrays, pero se pueden convertir con **`Array.from`**.
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
<script>
  const items = document.getElementsByTagName("li");

  console.log(items.length); // 2

  // Convertir a array
  const arrayItems = Array.from(items);
  arrayItems.forEach(item => console.log(item.textContent));
</script>

---

### **9. Tipos de nodos**
- **Elementos**: Nodos que representan etiquetas HTML.
- **Texto**: Nodos que contienen texto.
- **Comentarios**: Nodos que representan comentarios en el HTML.
- **Documento**: El nodo raíz del DOM.
<div><!-- Un comentario --></div>
<script>
  const div = document.querySelector("div");

  console.log(div.nodeType); // 1 (Elemento)
  console.log(div.firstChild.nodeType); // 8 (Comentario)
</script>

---

### **10. Autocorrección del navegador**
- El navegador corrige automáticamente el HTML mal formado al construir el DOM (ejemplo: añade `<tbody>` en las tablas).
  

---

### **11. Herramientas de desarrollo**
- **Inspección del DOM**: Usa las herramientas de desarrollador del navegador para inspeccionar y modificar el DOM.
- **Consola**: Puedes interactuar con el DOM desde la consola usando comandos como **`$0`** para referirte al elemento seleccionado.
- 
$0.textContent = "Texto Modificado";


---

### **12. Métodos de búsqueda en el DOM**
- **`document.getElementById(id)`**: Busca un elemento por su `id`.
- **`querySelector(css)`**: Devuelve el **primer elemento** que coincide con el selector CSS.
- **`querySelectorAll(css)`**: Devuelve **todos los elementos** que coinciden con el selector CSS.
- **`elem.matches(css)`**: Comprueba si el elemento coincide con el selector CSS.
- **`elem.closest(css)`**: Busca el **ancestro más cercano** que coincide con el selector CSS.
- **Métodos antiguos**:
  - **`getElementsByTagName(tag)`**: Busca elementos por etiqueta.
  - **`getElementsByClassName(className)`**: Busca elementos por clase.
  - **`getElementsByName(name)`**: Busca elementos por el atributo `name`.
<div id="miDiv" class="contenedor"></div>
<script>
  const divById = document.getElementById("miDiv");
  const divByClass = document.querySelector(".contenedor");
  const allDivs = document.querySelectorAll("div");

  console.log(divById); // <div id="miDiv" class="contenedor">
  console.log(divByClass); // <div id="miDiv" class="contenedor">
  console.log(allDivs); // NodeList de todos los div
</script>

---

### **Resumen rápido para el examen:**
1. **Atributos vs Propiedades**: Atributos son lo que está en el HTML, propiedades son lo que está en el DOM.
2. **Métodos clave**: `getAttribute`, `setAttribute`, `append`, `remove`, `cloneNode`.
3. **Propiedades clave**: `innerHTML`, `outerHTML`, `textContent`, `nodeType`, `nodeName`.
4. **Navegación**: `childNodes`, `children`, `parentNode`, `nextSibling`, `previousSibling`.
5. **Tipos de nodos**: Elementos, texto, comentarios, documento.
6. **Métodos de búsqueda**: `getElementById`, `querySelector`, `querySelectorAll`, `matches`, `closest`.
7. **Colecciones**: Vivas (`getElementsBy*`) vs estáticas (`querySelectorAll`).

---

¡Con esto deberías tener toda la información organizada y lista para tu examen! 🚀


