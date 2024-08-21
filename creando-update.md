# Creando Update

Ahora creamos las updates

```
[HttpPut("{id:int}")]
        public async Task<ActionResult> UpdateProduct(int id, [FromBody]Product product)
        {
            if (id != product.Id)
            {
                return BadRequest();
            }
            _context.Entry(product).State = EntityState.Modified;
            await _context.SaveChangesAsync();
            return NoContent();
        }
```

* Esta verificación asegura que el ID de la categoría que se está actualizando coincide con el ID proporcionado en la URL. Si no coinciden, devuelve una respuesta HTTP 400 Bad Request.
* `_context.Entry(product).State = EntityState.Modified`: Esto le dice a Entity Framework que la entidad `product` ha sido modificada y que debe actualizarse en la base de datos.
* `await _context.SaveChangesAsync()`: Guarda los cambios en la base de datos de manera asíncrona. Esta operación puede tardar un poco, por lo que se hace de manera asíncrona para no bloquear el hilo actual.
* `return NoContent()`: Devuelve una respuesta HTTP 204 No Content. Esto indica que la actualización se realizó correctamente, pero no hay contenido que devolver en la respuesta.
