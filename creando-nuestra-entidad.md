# Creando nuestra Entidad

Dentro de nuestro proyecto vamos a crear una carpeta llamada Product. Para hacerlo dentro de Rider lo haremos hacíendo click derecho al proyecto -> add-> Directory

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-04 a las 0.28.58.png" alt=""><figcaption><p>Figura 5</p></figcaption></figure>

Dentro de la carpeta vamos a crear una entidad llamada Product&#x20;

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-04 a las 0.29.23.png" alt=""><figcaption><p>Figura 6</p></figcaption></figure>

Para crear nuestra entidad seleccionaremos la opción de class.

<figure><img src=".gitbook/assets/Captura de pantalla 2024-06-04 a las 0.29.46.png" alt=""><figcaption><p>figura 7</p></figcaption></figure>

Las **entidades** son la r**epresentación de un objeto o concepto del mundo real** que se describe en una base de datos.

Dentro de nuestra entidad pondremos el ID, Name y Description

La entidad se debe ver de la siguiente forma

```
namespace acme_back.Product;

public class Product
{
    public int Id { get; set; }
    public string Name { get; set; } = null!;
    public string Description { get; set; }= null!;
}
```
