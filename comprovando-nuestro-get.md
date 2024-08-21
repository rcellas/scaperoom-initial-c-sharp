# Comprovando nuestro get

¿Cómo podemos ver las peticiones de nuestro controller?

Lo podemos hacer de diferentes formas:

1. Swagger

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-04 a las 2.02.42.png" alt=""><figcaption><p>Figura 9- Swagger</p></figcaption></figure>

2. Archivo http

```csharp
@testingnet_HostAddress = <http://localhost:5009>

GET {{testingnet_HostAddress}}/api/product
Accept: application/json
```

