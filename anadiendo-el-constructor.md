# Añadiendo el constructor

Ahora añadiremos, antes del get, nuestro constructor:

```
private readonly AppDbContext _context;
        
        public productController(AppDbContext context)
        {
            _context = context;
        }
```

Usar **\_context** en un controlador proporciona una manera eficiente y organizada de acceder y manipular los datos de la base de datos. Al integrar Entity Framework Core y aprovechar la inyección de dependencias, se mejora la mantenibilidad, escalabilidad y testabilidad de la aplicación, lo cual es fundamental para desarrollar aplicaciones web robustas y eficientes.

**1. `private readonly ApplicationDbContext _context;`**

* **`private readonly`**: Declara una variable de instancia privada que no puede ser modificada después de su inicialización. Esto significa que una vez que se asigna un valor a `_context`, no se puede cambiar.
* **`AppDbContext`**: El tipo de la variable `_context`. En este caso, `AppDbContext` es una clase que extiende `DbContext` y representa el contexto de la base de datos para la aplicación.
* El nombre `_context` es descriptivo y proporciona una indicación clara de que se trata de un objeto que representa el contexto de la base de datos.

**2. Constructor `productController(ApplicationDbContext context)`**

* **Constructor**: Un constructor es un método especial que se llama cuando se crea una nueva instancia de la clase. En este caso, el constructor `productController` es el constructor de la clase `ProductController`.
* **Parámetro `ApplicationDbContext context`**: Este constructor recibe una instancia de `ApplicationDbContext` como argumento.
* **Asignación `_context = context;`**: Dentro del constructor, el parámetro `context` se asigna al campo `_context`. Esto significa que la instancia de `AppDbContext` que se pasa al constructor se guarda en la variable `_context` para que pueda ser utilizada por otros métodos de la clase.

### **¿Por qué ponemos dos veces el ApplicationDbContext y context en este código?**

Solo hay una instancia de `AppDbContext`, que se pasa como parámetro en el constructor y se almacena en el campo privado `_context`. La duplicación de nombres (`AppDbContext` y `context`) es simplemente porque se utilizan en diferentes contextos: uno como el tipo de parámetro del constructor y otro como el nombre del parámetro en sí.

Con esta nueva estructura vamos a cambiar nuestro get&#x20;

```
[HttpGet]
        public async Task<ActionResult<List<Product>>> GetAllProduct()
        {
            var categories = await _context.Products.ToListAsync();
            return Ok(categories);
        }
```

* `_context.Product`: `_context` es una instancia del `AppDbContext` que representa el contexto de la base de datos. `Product` es una propiedad de este contexto que corresponde a la tabla de categorías en la base de datos.
* `ToListAsync()`: Este método convierte el resultado de la consulta en una lista (`List<Product>`) de manera asíncrona. Utilizar métodos asíncronos para operaciones de base de datos es una práctica recomendada, ya que evita bloquear el hilo que procesa las solicitudes, mejorando así el rendimiento y la escalabilidad de la aplicación.
* `await`: La palabra clave `await` se utiliza para esperar a que la tarea asíncrona se complete antes de continuar con la ejecución del código. Esto permite que el método libere el hilo mientras espera la finalización de la operación de base de datos, permitiendo que otros trabajos se realicen en paralelo.
