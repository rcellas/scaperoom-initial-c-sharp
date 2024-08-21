# Añadiendo nuestra base de datos en appsettings.Development.json

Una vez tenemos creada nuestra base de datos sql para el proyecto, haremos la configuración de nuestra base de datos dentro del proyecto.

Acudiremos al archivo appsettings.Development.json y pondremos lo siguiente antes del "Logging":

```
"ConnectionStrings": {
    "DefaultConnection": "Server=localhost,1433;Database=Acme;User=sa;Password=Root1234;TrustServerCertificate=True"
  },
```

**1. "ConnectionStrings":**

* Esta es una clave dentro del archivo de configuración que sirve como encabezado de sección. Identifica un bloque de configuraciones relacionadas con las cadenas de conexión.

2. **"DefaultConnection":**
   * Esta es otra clave dentro de la sección `"ConnectionStrings"`. Actúa como un nombre o alias para una cadena de conexión específica. "DefaultConnection" es una convención común que se usa para la conexión principal a la base de datos en una aplicación.
3. **Server=localhost,1433;Database=acme;User=sa;Password=Root1234;TrustServerCertificate=True**

* Este es el valor asociado con la clave `"DefaultConnection"`. Es una cadena separada por punto y coma que contiene los detalles necesarios para conectarse a un servidor de base de datos. A continuación, se muestra un desglose de las partes individuales:
  * `Server=localhost,1433`: Especifica la dirección (localhost) y el puerto (1433, que es un puerto predeterminado común para SQL Server) del servidor de base de datos.
  * `Database=acme`: Indica el nombre de la base de datos a la que desea conectarse (acme en este caso).
  * `User=sa`: Define el nombre de usuario para conectarse al servidor de base de datos (sa en este ejemplo).
  * `Password=Root1234`: Establece la contraseña para el nombre de usuario especificado (Root1234 aquí). **Es importante evitar almacenar información confidencial como contraseñas directamente en el código o en los archivos de configuración. Considere usar métodos más seguros para administrar las credenciales.**
  * `TrustServerCertificate=True`: Instruye a la aplicación a confiar en el certificado SSL del servidor (no recomendado para entornos de producción debido a problemas de seguridad).

Este fragmento de código define una cadena de conexión llamada `"DefaultConnection"` dentro del archivo de configuración. Esta cadena de conexión contiene la información necesaria para que su aplicación se conecte a un servidor de base de datos y una base de datos específicos.



> **Nota importante:** Almacenar contraseñas directamente en archivos de configuración no es una práctica segura.

Nos tendrá que quedar algo similar a esto

```
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost,1433;Database=acme;User=sa;Password=Root1234;TrustServerCertificate=True"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}

```
