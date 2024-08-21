---
description: Dentro del tutorial se hará con Rider
---

# Creando el proyecto

Al igual que hicimos en el pasado módulo, tendremos nuestro proyecto de pruebas o aprendizajes y luego nuestro proyectos formativos.

Por ello crearemos la api de nuestro proyecto de CRM.

Lo primero que haremos es crear nuestra **Solution** y **Project**

#### Solution/ Solución

* Una solución es un contenedor lógico que agrupa uno o más proyectos relacionados.
* Se utiliza para organizar proyectos que forman parte de una misma aplicación o sistema web complejo.
* La solución no contiene código en sí misma, sino que sirve como referencia a los proyectos que la componen.
* Permite gestionar las dependencias entre proyectos, compartir configuraciones y establecer propiedades generales para la aplicación.

#### Project/ Proyecto

* Un proyecto es la unidad básica de desarrollo en ASP.NET.
* Contiene el código fuente, los recursos y las configuraciones específicas de una parte de la aplicación web.
* Puede contener archivos de código C#, archivos HTML, CSS, JavaScript, imágenes y otros recursos necesarios para desarrollar la funcionalidad de la aplicación.
* Los proyectos pueden ser independientes o formar parte de una solución.

Para crearlo abriremos Rider y nos pondrá nuestro últimos proyectos, pero nos centraremos en el apartado de la Fg-1

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-03 a las 23.34.42.png" alt=""><figcaption><p>Figura 1- Menú inicial de Rider</p></figcaption></figure>

Aquí nos encontraremos para crear una nueva solución o abrir una solución (en caso de que no este dentro del panel de abajo). Le damos a **New Solution** y nos abrirá algo tal que así

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-04 a las 0.04.24.png" alt=""><figcaption></figcaption></figure>

Dentro de la creación de nuevos proyecto podremos seleccionar el tipo de proyecto (Console, Class Library, Web, Service ...), que en nuestro caso será web.

En su interior podremos el nombre de la solución (acme-crm-back) y en este caso debe coincidir con el mismo de projecto. Esto ya lo hará de forma automatica el propio Rider.&#x20;

Si necesitaramos un nombre diferente entre solución y proyecto, lo único que deberíamos hacer es escribir el nombre escogido.

Después ubicamos el proyecto donde lo queremos.

> Al estar usando rider ya no tendremos que crear una carpeta especifica para el proyecto

Le damos a Create Git Repository

Dejamos el target Framework y Language que nos viene por defecto

Y en template usaremos el Web Api

Para finalizar le daremos a create
