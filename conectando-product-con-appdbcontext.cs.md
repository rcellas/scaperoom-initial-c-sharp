# Conectando Product con AppDbContext.cs

Ahora ya tenemos nuestra entidad Product en Product.cs pero vamos ha conectarla ahora con nuestro AppDbContext.cs. Para ello añadiremos la siguiente línea:

```
public DbSet<Product.Product> Products { get; set; }
```

El **DbSet** nos permite configurar nuestra tabla y su estructura, pero atraera la información pertinente.&#x20;
