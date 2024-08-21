# Configurando nuestras entidades

Dentro de Entity Core, tenemos diferentes formas de configurar nuestras tablas.

1. Por convención: si por ejemplo nosotros llamamos Id a nuestra PK, el propio sistema entendera que eso hará esa función correspondiente dentro de nuestra migración.
2. Por anotaciones de datos: són un conjunto de atributos que podemos usar para realizar configuraciones. Por ejemplo: decirle el nombre de varchar que va a tener.

```
public class Product
{
    public int Id { get; set; }
    
    [StringLength(50)]
    public string Name { get; set; }
    public string Description { get; set; }
}
```

Después de añadir este nuevo cambio, haremos una nueva migración.

```csharp
dotnet ef migrations add NombreConfigurado
```

Le asignamos este nombre para identificar nuestra migración. Lo que veremos dentro de la nueva migración será que nos mostrará que conforme queremos alerterar la columna Name

```
 protected override void Up(MigrationBuilder migrationBuilder)
        {
            migrationBuilder.AlterColumn<string>(
                name: "Name",
                table: "Product",
                type: "nvarchar(50)",
                maxLength: 50,
                nullable: false,
                oldClrType: typeof(string),
                oldType: "nvarchar(max)");
        }
```

3.  Por la Api fuente: es un conjunto de métodos que podemos usar para realizar nuestras entidades. Cabe destacar que esta es una de las herramientas más importantes dentro de Entity Framework Core. Es por ello que si intentáramos algo que no podemos hacer ni por convención, ni por anotación de datos; lo tendríamos que hacer con este.

    Vamos ha usar el mismo ejemplo con el name.

    Antes de nada iremos al archivo de ApplicationsDBContext.cs y pondremos lo siguiente

    ```csharp
        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            //no podemos borrar la llamada a la base, ya que es la que se encarga de crear las tablas
            base.OnModelCreating(modelBuilder);

            modelBuilder.Entity<GenderFilms>().Property(p => p.Name).HasMaxLength(50);
        }

    ```

    Esta linea es lo mismo que hemos puesto antes.

**¿Cuál debemos usar?**

En otras versiones si que había una especificación pertinente. Pero ahora cualquiera de las dos es validad. Si nosotros hiciéramos, lo que se conoce MinimalApi la tercera forma sería la ideal.



