# Configurando AppDbContext en Program.cs

En el apartado de los builder.Services vamos a poner la siguiente líneas de código después del :

```
var builder = WebApplication.CreateBuilder(args);
```

```
builder.Services.AddDbContext<ApplicationDBContext>(options =>
{
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection"));
});
```

Esta línea de código se encuentra en un contexto de configuración de servicios en una aplicación [ASP.NET](http://asp.net/) Core utilizando Entity Framework Core para el acceso a datos. Vamos a desglosarla paso a paso:

1. `builder.Services`: Esto indica que se está accediendo al contenedor de servicios de [ASP.NET](http://asp.net/) Core, que se está configurando durante la inicialización de la aplicación.
2. `.AddDbContext<ApplicationDBContext>`: Esto agrega un DbContext al contenedor de servicios. `ApplicationDBContext` es la clase que representa el contexto de la base de datos en la aplicación. Este contexto se utiliza para interactuar con la base de datos utilizando Entity Framework Core.
3. `(options => { ... })`: Aquí se está configurando las opciones para el DbContext. Se está utilizando una expresión lambda para definir estas opciones.
4. `options.UseSqlServer(...)`: Dentro de la configuración de opciones, se está especificando que se utilizará SQL Server como proveedor de base de datos para el DbContext. Esto se hace llamando al método `UseSqlServer` en el objeto `options`.
5. `builder.Configuration.GetConnectionString("DefaultConnection")`: Aquí se está obteniendo la cadena de conexión a la base de datos desde la configuración de la aplicación. La configuración de la cadena de conexión se encuentra en el archivo `appsettings.json` o en otro lugar donde se haya configurado la aplicación.

En resumen, esta línea de código está agregando un DbContext a los servicios de la aplicación [ASP.NET](http://asp.net/) Core, configurándolo para que utilice SQL Server como proveedor de base de datos y proporcionándole la cadena de conexión a la base de datos desde la configuración de la aplicación. Esto permite que la aplicación interactúe con la base de datos utilizando Entity Framework Core.
