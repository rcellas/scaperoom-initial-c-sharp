# Migrar nuestra Entidad Producto

Iremos a la terminal y comprobamos a que altura estamos de nuestro proyecto.

Para hacer la migración haremos el siguiente comando

```csharp
dotnet ef migrations add Product
```

**Si sale el siguiente error**

An error occurred while accessing the Microsoft.Extensions.Hosting services. Continuing without the application service provider. Error: 'AddDbContext' was called with configuration, but the context type 'ApplicationDbContext' only declares a parameterless constructor. This means that the configuration passed to 'AddDbContext' will never be used. If configuration is passed to 'AddDbContext', then 'ApplicationDbContext' should declare a constructor that accepts a DbContextOptions and must pass it to the base constructor for DbContext.

Comprueba tienes bien escrito el AppDbContext de la forma que los hemos puesto en el punto de [Conectando Product con AppDbContext.cs](creando-el-appdbcontext.md)

Veremos que en nuestro proyecto se ha creado una nueva carpeta llamada Migrations. Veremos dos archivos. El primero refleja nuestra entidad y el segundo es un archivo de historial de migraciones.

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-04 a las 1.28.41.png" alt=""><figcaption><p>Figura 8- Migraciones</p></figcaption></figure>

Ahora iremos a ver que tenemos dentro del archivo que nos a realizado cuando hemos hecho la migración de nuestro modelo de bases de datos de product.

Por una parte vamos a tener la función Up, representa los cambios que vamos a realizar dentro de nuestra base de datos.

```
protected override void Up(MigrationBuilder migrationBuilder)
        {
            migrationBuilder.CreateTable(
                name: "Products",
                columns: table => new
                {
                    Id = table.Column<int>(type: "int", nullable: false)
                        .Annotation("SqlServer:Identity", "1, 1"),
                    Name = table.Column<string>(type: "nvarchar(max)", nullable: false),
                    Description = table.Column<string>(type: "nvarchar(max)", nullable: false)
                },
                constraints: table =>
                {
                    table.PrimaryKey("PK_Products", x => x.Id);
                });
        }
```

Lo que vemos aquí es:

* **migrationBuilder.CreateTable ->** creación de la tabla
* **Name ->** nombre de la tabla
* **Columns ->** contenido que llevarán las tablas y el como serán
* **Contrains ->** cual será su PK

Para que esto se vea reflajado en nuestra bd, lo que haremos es hacer el siguiente comando

```
dotnet ef database update 
```

