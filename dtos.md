# DTO's

Al trabajar con Web Apis no se recomienda exponer la entidades que nosotros usamos dentro de nuestra aplicación al resto de personas. Ni datos de entrada o salida.

También lo que hacemos, tal y como esta la api actual, es que el usuario haga peticiones incorrectas como ahora la posibilidad de enviar una id mayor a 0. Esto es nombrado over posting. Para hacer una simulación de este caso vamos a acudir a nuestro post y vamos a crear el siguiente usuario.

```
{
  "id": 546,
  "name": "test 2",
  "description": "string"
}
```

Al intentar hacer el post nos remitirá el siguiente error

<figure><img src=".gitbook/assets/Captura de pantalla 2024-04-04 a las 1.15.35.png" alt=""><figcaption></figcaption></figure>

Este error lo que nos esta diciendo es que no podemos insertar un valor explicito dentro de nuestra tabla de product , es decir no se pudo enviar nuestro id ya que es automático provocando este error.

A parte el usuario no debería tener acceso a poner la id que el quisiera.

Un DTO, o **Data Transfer Object**, es un patrón de diseño utilizado para transferir datos entre diferentes partes de una aplicación, especialmente entre la capa de presentación y la capa de negocio o entre diferentes servicios. Los DTOs son objetos simples que no contienen lógica de negocio, sino que solo almacenan datos.

El dto cumple dos partes de SOLID

* El **Principio de Responsabilidad Única (Single Responsibility Principle, SRP)**
* El **Principio de Segregación de Interfaces (Interface Segregation Principle, ISP).**

Para ello, lo que haremos es crear dentro de nuestra carpeta Product el archivo ProductDTO. Dentro de él, le vamos a poner lo siguiente:

```
namespace acme_back.Product;

public class ProductDto
{
    public int Id { get; set; }
    public string Name { get; set; } = null!;
    public string Description { get; set; }= null!;
}
```

Y también creamos el CreateProductDto, que nos servirá tanto para el create como para el update:

```
namespace acme_back.Product;

public class CreateProductDto
{
    public string Name { get; set; } = null!;
    public string Description { get; set; }= null!;
}
```

### **¿Por qué no ponemos el Id dentro del dto?**

* **Minimizar la Exposición de Datos**:
  * **Seguridad y Privacidad**: En algunas situaciones, puede ser importante no exponer el `Id` (u otros identificadores) a los clientes, especialmente si estos datos podrían ser sensibles o explotados.
  * **Control de Información**: Puedes controlar exactamente qué información se transfiere entre las capas de tu aplicación, evitando exponer detalles internos de la implementación.
* **Relevancia del Contexto**:
  * **Propósito Específico**: El DTO está diseñado para un propósito específico y, en ese contexto, el `Id` puede no ser relevante. Por ejemplo, si solo necesitas mostrar el nombre de la categoría en una lista desplegable, el `Id` puede no ser necesario.
  * **Simplicidad**: Simplificar el DTO solo a las propiedades necesarias para la operación específica hace que el objeto sea más fácil de manejar y entender.
* **Diseño Orientado a la Vista**:
  * **Adaptación a la Vista**: El DTO se adapta a los requerimientos de una vista específica en una interfaz de usuario. Si la vista no necesita el `Id`, no tiene sentido incluirlo en el DTO.
  * **UX y UI**: Focalizarse en la experiencia del usuario y la interfaz puede implicar la eliminación de datos innecesarios que podrían distraer o confundir al usuario.
