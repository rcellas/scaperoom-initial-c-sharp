# El interior de nuestro proyecto

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-03 a las 23.53.56.png" alt=""><figcaption><p>Figura 3- Proyecto inicial por defecto</p></figcaption></figure>

Dentro de aquí tenemos nuestro proyecto inicial. Vamos a conocer que significan los siguientes archivos

### **Program.cs**

Su función principal consiste en servir como **punto de entrada** para la aplicación, siendo el primer archivo que se ejecuta cuando se inicia la misma.

Las responsabilidades que tiene **Program.cs** son:

**Responsabilidades del Program.cs:**

1. **Configuración de la aplicación:** El archivo Program.cs se encarga de inicializar y configurar diversos aspectos cruciales de la aplicación, como:
   * **Servicios de dependencia:** Registrar y configurar los servicios que la aplicación necesita para funcionar correctamente.
   * **Middleware:** Definir el orden y la configuración del middleware, que son componentes de software que procesan las solicitudes HTTP.
   * **Entorno de ejecución:** Establecer el entorno de ejecución en el que se ejecutará la aplicación, como desarrollo, pruebas o producción.
2. **Creación del host web:** En el caso de aplicaciones ASP.NET Core, Program.cs es responsable de crear el host web, que es el componente que administra el ciclo de vida de la aplicación y maneja las solicitudes HTTP.

La estructura inicial es la siguiente:

<pre class="language-csharp"><code class="lang-csharp"><strong>var builder = WebApplication.CreateBuilder(args);
</strong>
// Add services to the container.
// Learn more about configuring Swagger/OpenAPI at https://aka.ms/aspnetcore/swashbuckle
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();

var summaries = new[]
{
    "Freezing", "Bracing", "Chilly", "Cool", "Mild", "Warm", "Balmy", "Hot", "Sweltering", "Scorching"
};

app.MapGet("/weatherforecast", () =>
    {
        var forecast = Enumerable.Range(1, 5).Select(index =>
                new WeatherForecast
                (
                    DateOnly.FromDateTime(DateTime.Now.AddDays(index)),
                    Random.Shared.Next(-20, 55),
                    summaries[Random.Shared.Next(summaries.Length)]
                ))
            .ToArray();
        return forecast;
    })
    .WithName("GetWeatherForecast")
    .WithOpenApi();

app.Run();

record WeatherForecast(DateOnly Date, int TemperatureC, string? Summary)
{
    public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
}
</code></pre>

#### Palabras clave de Program

**var builder = WebApplication.CreateBuilder(args):**  el término "builder" se refiere a una instancia del objeto `WebApplicationBuilder`. Este objeto se utiliza para configurar y construir una aplicación web. Con él podremos utilizarlo para los servicios.

**var app = builder.Build():** se utiliza para construir la instancia de `WebApplication` después de haber configurado los servicios y middlewares necesarios en el `WebApplicationBuilder`. Esta instancia es la aplicación real que se ejecutará y manejará las solicitudes HTTP.

### **acme-back.http**

Nos sirve para hacer testing de nuestros endpoints y lo veremos de la siguiente forma

```
@acme_back_HostAddress = http://localhost:5197

GET {{acme_back_HostAddress}}/weatherforecast/
Accept: application/json

###

```

### Appsettings.json/ Appsettings.Development.json

Archivo de configuración, como ahora añadir la conexión con nuestra base de datos

### Propierties -> launchSettings.json

Archivo de configuración

### Dependecies

Dependencias que necesita nuestros proyectos de .Net para funcionar

### &#x20;
