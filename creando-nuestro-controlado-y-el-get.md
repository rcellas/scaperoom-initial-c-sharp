# Creando nuestro controlado y el get

Para crear nuestro controlador dentro del proyecto lo que haremos es ir dentro de nuestra carpeta Product, click derecho→add→scaffolded item…→Api Controller-Empty

Una vez seleccionado la parte de Api escribiremos el nombre del controlador, en este caso productController.

Al generar el archivo nos encontraremos con algo similar a esto

```
using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;

namespace acme_crm.Category
{
    [Route("api/[controller]")]
    [ApiController]
    public class productController : ControllerBase
    {
    }
}

```

El controller es quien se encarga de recibir lo que pide el usuario, procesarlo y devolver una respuesta adecuada. Aquí es donde procesaremos la parte del CRUD.

Comenzaremos con la parte del get.

```
[HttpGet]
        public async Task<IActionResult> GetAllProducts()
        {
            var products = new List<Product>
            {
                new Product
                {
                    Id = 1,
                    Name = "Product 1",
                    Description = "Description 1"
                }
            };
            return Ok(products);
        }
```

* **\[HttpGet]**:
  * Esta línea es un **atributo** que indica que este método responderá a las solicitudes HTTP GET. En una API, esto significa que el método se usará para obtener información.
* **public async Task\<IActionResult> GetAllProducts()**:
  * `public`: El método es accesible desde otras partes de la aplicación.
  * `async`: El método es asíncrono, lo que significa que puede realizar operaciones que podrían tomar tiempo (como acceder a una base de datos) sin bloquear el hilo de ejecución principal.
  * `Task<IActionResult>`: Indica que el método devuelve una tarea (`Task`) que produce una acción resultado (`IActionResult`). `IActionResult` es una interfaz que representa el resultado de una acción del controlador y puede ser usado para devolver diferentes tipos de respuestas HTTP.



