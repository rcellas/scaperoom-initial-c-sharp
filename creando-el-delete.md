# Creando el delete

Por último tenemos haremos el delete

```
[HttpDelete("{id:int}")]
        public async Task<ActionResult> DeleteProduct(int id)
        {
            var product = await _context.Products.FindAsync(id);
            if ( product == null)
            {
                return NotFound();
            }
            _context.Products.Remove(product);
            await _context.SaveChangesAsync();
            return NoContent();
        }
```

`await _context.Products.FindAsync(id)`: Busca asíncronamente la categoría con el ID especificado en la base de datos. Si se encuentra, la variable `product` contendrá la categoría; de lo contrario, será `null`.

Si `product` es `null`, significa que no se encontró una categoría con el ID proporcionado. En este caso, se devuelve una respuesta HTTP 404 Not Found, indicando que no se encontró el recurso a eliminar.

`_context.Products.Remove(product)`: Marca la categoría para ser eliminada del contexto de la base de datos. Esta acción prepara la categoría para su eliminación.

`await _context.SaveChangesAsync()`: Guarda los cambios en la base de datos de manera asíncrona. Esta operación elimina realmente la categoría de la base de datos.

`return NoContent()`: Devuelve una respuesta HTTP 204 No Content. Esto indica que la eliminación se realizó correctamente, pero no hay contenido que devolver en la respuesta.

