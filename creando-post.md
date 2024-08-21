# Creando Post

Ahora tenemos la necesidad de crear nuestros productos. Por ello lo haremos de la siguiente forma:

```
 [HttpPost]
        public async Task<ActionResult<Product>> CreateProoduct([FromBody]Product product)
        {
            _context.Products.Add(product);
            await _context.SaveChangesAsync();
            return Ok(await _context.Products.FindAsync(product.Id));
        }
```

El atributo `[FromBody]` en el parámetro del método indica que el servidor debe tomar esos datos del cuerpo de la solicitud y convertirlos en un objeto de tipo `Product`

`_context.Products.Add(product)`: Este método agrega la nueva categoría al conjunto de categorías en el contexto de la base de datos (`AppDbContext`). Esto prepara el nuevo objeto para ser insertado en la base de datos, pero aún no se ha realizado la operación de inserción en la base de datos.

`await _context.SaveChangesAsync()`: Este método guarda los cambios pendientes en el contexto de la base de datos de manera asíncrona. Esto incluye la inserción de la nueva categoría en la base de datos. Al utilizar `await`, el método se suspende hasta que la operación de guardar cambios se completa, permitiendo que otros trabajos se realicen en paralelo sin bloquear el hilo actual.

* `await _context.Products.FindAsync(product.Id)`: Este método busca de manera asíncrona la categoría recién creada en la base de datos utilizando su ID. Esto asegura que la categoría que se retorna en la respuesta es la que se acaba de insertar, incluyendo cualquier valor predeterminado que la base de datos haya establecido (como un ID autogenerado).
* `return Ok(...)`: Esto crea una respuesta HTTP 200 OK con el objeto `Product` recién creado como contenido de la respuesta.

Dentro de nuestra documentación de Swagger se vería de la siguiente forma el post

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-04 a las 2.16.35.png" alt=""><figcaption><p>Figura 10- Post Swagger</p></figcaption></figure>

Podemos crear productos y luego lanzar el get y comprobar si sale dentro.



