# TiendaDeVinilos
## Descripcion general:

El sistema Tienda de Vinilos es una aplicación de consola diseñada para gestionar el catálogo de discos en vinilo disponibles para la venta. El sistema permite cargar vinilos de forma manual o desde archivos CSV, visualizar el catálogo completo y mantener un registro centralizado de los productos.

## Funciones principales:
- Carga manual de vinilos: El usuario puede ingresar datos de un vinilo (álbum, artista, precio) mediante la consola.

- Carga masiva desde archivo CSV: El sistema puede importar múltiples vinilos desde archivos CSV, facilitando la actualización y ampliación del catálogo.

- Visualización del catálogo: Se muestra al usuario la lista completa de vinilos disponibles en la tienda, con detalles claros.
## Patrones aplicados:
### Singleton (Clase Tienda)
#### Justificacion:

- Control de acceso a recurso único: Solo debe existir una instancia de la tienda que maneje el catálogo de vinilos, evitando inconsistencias o datos duplicados.

- Estado global compartido: Facilita el acceso centralizado al catálogo, ya que múltiples partes del programa (como la carga CSV o el menú de visualización) deben trabajar sobre el mismo conjunto de datos.
---
### Adapter (Clase ViniloAdapter2)
#### Justificacion:

- Abstracción de fuente de datos: El adaptador “adapta” la lectura del CSV a los objetos Vinilo del sistema, desacoplando la lógica de lectura del formato del archivo de la lógica del negocio.
---
### Iterator (Clase ViniloIterator)
#### Justificacion:

- Separación de la estructura y la iteración: Permite recorrer la lista de vinilos sin exponer su representación interna (por ejemplo, si decides cambiar la lista por otro tipo de colección).

- Uniformidad en recorrido: El mismo patrón puede usarse para recorrer cualquier colección en la tienda, no solo listas, manteniendo una interfaz común.
---
### Prototype (Clase Vinilo)
#### Justificacion:

- Clonación eficiente de objetos: Permite crear copias de objetos Vinilo existentes sin necesidad de construirlos desde cero (construcción costosa o compleja).

- Facilita modificaciones independientes: Puedes clonar un vinilo base y luego cambiar algunos atributos sin afectar el original (ideal si quieres replicar un vinilo y modificar solo algunos detalles, p.ej. precio o edición especial).

- Reduce dependencia del constructor: Evita el uso repetido de constructores con múltiples parámetros, que pueden ser propensos a errores o cambios frecuentes.

- Útil para prototipos cargados desde CSV: Si necesitas crear múltiples instancias similares o basadas en plantillas, usar clone() acelera la creación y mantiene la coherencia.

