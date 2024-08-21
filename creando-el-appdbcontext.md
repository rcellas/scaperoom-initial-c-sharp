# Creando el AppDBContext

Para que toda nuestra data se pueda almacenar en nuestra pase de datos, necesitaremos un lugar donde lo podamos hacer. Por ello necesitaremos un archivo llamado ApplicationDbContext

Pero antes de crear este archivo debemos instalar dos nuget. Cuando hablamos de nuget’s en [asp.net](http://asp.net) no hablamos de comida sino de los paquetes que harán funcionar nuestra aplicación. Esto dentro de nuestro Angular haría referencia a nuestro package de cuando instalamos por ejemplo: bootstrap

Instalaremos los siguientes nugets a través de la terminal

**En caso de esta en visual studio o rider**→ dotnet add package Microsoft.EntityFrameworkCore.Tools --version 8.0.6

**E instalar también el nuget de Sql Server** → dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 8.0.6

Si te has dado cuenta los **NuGet** (no nuggets de pollo),  se refiere a un **administrador de paquetes** indispensable para la gestión de bibliotecas de código reutilizable.

Escogeremos las versiones 8 más actuales, ¿por qué? Porqué actualmente en nuestro SDK lo tendremos a la versión 8. Con la nueva actualización, que se realizará en noviembre, lo que haremos coger los nugets pertinentes al versionado actual.

Después de tener esto instalado crearemos una **nueva carpeta llamada Data** y dentro de ella, **crearemos una clase** llamada : **ApplicationDBContext**

> Si tienes dudas de como crear la carpeta Data y la clase puedes acudir al punto [Creando nuestra Entidad](creando-nuestra-entidad.md)

Dentro de esta nueva clase, al lado de esta clase lo que haremos es llama DbContextOptions y  DBContext (paquete). Este paquete, es uno de los más importantes, puesto que podremos controlar configura la data de nuestra base de datos. Al igual que realizar consultas a otras tablas o Configuraciones.

Quedando el código de la siguiente forma

```
public class AppDbContext(DbContextOptions options) : DbContext(options)
{
    
}
```

#### ¿Qué significa el siguiente código?

`public AppDbContext(DbContextOptions options) : DbContext(options)` define un constructor público para la clase `AppDbContext`. Este constructor toma un único argumento de tipo `DbContextOptions`.

* `DbContextOptions`: Esta es una clase que contiene información de configuración para la conexión a la base de datos, como la cadena de conexión, el proveedor de la base de datos (por ejemplo, SQL Server, MySQL), etc.
* `options`: Este nombre de parámetro representa la instancia de `DbContextOptions` que se pasará al crear un nuevo objeto `AppDbContext`.
* `: DbContext(options)`: Esta parte del constructor llama al constructor de la clase base (`DbContext`) y le pasa el argumento `options`. Esto asegura que la clase base (DbContext) se inicialice correctamente con la información de configuración.

En resumen:

Este código crea una clase llamada `AppDbContext` diseñada específicamente para trabajar con una base de datos. Hereda funcionalidades de la clase `DbContext` y requiere información de configuración (`DbContextOptions`) al crear una nueva instancia. Esta información de configuración especifica cómo conectarse a la base de datos.

