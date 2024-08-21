# Restructurando nuestro controlador con los dto's

Regresamos a nuestro controller y vamos a cambiar nuestro crud.

Primero nuestro get

```
[HttpGet]
        public async Task<ActionResult<List<ProductDto>>> GetAllProduct()
        {
            var products = await _context.Products.ToListAsync();
            return Ok(products);
        }
```

Qué nos esta diciendo las siguiente líneas:

* **\[HttpGet]**:
  * Esta línea es un **atributo** que indica que este método responderá a las solicitudes HTTP GET. En una API, esto significa que el método se usará para obtener información.
*   **public async Task\<ActionResult\<List\<ProductDto>>> GetAllProduct()**:

    * `public`: El método es accesible desde otras partes de la aplicación.
    * `async`: El método es asíncrono, lo que significa que puede realizar operaciones que podrían tomar tiempo (como acceder a una base de datos) sin bloquear el hilo de ejecución principal.
    * `Task<ActionResult<List<ProductDto>>>`: Indica que el método devuelve una tarea (Task) que produce una acción resultado (ActionResult) con una lista de objetos `ProductDto`. `ActionResult` es una clase que representa el resultado de una acción del controlador



Hacemos lo mismo con Create, Update y Delete

#### Create

```
[HttpPost]
        public async Task<ActionResult<ProductDto>> CreateProduct(CreateProductDto createProductDto)
        {
            var product = new Product
            {
                Name = createProductDto.Name
            };
            _context.Products.Add(product);
            await _context.SaveChangesAsync();
            return Ok(product);
        }
```

#### Update

```
[HttpPut("{id:int}")]
        public async Task<ActionResult> UpdateProduct(int id, [FromBody]Category category)
        {
            var product = await _context.Products.FindAsync(id);
            if (product == null)
            {
                return NotFound();
            }
            product.Name = updateProductDto.Name;
            category.Description = updateCategoryDto.Description;
            await _context.SaveChangesAsync();
            return NoContent();
        }
```

#### Delete

```
[HttpDelete("{id:int}")]
        public async Task<ActionResult> DeleteProduct(int id)
        {
            var product = await _context.Productss.FindAsync(id);
            if (product == null)
            {
                return NotFound();
            }
            _context.Products.Remove(product);
            await _context.SaveChangesAsync();
            return NoContent();
        }
```
